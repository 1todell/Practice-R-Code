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

#For recoding data into new + existing variables (1) (EASIER WITH CONTINUOUS DATA)
dataset$newvariable <- ifelse(dataset$existingvariable #decide value#, #give new value#, #give else value#)
EXAMPLE: lfshh17$workage <- ifelse(lfshh17$age >15 & lfshh17$age <65, 1, 0)


#For recoding data into new + existing variables (2) (EASIER WITH CATEGORICAL DATA)
dataset$newvariable <- dataset$existingvariable
levels(dataset$newvariable) <- c("ValueLabelOne", "ValueLabelTwo",.. etc)
CHECK = levels(dataset$newvariable)

EXAMPLE: 
lfshhaj17$region <- lfshhaj17$govtor
levels(lfshhaj17$region) <- c("North East", "North East", "North West", "North West", "North West", "Yorkshire & Humberside", "Yorkshire & Humberside", "Yorkshire & Humberside", "East Midlands", "West Midlands", "West Midlands", "Eastern", "London", "London", "South East", "South West", "Wales", "Scotland", "Scotland", "Northern Ireland")

