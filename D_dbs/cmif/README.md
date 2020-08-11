
### correspSearch

+ [correspDesc](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-correspDesc.html)
+ [correspAction](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-correspAction.html)
+ [github](https://github.com/TEI-Correspondence-SIG/correspDesc)
+ [CMIF](https://github.com/TEI-Correspondence-SIG/CMIF) Correspondence Metadata Interchange Format
+ [correspSearch net](https://correspsearch.net/)
+ [SIG](https://tei-c.org/activities/sig/correspondence/)
+ [Schnitzler](https://schnitzler-briefe.acdh.oeaw.ac.at/pages/index.html)
+ [correspSearch API](https://correspsearch.net/index.xql?id=api)

data samples

+ [offline](./CMIF-Dateien/asbw-cmif.xml)
+ [online](https://correspsearch.net/search.xql?correspondent=all&publication=asbw_ea0a6dba-5789-4e6b-8631-7f9f329678e4)
  + [1889-08-02](https://schnitzler-briefe.acdh.oeaw.ac.at/pages/show.html?document=1889-08-02_01.xml&stylesheet=plain)

reference

+ [Arthur Schnitzler](https://d-nb.info/gnd/118609807)
+ [Wien](https://www.geonames.org/2761333) N48.2066,E16.37341

reminders / comments

+ API test, slow
+ [Raoul Auernheimer](https://correspsearch.net/search.xql?correspondent=all&publication=v02efeb3-b382-4ed8-a71f-1366a4647e76)

correspondence

+ [Briefwechsel mit Hermann Bahr, Sigmund Freud, Rainer Maria Rilke und Arthur Schnitzler ](http://d-nb.info/112987804X)

### workflow

+ browser opens at [localhost:8888](http:localhost:8888/)
+ navigate to `./D_dbs/3_py/`
+ open `validateDates.ipynb`
+ edit filenames
+ run notebook step by step
+ open output in vscode
+ Format Document, Beautify
+ save it
+ open in OpenRefine
+ edit suspicious
+ apply `./_sys/OpenRefine/tpl_Briefe1875_1912_corresp_WorkARoundBug.json`  
  because there is a bug in CMIF creator, see issue, data fields `cert` and `evidence` are flipped
+ export templating using `tpl_Briefe1875_1912_corresp_WorkARoundBug.json`
+ goto [CMIF Creator](https://correspsearch.net/creator/index.xql?l=en)
+ open exported json file
+ 