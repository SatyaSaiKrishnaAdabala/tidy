library("dplyr")


setwd("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset")
getwd()

# Loading Test Data
x_test <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/test/X_test.txt",header = F)
y_test <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/test/y_test.txt",header = F)
sub_test <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/test/subject_test.txt",header = F)

# Loading Training Data
x_train <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/train/X_train.txt",header = F)
y_train <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/train/y_train.txt",header = F)
sub_train <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/train/subject_train.txt",header = F)

features <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/features.txt",header = F)
head(features$V2,4)

names(x_train) <- features$V2
names(x_test) <- features$V2

names(y_train) <- "Activity_ID"
names(y_test) <- "Activity_ID"
names(sub_train) <- "Subject"
names(sub_test) <- "Subject"

Test_Set <- cbind(x_test,y_test,sub_test)
head(Test_Set,1)
Train_Set <- cbind(x_train,y_train,sub_train)
head(Train_Set)

Test_Set <- Test_Set[,which(duplicated(colnames(Test_Set)) == FALSE)]

Test_Set<- mutate(Test_Set, DataType ="Test")

Train_Set <- Train_Set[,which(duplicated(colnames(Train_Set)) == FALSE)]
Train_Set<- mutate(Train_Set, DataType ="Train")

# Combine DataSet

Activity_Set <- rbind(Train_Set,Test_Set)

# Extracts only Means and Standard Deviation

names(Activity_Set)

head(Activity_Set)

d <- grep("mean",colnames(Activity_Set),ignore.case = TRUE)
d1 <- grep("std",colnames(Activity_Set),ignore.case = TRUE)  

Meanstdset <- select(Activity_Set,DataType,Activity_ID,Subject,colnames(Activity_Set[,c(d,d1)]))

# Uses descriptive activity names to name the activities in the data set

activity_label <- read.table("C:/Users/admin/Downloads/getdata_projectfiles_UCI HAR Dataset (1)/UCI HAR Dataset/activity_labels.txt",header = F)
Meanstdset <- mutate(Meanstdset,Activity_ID2 = Meanstdset$Activity_ID) 
head(Meanstdset,1)
Meanstdset <- merge(Meanstdset,activity_label,by.x ="Activity_ID2" ,by.y = "V1")
head(Meanstdset,1)

# .Appropriately labels the data set with descriptive variable names.
nameset <- gsub ("tBody", "time-Body", names(Meanstdset), ignore.case=FALSE)
nameset <- gsub ("tGravity", "time-Gravity", nameset, ignore.case=FALSE)
nameset <- gsub ("Mag", "Magnitude", nameset, ignore.case=FALSE)
nameset <- gsub ("Gyro", "Gyroscope", nameset, ignore.case=FALSE)
nameset <- gsub ("Acc", "Accelerometer", nameset, ignore.case=FALSE)
nameset <- gsub ("fBody", "fastFourierTransform-Body", nameset, ignore.case=FALSE)
nameset <- gsub ("Freq", "Frequency", nameset, ignore.case=FALSE)
nameset <- gsub ("BodyBody", "Body", nameset, ignore.case=FALSE)

names(Meanstdset) <- nameset
head(Meanstdset,1)

# From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

average_set <- Meanstdset %>% select(-DataType) %>% group_by(Subject,Activity_ID,V2) %>% summarise_each(funs(mean))

head(average_set,1)

write.table(average_set, file="avedata.txt", row.names=FALSE, col.names=TRUE)




