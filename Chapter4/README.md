# 📍 4장 주석



</br>



###  나쁜 코드에 주석을 달지 마라. 새로 짜라.

#### - 브라이언 W. 커니핸, P.J. 플라우거



</br>



----



</br>



- ### 주석은 나쁜 코드를 보완하지 못한다.

  ###### 자신이 저지른 난장판을 주석으로 설명하려 애쓰는 대신에 그 난장판을 깨끗이 치우는데 시간을 보내라!

  > 코드에 주석을 추가하는 일반적인 이유는 코드 품질이 나쁘기 때문이다.



</br>



----



</br>



- ###  코드로 의도를 표현하라!

  - ##### 코드로 의도를 표현하지 않은 경우

    ```java
    // 직원에게 복지 혜택을 받을 자격이 있는지 검사한다.
    if((employee.flags & HOURLY_FLAG) && (employee.age > 65))
    ```

    

  - ##### 코드로 의도를 표현한 경우

    ```java
    if(employee.isEligibleForFullBenefits())
    ```

    

</br>



----



</br>



- ### 좋은 주석

  - #### 법적인 주석

    > 표준 라이선스나 외부 문서를 참조

    ```java
    // Copyright (C) 2003, 2004, 2005 by Object Mentor, Inc. All rights reserved
    // GNU General Public License 버전 2 이상을 따르는 조건으로 배포한다.
    ```

     

    </br>

    

  - #### 정보를 제공하는 주석

    > 기본적인 정보를 주석으로 제공하면 편하지만, 가능하다면 함수 이름에 정보를 담는 편이 더 좋다. 

    ```java
    // kk:mm:ss EEE, MM dd yyyy 형식이다
    Pattern timeMatcher = Pattern.compile("\\d*: \\d*: \\d*");
    ```

  

  ​	</br>

  

  - #### 의도를 설명하는 주석

    > 구현을 이해하게 도와주는 선을 넘어 결정에 깔린 의도까지 설명하는 경우가 있다. 

    ```java
    return 1 // 오른쪽 유형이므로 정렬 순위가 더 높다.
    ```

    더 나은 예제

    ```java
    // ~~~~ 한다.
    for(int i = 0; i < N ; i++){
    	// 구현 내용
    }
    ```

  

  </br>

  

  - #### 의미를 명료하게 밝히는 주석

    > 인수나 반환값이 표준 라이브러리나 변경하지 못하는 코드에 속한다면, 의미를 명료하게 밝히는 주석이 유용하다. 하지만 더 나은 방법이 없는지 고민하고 정확히 달도록 각별히 주의한다.

    

    </br>

  

  - #### 결과를 경고하는 주석

    > 다른 프로그래머들에게 결과를 경고하기 위한 목적으로 사용되는 주석이다. 
    >
    > 다른 프로그래머들의 실수를 면할 수 있게 도와준다. 

    

    </br>

    

  - #### TODO 주석

    > 앞으로 할일을 주석으로 남겨 놓는다. 
    >
    > 당장 구현하기 어려운 업무를 기술한다. 

  

  ​	</br>

  

  - #### 중요성을 강조하는 주석

    > 대수롭지 않은 코드의 중요성을 강조하기 위해서 주석을 사용한다.

  

  </br>

--------------

​		</br>



