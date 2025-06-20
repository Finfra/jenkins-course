# Gradle과 Artifactory 작업
* Build한 Gradle소스를 Artifactory에 배포하고 확인하는 예제 입니다.

## Gradle build Item에 Artifactory 셋팅
* Gradle build Item에 Artifactory 셋팅을 추가하여 Build시 Artifactory로 Artifact가 배포되도록 셋팅합니다. 또한, Build시 Gradle을 사용함으로 Gradle관련 셋팅도 같이 합니다.
1. Jenkins Home에서 gradle_build item클릭
![](img/1.png)

2. 좌측 메뉴에서 Configure 클릭
![](img/2.png)

3. Build Environment에서 Gradle-artifactory Integration 클릭
![](img/3.png)

4. More Details에서 Project uses the Artifactory Gradle Plugin에 체크
![](img/4.png)

5. Artifactory Configuration에서 Aritifactory deployment server 확인 후 Refresh Repositories 버튼 클릭 후 Publishing repository와 Custom staging Configuration이 Default로 비어 있는 것 확인
![](img/5.png)

6. build에서 Add build step 클릭 후 Invoke Gradle script 선택
![](img/6.png)

7. Gradle 설정이 잘 되어 있는지 확인 후 Save 버튼 클릭
![](img/7.png)

## Jenkins에 Gradle Setting
* 위의 Item에 Gradle 옵션이 제대로 작동하기 위해서는 Jenkins에 gradle 관련 옵션을 추가해야 하는데 이번 예제에서는 Jenkins에 Gradle 관련 옵션을 추가합니다.

1. Jenkins Home에서 Manage Jenkins메뉴에서 Global Tool Configuration클릭

![](img/g1.png)

2. Jenkins 서버에 접속해서 gradle 버전 확인

![](img/g2.png)

3. Add Gradle 버튼 클릭 후 name에 gradle라고 입력 후 위에서 확인한 Gradle version선택 후 Save버튼 클릭

![](img/g3.png)

## Gradle build Item에 Gradle 빌드 셋팅 추가
* Jenkins에 Gradle옵션이 추가되면 gradle_build Item의 Build옵션에 gradle version을 셋팅할 수 있게 되는데 이번 예제에서는 Gradel build item의 Gradle build 옵션을 완료하고 실행하여 Artifactory에 Artifact가 잘 배포 되었는지 확인합니다.


1.Jenkins Home에서 gradle_build 클릭

![](img/b1.png)

2. 좌측 메뉴에서 Consigure 클릭

![](img/b2.png)

3. build에서 invoek gradle script를 클릭해서 Gradle Version에서 gradle 확인 후 Save 버튼 클릭

![](img/b3.png)

4. gradle_build의 좌측 메뉴에서 Build Now 클릭

![](img/b4.png)

## Build 확인
1. 성공한 Build의 "으"모양 아이콘 클릭

![](img/c1.png)

2. jFrog Artifactory에서 세부 정보 확인

![](img/c2.png)

3. 성공한 빌드에서 Console Output확인

![](img/c3.png)

4. gradle_build의 좌측 메뉴에서  "으"모양 아이콘 클릭해서 jFrog Artifactory의 Artifact확인

![](img/c4.png)
