
LOGIN:
$ aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin <########>.dkr.ecr.us-west-2.amazonaws.com/test
Login Succeeded

BUILD:
$ docker build -t test .
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM httpd:2.4
 ---> b2c2ab6dcf2e
Step 2/2 : COPY * /usr/local/apache2/htdocs/
 ---> Using cache
 ---> 6a257e94ff2e
Successfully built 6a257e94ff2e
Successfully tagged test:latest

TAG:
$ docker tag <local_image>:<local_image_tag> <repository_url>:<image_Tag_you_wanna_proivde_in_ECR>
$ docker tag test:latest <########>.dkr.ecr.us-west-2.amazonaws.com/test:latest
$ docker tag test:latest <########>.dkr.ecr.us-west-2.amazonaws.com/test:ecr-myhttpd

PUSH:
$ docker push <repository_url>:<image_Tag_you_wanna_proivde_in_ECR>
$ docker push <########>.dkr.ecr.us-west-2.amazonaws.com/test:latest
The push refers to repository [<########>.dkr.ecr.us-west-2.amazonaws.com/test
]
7f5391784760: Pushed 
35ca97a06fb3: Pushed 
701ef2ccb5d3: Pushed 
81b4f0dc1e64: Pushed 
3e944ab7641d: Pushed 
c2adabaecedb: Pushed 
latest: digest: sha256:0f25ef44057b4b18f6b7df847b428d4c054e6ab42e49a5b435ba84a7e85ff246 size: 1574
