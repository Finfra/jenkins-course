# Unit Testing in Jenkins
## 정상적인 코드에 대한 Coding Quality 체크를 위한 Pipline 생성 및 확인
1. Jenkins Home에서 New Item 클릭

![](img/g1.png)

2. item name에 good-code라고 입력 → Pipeline선택 → OK 클릭

![](img/g2.png)

3.  Pipeline Script에 아래와 같은 코드 입력 후 Save 버튼 클릭
```
pipeline {
    agent any
    stages {
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/finfra/sonarqube-jacoco-code-coverage.git'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
```
![](img/g3.png)

4. Build Now 버튼 클릭 후 정상 작동여부 확인

![](img/g4.png)

5. SonarQube Home에서 정상 코딩 Quality확인

![](img/g5.png)



## 비정상적인 코드에 대한 Coding Quality 체크를 위한 Pipline 생성 및 확인
1. Jenkins Home에서 New Item 클릭

![](img/b1.png)

2. item name에 bad-code라고 입력 → Pipeline선택 → OK 클릭

![](img/b2.png)

3.  Pipeline Script에 아래와 같은 코드 입력 후 Save 버튼 클릭
```
pipeline {
    agent any
    stages {
        stage('Clone sources') {
            steps {
                git branch: 'bad-code', url: 'https://github.com/finfra/sonarqube-jacoco-code-coverage.git'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
```

![](img/b3.png)

4. Build Now 버튼 클릭 후 Quality Gate에 걸리는 것을 확인

![](img/b4.png)

5. SonarQube에서 Failed 난 것을 확인 후 sonarqube-jacoco-code-coverage 클릭

![](img/b5.png)

6. Maintainability Rating is worse tha A를 클릭

![](img/b6.png)

7. Major issue를 확인

![](img/b7.png)

8. Major issue의 원인을 파악함.

![](img/b8.png)
