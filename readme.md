# College Website DevOps Lab Practice

A detailed, step-by-step guide for beginners to build, version, and automate a simple college website using Git, Gitflow, and Jenkins.

---

## Task 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com).
2. Click **New Repository**.
3. Enter a repository name (e.g., `college-website-devops`).
4. Choose **Public** or **Private**.
5. Click **Create repository**.

---

## Task 2: Clone the Repository Locally

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

---

## Task 3: Create the HTML File

1. In your project folder, create a file named `index.html`.

```html
<!DOCTYPE html>
<html>
<head>
    <title>College Information</title>
</head>
<body>
    <h1>ABC College</h1>
    <p>Address: 123 Main Street, City, State, ZIP</p>
    <p>Contact Number: (123) 456-7890</p>
</body>
</html>
```

---

## Task 4: Initialize Git

```bash
git init
```

---

## Task 5: Add and Commit the HTML File

```bash
git add index.html
git commit -m "Add initial college website HTML"
```

---

## Task 6: Create and Switch to the Develop Branch

```bash
git checkout -b develop
```

---

## Task 7: Add Remote and Push Develop Branch

```bash
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin develop
```

---

## Task 8: Initialize Gitflow

```bash
git flow init
```
- Accept all defaults by pressing Enter.

---

## Task 9: Start a Feature Branch for Enhancements

```bash
git flow feature start enhance-website
```

---

## Task 10: Update `index.html` (Add NAAC Code & Courses)

Edit `index.html` and add:

```html
    <p>NAAC Code: NAAC12345</p>
    <p>Courses Offered: B.Sc, B.Com, B.A</p>
```

---

## Task 11: Add and Commit the Changes

```bash
git add index.html
git commit -m "Add NAAC code and courses to website"
```

---

## Task 12: Finish the Feature Branch

```bash
git flow feature finish enhance-website
```

---

## Task 13: Push Changes to Develop Branch

```bash
git push origin develop
```

---

## Task 14: Create a Jenkinsfile for Automation

Create a file named `Jenkinsfile`:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'No build step needed for static HTML.'
            }
        }
        stage('Test') {
            steps {
                script {
                    if (!fileExists('index.html')) {
                        error('index.html not found!')
                    }
                    echo 'index.html exists.'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'index.html', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy step placeholder. Add deployment scripts here if needed.'
            }
        }
    }
}
```

---

## Task 15: Add and Commit Jenkinsfile

```bash
git add Jenkinsfile
git commit -m "Add Jenkinsfile for CI pipeline"
git push origin develop
```

---

## Task 16: Jenkins Configuration

1. **Install Jenkins**  
   - Download and install Jenkins from [jenkins.io](https://jenkins.io/download/).
   - Start Jenkins and open it in your browser (`http://localhost:8080`).

2. **Create a New Pipeline Job**
   - Click **New Item**.
   - Enter a job name (e.g., `college-website-pipeline`).
   - Select **Pipeline** and click OK.

3. **Configure Source Control**
   - In the job configuration, scroll to **Pipeline**.
   - Select **Pipeline script from SCM**.
   - Choose **Git**.
   - Enter your repository URL:  
     `https://github.com/<your-username>/<your-repo>.git`
   - Set branch to `develop`.

4. **Save and Build**
   - Click **Save**.
   - Click **Build Now** to run your pipeline.

---

**You now have a complete DevOps workflow for your static college website, including Git, Gitflow, and Jenkins automation!**