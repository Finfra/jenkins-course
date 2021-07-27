# Start building CI and CD pipeline with Jenkins and Maven
## Start building pipeline with Jenkins and Maven
1. Jenkins Home에서 "war_deployment"클릭

![](img/1.png)

2. Configure클릭

![](img/2.png)

3. Build → Add build step → Copy artifacts from another project 선택

![](img/3.png)

4. Project name에 "git_source" 입력후 Apply

![](img/4.png)

5. Jenkins Home에서 Manage Jenkins에서 Manage Plugins 클릭

![](img/5.png)

6. Available → Deploy to container로 검색 → Deploy to container 체크 → Install Without restart 클릭

![](img/6.png)

7. Configure클릭

![](img/2.png)

8. Tomcat 서버 ip 확인 후 접속

![](img/9.png)

9. Jenkins Home에서 "war_deployment"클릭

![](img/1.png)

10. Configure클릭

![](img/2.png)

11. Post-build Actions에서 "Deploy war/ear to a container"선택 후 WAR/EAR files에 "**/*.war"입력하고 Constext path에 "finfra_app_$BUILD_NUMBER"입력 후 Add Container 버튼 클릭

![](img/11.png)

12. Tomcat Version 지정

![](img/12.png)

13. 아이디와 비번 추가 위해 add버튼 선택 후 Jenkins 클릭

![](img/13.png)
14. tomcat서버에 접속해서 비번을 얻고 Password항목에 입력

![](img/14.png)

15. ID에 admin_forTomcat입력 후 Add 클릭

![](img/15.png)

16. Credentials에 admin/**** 을 선택

![](img/16.png)
17. Tomcat URL에 http://jm1:8080 입력

![](img/17.png)

18. Build Triggers → build after other projects are built 체크 → Projects to watch에 "git_source"입력 → Save 버튼 클릭

![](img/18.png)


## Git Source와 앱간 연동
1. "git_source" item의

![](img/c1.png)

2. "Build other project"선택

![](img/c2.png)
3. Downstream Project Names에 war_deployment 입력 후 Save버튼 클릭

![](img/c3.png)

## Pipeline 확인
1. Jenkins Home에서 war_finfra_deploy 클릭

![](img/p1.png)

2. Run 클릭

![](img/p2.png)

3. 10초 이상 기다리고 브라우저 리프레쉬 해줌.

![](img/p3.png)

4. Tomcat서버에서 배포가 잘 되었는지 확인함.

![](img/p4.png)

5. 해당 Deploy의 Contents

![](img/p5.png)

## cf)  git Repository를 fork떠서 내용을 수정하고 적용되는지 확인해 보세요.
