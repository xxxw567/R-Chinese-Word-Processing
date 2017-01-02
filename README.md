Legal document processing
================
Xia YIwei, Nemo
Sunday, January 01, 2017

Chinese legal documents processing
==================================

In the year 2014, the Chinese supreme people's court has release a **[document](http://www.chinacourt.org/article/detail/2013/11/id/1152212.shtml)** to collect and publish all the sentence documents made by court at each level in China.

The goal of current R package(functions) is tried to develop some useful tools to analyzing those Chinese document.

Current R package depends on [Rwordseg](https://github.com/lijian13/Rwordseg) package made by Lijian, please install the package before make full use of the current package.

1.Websites of legal documents
-----------------------------

-   [Offical website](http://wenshu.court.gov.cn/)
-   [OpenLaw](http://openlaw.cn/)

2.Aims
------

-   Develop a useful R package process the Chinese characters in Legal documents
-   Other types of Chinese documents

3.install all the functions
---------------------------

``` r
library(devtools)
install_github("xxxw567/legalwordproc")
library(legalwordproc)
```

4.Developed functions
---------------------

-   basic functions (input输入字符串, find目标字符串)

1.  ischinexist
2.  findpos
3.  cutsentence

-   cnextract
    Extract from A to B, position A+1 to b

``` r
cnextract("判处有期徒刑十二年,缓刑一年","判处",",")
```

    ## [1] "有期徒刑" "十二年"   ","

-   Chinese words to date/number
    Single Chinese character to number or to number of month 支持小于100年,单个中文字符,如果非中文,返回原始值

``` r
chinntoda("五")
```

    ## [1] 5

``` r
chinntoda("一年")
```

    ## [1] 12

``` r
chinntoda("one")
```

    ## [1] "one"

-   Convert Chinese number to Arabic Number
    &gt; 这个有点难,其实交给其他软件做更好

``` r
a<-"181208900.00"
b<-"三十万"
c<-"45万"
d<-"5.9万"
e<-"三千余"
f<-"6万余"
g<-"3百万"
h<-"310万"
i<-"300000余"
j<-"3.98万"
k<-"九万"
l<-"壹佰万"
m<-"三十三万"
n<-"三百三十三万"
o<-"三千三百三十三万"
p<-"三千三百三十三万四千五百二十九"

matrix(sapply(c(a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p),codemoney))
```

    ##            [,1]
    ##  [1,] 181208900
    ##  [2,]    300000
    ##  [3,]    450000
    ##  [4,]     59000
    ##  [5,]      3000
    ##  [6,]     60000
    ##  [7,]   3000000
    ##  [8,]   3100000
    ##  [9,]    300000
    ## [10,]     39800
    ## [11,]     90000
    ## [12,]   1000000
    ## [13,]    330000
    ## [14,]   3330000
    ## [15,]  33330000
    ## [16,]  33334529

5.Useful links
--------------

-   [how to source file in GitHub](https://tonybreyal.wordpress.com/2011/11/24/source_https-sourcing-an-r-script-from-github/)
-   [how to download data from GitHub](https://github.com/opetchey/RREEBES/wiki/Reading-data-and-code-from-an-online-github-repository)
-   [inroduction of Rmarkdown](http://rmarkdown.rstudio.com/?version=0.98.1103&mode=desktop)
-   [Rmarkdown chectsheet](http://www.rstudio.com/wp-content/uploads/2016/03/rmarkdown-cheatsheet-2.0.pdf)
-   [RStudio+Markdown+Pandoc](http://www.jianshu.com/p/a97b4a9f6d5b)

-   [how to write R package](http://cos.name/2011/05/write-r-packages-like-a-ninja/)
-   [write R package1\_2013](http://blog.fens.me/r-package-faster/)
-   [write R package2\_2013](http://blog.fens.me/r-build-package/)
