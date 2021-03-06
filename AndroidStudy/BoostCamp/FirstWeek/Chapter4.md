# 액티비티 살펴보기

- **액티비티 이해**

	 - 액티비티(Activity)는 **사용자 인터페이스 화면**을 관리하는 컴포넌트이다. 액티비티 역할을 하기 위해서는 Activity 클래스를 상속해야 하며, 액티비티가 기본적으로 가지고 있는 생명주기 메소드를 재정의해서 원하는 기능을 구현해야 한다.
 
	 - main메소드를 호출하는 프로그램과 달리, 안드로이드 시스템은 엑티비티 객체에서 **특정한 콜백함수를 호출**함으로써 특정 생명주기 구역에 대응하여 코드를 시작한다.


	 - 앱에서 액티비티를 이용하려면 **AndroidManifest에 액티비티와 속성들**을 선언해야 한다.

- **액티비티 생명주기 메소드**
	- **onCreate() :** <br>
      -- 액티비티가 **생성될 때** 호출되며 **사용자 인터페이스 초기화**에 사용<br>
      -- 전체 생명주기 안에 **오직 한번만** 일어나야할 로직을 여기서 수행한다.
	
	- **onStart() :** <br>
			-- 액티비티가 사용자에게 **보여지기 바로 직전**에 호출 <br>
			-- 빠르게 끝남

	- **onResume() :** <br>
			-- 액티비티가 사용자와 **상호작용하기 바로 전**에 호출됨 <br>
			-- onPause로 인하여 릴리즈된 컴포넌트를 **초기화** 하는데 적당한 메소드
	
	- **onPause() :** <br>
			-- **다른 액티비티가 보여질 때** 호출됨(액티비티를 떠날때)<br>
			-- **리소스를 릴리즈** 하고 **간단한 데이터를 저장**하기에 적당한 메소드(ex) camera, 스레드 중지 등...<br>
			-- 메소드가 끝나기전에 부하가 큰 작업은 다 끝나지 않을 수 있기 때문에 그런 작업들은 onStop에서 수행한다 (ex) DB 트랜잭션<br>
	
	- **onStop():**<br>
			-- 액티비티가 더이상 사용자에게 **보여지지 않을 때** 호출됨<br>
			-- DB에 저장하는 작업, Broadcast Receiver 해제와 같은 작업 수행<br>
			-- onRestart로 다시 액티비티로 복귀<br>

 	- **onDestroy():** <br>
			-- **액티비티가 소멸될 때** 호출됨 	 <br>
      -- finish() 메소드가 호출되거나 시스템이 메모리 확보를 위해 액티비티를 제거할   때 호출됨.<br>

 	- **onRestart():** 	<br>
			-- 액티비티가 멈췄다가 **다시 시작되기 바로 전**에 호출됨.
