# 📍 2장 의미있는 이름

### 의미있는 이름을 짓기위한 간단한 규칙들


- #### 의도를 분명히 밝혀라

  > 단순히 이름만 고쳤는데도 함수가 하는 일에 대해 이해하기 쉬워진다.

  ```java
  int d; // 의도를 분명히 드러내지 못하는 변수명
  int elapseTimeInDays; // 의도를 분명히 드러내는 변수명
  ```

  

  </br>

  

- #### 그릇된 정보를 피하라

  > 그릇된 단서는 코드의 의미를 흐린다.

  ``` java
  int hp; // hypotenuse의 약어. 하지만 오해의 소지가 있음.
  class Account{} // Account라는 class라는 것이 분명함 
  ```

  

  </br>

  

- #### 의미 있게 구분하라

  > 읽는 사람이 차이를 알도록 이름을 짓는다.

  ``` java
  // 의미를 구별하기 힘든 경우 (= 어떤 기능을 하는지를 정확히 추측하기가 힘듦.)
  moneyAccount();
  money();
  
  // 의미를 구별하기 쉬운 경우
  getActiveAccount();
  getActiveAccounts();
  ```

  

  </br>

  

- #### 발음하기 쉬운 이름을 사용하라

  > 발음하기 쉬운 단어를 사용함으로써 가독성을 높인다.

  ``` java
  // 발음하기 어려운 경우
  class DtaRcrd102{
    private Date genmdhms;
    private Date modymdhms;
    private final String pszqint = "102";
  }
  
  // 발음하기 쉬운 경우
  class Customer{
    private Date generationTimestamp;
    private Date modificationTimestamp;
    private final String recordId = "102";
  }
  ```

  

  </br>

  

- #### 검색하기 쉬운 이름을 사용하라

  > 문자 하나를 사용하는 이름과 상수는 텍스트 코드에서 쉽게 눈에 띄지 않는다.

  ``` java
  // 검색하기 어려운 이름 (= 검색하면 많은 요소들이 나오는 경우)
  int e;
  
  // 검색하기 쉬운 이름
  int realDaysPerIdealDay = 4;
  ```

  

  </br>

  

- #### 인코딩을 피하라
  - ##### 헝가리식 표기법

    > 컴파일러가 타입을 점검하지 않을 경우에는 변수명에 타입명을 적어주었다.

      ```  java
    PhoneNumber phoneString; // 헝가리식 표기법
      ```

    

  </br>

  

  - #####멤버 변수 접두어

    > 클래스와 함수는 접두어가 필요 없을 정도로 작아야한다. 그러므로 멤버 변수 접두어를 붙일 필요가 없다.

      ```  java
    // 멤버 변수 접두어를 사용한 경우
    public class Part{
      private String m_dsc; // 설명 문자열
      void setName(String name){
        m_dsc = name;
      }
    }
    
    // 멤버 변수 접두어를 사용하지 않은 경우
    public class Part{
      String description;
      void setDescription(String description){
        this.description = description;
      }
    }
      ```

  

  ​		</br>

  

  - ##### 인터페이스 클래스와 구현 클래스

    > 인터페이스 이름은 접두어를 붙이지 않는 것이 좋다.
    >
    > 이유) 주의를 흐트리고 과도한 정보를 제공

  

  ​	</br>

- #### 자신의 기억력을 자랑하지 마라

  > 자신의 능력을 좋은 방향으로 사용하여 남들이 이해하는 코드를 제공해 주는 것이 좋다.

  

  </br>


- #### 클래스 이름

  > 클래스 이름과 객체 이름은 명사나 명사구가 적합하다.

    ```  java
  // 적합하지 않은 클래스 이름
  Class Data(){};
  
  // 적합한 클래스 이름
  Class Customer(){};
    ```

  

- #### 메소드 이름

  > 메소드 이름은 동사나 동사구가 적합하다
  >
  > 생성자를 중복정의할 때는 정적 팩토리 메소드를 사용한다.

    ```  java
  // 적합한 메소드 이름
  postPayment();
  deletePage();
    ```
  
``` java
  // 정적 팩토리 메소드를 사용하지 않은 경우
  Complex fulcrumPoint = new Complex(23.0);
  
  // 정적 팩토리 메소드를 사용한 경우
  Complex fulcrumPoint = Complex.FromRealNumber(23.0);
  ```
  
  
  
  </br>
  
  
  
