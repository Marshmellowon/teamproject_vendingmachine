# Vending machine

##### 참여자: 이상원, 허현, 김병헌

## 1. 개발 환경

- Java Devleopemnt Kit 14.0.1
- JavaFx-SDK 11.0.2
- SceneBuilder - GLUON

## 2. 기본 세팅

### 1. Create JavaFx Project

![프로젝트 생성](https://github.com/Marshmellowon/imagefile/blob/master/javafx%20project%20making.JPG?raw=true)  
 JavaFx 프로젝트를 생성한다.

### 2. Library 설정

![library 설정](https://github.com/Marshmellowon/imagefile/blob/master/library%20%EC%82%AC%EC%A7%84.JPG?raw=true)
프로젝트 우클릭 -> Open Module Settings ->  
 Libraries -> 추가(+) -> Java -> jfxrt.jar 선택

### 3. Run/Debug Configurations 설정

![Run/Debug Configurations 설정](https://github.com/Marshmellowon/imagefile/blob/master/vm%20option.JPG?raw=true)  
 상단 탭 Run -> Edit Configurations ->  
 VM Option : --module-path="javafx SDK 위치\lib" --add-modules=javafx.controls,javafx.fxml

### 4. 실행

![빈 프로젝트 실행 화면](https://github.com/Marshmellowon/imagefile/blob/master/javafx%20%EC%8B%A4%ED%96%89%ED%99%94%EB%A9%B4.JPG?raw=true)  
 초기 JavaFx 프로젝트의 실행 화면 이다

이렇게 JavaFx를 위한 기본적인 설정이 끝났다.

## 3. Scene Builder

scene builder는 JavaFx로 UI를 구성하는 작업을 좀더 편하게 해주는 시각적인 레이아웃 도구이다.  
FXML파일을 생성하는데 사용된다.

- Scene Builder 연결  
  프로젝트 내에 src폴더 -> sample폴더(기본 JavaFx프로젝트 생성시)  
  -> sample.fxml 우클릭 -> Open in Scenebuilder  
  -> 프로젝트 생성 후 처음으로 scene builder를 열때는 사용할 scenebuilder.exe를 지정해 줘야 한다.

이제 UI를 신속하게 구현할 수 있는 작업도 끝났다.

## 4. 자판기

자판기를 만들어 보자

### 1. Controller를 연결해 준다.

![controller](https://github.com/Marshmellowon/imagefile/blob/master/%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC.JPG?raw=true)

### 2. Scene Builder 구성

![scenebuilder 화면](https://github.com/Marshmellowon/imagefile/blob/master/%EC%8B%A0%EB%B9%8C%EB%8D%94%20%ED%99%94%EB%A9%B4.JPG?raw=true)  
 자판기를 구성할 레이아웃을 만들어 준다.

### 3. id 지정

![id](https://github.com/Marshmellowon/imagefile/blob/master/code%20%ED%99%94%EB%A9%B4.JPG?raw=true)  
 id와 OnAction을 지정해 줘야 한다.

### 4. Main.java

![main code](https://github.com/Marshmellowon/imagefile/blob/master/main%ED%99%94%EB%A9%B4.JPG?raw=true)  
 Main.java의 구성이다. FXMLLoader로 FXML을 연결 시켜 준다.  
 창의 크기와 title을 바꿀 수 있다.

### 5. sample.fxml 화면

![fxml화면](https://github.com/Marshmellowon/imagefile/blob/master/fxml%20%ED%99%94%EB%A9%B4.JPG?raw=true)  
 scene builder에서 레이아웃을 구성하면 sample.fxml파일이 자동으로 생성된다.

### 6. Controller.java

#### - 더하기 버튼 동작

```java
public void plus(ActionEvent event) {
        int val; //수량에 있는 금액 int로
        String res; // 수량에 있는 string 가져오기
        String set; // 수량에 string 보내기
        String tf4val; // 현재 금액에 string 가져오기

        res = tf1.getText();
        val = Integer.parseInt(res);
        val += 1;
        set = Integer.toString(val);
        tf1.setText(set);
        func(6000);
    }
```

- 각 더하기 버튼을 눌렀을 경우의 동작이다.
- 수량 Textfield의 수량을 int형으로 변경하여 1을 더한 수량값을 다시수량 Textfield에 넣는다.

#### - 빼기 버튼 동작

```java
public void sub1(ActionEvent event) {
        int val3;
        String res3;
        String set3;

        res3 = tf1.getText();
        val3 = Integer.parseInt(res3);
        val3 -= 1;
        set3 = Integer.toString(val3);
        tf1.setText(set3);

        /*금액에서 빼기*/
        subfunc(6000);
        if (val3 < 0) {
            alert.setTitle("ERROR");
            alert.setHeaderText("수량이 없습니다");
            alert.showAndWait();
            tf1.setText("0");
            String a = tf4.getText();
            int r = Integer.parseInt(a);
            r += 6000;
            String e = Integer.toString(r);
            tf4.setText(e);
        }
    }
```

- 수량 빼기 버튼의 동작이다.
- 수량 Textfield의 수량을 int형으로 변경하여 1을 빼준뒤 다시 수량 Textfield에 넣는다.

#### - 현재 금액 Textfield

```java
public void func(int t) {
        int tf4int;
        String tf4val; // 현재 금액에 string 가져오기
        String taset;
        tf4val = tf4.getText();
        tf4int = Integer.parseInt(tf4val);
        tf4int += t;
        taset = Integer.toString(tf4int);
        tf4.setText(taset);
    }

    public void subfunc(int t2) {
        int tf4int2;
        String taset2;
        String tf4val;
        tf4val = tf4.getText();
        tf4int2 = Integer.parseInt(tf4val);
        tf4int2 -= t2;
        taset2 = Integer.toString(tf4int2);
        tf4.setText(taset2);
    }
```

- 현재 금액 Textfield의 금액을 더하거나 빼주는 함수다.
- 각 함수는 각 더하기 버튼과 빼기 버튼에서 동작이 이루어 진다.

#### - 거스름돈 알고리즘

```java
public void confirm() {
        String gettf4 = tf4.getText();
        int gettf4int = Integer.parseInt(gettf4);
        /*금액 입력창*/
        TextInputDialog dialog = new TextInputDialog();
        dialog.setTitle("확인");
        dialog.setHeaderText("투입 금액을 입력하시요");
        dialog.setContentText("금액");
        dialog.showAndWait();
        String a = dialog.getResult();
        tf5.setText(a); //금액 표시
        int resultmon = Integer.parseInt(a);
        int change = resultmon - gettf4int;

        /*거스름돈 알고리즘*/
        int[] coin = {10000, 5000, 1000, 500, 100, 50, 10};
        int leftcoin = 9;
        String[] str = new String[coin.length];
        for (int i = 0; i < coin.length; i++) {
            str[i] = Integer.toString(change / coin[i]);
            if (change / coin[i] > 0) {
                String m = Integer.toString(coin[i]);
                change %= coin[i];
                if (leftcoin >= change) {
                    leftcoin = change;
                }
            }
        }
    }
```

- 확인 버튼을 눌러 투입 금액을 입력 할 수 있는 창을 띄운다.
- 투입 금액 - 결재 금액 = 거스름돈, 거스름돈 알고리즘에 넣어 10000원부터 개수를 찾아낸다.
- 10원 이하는 남은 금액에 출력 한다.

자세한 코드는 [자판기 팀프로젝트](https://github.com/Algorithmteam2020/teamproject_vendingmachine/tree/master/src/sample) 를 참고.

### 7. 실행

![자판기 실행 화면](https://github.com/Marshmellowon/imagefile/blob/master/%EC%9E%90%ED%8C%90%EA%B8%B0%20%EC%8B%A4%ED%96%89.JPG?raw=true)  
 자판기 실행 화면 이다.

### 8. 동작 영상

[![image](https://github.com/Marshmellowon/imagefile/blob/master/%EC%9E%90%ED%8C%90%EA%B8%B0%20%EC%8B%A4%ED%96%89.JPG?raw=true)](https://www.youtube.com/embed/q6rl-1PpXjU)
   
## 9. 정리
> 자판기에서 남은 거스름돈을 보여주는 프로그램을 짜 보았다. 처음에 JavaFx와 Scene Builder를 연결하는 과정에서 시간이 많이 걸렸다.    
> 라이브러리 설정과 VM Option이 중요한 포인트였다. 연결이 된 후에는 레이아웃을 만들고 동작을 할 버튼에서 발생할 이벤트를 만들어주는것은 쉬웠다.   
> 더하기 버튼과 빼기 버튼에서 TextField를 파라미터로 불러와서 하나의 메서드에 여러개의 버튼을 연결하고 싶었지만 실패했다.
> 마지막 금액 출력에서 for문을 사용하려고 시도하였으나 실패하여 코드가 좀 길어졌다.    
> 다음에는 더 깔끔한 코드를 짤 수 있도록 노력해야겠다.