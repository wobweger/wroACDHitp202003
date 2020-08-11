# Workflow Arthur Schnitzler Briefe

This workflow describes step performed to convert letter index into CMIF format.
Utilized tools:

+ [Transkribus](https://transkribus.eu/Transkribus/#)
+ [OpenRefine](https://openrefine.org/)
+ [VS code](https://code.visualstudio.com/)
+ python ([Jupyter](https://jupyter.org/) Notebooks)

|step   | comment |
|---    |---|
|       |![OpenRefine](./v_img/transkribus_20200716_00.png)|
|       |regions defined manually|
|       |![OpenRefine](./v_img/transkribus_20200716_10.png)|
|       |line detection automatically|
|       |text recognition|
|       |![OpenRefine](./v_img/20200804_00_Transkribus_50.png)|
|       |export document as simple text |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_00.png)|
|       |[OpenRefine](https://openrefine.org/) is free to download and use |
|       |it's a java web server (currently java8) |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_01.png)|
|       |launch OpenRefine in your shell |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_02.png)|
|       |web service is ready on your local machine at port 3333 |
|       |browser FireFox and Chrome will do |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_03.png)|
|       |browse your input file |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_03a.png)|
|       |left is original scanned |
|       |right is transkribus output, simple text format |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_03b.png)|
|       |click `Next` |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_03c.png)|
|       |adjust import option, I left defaults |
|       |click `Create Project >>`|
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_03e.png)|
|       |now your project is started |
|       |apply operations to shape your data|
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_04.png)|
|       |if you had done so previously, it's possible to apply operations again|
|       | assuming you preserved those operations|
|       |open `Undo/Redo`|
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_05.png)|
|       |copy previous operations to reapply|
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_06.png)|
|       |paste previous action in and `Perform Operations`|
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_08.png)|
|       |notice result |
|       |data is shaped as before |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_11.png)|
|       |OpenRefine allows edit |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_14.png)|
|       |OCR recognition isn't error free |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_15.png)|
|       |edit manually |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_16.png)|
|       |edition uses `[` `]` to flag uncertain data, human readable dates may be converted into more machine friendly form |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_17.png)|
|       |use a human to bring sense into data |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_18.png)|
|       |OCR led to year `190` which is way off |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_19.png)|
|       |when you are done, export data as json using templating |
|       |![OpenRefine](./v_img/20200804_01_OpenRefine_20.png)|
|       |at this step, defaults are good |

## Jupyter Notebooks

We finish basic conversion, now it would be good to
validate your work before going further.
A high level programming language may be useful.
I personally like python very much, in conjunction
with jupyter notebook it's even more simple to perform
an infrequent used workflow. Notes help to explain what is
going on and debugging is also simple.

on CentOS 8 adding package looks like following:

```shell
pip3 install jupyterlab
```

after package has been installed

```shell
jupyter notebook
```

