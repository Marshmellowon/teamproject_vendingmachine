# Vending machine
##### 참여자: 이상원, 허현, 김병헌

### 1. 개발 환경
- Java Devleopemnt Kit 14.0.1   
- JavaFx-SDK 11.0.2   
- SceneBuilder - GLUON

### 2. 기본 세팅
1. Create JavaFx Project     
![프로젝트 생성](https://github.com/Marshmellowon/imagefile/blob/master/javafx%20project%20making.JPG?raw=true)   
JavaFx 프로젝트를 생성한다.   

2. Library 설정
![library 설정](https://github.com/Marshmellowon/imagefile/blob/master/library%20%EC%82%AC%EC%A7%84.JPG?raw=true)
프로젝트 우클릭 -> Open Module Settings ->    
Libraries -> 추가(+) -> Java -> jfxrt.jar 선택    

3. Run/Debug Configurations 설정   
![Run/Debug Configurations 설정](https://github.com/Marshmellowon/imagefile/blob/master/vm%20option.JPG?raw=true)   
상단 탭 Run -> Edit Configurations ->    
VM Option : --module-path="javafx SDK 위치\lib" --add-modules=javafx.controls,javafx.fxml   

4. 실행   
![빈 프로젝트 실행 화면](https://github.com/Marshmellowon/imagefile/blob/master/javafx%20%EC%8B%A4%ED%96%89%ED%99%94%EB%A9%B4.JPG?raw=true)   
초기 JavaFx 프로젝트의 실행 화면 이다   

이렇게 JavaFx를 위한 기본적인 설정이 끝났다.   
### 3. Scene Builder
scene builder는 JavaFx로 UI를 구성하는 작업을 좀더 편하게 해주는 시각적인 레이아웃 도구이다.   
FXML파일을 생성하는데 사용된다.

- Scene Builder 연결   
프로젝트 내에 src폴더 -> sample폴더(기본 JavaFx프로젝트 생성시)   
-> sample.fxml 우클릭 -> Open in Scenebuilder    
-> 프로젝트 생성 후 처음으로 scene builder를 열때는 사용할 scenebuilder.exe를 지정해 줘야 한다.

이제 UI를 신속하게 구현할 수 있는 작업도 끝났다.

### 4. 자판기 
자판기를 만들어 보자
1. Controller를 연결해 준다.   
   ![controller](https://github.com/Marshmellowon/imagefile/blob/master/%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC.JPG?raw=true)   

2. Scene Builder 구성   
![scenebuilder 화면](https://github.com/Marshmellowon/imagefile/blob/master/%EC%8B%A0%EB%B9%8C%EB%8D%94%20%ED%99%94%EB%A9%B4.JPG?raw=true)   
자판기를 구성할 레이아웃을 만들어 준다.   

4. id 지정   
![id](https://github.com/Marshmellowon/imagefile/blob/master/code%20%ED%99%94%EB%A9%B4.JPG?raw=true)   
id와 OnAction을 지정해 줘야 한다.   

4. sample.fxml 화면   
![fxml화면](https://github.com/Marshmellowon/imagefile/blob/master/fxml%20%ED%99%94%EB%A9%B4.JPG?raw=true)   
scene builder에서 레이아웃을 구성하면 sample.fxml파일이 자동으로 생성된다.

5. Controller.java   
![controller 사진](https://github.com/Marshmellowon/imagefile/blob/master/controller%20%EC%BD%94%EB%93%9C.JPG?raw=true)   
Controller code 화면이다.   
자세한 코드는 [자판기 팀프로젝트](https://github.com/Algorithmteam2020/teamproject_vendingmachine) 를 참고.   

6. Main.java    
![main code](https://github.com/Marshmellowon/imagefile/blob/master/main%ED%99%94%EB%A9%B4.JPG?raw=true)   
Main.java의 구성이다. FXMLLoader로 FXML을 연결 시켜 준다.   
창의 크기와 title을 바꿀 수 있다.   

7. 실행   
[자판기 실행 화면]   
자판기 실행 화면 이다.   

8. 동작 영상   
[영상]