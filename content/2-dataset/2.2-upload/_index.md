+++
title = "Upload dataset"
date = 2025
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++


### S3 Bucket

After creating the folders containing **images** along with the **.jsonl** files from the previous data preprocessing step, the next step is to upload all the data to **Amazon S3**. This is a crucial step in preparing for the **fine-tuning** process on **AWS Bedrock**, as the model requires direct access to the files stored in **S3** throughout the training process.

- Create a folder structure as follows:

![S3-Dataset](/images/2-dataset/s3_dataset.png)

- Upload the image folders for both **training** and **testing** datasets.

![S3-Dataset](/images/2-dataset/s3_train.png)

- Upload the **.jsonl** files for both **training** and **testing** datasets.

![S3-Dataset](/images/2-dataset/s3_train_js.png)