- ### 나쁜 주석

  > 허술한 코드를 지탱 / 엉성한 코드를 변명 / 미숙한 결정을 합리화하는 주석이 대부분이다. 

  - #### 주절거리는 주석

    > 주절거리는 주석은 코드 판독이 불가능하다. 

    

    </br>

    

  - #### 같은 이야기를 중복하는 주석

    > 주석이 코드보다 더 많은 정보를 제공하지 못한다. 이러한 주석은 코드만 지저분하고 정신없게 만든다. 

    

    </br>

    

  - #### 오해할 여지가 있는 주석

    > 프로그래머의 의도에 딱 맞을 정도로 엄밀하게 주석을 달지 못하는 경우가 발생할 수 있다. 
    >
    > 이럴 경우 주석으로 인해 코드 해석의 혼란성이 증가할 수 있다. 

    

    </br>

    

  - #### 의무적으로 다는 주석

    > 아래와 같은 주석은 아무 가치도 없다. 

    ```java
    /*
    * @param title: CD 제목
    * @param author: CD 저자
    * @param tracks: CD 트랙 숫자
    */
    ```

    

    </br>

    

  - #### 이력을 기록하는 주석

    > 소스코드 관리 시스템의 존재로 변경이력을 기록하는 주석은 제거하는 편이 좋다. 

  

  ​	</br>

  

  - #### 있으나 마나 한 주석

    > 당연한 사실을 언급하는 주석은 프로그래머에게 주석을 무시하는 습관을 줄 수 있다.

    ```java
    /** 월 중 일자 */
    private int dayOfMonth
    ```

    

    </br>

    

  - #### 무서운 잡음

    > 문서를 제공해야하는 잘못된 욕심으로 탄생한 잡음을 생성한다. 
    >
    > 잘라서 붙혀넣기 오류가 생길 수도 있다.

    ```java
    // the name
    private String name;
    
    // the version
    private String version;
    
    // the version
    private String licenceName;
    ```

  

  ​		</br>

  

  - #### 함수나 변수로 표현할 수 있다면 주석을 달지 마라

    - ##### 주석으로 코드를 설명한 경우

      ```java
      // 전역 목록 <smodule>에 속하는 모듈이 우리가 속한 하위 시스템에 의존하는가?
      if(smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
      ```

    - ##### 변수와 함수로 코드를 설명한 경우

      ```java
      ArrayList moduleDependees = smodule.getDependSubsystems();
      String ourSubSystem = subSysMod.getSubSystem();
      if(moduleDependees.contains(ourSubSystem))
      ```

    

    ###### 		주석이 필요하지 않은 코드는 코드로 주석을 표현하도록 노력하자.

    

  </br>

  

  - #### 위치를 표시하는 주석

    > 위치를 표현하는 주석은 반드시 필요할 때만, 드물게 사용해야한다.그렇지 않으면 낮은 가독성을 유발할 수 있다.

    ```java
    // ACTION //////////////
    ```

    

    </br>

    

  - #### 닫는 괄호에 다는 주석

    > 작고 캡슐화된 함수에서는 닫는 괄호에 주석을 달아도 의미가 없다. 

    ```java 
    try{
    	
    } catch {
      
    } // catch
    ```

    

    </br>

    

  - #### 주석으로 처리한 코드

    > 다른 프로그래머들이 주석을 지우기를  조심스럽게 만든다. 이로인해 쓸모없는 코드가 쌓이는 경우가 많다.

    ```java
    int num;
    // int n;
    ```

  

  ​	</br>

  

  - #### HTML 주석

    > HTML 주석은 편집기 /IDE에서조차 읽기 어렵다.

  

  ​	</br>

  

  - #### 전역 정보

    > 주석을 달아야 한다면 근처에 있는 코드만 기술하라. 
    >
    > 전역 정보는 바로 아래의 함수가 아니라 시스템 어디가에 있는 다른 함수를 설명한다는 의미를 가지고 있다.

    ```java
    /* 포트 기본값: 80 */
    ```

  

  ​	</br>

  

  - #### 너무 많은 정보

    > 장황한 정보를 늘어놓지 마라. 필요 없다.

    

    ​	</br>

    

  - #### 모호한 관계

    > 코드는 둘 사이의 관계가 명백해야한다. 
    >
    > 주석 자체가 다시 설명을 요구한다면 이는 좋은 주석이 아니다. 

  

  ​		</br>

  #### 	

  - #### 함수 헤더

    > 짧은 함수는 긴 설명이 필요하지 않다.
    >
    > 함수 헤더는 짧고 한가지만 수행하며 이름을 잘 붙힌 함수가 주석보다 낫다. 

    

  ​		</br>

  

--------

#### 

</br>

### 느낀점

> 프로그래밍을 할 때, 주석을 많이 달아놓곤 했었다. 그것도 아주 정갈하고 예쁘게.  그 이유는 내 기억력이 내가 코딩한 모든 코드를 담아내기에는 부족하다는 것을 알기 때문이였다. 그런데 '4장 주석' 을 읽어보니, 애초에 주석이 필요없이 코드를 짜는 것이 가장 중요한 부분이였고, 나는 이에 반하는 행동을 하고 있었던 것이다.  분명 한번에 괜찮은 코드를 짜기란 그리고 한번에 주석을 표현할 코드를 구현하는 것 자체가 쉽지 않을 것이라는 알지만, 미리 적어놓은 주석을 코드에 녹이는 순서로 코딩을 하게된다면 주석이 많이 없어지지 않을까? 라는 생각을 하게되었다. 이번 4장은 나에게 정말 큰 충격을 주었고, 오늘부터라도 코딩을 할 때, 주석을 달지 않고 오직 코드를 통해서 자신의 이야기 할 수 있는 개발자가 되어야겠다고 생각했다. 



</br>



------



</br> 

- ### 내가 개선한 한줄 코드 소개

  > 온라인 시험 부정행위 방지 ios 앱 일부 발췌 (제가 100% 코딩한 코드입니다!)

  - #### 리팩터링 전

    ```swift
    override func viewDidLoad() {
            super.viewDidLoad()
            updateUI()
            answerTextField.addDoneButtonOnKeyboard()
            
            // 카메라 권한 체크
            if AVCaptureDevice .authorizationStatus(for: .video) == .authorized{
                GazeTracker.initGazeTracker(license: "dev_zjr3b5ffioy6jiynqtv99txxoi5dswqo6nukescw", delegate: self)
            } else {
                AVCaptureDevice.requestAccess(for: .video, completionHandler: {
                    response in
                    if response{
                        GazeTracker.initGazeTracker(license: "dev_zjr3b5ffioy6jiynqtv99txxoi5dswqo6nukescw", delegate: self)
                    }
                })
            }
        }
    func updateUI(){
            courseNameLabel.text = courseName
            professorLabel.text = professorName
        }
    ```

    

  - #### 리팩터링 후

    ```swift
    override func viewDidLoad() {
            super.viewDidLoad()
            updateUI()
            answerTextField.addDoneButtonOnKeyboard()
            cameraPermissionCheck()
            
        }
        
        func updateUI(){
            courseNameLabel.text = courseName
            professorLabel.text = professorName
        }
        
        func cameraPermissionCheck(){
            if AVCaptureDevice .authorizationStatus(for: .video) == .authorized{
                GazeTracker.initGazeTracker(license: "dev_zjr3b5ffioy6jiynqtv99txxoi5dswqo6nukescw", delegate: self)
            } else {
                AVCaptureDevice.requestAccess(for: .video, completionHandler: {
                    response in
                    if response{
                        GazeTracker.initGazeTracker(license: "dev_zjr3b5ffioy6jiynqtv99txxoi5dswqo6nukescw", delegate: self)
                    }
                })
            }
        }
    ```

    
