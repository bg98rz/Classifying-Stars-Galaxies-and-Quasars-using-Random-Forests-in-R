# Sloan Digital Sky Survey (SDSS) DR14 dataset
#   Source: https://www.sdss.org/dr14/


# Load relevant libraries for exploration & 
#   random-forest classification
library("ggplot2")
library("GGally")
library("dplyr")
library("RColorBrewer")
library("ggthemes")
library("gridExtra")
library("ggrepel")
library("plotly")
library("corrgram")
library("party")
library("randomForest")
library("pROC")
library("caret")

# Set  working directory
setwd("C:/Users/Dylan/Desktop")


#### #### #### #### ####  Data Preperation  #### #### #### #### #### 


# Load data into environment
artefacts <- read.csv('artefacts.csv') 

# Inspect data
str(artefacts)
head(artefacts)
tail(artefacts)

# Check for NA values
x <- sum(is.na(artefacts))
x

# Drop ID variables: fiberID, specobjid, objid, rerun
artefacts <- artefacts[-c(1, 13, 18, 9, 10)]

# Inspect data after dropping columns
str(artefacts)


#### #### #### #### ####  Exploratory Analysis  #### #### #### #### ####


# Check correlations
corrgram(artefacts,  upper.panel=panel.cor, main="SDSS DR14 Dataset - 10 Variables", legend=TRUE)

#### #### Box & Density plots #### ####


