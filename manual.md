# Simple Steps for All 10 DevOps Experiments

## 1. Explore Git and GitHub Commands

1. Install Git:

   ```bash
   sudo apt install git
   ```
2. Configure Git:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "youremail@gmail.com"
   ```
3. Create a project folder:

   ```bash
   mkdir gitdemo
   cd gitdemo
   ```
4. Initialize repository:

   ```bash
   git init
   ```
5. Create a file:

   ```bash
   nano file.txt
   ```
6. Add file:

   ```bash
   git add file.txt
   ```
7. Commit changes:

   ```bash
   git commit -m "First commit"
   ```
8. Check logs:

   ```bash
   git log
   ```
9. Create branch:

   ```bash
   git branch test
   ```
10. Push to GitHub:

```bash
git remote add origin <repo-url>
git push -u origin main
```

---

# 2. Flask DevOps Application

1. Install packages:

   ```bash
   sudo apt install python3 python3-pip virtualenv
   ```
2. Create project:

   ```bash
   mkdir flask_app
   cd flask_app
   ```
3. Create virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
4. Install Flask:

   ```bash
   pip install flask
   ```
5. Create `app.py`
6. Run app:

   ```bash
   python app.py
   ```
7. Create `requirements.txt`
8. Create `build.sh`
9. Run build:

   ```bash
   bash build.sh
   ```
10. Test app:

```bash
python -m unittest test_app.py
```

11. Add `/health` endpoint for monitoring.

---

# 3. Create Job Using Jenkins

1. Install Java.
2. Install Jenkins.
3. Start Jenkins:

   ```bash
   sudo systemctl start jenkins
   ```
4. Open browser:

   ```
   http://localhost:8080
   ```
5. Unlock Jenkins using admin password.
6. Install suggested plugins.
7. Create admin user.
8. Click **New Item**.
9. Select **Freestyle Project**.
10. Add build step:

```bash
echo "Hello Jenkins"
```

11. Save and click **Build Now**.
12. Check console output.

---

# 4. Configuration Management Using Ansible

1. Install Ansible:

   ```bash
   sudo apt install ansible
   ```
2. Create inventory file:

   ```bash
   nano hosts.ini
   ```
3. Add:

   ```ini
   [local]
   localhost ansible_connection=local
   ```
4. Create playbook:

   ```bash
   nano setup.yml
   ```
5. Add tasks to install curl.
6. Run playbook:

   ```bash
   ansible-playbook -i hosts.ini setup.yml
   ```
7. Verify installation:

   ```bash
   curl --version
   ```

---

# 5. Gradle Project Setup

1. Install Gradle:

   ```bash
   sudo apt install gradle
   ```
2. Create project:

   ```bash
   mkdir HelloGradle
   cd HelloGradle
   ```
3. Initialize project:

   ```bash
   gradle init --type java-application
   ```
4. Open `build.gradle`.
5. Add dependencies and custom task.
6. Build project:

   ```bash
   gradle build
   ```
7. Run application:

   ```bash
   gradle run
   ```
8. Run custom task:

   ```bash
   gradle hello
   ```

---

# 6. Install and Explore Selenium

1. Install Python and VS Code.
2. Install Selenium:

   ```bash
   pip install selenium
   ```
3. Download ChromeDriver.
4. Create project folder.
5. Create `test_google.py`
6. Write Selenium code.
7. Run script:

   ```bash
   python test_google.py
   ```
8. Observe browser automation.

---

# 7. Docker Containerized Application

1. Install Docker Desktop.
2. Create project folder:

   ```bash
   mkdir docker-flask-app
   cd docker-flask-app
   ```
3. Create `app.py`
4. Create `requirements.txt`
5. Create `Dockerfile`
6. Build image:

   ```bash
   docker build -t flask-docker-app .
   ```
7. Run container:

   ```bash
   docker run -p 5000:5000 flask-docker-app
   ```
8. Open:

   ```
   http://localhost:5000
   ```
9. Check Docker images:

   ```bash
   docker images
   ```

---

# 8. Kubernetes Container Automation

1. Install `kubectl`.
2. Install Minikube.
3. Start cluster:

   ```bash
   minikube start
   ```
4. Check pods:

   ```bash
   kubectl get po -A
   ```
5. Create deployment:

   ```bash
   kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
   ```
6. Expose deployment:

   ```bash
   kubectl expose deployment hello-minikube --type=NodePort --port=8080
   ```
7. View service:

   ```bash
   kubectl get services
   ```
8. Open application:

   ```bash
   minikube service hello-minikube
   ```

---

# 9. Continuous Security Using Snyk

1. Open VS Code.
2. Go to Extensions.
3. Install **Snyk Security** extension.
4. Login to Snyk account.
5. Download vulnerable project:

   ```text
   pygoat
   ```
6. Open project in VS Code.
7. Enable Snyk Code scanning.
8. Wait for scan results.
9. Review vulnerabilities and fixes.

---

# 10. Maven Project and POM File

1. Install Maven:

   ```bash
   sudo apt install maven
   ```
2. Create Maven project:

   ```bash
   mvn archetype:generate -DgroupId=com.example -DartifactId=MyMavenApp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
   ```
3. Go to project:

   ```bash
   cd MyMavenApp
   ```
4. Open `pom.xml`
5. Add dependencies/plugins.
6. Compile project:

   ```bash
   mvn compile
   ```
7. Run tests:

   ```bash
   mvn test
   ```
8. Package project:

   ```bash
   mvn package
   ```
9. Clean project:

   ```bash
   mvn clean
   ```

# 1. Git and GitHub Commands

## Commands

```bash
mkdir gitdemo
cd gitdemo
git init
```

## Create File

### file.txt

```txt
Hello Git
```

## Commands

```bash
git add file.txt
git commit -m "First commit"
git branch test
git log
```

---

# 2. Flask DevOps Application

## Step 1: Create Project

```bash
mkdir flask_app
cd flask_app
python3 -m venv venv
source venv/bin/activate
pip install flask python-dotenv
```

---

## File 1: app.py

```python
import os
from flask import Flask
from dotenv import load_dotenv

