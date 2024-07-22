# Storing Django Static and Media Files on Amazon S3

## Want to learn how to build this?

Check out the [post](https://testdriven.io/blog/storing-django-static-and-media-files-on-amazon-s3/).

## steps to deploy it on ec2

1. clone to repo using git clone 

2. install docker on ec2 instance 

3. go to cloud-gallery/app/hello-django/settings.py to make the following changes 
    - allowed hosts= ['ip addpress'] add ec2 public ip address
    - CSRF_TRUSTED_ORIGINS=['ec2 ip address'] add ec2 public ip address
    
4. go to storage-s3/docker-compose.yml  
    - update aws-s3 bucket name 
    - udpate aws access key 
    - update aws secret key 

5. run docker compose up -d --build 

6. run docker compose exec web python manage.py makemigrations

7. run  docker-compose exec web python manage.py migrate

8. go to security group associated with this ec2 instance > edit inbound rules> allow custom tcp port 1337

9. go to web browser and search for http://ec2-instanceip:1337

