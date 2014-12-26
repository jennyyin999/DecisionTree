DecisionTree
============

R try outs to make decision trees.
Aplikasi R terkini adalah untuk membuat "pohon keputusan" (PK) atau "decision tree" (DT).

A decision tree is a decision support tool that uses a tree-like graph or model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It is one way to display an algorithm (Wikipedia).

Decision trees are produced by algorithms that identify various ways of splitting a data
set into branch-like segments. These segments form an inverted decision tree that
originates with a root node at the top of the tree. The object of analysis is reflected in this
root node as a simple, one-dimensional display in the decision tree interface (SAS).

Dari definisi di atas dijelaskan bahwa DT:

memanfaatkan prinsip regresi: regresi linear atau linear regression (LR), dalam hal ini adalah multiple linear regression (MLR).
karena itu beberapa sumber juga menyebut DT sebagai "pohon regresi" atau "regression tree".
melibatkan banyak variabel, dalam hal ini independent variables (IV).
bertujuan untuk mengurutkan peran IV tersebut kepada dependent variable (DV).
memerlukan pemahaman teori yang cukup dari penggunanya untuk dapat menjawab masalah (research question) dan untuk memberikan argumentasi terhadap DT yang dihasilkan oleh piranti lunak (Stata, Statistica, Minitab, SPSS, SAS, atau dalam hal ini kita menggunakan R dengan R Studio).
Apakah R? Anda bisa kunjungi tautan ini dan ini.

Apakah R Studio? Anda bisa kunjungi tautan ini dan ini.

Apakah package itu? Anda bisa kunjungi tautan ini.

Beberapa package yang harus diinstal dari server CRAN adalah: "tree", "rpart", "randomForest". Anda mungkin bisa mencoba juga package: "party", "evtree".

Langkah 1: install package dengan perintah:

install.packages("tree")
install.packages("rpart")
install.packages("randomForest")
install.packages("party")
install.packages("evtree")

atau lakukan sekaligus dengan perintah

install.packages(c("tree, "rpart", "randomForest", "party", evtree")

Langkah 2: load package dengan perintah "library ("package")" atau "require("package")"

library("tree")
library("rpart")
library("randomForest")
library("party")
library("evtree")

Follow my next posts on this subject. For the impatience, visit my Github for the complete code dan data set.
