#Loading Libraries 

library(assertive)
library(caret)
library(caTools)
library(dplyr)
library(rpart)
library(rpart.plot)
library(randomForest)
library(yardstick)
library(pROC)
library(class)
library(randomForest)
library(naivebayes)

#Loading and inspecting the dataset

df <- read.csv("/Users/prathamdave/Desktop/Autism_Early_Detection_Dataset.csv")
str(df)
glimpse(df)

#Data cleaning (note: the dataset has already been cleaned to some extent - text variables have been replaced with numeric ones (e.g. yes/no was replaced with 1/0) and variables that do not influence the response variables (e.g. user ID) have been deleted)

#First, the factor (categorical) versions of all variables except age in months will be added to the dataset

df <- df %>%
mutate(A1_Factor = as.factor(A1))

df <- df %>%
mutate(A2_Factor = as.factor(A2))

df <- df %>%
mutate(A3_Factor = as.factor(A3))

df <- df %>%
mutate(A4_Factor = as.factor(A4))

df <- df %>%
mutate(A5_Factor = as.factor(A5))

df <- df %>%
mutate(A6_Factor = as.factor(A6))

df <- df %>%
mutate(A7_Factor = as.factor(A7))

df <- df %>%
mutate(A8_Factor = as.factor(A8))

df <- df %>%
mutate(A9_Factor = as.factor(A9))

df <- df %>%
mutate(A10_Factor = as.factor(A10))

df <- df %>%
mutate(Sex_Factor = as.factor(Sex))

df <- df %>%
mutate(Ethnicity_Factor = as.factor(Ethnicity))

df <- df %>%
mutate(Jaundice_Factor = as.factor(Jaundice))

df <- df %>%
mutate(Family_mem_with_ASD_Factor = as.factor(Family_mem_with_ASD))

df <- df %>%
mutate(Who.completed.the.test_Factor = as.factor(Who.completed.the.test))

df <- df %>%
mutate(Class.ASD.Traits_Factor = as.factor(Class.ASD.Traits))

#Second, we wil remove the integer forms of the variables 

df$A1 <- NULL
df$A2 <- NULL
df$A3 <- NULL
df$A4 <- NULL
df$A5 <- NULL
df$A6 <- NULL
df$A7 <- NULL
df$A8 <- NULL
df$A9 <- NULL
df$A10 <- NULL
df$Sex <- NULL
df$Ethnicity <- NULL
df$Jaundice  <- NULL
df$Family_mem_with_ASD <- NULL
df$Who.completed.the.test <- NULL
df$Class.ASD.Traits  <- NULL

#Reinspecting data
str(df)

#Splitting the data

split = sample.split(df$Class.ASD.Traits_Factor, SplitRatio = 0.8)
training_set = subset(df, split == TRUE)
test_set = subset(df, split == FALSE)

#Model 1 - Multiple Logistic Regression 

logistic_model <- glm(Class.ASD.Traits_Factor ~., data = training_set, family = "binomial")

#Evaluating Model 1 (Multiple Logistic Regression)

actual_responses_testing_data <- test_set$Class.ASD.Traits_Factor
logistic_model_prob <- predict(logistic_model, test_set, type = "response")
logistic_model_prob_round <- round(logistic_model_prob)
outcomes <- table(actual_responses_testing_data, logistic_model_prob_round)
outcomes
confusion_logistic_model <- conf_mat(outcomes)
summary(confusion_logistic_model, event_level = "second")

#The multiple logistic regression model's accuracy is 99.5% on the testing data (unseen data)

#Model 2 - Decision Tree Based Model

decision_tree_model <- rpart(Class.ASD.Traits_Factor ~., data = training_set, method = "class", control = rpart.control(cp = 0))

#Visualising Model 2 (Decision Tree Based Model)

rpart.plot(decision_tree_model, type = 3, box.palette = c("red", "green"), fallen.leaves = TRUE)

#Evaluating Model 2 (Decision Tree Based Model)

decision_tree_model_predictions <- predict(decision_tree_model, test_set, type = "class")
outcomes_tree <- table(actual_responses_testing_data, decision_tree_model_predictions)
outcomes_tree
confusion_tree_model <- conf_mat(outcomes_tree)
summary(confusion_tree_model, event_level = "second")

#The decision tree model's accuracy is 91.5% on the testing data (unseen data)

#Pruning the decision tree model 

plotcp(decision_tree_model)
decision_tree_model_pruned <- prune(decision_tree_model, cp = 0.012)

#Evaluating Model 2 - Pruned (Decision Tree Based Model)

decision_tree_model_pruned_predictions <- predict(decision_tree_model_pruned, test_set, type = "class")
mean(decision_tree_model_pruned_predictions == actual_responses_testing_data)

#The pruned decision tree model's accuracy is 91.46% on the testing data (unseen data)

#Model 3 - Random Forest 

random_forest_model <- randomForest(Class.ASD.Traits_Factor ~., data = training_set)

#Evaluating the random forest model 

random_forest_predictions <- predict(random_forest_model, test_set, type = "class")
outcomes_forest <- table(actual_responses_testing_data, random_forest_predictions)
outcomes_forest
confusion_forest_model <- conf_mat(outcomes_forest)
summary(confusion_forest_model, event_level = "second")

#The random forest model's accuracy is 97.6% on the testing data (unseen data)

#Model 4 - Naive Bayes

set.seed(120) 
naive_bayes_model <- naive_bayes(Class.ASD.Traits_Factor ~., data = training_set)

#Evaluating the naive bayes model 

naive_bayes_predictions <- predict(naive_bayes_model, test_set)
confusion_naive_bayes <- table(actual_responses_testing_data, naive_bayes_predictions)
confusionMatrix(confusion_naive_bayes)

#The naive bayes model's accuracy is 96.21% on the testing data (unseen data)
