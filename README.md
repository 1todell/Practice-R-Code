# Practice-R-Code
Practice R Code for Training
#For importing SPSS subsets of datasets into R (with existing variable labels)
install.packages("memisc")
library(memisc) 
importer <- spss.system.file("W:/SPSS datasets/LFS household/PHHWT17/2017/AJ17.sav")
lfshh17 <- subset(importer, select=c(phhwt17, age, futype6, relhfu, fuserial, ilodefr, govtor, sex, inecac05, ftpt, ayfl19, fdpch19, sc10mmj, soc10m, hiqul15d))

#For converting imported SPSS data from data.set to data.frame/data.table -> for analysis
newdataset <- as.data.frame(existingdataset)
setDT(newdataset)

EXAMPLE:
lfshhaj17 <- as.data.frame(lfshh17)
setDT(lfshhaj17)