will launch [jupyter](http://localhost:8888/) web service at your local machine.

`validateDates.ipynb` reshapes json created by OpenRefine.
Names spanning over multiple lines are combined into 1 and dates listed are
validated, a chronological order is assumed.

|step   | comment |
|---    |---|
|       |![OpenRefine](./v_img/20200804_02_JupyterNoteBook_02.png)|
|       | |
|       |![OpenRefine](./v_img/20200804_02_JupyterNoteBook_00.png)|
|       |easy installation using `pip`, `pip3` for python 3.x |
|       |![OpenRefine](./v_img/20200804_02_JupyterNoteBook_02.png)|
|       |navigate to a path (repo) and launch jupyter notebook|
|       |enter in your shell `jupyter notebook`|
|       |![OpenRefine](./v_img/20200804_02_JupyterNoteBook_03.png)|
|       |navigate to notebook, `D_dbs/3_py/validateDates.ipynb` |
|       |run each step (click play button in toolbar) |
|       |jumping is also possible and permitted|
|       |at step `In [7]` output file is generated|
|       |![OpenRefine](./v_img/20200805_02_JupyterNoteBook_05.png)|
|       |check output file with your editor of choice|
|       |![vscode](./v_img/20200805_03_vscode_00.png)|
|       |you may want to reshape json file (optional) |
|       |![vscode](./v_img/20200805_03_vscode_01.png)|
|       |extension `Beautify` generate a nice looking json |
|       |open context menu and pick `Format Document`|
|       |![vscode](./v_img/20200805_03_vscode_02.png)|
|       |result is much more human friendly |



## validateDates

on OCR text recognition might not be error free.
you take a glance to transkribus result and all looks good.
nevertheless a sematic check on result is useful.

**our data is a index form a book**
it starts with names (receiver of letter) in maybe multiple lines,
followed by dates, which are sorted, from older to newer.

```text
Friedmann, Ernst
13. 9. 1912
Friese, Carl
13. 2. 1907
20. 2. 1907
Fulda, Ludwig
28. 11. 1898
28. 12. 1898
4. 1. 1899
10. 3. 1890
25. 4. 1899
20. 6. 1900
23. 6. 1900
7. 7. 1900
17. 1. 1901
22. 3. 1901
8. 6. 1901
23. 7. 1904
25. 8. 1904
Glümer, Marie
Sommer 1889
4. 8. 1889
5. 8. 1889
```

with OpenRefine, a json was created

```json
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1898-12-28",
    "date_text": "28. 12. 1898",
    "uncertain": false
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1899-01-04",
    "date_text": "4. 1. 1899",
    "uncertain": false,
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1890-03-10",
    "date_text": "10. 3. 1890",
    "uncertain": false,
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1899-04-25",
    "date_text": "25. 4. 1899",
    "uncertain": false
}, {
```

only a focused sight at this data, text or refined data, will reveal recognition error
at `10. 3. 1890` (1890-03-10), seen in context, it is supposed to be `10. 3. 1899`;
however we don't want to replace humans, so it's up to a human to decide.

**goal** of this notebook is to find suspicious dates, out of order dates.
if a newer date was present in previous line, one of those two is properly
wrong.

```json
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1898-12-28",
    "date_text": "28. 12. 1898",
    "uncertain": false
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1899-01-04",
    "date_text": "4. 1. 1899",
    "uncertain": false,
    "suspicious": "true"
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1890-03-10",
    "date_text": "10. 3. 1890",
    "uncertain": false,
    "suspicious": "true"
}, {
    "recv": "Fulda, Ludwig",
    "date_when": "1899-04-25",
    "date_text": "25. 4. 1899",
    "uncertain": false
}, {
```

## CMIF

at this point we successfully shaped text input into a table,
manually corrected errors, generated a json representation
and validated dates. now we'd like to get a CMIF json file.

|step   | comment |
|---    |---|
|       |![OpenRefine](./v_img/20200805_02_JupyterNoteBook_05.png)|
|       | |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_00.png)|
|       |click `Open ...`  |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_01.png)|
|       |click `Browse` |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_02.png)|
|       |find your file |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_03.png)|
|       |click `Next >>` |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_04.png)|
|       |pick row |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_05.png)|
|       |`Create Project >>` |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_07.png)|
|       |find suspicious values now |
|       |correct those accordingly|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_08.png)|
|       |when all is good |
|       |export using `Templating ...` again|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_09.png)|
|       |defaults need to be adjusted |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_10.png)|
|       |copy previously researched json format in |
|       |prefix section |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_11.png)|
|       |row template section |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_12.png)|
|       |suffix section |
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_13.png)|
|       |note preview from time to time|
|       |if you are happy click `Export`|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_14.png)|
|       |do remember filename|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_15.png)|
|       |locate exported file|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_16.png)|
|       |move it to repo|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_17.png)|
|       |give appropriate name|
|       |![OpenRefine](./v_img/20200805_04_OpenRefine_18.png)|
|       |use your text editor to take a look|

now we are almost there.
just open [CMIF Creator](https://correspsearch.net/creator/index.xql?l=en)

|step   | comment |
|---    |---|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_00.png)|
|       |navigate to CMIF Creator|
|       |browse file|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_01.png)|
|       |pick CMIF json (or xml) file|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_02.png)|
|       |inspect data|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_03.png)|
|       |inspect data|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_04.png)|
|       |complete GND information|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_05.png)|
|       |make your choice on GND information|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_06.png)|
|       |GND has been updated|
|       |![CMIF Creator](./v_img/20200805_05_CMIFcreator_07.png)|
|       |all entries with identical receiver has been updated as well|
