# 1. Data setup
## 1.1 Data input
data <- as.data.frame(read.csv("Data01.csv", header = TRUE))
str(data)
summary(data)

## 1.2 Data grouping
#do this to make a preliminary classification of the variables
groupIPM <- data[,c("IP11", "IK11", "IDB11", 
                  "AHH11", "AMH11", "INDAMH11",
                  "RLS11", "INRLS11", 
                  "PPP11", "INPPP11",
                  "IPM11")]


groupEkon <- data[,c("IDB11", 
                     "LPE11",  
                     "PPP11", 
                     "INPPP11",
                     "IPM11", 
                     "LPP11",
                     "TPT11",
                     "PM07",
                     "PM08",
                     "PM09",
                     "PM10",
                     "TPT07",
                     "TPT08",
                     "TPT09",
                     "TPT10",
                     "LPDRB07",
                     "LPDRB08",
                     "LPDRB09",
                     "LPDRB10",
                     "LPDRB11")]

# 2. Linear models 
## 2.1 Using "lm" and "glm" basic stat
#Generate lm model
lm0 <- lm(IPM11 ~., data = data)
lm0.step <- step(lm1) #stepwise "lm"

lm1 <- lm(IPM11 ~ IP11 + IK11 + IDB11 +  
          AHH11 + AMH11 + INDAMH11 +
          RLS11 + INRLS11 + PPP11 +
          INPPP11, data = groupIPM)
lm1.step <- step(lm1) #stepwise "lm"

#generate glm model
glm0 <- glm(IPM11 ~., data = data) #using all the predictors at once
glm0.step <- step(lm1) #stepwise "lm"

glm1 <- glm(IPM11 ~ ., data = groupIPM) #using the predictors in "groupIPM"
glm1.step <- step (glm1) #stepwise "glm"

glm2 <- glm(IPM11 ~ IP11 + IK11 + IDB11 +  
              AHH11 + AMH11 + INDAMH11 +
              RLS11 + INRLS11 + PPP11 +
              INPPP11, family = Gamma(link = "log"), data = groupIPM)
glm3 <- glm(IPM11 ~ IP11 + IK11 + IDB11 +  
              AHH11 + AMH11 + INDAMH11 +
              RLS11 + INRLS11 + PPP11 +
              INPPP11, family = Gamma, data = groupIPM)

#Evaluate model "lm0"
summary(lm0, correlation = T)  # model summary
coef(lm0)     # model coeff
resid(lm0)    # model residual
fitted(lm0)   # predicts Y values
confint(lm0, level=0.95) # CIs for model parameters 
anova(lm0)    # anova table 
influence(lm0) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(lm0)
dev.off()

#Evaluate model "lm1"
summary(lm1, correlation = T)  # model summary
coef(lm1)     # model coeff
resid(lm1)    # model residual
fitted(lm1)   # predicts Y values
confint(lm1, level=0.95) # CIs for model parameters 
anova(lm1)    # anova table 
influence(lm1) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(lm1)
dev.off()

#Evaluate model "glm0"
summary(glm0, correlation = T)  # model summary
coef(glm0)     # model coeff
resid(glm0)    # model residual
fitted(glm0)   # predicts Y values
confint(glm0, level=0.95) # CIs for model parameters 
anova(glm0)    # anova table 
influence(glm0) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(glm0)
dev.off()

#Evaluate model "glm1"
summary(glm1, correlation = T)  # model summary
coef(glm1)     # model coeff
resid(glm1)    # model residual
fitted(glm1)   # predicts Y values
confint(glm1, level=0.95) # CIs for model parameters 
anova(glm1)    # anova table 
influence(glm1) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(glm1)
dev.off()

#Evaluate model "glm2"
summary(glm2, correlation = T)  # model summary
coef(glm2)     # model coeff
resid(glm2)    # model residual
fitted(glm2)   # predicts Y values
confint(glm2, level=0.95) # CIs for model parameters 
anova(glm2)    # anova table 
influence(glm2) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(glm2)
dev.off()

#Evaluate model "glm3"
summary(glm3, correlation = T)  # model summary
coef(glm3)     # model coeff
resid(glm3)    # model residual
fitted(glm3)   # predicts Y values
confint(glm3, level=0.95) # CIs for model parameters 
anova(glm3)    # anova table 
influence(glm3) # regression diagnostics
layout(matrix(c(1,2,3,4),2,2)) # optional 4 graphs/page 
plot(glm3)
dev.off()

## 2.2 Variable selection using "MASS" 
library("MASS")
step.lm1 <- stepAIC(lm1, direction = "both")
step.lm1$anova # display results

## 2.3 Multiple linreg using GAM "mgcv" package
#load library
library("mgcv") 
#build model
k1 <- 3 #set knots value
bsm <- "cs" #set base smoothing parameter
#model with gaussian family
gam1 <- gam(IPM11 ~ s(IP11, k=k1, bs=bsm) + s(IK11, k=k1, bs=bsm) + s(IDB11, k=k1, bs=bsm) + 
            s(AHH11, k=k1, bs=bsm) + s(AMH11, k=k1, bs=bsm) + s(INDAMH11, k=k1, bs=bsm) +
            s(RLS11, k=k1, bs=bsm) + s(INRLS11, k=k1, bs=bsm) + s (PPP11, k=k1, bs=bsm) +
            s(INPPP11, k=k1, bs=bsm), data = groupIPM)
