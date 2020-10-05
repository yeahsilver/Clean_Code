## 📍 10장 클래스



### 	"도구 상자를 어떻게 관리하고 싶은가?

### 	작은 서랍을 많이 두고 기능과 이름이 명확한 컴포넌트를 나눠 넣고 	싶은가?

### 	아니면 큰 서랍 몇개를 두고 모두를 던져 넣고 싶은가?"



</br>



-----



</br>



- ### 클래스 체계

  - #### 캡슐화

    > 같은 패키지 안에서 테스트 코드가 함수를 호출하거나 변수를 사용해야 한다면, 그 함수나 변수를 protected로 선언하거나 패키지 전체로 공개한다. 



</br>



------



</br>



- ### 클래스는 작아야 한다!

  > 클래스를 만들 때 첫 번째 규칙은 크기다. 클래스는 작아야 한다. 
  >
  > 작명은 클래스 크기를 줄이는 첫 번째 관문이다.

  

  </br>

  

  - #### 단일 책임 원칙

    > 클래스나 모듈을 변경할 이유가 단 하나뿐이여야 한다는 원칙이다.
    >
    > 큰 클래스 몇개가 아니라 작은 클래스 여럿으로 이뤄진 시스템이 더 바람직하다.

  

  </br>
  - #### 응집도

    > 클래스에 속한 메서드와 변수가 서로 의존하며 논리적인 단위로 묶이는 것을 응집도가 높다고 이야기한다. 

  </br>

  - #### 응집도를 유지하면 작은 클래스 여럿이 나온다

    > 큰 함수를 작은 함수 여럿으로 나누기만 해도 클래스 수가 많아진다.

    ###### 응집도를 유지하면 코드의 길이가 길어지는 이유

    	1. 더 길고 서술적인 변수 이름을 사용한다.
     	2. 코드에 주석을 추가하는 수단으로 함수 선언과 클래스 선언을 활용한다.
     	3. 가독성을 높이고자 공백을 추가하고 형식을 맞춘다.



</br>



------



</br>



- ### 변경하기 쉬운 클래스

  > 깨끗한 시스템은 클래스를 체계적으로 정리하여 변경에 수반하는 위험을 낮춘다. 

  

  <br>

  

  ##### 변경이 필요한 클래스

  > 새로운 SQL문을 지원하려면 반드시 SQL 클래스에 손을 대야한다. 

  ```java
  public class SQL{
  	public SQL();
  	public string Create();
  	pulbic string Update();
  	....
  }
  ```

  

  </br>

  ##### 닫힌 클래스 집합

  > OCP 원칙도 지원한다. 
  >
  > 이상적인 시스템이라면 새 기능을 추가할 때 시스템을 확장할 뿐 기존 코드는 변경하지 않는다. 

  ```java
  abstract public class SQL(){
  	public SQL();
  	abstact public String generate();
  }
  
  public class Create extends SQL{
  	public CreateSQL();
  	@override public String generate();
  }
  .....
  ```

  

  

</br>



-----



</br>

- ### 오늘의 한줄 코드

  ##### 리팩터링 전

  > 메인 클래스에 table view 속성 배치

  ```swift
  func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
          return 80.0
      }
      
      func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
          return myCourses.count
      }
      
      func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
          let cell = UITableViewCell(style: .subtitle, reuseIdentifier: nil)
          cell.textLabel?.text = myCourses[indexPath.row].title
          cell.detailTextLabel?.text = myCourses[indexPath.row].owner?.name
          return cell
      }
      
      func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath){
          rowSelected = indexPath.row
          performSegue(withIdentifier: "showDetail", sender: self)
      }
  ```

  

  ##### 리팩터링 후

  > extension으로 table view 속성 분리

  ```swift
  extension MainViewController: UITableViewDataSource {
      
      func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
          return myCourses.count
      }
      
      func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
          let cell = UITableViewCell(style: .subtitle, reuseIdentifier: nil)
          cell.textLabel?.text = myCourses[indexPath.row].title
          cell.detailTextLabel?.text = myCourses[indexPath.row].owner?.name
          return cell
      }
  }
  
  extension MainViewController: UITableViewDelegate {
      func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath){
          rowSelected = indexPath.row
          performSegue(withIdentifier: "showDetail", sender: self)
      }
      func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
          return 80.0
      }
  }
  
  ```

  





----



</br>



### 느낀 점

> java를 많이 사용하지 않고, C++를 자주 사용하는데,  그러다보니 class에 대한 개념이 아직 익숙치 않다. 개념에 대해 잘 알지 못하다보니, 오히려 잡생각 없이 받아들일 수 있었고, 덕분에 이번 챕터를 읽으면서 이해하기 편했다. 이번 챕터에서는 클래스에 대한 정보를 효율적으로 사용하는 방법을 익혔기에, 이제 객체 지향 프로그래밍을 사용할 때, 이 점을 유의하면서 리팩터링을 하도록 노력해야겠다고 생각했다. 





