---
title: "자바스크립트에서 새로운 것들"
toc: true
toc_sticky: true

categories:
  - Javascript
tags:
  - basic

last_modified_at: 2020-02-19T14:48:00+00:00
---

**매우 주관적인 포스트로서 사실과 다를수도 있습니다. 개인적인 정리 차원입니다.**

나는 이전에 C와 C++을 약 2년간 공부하고 이후에 자바나 C#, 파이선을 조금씩 경험한 적이 있다.

모든 언어들은 각각의 특성이 있지만, 자바스크립트와 파이선은 다른언어들과는 다른 특성을 가지는것 같아서

이에 대하여 느낀점들을 작성해 보려고 한다.

​

자바스크립트는 파이선을 조금 건들여 봤었던 내가 보기에서는 둘은 유사한 점이 많다.

함수 선언도 비슷하고, 딕셔너리, 맵등의 함수가 존재한다는것도 유사하다.

하지만 자바스크립트가 조금더 자유분방한 언어인것 같다.

​

자바스크립트는 대부분은 값을 전달하지만 객체 혹은 펑션인 경우는 주소값을 전달하는것 같다.

그러므로, 선언되지 않은 변수를 사용하는 경우가 아니라면, 그 변수에 없는 특성을 if문에서도 사용이 가능하다.

선언되지 않은 특성은 무조건 '정의되지 않음'이라는 값을 가지게 될테니까.

​

그리고 이번에 자바스크립트를 공부하면서 느낀건데,

여태 주력으로 사용하던 C++는 함수의 인풋으로 함수를 받아 본 기억이 없다.(되지만 내가 모르는 걸수도 있다.)

하지만 자바스크립트에서는 오브젝트이건, 함수이건, 변수이건, 배열이건 인풋으로 받을수가 있었다.

또한 인풋으로 받은 어떤것에 대하여 함수에서 특정 특성을 지정해줄수도 있었다.

이 특성은 스코프때문에 임시변수가 회수되는것처럼 회수되지 않고 스코프 밖으로 벗어날때 까지 사용이 가능하다.

이를 이용해서 memoize를 직접 구현해 볼때는 인풋으로 함수를 받아서 그 함수에 인풋들이라는 특성을 새로이 추가해 준적도 있다.

​

이런것들이 가능한 이유는 위에서 언급했듯이 객체나 펑션은 메모리에 저장된 주소값을 전달해 주기 때문이다.

마치 집에 tv가 뭔지 제품명만 알려주는 것과는 다르게 집 주소를 알려주고 그 집의 tv 모델명을 보는것과 같다고 할까?

어쨋든 이런이유로 함수와 객체에서 새로운 특성을 지정해줄수 있다.

그 특성 때문에 함수나 객체를 리턴하는 경우에 객체와 함수의 인자들이나, 함수의 전역변수들은 초기화가 되지않아서 당황했던 적이 있다.

이걸 이용해서 일정 시간이후에 함수를 실행하게 하는 throttle함수를 작성할수 있다. 스레드에서 사용하는 뮤텍스 락과 비슷하게 변수를 이용해서 락을 걸면 된다. 함수의 주소값은 프로그램이 종료되기 전까지는 변수는 유지될것이니, 전역 변수로 락으로 사용할 변수만 선언해주면 된다.