#model with gamma family
gam2 <- gam(IPM11 ~ s(IP11, k=k1, bs=bsm) + s(IK11, k=k1, bs=bsm) + s(IDB11, k=k1, bs=bsm) + 
              s(AHH11, k=k1, bs=bsm) + s(AMH11, k=k1, bs=bsm) + s(INDAMH11, k=k1, bs=bsm) +
              s(RLS11, k=k1, bs=bsm) + s(INRLS11, k=k1, bs=bsm) + s (PPP11, k=k1, bs=bsm) +
              s(INPPP11, k=k1, bs=bsm), family=Gamma(link=log), data = groupIPM)
#evaluate model
plot(gam1, pages=1)
dev.off()
gam.check(gam1)
summary(gam1)

plot(gam2, pages=1)
gam.check(gam2)
summary(gam2) #signif AHH11, AMH11, INDAMH11, RLS11, INPPP11 
plot(fitted(gam2),residuals(gam2))
dev.off()


#3. Decision tree
##3.1 Using "tree" package
#load library
library("tree")
#generate model
treeIPM <- tree(IPM11 ~ ., data = groupIPM)
treeEkon <- tree(IPM11 ~ ., data = groupEkon)
#evaluate model
summary(treeIPM)
summary(treeEkon)
deviance(treeIPM, detail = F)
deviance(treeEkon, detail = F)
plot(treeIPM)
text(treeIPM, cex = 0.5)
dev.off()
plot(treeEkon)
text(treeEkon, cex = 0.5)
dev.off()
#cross validate the model (where to stop prunning)
cvTreeIPM <- cv.tree(treeIPM, FUN = prune.tree)
cvTreeEkon <- cv.tree(treeEkon, FUN = prune.tree)
par(mfrow=c(1,2))
mtext("Cross validation plots")
plot(cvTreeIPM$size, cvTreeIPM$dev, 
     type = "l", 
     col = "red", 
     main = "Group 1")
plot(cvTreeEkon$size, cvTreeEkon$dev, 
     type = "l", 
     col = "green", 
     main = "Group 2")


#use optimum number of nodes to prune the tree
treePruneIPM <- prune.tree(treeIPM, best=2)
treePruneEkon <- prune.tree(treeEkon, best=2)

#summary
summary(treePruneIPM)
summary(treePruneEkon)

#plot pruned tree
plot.new()
par(mfrow=c(1,2))
plot(treePruneIPM)
text(treePruneIPM, cex = 0.8)
plot(treePruneEkon)
text(treePruneEkon, cex = 0.8)

##3.2 Using "rpart" package
#load library
library("rpart")
#generate model
rpartIPM <- rpart(IPM11 ~ ., data = groupIPM)
rpartEkon <- rpart(IPM11 ~ ., data = groupEkon)
#evaluate model
print(rpartIPM)
summary(rpartIPM)
plot(rpartIPM, compress=TRUE)
text(rpartIPM, use.n=TRUE)
dev.off()
plot(rpartEkon, compress=TRUE)
text(rpartEkon, use.n=TRUE)
dev.off()

##3.3 Using "party" package
#load library
#install.packages("party")
library("party")
#generate model
partyIPM <- ctree(IPM11 ~ ., data = groupIPM)
partyEkon <- ctree(IPM11 ~ ., data = groupEkon)
#evaluate model
plot(partyIPM)
dev.off()
plot(partyEkon)
dev.off()

predict(partyIPM)
predict(partyEkon)


##3.4 Using "evtree" package
#load library
#install.packages("evtree")
library("evtree")
#generate model
evIPM <- evtree(IPM11 ~ ., data = groupIPM)
evEkon <- evtree(IPM11 ~ ., data = groupEkon)
#evaluate model
plot(evIPM)
dev.off()
plot(evEkon)
dev.off()

##3.5 Using "randomForest" package
#load library
#install.packages("randomForest")
library("randomForest")
#generate model
rfModelIPM <- randomForest(IPM11 ~ ., data = groupIPM, 
                           ntree = 1000, 
                           mtry = 5,
                           importance = TRUE,
                           do.trace = 100, 
                           proximity=TRUE)

rfModelEkon <- randomForest(IPM11 ~ ., data = groupEkonImp,
                            ntree = 1000, 
                            mtry = 5,
                            importance = TRUE,
                            do.trace = 100, 
                            proximity=TRUE)

#evaluate RF model
print(rfModelIPM)
print(rfModelEkon)

par(mfrow=c(1,2))
plot(rfModelIPM)
plot(rfModelEkon)
dev.off()

varImpPlot(rfModelIPM)
varImpPlot(rfModelEkon)

#REFERENCES: 
#http://www.r-bloggers.com/a-brief-tour-of-the-trees-and-forests/
#http://www.statmethods.net/advstats/cart.html
#http://en.wikibooks.org/wiki/Data_Mining_Algorithms_In_R/Classification/Decision_Trees
#http://www.statsoft.com/Textbook/Classification-and-Regression-Trees
#http://www.rdatamining.com/examples/decision-tree
#http://cran.r-project.org/doc/contrib/Zhao_R_and_data_mining.pdf
