# DevOps CI/CD Pipeline Project

## Application Build Process

This project demonstrates an end-to-end CI/CD pipeline using Git, GitHub, Jenkins, Maven, and Apache Tomcat.

### Pipeline Workflow

```
Developer
    │
    ▼
Git Server
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins Job
    │
    ├── Pull Source Code
    ├── Compile Java Application
    ├── Run Maven Build
    ├── Generate WAR File
    ▼
Apache Tomcat Server
    │
    ▼
Application Deployment
```

## Build Steps

### Step 1: Clone the Repository

```bash
git clone https://github.com/<your-username>/<repository-name>.git
cd <repository-name>
```

---

### Step 2: Verify Java Installation

```bash
java -version
```

---

### Step 3: Verify Maven Installation

```bash
mvn -version
```

---

### Step 4: Build the Application

Compile the project and generate the WAR file.

```bash
mvn clean package
```

After a successful build, the WAR file will be available under:

```
target/
```

Example:

```
target/sampleapp.war
```

---

### Step 5: Configure Jenkins

Create a Jenkins Freestyle or Pipeline Job.

Configure the following:

- Source Code Management: Git
- Repository URL: GitHub Repository
- Branch: main (or master)
- Build Tool: Maven
- Goals:

```
clean package
```

Save and Build the Job.

---

### Step 6: Jenkins Build Process

Jenkins performs the following tasks:

- Pulls source code from GitHub
- Compiles Java source code
- Downloads project dependencies
- Executes Maven build
- Generates WAR artifact
- Marks build as Success or Failure

---

### Step 7: Deploy to Apache Tomcat

Copy the generated WAR file to the Tomcat webapps directory.

Linux

```bash
cp target/*.war /opt/tomcat/webapps/
```

Windows

```
Copy target\<application>.war
to

C:\Program Files\Apache Software Foundation\Tomcat\webapps\
```

Restart Tomcat.

---

### Step 8: Access the Application

```
http://<Tomcat-IP>:8080/<application-name>
```

Example

```
http://localhost:8080/sampleapp
```

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Git | Version Control |
| GitHub | Source Code Repository |
| Jenkins | Continuous Integration |
| Maven | Build Automation |
| Java | Application Development |
| Apache Tomcat | Application Server |

---

## CI/CD Flow

```
Developer
     │
     ▼
 Git Server
     │
     ▼
 GitHub Repository
     │
     ▼
 Jenkins
     │
     ├── Git Pull
     ├── Maven Build
     ├── Generate WAR
     ▼
 Apache Tomcat
     │
     ▼
 Application Running
```

## Build Command

```bash
mvn clean package
```

## Deploy Command

Linux

```bash
cp target/*.war /opt/tomcat/webapps/
```

## Result

- Source code stored in GitHub
- Jenkins automatically pulls the latest code
- Maven builds the Java application
- WAR file is generated
- Apache Tomcat deploys the application
- Application becomes accessible through a web browser