ra_box <- boxplot(artefacts$ra, main="Right-Ascencion Box Plot")
# Configure density plot for column: Right-Ascencion 
artefact_ra_density <- artefacts %>%
  ggplot(aes(x = artefacts$ra)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Right-Ascencion") + 
  ggtitle('Right-Ascencion Density Plot') 
# Plot data
ggplotly(artefact_ra_density)
# Display Summary
summary(artefacts$ra)


dec_box <- boxplot(artefacts$dec, main="Declination Box Plot")
# Configure density plot for column: Declination 
artefact_dec_density <- artefacts %>%
  ggplot(aes(x = artefacts$dec)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Declination") + 
  ggtitle('Declination Density Plot') 
# Plot data
ggplotly(artefact_dec_density)
# Display Summary
summary(artefacts$dec)

u_box <- boxplot(artefacts$u, main="U (Ultraviolet) Box Plot")
# Configure density plot for column: u
artefact_u_density <- artefacts %>%
  ggplot(aes(x = artefacts$u)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("u (Ultraviolet)") + 
  ggtitle('SDSS Filter - u (Ultraviolet) Density Plot') 
# Plot data
ggplotly(artefact_u_density)
# Display Summary
summary(artefacts$u)

g_box <- boxplot(artefacts$g, main="g (Green) Box Plot")
# Configure density plot for column: g
artefact_g_density <- artefacts %>%
  ggplot(aes(x = artefacts$g)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("g (Green)") + 
  ggtitle('SDSS Filter - g (Green) Density Plot') 
# Plot data
ggplotly(artefact_g_density)
# Display Summary
summary(artefacts$g)

r_box <- boxplot(artefacts$r, main="r (Red) Box Plot")
# Configure density plot for column: r
artefact_r_density <- artefacts %>%
  ggplot(aes(x = artefacts$r)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("r (Red)") + 
  ggtitle('SDSS Filter - r (Red) Density Plot') 
# Plot data
ggplotly(artefact_r_density)
# Display Summary
summary(artefacts$r)

i_box <- boxplot(artefacts$i, main="i (Near Infra-red) Box Plot")
# Configure density plot for column: i
artefact_i_density <- artefacts %>%
  ggplot(aes(x = artefacts$i)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("i (Near Infra-red)") + 
  ggtitle('SDSS Filter - i (Near Infra-red) Density Plot') 
# Plot data
ggplotly(artefact_i_density)
# Display Summary
summary(artefacts$i)

z_box <- boxplot(artefacts$z, main="z (Infra-red) Box Plot")
# Configure density plot for column: z
artefact_z_density <- artefacts %>%
  ggplot(aes(x = artefacts$z)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("z (Infra-red)") + 
  ggtitle('SDSS Filter - z (Infra-red) Density Plot') 
# Plot data
ggplotly(artefact_z_density)
# Display Summary
summary(artefacts$z)

# Configure density plot for column: run
artefact_run_density <- artefacts %>%
  ggplot(aes(x = artefacts$run)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Run") + 
  ggtitle('Run Density Plot') 
# Plot data
ggplotly(artefact_run_density)
# Display Summary
summary(artefacts$run)

# Configure density plot for column: rerun
artefact_rerun_density <- artefacts %>%
  ggplot(aes(x = artefacts$rerun)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Rerun") + 
  ggtitle('Rerun Density Plot') 
# Plot data
ggplotly(artefact_rerun_density)
# Display Summary
summary(artefacts$rerun)

# Configure density plot for column: camcol
artefact_camcol_density <- artefacts %>%
  ggplot(aes(x = artefacts$camcol)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("camcol") + 
  ggtitle('Camcol Density Plot') 
# Plot data
ggplotly(artefact_camcol_density)
# Display Summary
summary(artefacts$camcol)

# Configure density plot for column: redshift
artefact_redshift_density <- artefacts %>%
  ggplot(aes(x = artefacts$redshift)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Redshift") + 
  ggtitle('Redshift Density Plot') 
# Plot data
ggplotly(artefact_redshift_density)
# Display Summary
summary(artefacts$redshift)

# Log Transformed redshift plot - For better visual representation of distribution
log_artefact_redshift_density <- artefacts %>%
  ggplot(aes(x = log(artefacts$redshift))) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Redshift") + 
  ggtitle('Log Transformed Redshift Density Plot') 
# Plot data
ggplotly(log_artefact_redshift_density)
# Display Summary
summary(artefacts$redshift)

# Configure density plot for column: plate
artefact_plate_density <- artefacts %>%
  ggplot(aes(x = artefacts$plate)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("Plate") + 
  ggtitle('Plate Density Plot') 
# Plot data
ggplotly(artefact_plate_density)
# Display Summary
summary(artefacts$plate)

# Configure density plot for column: mjd
artefact_mjd_density <- artefacts %>%
  ggplot(aes(x = artefacts$mjd)) + 
  geom_density() + 
  theme(legend.position="none") + 
  xlab("MJD") + 
  ggtitle('MJD Density Plot') 
# Plot data
ggplotly(artefact_mjd_density)
# Display Summary
summary(artefacts$mjd)

# Build histogram for class variable
ggplot(artefacts, aes(artefacts$class, fill=artefacts$class)) + 
  geom_bar() +
  coord_flip() +
  labs(x = "Frequency") +
  labs(y = "Artefact Type") +
  labs(colours = "Artefact Type") +
  labs(title = "Frequency of Artefact Type") +
  scale_fill_discrete(name = "Artefact Type")
summary(artefacts$class)

# paired scatter plot, color by class
ggpairs(artefacts, diag="blank", upper="blank", aes(color=artefacts$class), lower=) + 
  ggtitle("SDSS DR14 Dataset -- 15 variables")


#### #### Modelling #### ####

#set seed
set.seed(8514)   
smp <- floor(0.75*nrow(artefacts))  # create value for splitting data into train and test.
i <- sample(seq_len(nrow(artefacts)),size = smp) 
train <- artefacts[i,] #creates the training dataset with row numbers stored in i
test <- artefacts[-i,]  # creates the test dataset excluding the row numbers mentioned in i


# mtry = The number of variables that are to be considered at each
#         node in the desicion trees that make up each forest.

# build model for every mtry value, using default 500 trees
temp_model <- list()
for(i in 1:15){
  
  temp_model[[i]] <- randomForest(train$class ~ ., data=train, ntree=500, mtry=i, importance=TRUE)
}

# How will adding more trees affect model performance?
# build model using trees=1000, mtry=default
thousand_tree_model <- randomForest(train$class ~ ., data=train, ntree=1000, mtry=9, importance=TRUE)


# inspect models post-training
temp_model
thousand_tree_model

#### #### Model Testing #### ####

predictions <- list()
# Test each model on test set
for(i in 1:15){
  
  predictions[[i]] <- predict(temp_model[[i]], test)
}

# test 1000 tree model
thous_pred <- predict(thousand_tree_model, test)


#### #### ROC #### #### 

roc_store <- list()
# Generate ROC data for each test
for(i in 1:15){
  
  roc_store[[i]] <- multiclass.roc(test$class, as.integer(predictions[[i]]))
}

thous_roc <- multiclass.roc(test$class, as.integer(thous_pred))

#### #### Confusion Matrices #### ####

conf_mat <- list()
# get confusionMat for each model
for(i in 1:15){
  
  conf_mat[[i]] <- confusionMatrix(predictions[[i]], test$class)
  print(conf_mat[[i]])
}

thous_confmat <- confusionMatrix(thous_pred, test$class)


#### #### Accuracies #### ####

points_s <- list()
# extract accuracies from confMat object
for(i in 1:15){
  
  points_s[[i]] <- conf_mat[[i]]$overall[1]
}

thous_acc <- thous_confmat$overall[1]


#### #### #### #### ####  Model Evaluation  #### #### #### #### ####

# view confusion matrices
conf_mat
thous_confmat

# view model accuracies on test set
for(i in 1:15){
  
  cat(sprintf("mtry = %s | Acc: %s \n", i, conf_mat[[i]]$overall[[1]]))
}

print(thous_acc)

# plot ROC curve for each model 
for(i in 1:15){
  x <- "mtry = "
  y <- i
  x <- paste(x, y)
  
  rs <- roc_store[[i]][['rocs']]
  plot(rs[[1]], print.auc=TRUE, auc.polygon=TRUE, grid=c(0.1, 0.2),
       grid.col=c("green", "red"), max.auc.polygon=TRUE,
       auc.polygon.col="blue", print.thres=FALSE, main=x)
  sapply(2:length(rs),function(i) lines.roc(rs[[i]],col=i))
}

thous_rs <- thous_roc[['rocs']]
plot(thous_rs[[1]], print.auc=TRUE, auc.polygon=TRUE, grid=c(0.1, 0.2),
     grid.col=c("green", "red"), max.auc.polygon=TRUE,
     auc.polygon.col="blue", print.thres=FALSE, main=x)
sapply(2:length(rs),function(i) lines.roc(rs[[i]],col=i))


#### #### #### #### #### #### Experiment 1 ### #### ### ### ###

# test how redshift variable effects performance of classifier
# Does the inclusion of redshift column have a major impact
# on model performance?

# drop redshift column
df_drop_redshift <- train[-c(13)]

# train model
no_redshift_model <- randomForest(train$class ~ ., data=df_drop_redshift, ntree=500, mtry=9, importance=TRUE)

# inspect model post-training
no_redshift_model

# test model
no_redshift_pred <- predict(no_redshift_model, test)

# generate confusion matrix
confusionMatrix(no_redshift_pred, test$class)

# generate & plot ROC data
roc_2 <- multiclass.roc(test$class, as.integer(no_redshift_pred))
rs <- roc_2[['rocs']]
plot(rs[[1]], print.auc=TRUE, auc.polygon=TRUE, grid=c(0.1, 0.2),
     grid.col=c("green", "red"), max.auc.polygon=TRUE,
     auc.polygon.col="blue", print.thres=FALSE)
sapply(2:length(rs))




