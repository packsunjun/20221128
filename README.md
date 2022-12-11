# 221128
태그 클레스는 여러개 생성가능

이벤트 - 사용자가 클릭이나 움직이게해서 발생

리스너 - 70여개의 이벤트가있는데 모든 DOM개체가 다 처리하지 않고 검사하고 함
HTML 태그 내에 작성
DOM 객체의 이벤트 리스너 프로퍼티에 작성
DOM 객체의 addEventListener() 메소드 이용

익명함수 - 해당 파일에서만 사용

이벤트 객체 - 이벤트 발생 순간 이벤트 정보 까지 담아서 제공함
1. 발생한 이벤트에 관련된 다양한 정보를 담은 객체
2. 예) mousedown 이벤트의 경우, 마우스 좌표와 버튼 번호 등
        keydown 이벤트의 경우, 키 코드 값 등
3. 이벤트가 처리되고 나면 이벤트 객체 소멸

이벤트 객체는 이벤트 리스너 함수의 첫 번째 매개변수에 전달
1. 이름을 가진 이벤트 리스너
2. 익명 함수의 경우
3. HTML 태그에 이벤트 리스너 : event 라는 이름으로 전달
> <script>
            var div = document.getElementById("div"); // 이벤트 메시지 출력 공간
            var button = document.getElementById("button");

            // body 객체에 캡쳐 리스너 등록
            document.body.addEventListener("click", capture, true); // 켭쳐 단계(1) 

            // 타겟 객체에 버블 리스너 등록
            button.addEventListener("click", bubble, false); // 버블 단계(2)

            // body 객체에 버블 리스너 등록
            document.body.addEventListener("click", bubble, false); // 버블 단계(3)

            function capture(e) { // e는 이벤트 객체
                let obj = e.currentTarget; // 현재 이벤트를 받은  DOM 객체
                let tagName = obj.tagName; // 태그 이름
                div.innerHTML += "<br>capture 단계 : " + tagName + " 태그 " + e.type + "이벤트";
            }

            function bubble(e) { // e는 이벤트 객체
                let obj = e.currentTarget; // 현재 이벤트를 받은  DOM 객체
                let tagName = obj.tagName; // 태그 이름
                div.innerHTML += "<br>bubble 단계 : " + tagName + " 태그 " + e.type + "이벤트";
            }
        </script>
	
![3](https://user-images.githubusercontent.com/112832753/206889510-f47c00ea-1657-44db-8b48-c25653c600af.PNG)

이벤트 리스너 작성 방법 4 가지 
(1) HTML 태그
(2) 이벤트 리스너
    프로퍼티
(3) addEventListener()
    메소드 이용
(4) 익명 함수 이용
(5) 익명 함수 이용

이벤트 객체에 들어있는 정보
1. type
2. target
3. currentTarget

onclick="return false">
	이동 안되는 링크
var ret = confirm = 예, 아니요 //true false

이벤트가 흘러가는 과정
캡쳐 단계(capturing phase) 
이벤트가 window 객체에서 중간의 모든 DOM 객체를 거쳐 타겟 객체에 전달되는 과정
이벤트가 거쳐가는 모든 DOM 객체(window포함)의 이벤트 리스너 실행 
버블 단계(bubbling phase) 
이벤트가 타겟에서 중간의 모든 DOM 객체를 거쳐 window 객체에 전달되는 과정 
이벤트가 거쳐가는 모든 DOM 객체(window포함)의 이벤트 리스너 실행 

onload 
window 객체에 발생
웹 페이지의 로딩 완료시 호출되는 이벤트 리스너