- #### 기발한 이름은 피하라

  > 기발한 이름은 의도를 분명하고 솔직하게 표현할 수 없다. 

    ``` java
  // 기발한 이름
  whack();
  eatMyShort();
  
  // 명료한 이름
  kill();
  abort();
    ```

  

​	</br>



- #### 한 개념에 한 단어를 사용하라

  > 메소드와 메소드 이름은 독자적이고 일관적이여야 한다.

    ``` java
  /* 
  	같은 의미를 내포하는 변수명. 
  	manager나 controller 둘 중 하나를 선택해서 사용해야함. 
  */
  
  DeviceManager;
  DeviceController;
    ```

  

  </br>

  

- ####  말장난을 하지 마라

  > 한 단어를 두 가지 목적으로 사용하지 않아야 한다.

    ``` java
  // 더하기를 하는 메소드
  int add(){};
  
  /* 
  	값을 넣어주는 메소드
  	이때 메소드를 add라고 정의하면 해당 코드가 어떤 의미를 가지는지 이해하기 힘듦.
  */
  int insert(){};
    ```

  

  </br>



- #### 해법 영역에서 가져온 이름을 사용하라

  > 기술 개념에는 기술이름이 가장 적합하듯, 영역에 맞게 이름을 사용해야한다.



​	</br>



- #### 문제영역에서 가져온 이름을 사용하라	

  > 적절한 프로그래머 용어가 없다면 문제 영역에서 이름을 가져온다.



</br>



- #### 의미 있는 맥락을 추가하라

  > 맥락을 개선하면 함수를 쪼개기가 쉬워지므로 알고리즘도 좀 더 명확해진다.

  ``` java
  // 맥락이 분명하지 않은 변수
  private void printGuessStatistics(char candidate, int count){
    if (count == 0){
      number = "no";
    } else if (count == 1) {
      number = "1";
    }
    
    String guessMessage = String.format("There %s", verb);
    print(guessMessage);
  }
  
  // 맥락이 분명한 변수
  
  private class GuessStaticsMessage{
    public String make(char candidate, int count){
      createPluralDependenMessageParts(count);
      return String.format(
      "There %s", verb);
    }
    
    private void createPluralDependenMessageParts(int count){
      if(count == 0){
        thereAreNoLetters();
      } else if(count == 1){
        thereIsOneLetter();
    	} else {
        thereAreManyLetters(count);
      }
  }
  ```



- #### 불필요한 맥락을 없애라

  > 일반적으로 짧은 이름이 긴 이름보다 좋지만, 의미가 분명한 경우가 아니라면이름에 불필요한 맥락을 추가할 필요가 없다.

  ``` java
  // 불필요한 맥락을 가진 변수명
  int AccountAddress;
  int GSDAccountAddress;
  
  // 불필요한 맥락을 가지지 않은 변수명
  int postalAddress;
  int MACUrl;
  ```



</br>



----------



</br>

- #### 느낀점

  > 코딩을 하면서, 함수를 여러가지 만드는 경우에 가끔 왜 이렇게 함수를 여러가지 만들까? 그냥 한 메소드 안에 모든 것을 넣어도 되지 않은가? 주석처리 잘 하면 되지 않나? 라는 생각을 한 적이 있었다. 함수를 적게 만들면서 전역변수를 많이 사용하지 않아도 되니까 더 효율적이지 않을까? 했는데, 이 경우는 내가 혼자 작업할 때 한정이라는 것을 알게 되었다.  프로젝트를 진행하면서 혼자했던 프로젝트도 있고, 팀원들과 협업해서 프로젝트를 한 경험 모두 있는데, 혼자 프로그래밍을 한 경우의 시간이 더 많았어서 그런지 코드의 의미를 부여하지 않고 작업한 경우가 부지기수였다. 이렇게 과거의 나에 대해 생각을 하면서 2장을 읽게되니, 아직 배워야할 점이 정말 많다라는 것을 느꼈다. 또한 취업을 하게되면, 모든 프로젝트를 다른 분들과 함께하게 되기에, 2장의 내용을 잘 기억하며 개인프로젝트, 그리고 그룹 프로젝트에 적용해보면 더욱 좋은 코드를 만들어 나갈 수 있을 것이라는 확신이 들었다. 

</br>

----------
