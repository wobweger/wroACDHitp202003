hello I'm Walter,
I was lucky enough to be assigned to project Arthur Schnitzler Briefe conducted by Martin.

use the hashtag to explore more on twitter.

correspSearch dot net is a platform hosted by 
Berlin-Brandenburg Academy of Sciences and Humanities intended to facilitate correspondence search, who wrote when and where a letter to whom.
to do so, a TEI variation called CMIF has to be prepared.
Correspondence Metadata Interchange Format

there is an online editor available, as you see here.
GND, gemeinsame Normdaten geo locations are supported and resolvable.

input data were letter in print, scanned already.
the larger volumes contained a index, three columns starting with recipient and dates.

there are multiple approaches to tackle task to convert index into an CMIF.

Martin inspired me to following workflow

first we use transkribus to perform a text recognition.
important to mention is that text area recognition needed a little help, manual selection was unavoidable.

now all lines of the index were in a text file, line by line.

with OpenRefine this messy data was shaped into a table.
during this process, problems in text recognition surfaced.
on first glance correct dates, couldn't be, because they weren't chronological.

to detect such problems, a little python script in jupyter notebook was created.

as final step, by means of OpenRefine suspect dates were edited manually.
and shaped into CMIF json file, which CMIF Creator can load.
GND has been adjusted manually by Martin.

