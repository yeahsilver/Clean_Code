## 📍 7장 오류 처리



</br>



- ### 오류 코드보다 예외를 사용하라

  > 오류가 발생하면 예외를 던지는 편이 낫다. 



</br>



------



</br>



- ### Try-Catch-Finally문부터 작성하라

  > Try-Catch-Finally문으로 시작하면 try 블록에서 무슨 일이 생기든지 호출자가 기대하는 상태를 정의하기 쉬워진다.
  >
  > 강제로 예외를 일으키는 테스트 케이스를 작성한 후 테스트를 통과하게 코드를 작성하는 방법을 권장한다.



</br>



--------



</br>

- ### 미확인(unchecked) 예외를 사용하라

  > 확인된 예외는 OCP를 위반한다

  ###### - 확인된 예외

  > 확인된 예외는 메서드에 throws 키워드로 정의되어있는 예외들이다. 따라서 사용자가 해당 메서드를 사용할 때 발생하는 예외를 확인할 수 있으므로 꼭 try-catch 블록으로 예외를 처리해야 한다.

  ###### - 미확인 예외

  >  자바가 알아서 던져주는 예외이다. 따라서 메서드에 throws 키워드를 사용해 정의하지 않아도 된다. 미확인된 예외는 RuntimeException을 상속받아야 한다.

  ###### - OCP (Open-Closed Principle)

  > 소프트웨어 객체(클래스나 모듈)는 확장에는 열려있어야 하고, 수정에는 닫혀 있어야 한다.  ==> 재사용이 많은 모듈을 고찰 때 그 모듈을 사용하는 여러 모듈을 고쳐아 한다면, 코드를 수정하기가 어렵다. 따라서 클래스나 모듈은 하나의 역할(동작)을 수행하는 것이 좋다 (=모듈의 유연성, 재사용성, 유지보수성에 좋다)

  



</br>



-----



</br>

- ### 예외에 의미를 제공하라

  > 예외를 던질 때는 전후상황을 충분히 덧붙인다. 그러면 오류가 발생한 원인과 위치를 찾기 쉬워진다. 
  >
  > 오류 메시지에 정보를 담아 예외와 함께 던진다. 이때 실패한 연산 이름과 실패 유형도 언급한다. 



<br>



-----



</br>



- ### 호출자를 고려해 예외 클래스를 정의하라

  ##### 변경 전: 외부 라이브러리가 던질 예외를 모두 잡아냄

  ```java
  ACMEPort port = new ACMEPort(12);
  
  try{
  	port.open();
  } catch(DeviceResponseException e){
  	reportPortError(e);
  	logger.log("Device response exception", e);
  } catch(AT1212UnlockedException e){
  	reportPortError(e);
  	logger.log("Device response exception", e);
  } finally{
    ...
  }
  ```

  

  ##### 변경 후: 호출하는 라이브러리 API 감싸기

  ```java
  LocalPort port = new LocalPort(12);
  
  try{
  	port.open();
  } catch(PortDeviceFailture e){
  	reportError(e);
  } finally{
  	...
  }
  ```



<br> 

------



</br>



- ###  정상 흐름을 정의하라

  > 특수 사례 패턴을 설계하면 클라이언트 코드가 예외적인 상황을 처리할 필요가 없어진다.

  ###### - 특수 사례 패턴

  > 클래스를 만들거나 객체를 조작해 특수 사례를 처리하는 방식.



</br>



-----



</br> 

- ### null을 반환하지 마라

  > null을 반환하는 코드는 일거리를 늘릴 뿐만 아니라 호출자에게 문제를 떠넘긴다. 
  >
  > 메서드에서 null을 반환해야한다면 예외를 던지거나 특수 사례 객체를 반환하는 것이 좋다.

  ##### 변경 전

  ```java
  List<Employee> employees = getEmployees();
  if(employee != null){
  	for(Employee e: employees){
  		totalPay += e.getPay();
  	}
  }
  ```

  

  ##### 변경 후

  ```java
  List<Employee> employees = getEmployees();
  for(Employee e: employees){
  	totalPay += e.getPay();
  }
  
  public List<Employee> getEmployees(){
  	if(직원이 없다면){
  		return Collections.emptyList();
  	}
  }
  ```

  

</br>



-------



</br>



- ### null을 전달하지 마라

  > 정상적인 인수로 null을 기대하는 API가 아니라면 메서드로 null을 전달하는 코드는 최대한 피한다.
  >
  > null을 넘기지 못하도록 금지하는 규칙을 정해놓는 것이 합리적이다.

  ##### 변경 전

  ```java
  public class MetricsCalculator{
  	public double xProjection(Point p1, Point p2){
  		return (p2.x - p1.x) * 1.5;
  	}
  }
  
  // NullPointerException 발생
  calculator.xProjection(null, new Point(12, 13)); 
  ```

  

  ##### 변경 후

  ```java
  public class MetricsCalculator{
  	public double xProjection(Point p1, Point p2){
  		if(p1 == null || p2 == null){
  			throws InvalidArgumentException("Invalid argument for MetricsCalculator.xProjection");
  		}
  		return (p2.x - p1.x) * 1.5;
  	}
  }
  ```



</br>



------



</br>

- ### 느낀 점

  > 항상 코딩을 할 때  예외처리가 왜 필요한지, 예외처리의 중요성이 무엇인지 이해를 하지 못해서 예외처리를 하지 않았다. 특히 내가 작성한 코드 대부분은 null을 사용한 경우가 많았다. 사실 null을 사용하는 것이 나쁜 습관이라는 것을 인지하지 못했다. 그래도 이번 챕터를 읽고 나서 최대한 null을 사용하지 말아야지! 라는 생각은 뼈져리게 새긴 것 같다. 부수적으로 예외처리의 중요성 또한 느끼게 되었다!

  

</br>



-----



</br>

- ### 내가 개발한 한줄 코드 소개

  > 온라인 시험 부정행위 방지 iOS 앱 플랫폼 [imonitor](https://github.com/SSU-IMonitor/imonitor-app) 일부 발췌 (본인 코딩) 

  ##### 이번주에는 내가 개선한 한줄 코드 대신 내가 개발한 한줄 코드를 소개해드리도록 하겠습니다. 오류 처리에 능숙하지 않아서 더 나은 방법을 알고 계신다면 제게 알려주시면 감사하겠습니다 :)

  ```swift
  if let data = data {
                  do {
                      let myResponse = response as! HTTPURLResponse
                          print("Status Code:", myResponse.statusCode)
                      
                      if myResponse.statusCode == 200 {
                          let user = try JSONDecoder().decode(LoginInfo.self, from: data)
                          print(user.userInfo.id)
                          
                          DispatchQueue.main.async {
                              self.idText = user.userInfo.id
                              self.nameText = user.userInfo.name
                              self.majorText = user.userInfo.major
                              self.accessToken = user.accessToken
                              self.setLoading()
                          }
                      } else if myResponse.statusCode == 404 || myResponse.statusCode == 500 {
                          self.alertLogin()
                      } else {
                          let error = try JSONDecoder().decode(ErrorInfo.self, from: data)
                          print(error.message)
                      }
                  } catch {
                      print("error: ", error)
                  }
              }
          }.resume()
  ```

  

  ##### 

</br>



-----



</br>



- ### Reference List

  - [확인 / 미확인 예외](https://blog.naver.com/wilgur513/221837556515)
  - [OCP](https://blog.naver.com/dmswjd93/221537557107)









