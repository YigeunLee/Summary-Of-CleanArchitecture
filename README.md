# Summary-Of-CleanArchitecture
Summary Of CleanArchitecture

용어 정리
-SOLID:중간 수준의 소프트웨어 구조가 아래와 같도록 만드는 데 있음
  1. 변경에 유연할 것
  2. 이해하기 쉬울 것
  3. 많은 소프트웨어 시스템에 사용될 수 있는 컴포넌트 기반이 되는 것
  
-SOLID의 원칙 요소:
  1.SRP: 단일 책임 원칙
    > 각 소프트웨어 모듈은 변경의 이유가 하나이어야 한다, 하나의 모듈은 하나의 액터만을 책임져야 한다
  2.OCP: 개방-폐쇄 원칙
    > 기존 코드를 수정하기 보다 새로운 코드를 추가하여 행위를 변경하여야 한다
  3.LSP: 리스코프 치환 원칙
    > 상호 대체 가능한 구성요소를 이용해 소프트웨어 시스템을 만들 수 있으려면, 이들 구성요소는 반드시 서로 치환 가능해야 한다
  4.ISP: 인터페이스 분리 원칙
    > 소프트웨어 설계자는 사용하지 않은 것에 의존하지 않아야 한다
  5.DIP: 의존성 역전 원칙
    > 고수준 정책을 구현하는 코드는 저수준 세부사항을 구현하는 코드에 절대로 의존해서는 안 된다. 세부사항이 정책에 의존해야 한다
  
-SRP에 대하여:
  1. 다음과 같은 상황이 존재한다고 가정하자
      class Employee{
        public void CalculatePay(){ // 회계팀에서 기능을 정의하고 사용한다
            RegularHours();
        }
        public void ReportHours(){ // 인사팀에서 기능을 정의하고 사용한다
            RegularHours();
        }
        private void RegularHours(){
            // 업무시간을 계산한다
        }
    > 위 Employee 클래스는 회계팀이라는 액터와 인사팀이라는 액터를 책임지기 때문에 SRP를 위배한다
    > 회계팀과 인사팀의 업무시간 계산방법이 다르므로 잘못된 결과를 출력할 수 있다
    > 해결방안은 다음과 같다
      class Facade{
          PayCalculator paycalculator;
          HourReporter hourReporter;
          EmployeeSaver employeeSaver;
          
          public void calculatePay(){
              paycalculator.calculatePay();
          }
          // 생략 //
      }
      > 각 액터별 책임을 지는 객체를 생성하고 기능을 위임한다.
      
      
      작성 중...2020-10-19
    
