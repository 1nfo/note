#DataScience track @jhu
---
##toolbox
###prepare R for  linux
>sudo apt-get install r-base
R

---
##getting and cleaning
###raw and tidy
tidy data=raw data + meta data +  what have you done to produce tidy from raw
### load data
>download.file(url,destfile,method)

method is not default as '**curl**' on Mac
No Need to download for every times, but be sure to record when you did

>read.table()

maybe you need pare like "sep=',',header=TRUE"
>read.csv()

queto="",==why would it solve problems that file contains ` or '==
>read.csv2()

==what difference==
>read.xlsx(file,sheetIndex,colIndex,rowIndex)
>read xmlTreeParse(url,useInternet)
data<-applyXpath(datafile,xpath,return_value)

读取xml，获取其中的值
>libaray(jsonlite)
var<-fromJSON(address)
jsonval<-toJson(var)
###subsetting
slice, func in slice, join