load_dotenv()

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, DevOps!"

@app.route('/health')
def health():
    return {"status": "up"}, 200

if __name__ == "__main__":
    port = int(os.getenv("FLASK_PORT", 5000))
    app.run(host='0.0.0.0', port=port)
```

---

## File 2: requirements.txt

```txt
flask==2.1.0
python-dotenv
```

---

## File 3: build.sh

```bash
#!/bin/bash

echo "Setting up environment..."

python3 -m venv venv
source venv/bin/activate

pip install -r requirements.txt

echo "Environment setup complete"
```

Run:

```bash
bash build.sh
```

---

## File 4: test_app.py

```python
import unittest
from app import app

class TestApp(unittest.TestCase):

    def test_home(self):
        tester = app.test_client(self)
        response = tester.get('/')

        self.assertEqual(response.status_code, 200)
        self.assertEqual(response.data, b"Hello, DevOps!")

if __name__ == "__main__":
    unittest.main()
```

Run:

```bash
python -m unittest test_app.py
```

---

## File 5: .env

```env
FLASK_PORT=5000
```

Run App:

```bash
python app.py
```

---

# 3. Jenkins Job

## Build Step Command

Inside Jenkins → Execute Shell

```bash
echo "Hello Jenkins"
```

No files required.

---

# 4. Ansible Configuration Management

## File 1: hosts.ini

```ini
[local]
localhost ansible_connection=local
```

---

## File 2: setup.yml

```yaml
---
- name: Basic Server Setup
  hosts: local
  become: yes

  tasks:
    - name: Update apt cache
      apt:
        update_cache: yes

    - name: Install curl
      apt:
        name: curl
        state: present
```

Run:

```bash
ansible-playbook -i hosts.ini setup.yml
```

---

# 5. Gradle Project

## Create Project

```bash
mkdir HelloGradle
cd HelloGradle
gradle init --type java-application
```

---

## File: build.gradle

```groovy
plugins {
    id 'java'
    id 'application'
}

group = 'com.example'
version = '1.0'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'junit:junit:4.13.2'
}

application {
    mainClass = 'com.example.App'
}

task hello {
    doLast {
        println 'Hello, Gradle!'
    }
}
```

---

## File: App.java

Location:

```text
src/main/java/com/example/App.java
```

```java
package com.example;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello Gradle");
    }
}
```

Run:

```bash
gradle build
gradle run
gradle hello
```

---

# 6. Selenium Automation

## Install

```bash
pip install selenium
```

---

## File: test_google.py

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

driver = webdriver.Chrome()

driver.get("https://www.google.com")

search_box = driver.find_element(By.NAME, "q")

search_box.send_keys("Selenium with Python")

search_box.send_keys(Keys.RETURN)

time.sleep(3)

driver.quit()
```

Run:

```bash
python test_google.py
```

---

# 7. Docker Containerized Application

## Step 1

```bash
mkdir docker-flask-app
cd docker-flask-app
```

---

## File 1: app.py

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from Docker!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

## File 2: requirements.txt

```txt
Flask==3.1.0
```

---

## File 3: Dockerfile

```dockerfile
FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
```

---

## Commands

```bash
docker build -t flask-docker-app .
docker run -p 5000:5000 flask-docker-app
```

Open:

```text
http://localhost:5000
```

---

# 8. Kubernetes Automation

## File: deployment.yaml

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-minikube

spec:
  replicas: 1

  selector:
    matchLabels:
      app: hello

  template:
    metadata:
      labels:
        app: hello

    spec:
      containers:
      - name: hello-container
        image: kicbase/echo-server:1.0
        ports:
        - containerPort: 8080
```

---

## File: service.yaml

```yaml
apiVersion: v1
kind: Service
metadata:
  name: hello-service

spec:
  type: NodePort

  selector:
    app: hello

  ports:
  - port: 8080
    targetPort: 8080
```

---

## Commands

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
minikube service hello-service
```

---

# 9. Snyk Security

No coding files required.

## Commands

Install extension in VS Code.

Optional CLI:

```bash
npm install -g snyk
```

Login:

```bash
snyk auth
```

Scan:

```bash
snyk test
```

---

# 10. Maven Project

## Create Project

```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=MyMavenApp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

---

## File: pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>

    <artifactId>MyMavenApp</artifactId>

    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>

    <dependencies>

        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>

                <artifactId>maven-compiler-plugin</artifactId>

                <version>3.8.1</version>

                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>

            </plugin>

        </plugins>
    </build>

</project>
```

---

## File: App.java

Location:

```text
src/main/java/com/example/App.java
```

```java
package com.example;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello Maven");
    }
}
```

---

## Commands

```bash
mvn compile
mvn test
mvn package
mvn clean
```

