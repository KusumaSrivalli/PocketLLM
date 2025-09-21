git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git init                    # initialize a new repo
git clone <url>             # clone an existing repo
git status                  # check changes
git add <file>              # stage file
git add .                   # stage all files
git commit -m "message"     # commit staged changes
git commit -am "message"    # stage and commit tracked files
git diff                    # see changes not staged
git diff --staged           # see staged changes
**4. Branching & Merging**
git branch                  # list branches
git branch <name>           # create new branch
git checkout <branch>       # switch branch
git checkout -b <branch>    # create & switch branch
git merge <branch>          # merge branch into current
git branch -d <branch>      # delete branch
git branch -D <branch>      # force delete branch
**5.Remote repos**
git remote -v               # list remotes
git remote add <name> <url> # add a remote
git fetch                   # fetch updates
git pull                    # fetch + merge
git push                    # push changes
git push -u origin <branch> # push and set upstream
**6. Undoing Changes**
git checkout -- <file>       # discard changes in working directory
git restore <file>           # new way to discard changes
git reset <file>             # unstage a file
git reset --soft HEAD~1      # undo last commit, keep changes staged
git reset --hard HEAD~1      # undo last commit, discard changes
git revert <commit>          # undo commit by creating new commit
**7. Viewing History**
git log                     # show commit history
git log --oneline --graph 


**Step 1: Create a New Repository on GitHub**
Go to GitHub.

Log in to your account.

Click + (top-right corner) → New repository.

Give it a name (e.g., simple-java-maven-app).

Choose Public or Private as per your need.

Do not initialize with a README (since you already have one locally).

Click Create repository.

**Step 2: Open Command Prompt in Your Project Folder**
Make sure you are in your project directory:

cd C:\Users\DELL\git\simple-java-maven-app
**Step 3: Initialize Git (if not already initialized)**
git init
**Step 4: Add Remote Repository**
Replace your-username with your GitHub username:

git remote add origin https://github.com/your-username/simple-java-maven-app.git
**Step 5: Stage and Commit Changes**
git add .
git commit -m "Updated pom.xml and project files"
**Step 6: Push to GitHub**
If this is your first push, use:

git branch -M main
git push -u origin main
After this, just use: git push

**if not working ----**
git remote -v
git remote remove origin
git remote add origin https://github.com/KusumaSrivalli/simple-java-maven-app.git
git push -u origin main

**Dockerfile**
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY target/simple-java-maven-app-1.0-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]

docker build -t myappimage .
docker run -d -p 8080:8080 --name myappcontainer myappimage

FROM tomcat:9.0
COPY target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]

**Docker image:**
version: "3.9"
services:
  app:
    image: myprojectimage
    container_name: myproject_app
    ports:
      - "9090:8080"   # HostPort:ContainerPort, App accessible at http://localhost:9090
    environment:
      DB_HOST: db
      DB_USER: user
      DB_PASSWORD: password
      DB_NAME: mydb
    depends_on:
      - db

  db:
    image: mysql:8
    container_name: myproject_db
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: mydb
      MYSQL_USER: user
      MYSQL_PASSWORD: password
    volumes:
      - db_data:/var/lib/mysql
    ports:
      - "3306:3306"   # Optional, only if you want to connect from host

volumes:
  db_data:


Save the file as docker-compose.yml in your project folder.
In terminal, go to that folder.
Run:
docker-compose up -d
Check if services are running:
docker-compose ps
Access your app at:
http://localhost:9090




