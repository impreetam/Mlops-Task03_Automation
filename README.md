# mlops-automation
Final Project of Mlops Training Under Guidance of Vimal daga Sir.

MLOps : ML & DevOps Integration

"MLOps is a set of practices that combines Machine Learning , DevOps and Data Engineering , which aims to deploy and maintain ML systems in production reliably and efficiently."
Why we need MLOps ?

In the world of traditional software development , a set of practices known as DevOps have made it possible to ship software to production in minutes and to keep it running reliably. DevOps relies on tools , automation and workflows to abstract away the accidental complexity . This approach has been so successful that many companies are already adept it , so why can't we simply keep doing the same thing for ML ??

The root cause is that there's a fundamental difference between ML and traditional software. ML is not just code , it's code plus data. An ML model , the artifact that you end up putting in production , is created by applying an algorithm to a mass of training data , which will affect the behavior of the model in production.The model behavior depends on the input data that it will receive at prediction time.

while code is carefully crafted in a controlled development environment , data comes from that unending entropy source known as "the real world". The challenge of an ML process is to create a bridge between the two , Data and Code . This fundamental disconnect causes several important challenges that need to be solved by anyone trying to put an ML model in production successfully.

Data Engineering does provide important tools and concepts that are indispensable to solving the puzzle of ML in production. In order to crack it , we need to combine practices from DevOps and Data Engineering , adding some that are unique to ML.
» Following is the ML-DevOps integration task overview:

Task Overview :-
Create container image that's has python3 and Keras or numpy installed using dockerfile.
When we launch this image , it should automatically starts train the model in the container.
Create a job chain of job1 , job2 , job3 , job4 and job5 using build pipeline plugin in jenkins.
job1: Pull the Github repo automatically when some developers push repo to Github.
job2: By looking at the code or program file , jenkins should automatically start the respective machine learning software installed interpreter install image container to deploy code and start training( eg. If code uses CNN , then jenkins should start the container that has already installed all the software required for the cnn processing.)
job3: Train your model and predict accuracy or matrics.
job4: If matrics accuracy is less than 80% , then tweak the machine learning model architecture.
job5: Retrain the model or notify that the best model is being created.
Create one extra job job6 for monitor: If container where app is running , fails due to any reason then this job should automatically start the container again from where the last trained model left.

» Following are the solutions for each job one-by-one :
→ Our very first task is to create a dockerfile in text editor 'gedit' ,this Dockerfile creates an image that have python3 , keras or numpy instlled.
To create or build an image the following command is used:
docker build -t <image_name>:<version> <location of the dockerfile>
Image is created now and ready to use.
• job1: 1job
our first job is to pull the repo automatically when developer push repo to the GitHub.
• job2 : 2job
By looking at the code or program file, Jenkins should automatically start the respective machine learning software installed interpreter install image container to deploy code and start training( eg. If code uses CNN, then Jenkins should start the container that has already installed all the softwares required for the cnn processing).
Since , job2 is triggered after job1 so job1 is working as downstream for job2 , hence job2 is triggered after job1.
• job3: 3job
In this job we will predict matrics or accuracy of our model.
job3 is triggered by job2.
• job4: 4job
If metrics accuracy is less than 80% , then tweak the machine learning model architecture.
Here we used the file "rebuild.py" to check the accuracy which run epochs and iteration to check the accuracy .If the accuracy is greater then 80 % it sends the "success.py" mail In case ,if accuracy is less than 80% it will sends the failure.py mail .It depends on its accuracy.
• job5: 5job
Build-pipeline:~
Hence , throughout the whole process of completion of this project , it took me almost 15 days to complete , although it was small project. I that I came to learn Intergration of ML with DevOps throughout this whole project.
