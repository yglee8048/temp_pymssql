# pymssql environment for AWS lambda

## WHY

When I tried to use mssql in AWS lambda, I met a problem with **"can not import module"** message.  
Finally, I found the solution, **building python virtual environment in EC2 Linux**, but it was not easy for me.  
So I share the pymssql module files that are **available in AWS lambda** to make it easier for beginners like me.  
I hope these files help you guys just a little.


## Use this environment WHEN...

1. If you want to use pymssql module in AWS lambda.
2. If you meet error when you use pymssql module in AWS lambda like **"[ERROR] Runtime.ImportModuleError: Unable to import module 'app': No module named 'pymssql'"**


## HOW

**Just clone or download** these files and **zip them with your python code** to upload to AWS lambda console.


## Check points

1. This is pymssql module for **'python 3.7'**.  You have to **choose 'python 3.7', not 'python 3.8'** which is default version on AWS lambda.
2. This environment contains **pymssql module** and **requests module**. If you don't want requests module, then just except the folders whose name are *'requests'*, *'requests-2.22.0.dist-info'*.
3. If you want to add other modules, just command ```'pip install <module_name> -t <route>```.


## I did like this..

1. make EC2 with Linux.

2. command followings.
```
sudo yum install python3-devel freetds-devel gcc git

git clone https://github.com/yglee8048/temp_pymssql.git

sudo pip3 install virtualenv
virtualenv -p python3 virtualenv

source virtualenv/bin/activate && cd temp_pymssql

sudo pip3 install pymssql -t .
sudo pip3 install requests -t .

git add .
git commit -m "commit message"
git push -u origin master
```


## for Koreans

pymssql 모듈입니다.  
window 환경에서 pymssql을 설치 후 압축해서 lambda에 올리면 자꾸 'can not import' 라고 나오는 문제가 있었습니다.

저는 EC2 를 하나 만들어서 Linux 환경에서 module을 설치하여 해결했습니다.  
꽤 해맸었기 때문에 다른 분들은 저처럼 해매지 마시라고 공유드립니다.

받으셔서 코드와 함께 lambda에 올리면 pymssql을 사용할 수 있습니다.  
조금이나마 도움이 되셨으면 좋겠습니다.
