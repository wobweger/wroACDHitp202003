# Workflow CMIF uncertain dates

CMIF Creator currently has a little problem see
[here](https://github.com/correspSearch/CMIF-Creator/issues/13),
to make a long story short, json and xml data does not match
representation on GUI.

As a work around, we agreed on modifying data,
make them intentionally incorrect, so that human sees
correct checkbox ticked.

This can be accomplished by 2 additional steps in OpenRefine.

|step   | comment |
|---    |---|
|       |apply [dateCert_WorkARoundBug.json](./D_dbs/1_sys/dateCert_WorkARoundBug.json)|
|       |export Templating using [tpl_Briefe1875_1912_corresp_WorkARoundBug.json](./D_dbs/1_sys/tpl_Briefe1875_1912_corresp_WorkARoundBug.json)
|       |or [tpl_Briefe1913_1931_corresp_WorkARoundBug.json](./D_dbs/1_sys/tpl_Briefe1913_1931_corresp_WorkARoundBug.json)
