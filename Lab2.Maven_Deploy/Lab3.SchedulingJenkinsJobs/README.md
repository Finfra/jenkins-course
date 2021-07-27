# Scheduling Jenkins Jobs  : Source Control Polling
## Maven Setting : Build option
1. jenkins 홈에서 전 실습에서 생성한 Item인 git_source클릭

![](img/1.png)
2. 설정 변경을 위해 Configure클릭

![](img/2.png)

3. Build에서 Add build step선택 후 Execute shell 클릭

![](img/3.png)
4. "mvn package"라고 입력라고 후 Save 버튼 클릭

![](img/4.png)

5. Maven Build를 할 서버에 접속하여 Maven version을 확인

![](img/5.png)

6. Jenkins Home에서 Manage Jenkins 버튼 클릭 후 Global Tool Configuration 클릭

![](img/6.png)

7. Maven 항목에 Add Maven 버튼 클릭 후 Name에 Maven입력 후 Maven version 선택 후 Save 버튼 클릭

![](img/7.png)

## Item Setting
1. Jenkins Home에서 "git_source"선택

![](img/i1.png)

2. Configure → Add post-build action → Archive the artifacts 선택

![](img/i2.png)

3. Git Repository에 접속해서 Pom파일 위치를 알아내서 Files to artifacts에 "multi3/*.war"

![](img/i3.png)

4. Build Now 클릭해서 Build()

![](img/i4.png)

5. Jenkins Home에서 Build 성공여부 확인

![](img/i5.png)

6. "git_source"의 빌드 버전을 클릭하고 Console Output을 클릭해서 Console의 로그와 성공여부 확인 가능

![](img/i6.png)

7. "git_source"의 정보화면에서 Build된 war파일도 확인 가능

![](img/i7.png)

## Build Job을 포함하는 PipeLine 생성
1. Jenkins Home에서 + 버튼 클릭

![](img/p1.png)

2. View name에 "war_finfra_deploy"입력 → Build Pipeline View → OK

![](img/p2.png)

3. Setting확인 후 OK

![](img/p3.png)

4. 생성된 Pipeline 확인(특히 select Initial Job)

![](img/p4.png)



## 배포를 하는 Copy Item 생성
1. Jenkins Home → New Item → Enter an item name에  war_deployment 입력 → Freestyle Project → OK

![](img/c1.png)

2. Build Environment → Delete workspace before build starts 체크 → Save 클릭

![](img/c2.png)

3. Jenkins Home에서 Manage Jenkins에서 Manage Plugins 클릭

![](img/c3.png)

4. Available → Copy로 검색 → Copy Aritfact 체크 → Dwonload without restart 클릭

![](img/c4.png)
