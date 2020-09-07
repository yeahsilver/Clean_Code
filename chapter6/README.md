# 📍  6장 객체와 자료구조



</br>



- ### 자료 추상화

  > 추상 인터페이스를 제공해 사용자가 구현을 모른 채 자료의 핵심을 조작할 수 있어야 진정한 의미의 클래스다.
  >
  > 자료를 세세하게 공개하는 것 보다는 추상적인 개념으로 표현하는 편이 좋다.

  ```java
  // 구현을 외부로 노출
  public class Point{
  	public double x;
  	public double y;
  }
  ```

  ```java
  // 구현을 완전히 숨김
  public interface Point{
  	double getX();
  	double getY();
  	double setCartesian(double x, double y)
  	double getR();
  	double getTheta();
  	void setPolar(double r, double theta)
  }
  ```

  

</br>



------



</br>



- ### 자료 / 객체 비대칭

  > 자료구조는 자료를 그대로 공개하며 별 다른 함수를 제공하지 않는다. 

  ##### 절차지향적인 도형

  > 새 도형을 추가하고 싶을 경우 Geometry 클래스에 속한 함수를 모두 고쳐야 한다.

  ```java
  public class Square{
  	public Point topLeft;
  	public double side;
  }
  
  public class Geometry {
  	public final double PI = 3.141592;
  	
  	public double area(Object shape) throws NoSuchShapeException{
  		if (shape instanceof Square){
  			Square s = (Square) shape;
  			return s.side * s.side;
  		}
  	}
  }
  ```

  ##### 객체 지향적인 도형

  > 새 도형을 추가해도 기존 함수에 아무런 영향을 미치지 않지만 새 함수를 추가하고 싶다면 도형 클래스 전부를 고쳐야 한다.

  ```java
  public class Square implements Shape{
  	private Point topLeft;
  	private double side;
  	
  	public double area(){
  		return side * side;
  	}
  	
  	public class Rectangle implements Shape{
  		private Point topLeft;
  		private double height;
  		private double width;
  		
  		public double area(){
  			return height * height
  		}
  	}
  }
  ```

  

  ### " 절차적인 코드는 기존 자료 구조를 변경하지 않으면서 새 함수를 추가하기 쉽다. 

  ### 반면 객체 지향 코드는 기존 함수를 변경하지 않으면서 새 클래스를 추가하기 쉽다. "



</br>



-------



</br>

- ### 디미터 법칙

  > 객체는 조회 함수로 내부 구조를 공개하면 안된다. 

  - #### 기차 충돌

    > 여러 객체가 한 줄로 이어진 기차처럼 보이는 코드

    ```java
    final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
    ```

    ##### 자료구조는 무조건 함수 없이 공개 변수만 포함하고 객체는 비공개 변수와 공개 함수를 포함하라. 이러한 형태로 구현하자.

    ```java
    final String outputDir = ctxt.options.scratchDir.absoultePath;
    ```

  - #### 잡종 구조

    > 절반은 객체, 절반은 자료구조인 잡종 구조는 어중간하게 내놓은 설계에 불과하다.
    >
    > 이러한 형태의 코드는 되도록 피하자.

  - #### 구조체 감추기

    ```java
    // 객체에 공개해야하는 메서드가 너무 많아진다.
    ctxt.getAbsolutePathOfScratchDirectoryOption();
    
    // 자료구조를 반환.
    ctxt.getScratchDirectoryOption().getAbsolutePath()
      
    // 이러한 형태의 코드를 작성하자
    BufferedOutputStream bos = ctxt.createScratchFileStream().classFileName
    ```

    

</br>



-----



</br>



- ### 자료 전달 객체

  > 공개변수만 있고 함수가 없는 클래스이다.

  ##### 빈(bean) 구조

  > 비공개 변수를 조회/설정 함수로 조작한다. 하지만 이러한 구조는 별 다른 이익을 제공하지 않는다. 

  - #### 활성 레코드

    > DTO(Data Transfer object)의 특수한 형태이다. 
    >
    > 공개 변수가 있거나 비공개 변수에 조회/설정 함수가 있는 자료구조이지만, 대개 save나 find와 같은 탐색 함수도 제공한다. 



</br>



------



</br>

- ### 결론

  > 객체는 동작을 공개하고 자료를 숨긴다.
  >
  > 새료운 자료 타입을 추가하는 유연성이 필요하다면 객체가 더욱 적합하다.



</br>

-----



</br>



- ### 느낀점

  > 주로 c++로 코딩을 하고, 객체보다는 절차지향적인 구조에 익숙해져있는 사람으로써 이번 6장을 읽으면서 약간 이해가 안되는 부분이 있었다. 그래서 몇번씩 읽어보며 정리를 해보니 이해가 조금씩 가기 시작했다. 무조건 객체지향이 좋다! 절차지향이 좋다! 라고 판별할 수 없는 각자 가지고 있는 자신만의 장점이 매력적이게 느껴졌고, 이번 챕터는 나에게 객체지향과 절차지향의 구조에 대해 다시 한번 생각해보게 되는 계기를 제공해주었고, 



