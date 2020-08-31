# 📍 5장 형식 맞추기



</br>



  ### 프로그래머라면 형식을 깔끔하게 맞춰 코드를 짜야한다. 
  ### 코드 형식을 맞추기 위한 간단한 규칙을 정하고 그 규칙을 착실히 따라야 한다.



</br>



------



</br>

- ### 형식을 맞추는 목적

  > 코드 형식은 의사소통의 일환이다.
  >
  > 오늘 구현한 코드의 가독성은 앞으로 바뀔 코드의 품질에 지대한 영향을 미친다.



</br>



-----



</br>



- ### 적절한 행 길이를 유지하라

  >500줄을 넘지 않고 대부분 200줄 정도인 파일로도 커다란 시스템을 구축할 수 있다.
  >
  >일반적으로 큰 파일보다 작은 파일이 이해하기 쉽다. 

  

  </br>

  

  - #### 신문 기사처럼 작성하라

    > 이름은 간단하면서 설명이 가능하게 지어라.
    >
    > 아래로 내려갈 수록 세세하게 묘사한다.
    >
    > 신문의 기사는 대부분 아주 짧다. 그러니 코드도 짧게 작성하라!

    

  </br>

  

  - #### 개념은 빈 행으로 분리하라

    > 생각 사이에는 빈 행을 넣어 분리해야 마땅하다.
    >
    > 빈 행은 새로운 개념을 시작한다는 시각적 단서가 될 수 있다. 
    >
    > 빈 행은 가독성을 높인다.

    

  </br>

  

  - #### 세로 밀집도

    > 서로 밀접한 코드 행은 세로로 가까이 놓여야 한다.

    ###### 세로 밀집도 구현 전

    ```java
    public class ReporterConfig{
    	/*
    	* 리포터 리스너의 클래스 이름
    	*/
    	private String m_className;
    	
    	/*
    	*	리포터 리스너의 속성
    	*/
    	private List<property> m_properties = new ArrayList<Property>();
    	public void addProperty(Property property){
    		m_properties.add(property);
    	}
    }
    ```

    

    </br>

    

    ###### 세로 밀집도 구현 후

    ```java
    public class ReporterConfig{
    	private String m_className;
    	private List<property> m_properties = new ArrayList<Property>();
    	
    	public void addProperty(Property property){
    		m_properties.add(property);
    	}
    }
    ```

    

    </br>

    

  - #### 수직거리

    > 변수는 사용하는 위치에 최대한 가까이 선언한다. 

    ```java
    private satic void readPreferences(){
    	InputStream is = null;
    	try{
    		is =. ew FileInputStream(getPreferenceFile());
    		setPreferences().load(is);
    	} catch (IOException e){
    		try{
    			if(is != null) is.close();
    		} catch (IOException e1){
    		}
    	}
    }
    ```

    > 인스턴스 변수는 클래스의 맨 처음에 선언한다. (c++에서는 맨 마지막에 선언 (=가위규칙))

    ```java
    private String fName;
    
    private vector<Test> fTests = new Vector<Test>(10);
    public testSuite(){
    ...
    }
    ```

    > 한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치한다. 
    >
    > 개념적인 친화도거 높을수록 코드를 가까이 배치한다.

    ```java
    public class Assert{
    	static public void assertTrue(String message, boolean condition){
    		if(!condition)
    			fail(meddage);
    	}
    	static public void assertTrue(boolean condition){
    		assertTrue(null, condition);
    	}
    }
    ```

    

    </br>

    

  - #### 세로 순서

    > 함수 호출 종속성은 아래 방향으로 유지한다. 
    >
    > 가장 중요한 개념을 먼저 표현한다.

    

    </br>

    

- ### 가로 형식 맞추기

  > 프로그래머는 명백하게 짧은 행을 선호한다.

  - #### 가로 공백도와 밀집도

    > 공백을 사용해 밀접한 개념과 느슨한 개념을 표현한다. 

    ```java
    private void measureLine(String line){
    	lineCount++;
    	int lineSize = line.length();
    	totalChars += lineSize;
    	lineWidthHistogram.addLine(lineSize, lineCount);
    	recordWidestLine(lineSize);
    }
    ```

    ```java
    public class Quadratic {
    	public static double root1(double a, double b, double c){
    		double determinant = determinant(a,b,c);
    	}
    }
    ```

    

  - #### 가로 정렬

    > 정렬은 엉뚱한 부분을 강조하기에 진짜 의도가 가려지는 경우가 많다.

  

  ​	</br>

  

  - #### 들여쓰기

    > 범위로 이루어진 계층을 표현하기 위해 코드를 들여쓴다. (while / if문 포함)

    

    

  - #### 가짜 범위

    > while문 끝에 세미콜론을 붙히는 경우 => 괄호로 감싼다.

    ```java
    while(dis.read(buf, 0, reaBufferSize) != 1)
    ;
    ```

    

</br>



------



</br>

- ### 팀 규칙

  > 팀은 한가지 규칙에 합의해야 한다. 그리고 모든 팀원은 그 규칙을 따라야 한다.
  >
  > 좋은 소프트웨어 시스템은 읽기 쉬운 문서로 이루어진다.



</br>



------



</br>



- ### 느낀점

  > 지금까지 프로젝트를 진행하면서 그냥 읽기 좋게 빈행을 만들고 내 마음대로 코딩을 했었다. 내 마음대로 형식을 맞추다보니 문득 형식을 맞추는 것도 규칙이 있지 않을까? 라고 생각을 했으면서도 그 규칙을 찾아보지는 않았던 것 같다. 역할이 주어진 뒤 코딩을 하면 어차피 코딩하는 내가 주인공이고 나만 알아볼 수 있으면 되겠지! 라는 마음 때문이였다. 하지만 이번 챕터를 정독한 뒤, 저번 챕터를 읽을 때와 마찬가지로 내 코드에 대해 반성을 하게 되었다. 그 이유는 내 생각이 너무너무 잘못되었다는 것을 알게되었기 때문이다. 내 태도부터 내 습관까지 모든게 다 문제였다! 그래서  이번 챕터를 읽은 오늘부터라도 규칙을 잘 지키며 아주 예쁜 코드를 만들고 싶다라는 생각이 들었다. 



</br>



-----



</br>



- ### 내가 개선한 한줄 코드 소개

  > 온라인 시험 부정행위 방지 ios 앱 일부 발췌 (본인 코딩)

  - ##### 리팩터링 전

    > 빈행의 형식이 규칙적이지 않음

    ```swift
    func moveToMain(){
            DispatchQueue.main.async {
                let vc = self.storyboard?.instantiateViewController(identifier: "main") as! MainViewController
                              
                vc.modalPresentationStyle = .fullScreen
                vc.idText = self.idText
                vc.nameText = self.nameText
                vc.majorText = self.majorText
                vc.accessToken = self.accessToken
                
                              
                self.present(vc, animated: true)
            }
        }
    ```

    

  - ##### 리팩터링 후

    ```java
     func moveToMain(){
            DispatchQueue.main.async {
                let vc = self.storyboard?.instantiateViewController(identifier: "main") as! MainViewController
                vc.modalPresentationStyle = .fullScreen
                vc.idText = self.idText
                vc.nameText = self.nameText
                vc.majorText = self.majorText
                vc.accessToken = self.accessToken
                              
                self.present(vc, animated: true)
            }
        }
    ```

    
