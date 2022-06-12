
## 다음의 조건을 만족하는 대중교통 시스템을 완성시키세요

### 탑승객
- 탑승객은 탑승객의 이름과 교통카드 잔액정보를 가지고있다
- 탑승객은 교통카드를 충전할 수 있다
- 탑승객은 교통수단을 탑승할 수 있다
(단, 교통카드 잔액이 탑승하려는 교통수단의 요금보다 적으면 '잔액이 부족합니다' 라는 문구가 뜨며 탑승하지못한다)


### 교통수단
- 버스와 지하철 두가지 교통수단이 있으며 각각 Bus,Subway 클래스로 구현한다
- 버스요금은 1000원 지하철요금은 1500원이다


``` java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner scanner=new Scanner(System.in);
		
		System.out.println("탑승객의 이름을 입력해주세요");
		String name=scanner.next();

		Passenger passenger=new Passenger(name);
		Bus bus=new Bus();
		Subway subway=new Subway();
		
		while(true) {
			//탑승객 정보 표시
			System.out.println(passenger);
			
			
			System.out.println("실행할 활동을 선택해주세요(1:충전,2:탑승,3:종료)");
			int type=scanner.nextInt();
			
			//충전을 선택한경우
			if(type==1) {
				System.out.println("충전할 금액을 입력해주세요");
				int money=scanner.nextInt();
				passenger.charge(money);
			}
			//탑승을 선택한경우
			else if(type==2) {
				System.out.println("탑승할 교통수단을 입력해주세요(1: 버스, 2:지하철)");
				int transportationType=scanner.nextInt();
				
				//버스를 선택한경우
				if(transportationType==1) {
					passenger.take(bus);
				}
				else if(transportationType==2) {
					passenger.take(subway);
				}
			}
			//종료인경우
			else {
				System.out.println("시스템을 종료합니다");
				break;
			}
			
		}
	}
}
```
