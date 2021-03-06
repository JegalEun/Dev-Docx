네트워크를 통해 서버로부터 데이터를 가져오기 위한 통신 방식은 크게 `Http 통신`과 `Socket 통신` 2가지가 있다.

오늘은 이 2가지 통신 방식의 차이에 대해 알아보는 시간을 가질 것이다.

우선 간단하게 말하자면 `HTTP`와 `Socket`의 가장 큰 차이점은 **접속을 유지하는 지의 여부**이다. 

# HTTP 통신
`HTTP 통신`은 `client`의 요청이 있을 때만 `Server`가 응답하여 처리를 한 후에 곧바로 연결을 끊는 방식이다.
보통 많은 웹사이트들이 이 방식을 채택하고 있다. 

<img width="813" alt="HTTP 통신" src="https://user-images.githubusercontent.com/43868540/96217342-5721ca80-0fbd-11eb-9d02-c846f26cabff.png">

> [출처 dentuniverse.tistory](https://dentuniverse.tistory.com/22)

예를 들어서 인스타그램같은 경우와 페이스북 같은 경우를 생각해보자.

처음 접속한 후에 위를 잡아 당겨야 새로운 사진이 나오는 것처럼 **새로고침**이라는 요청을 주어야지 `Client`는 `Server`에게 정보를 요청하고 응답을 받아 화면을 보여준다.

이러한 연결 방식은 `Client`가 요청을 보내는 경우에만 `Server`가 응답하는 단방향적 통신으로, `Server`가 `Client`로 요청을 보낼 수는 없다.

`Client`는 `Server`에게 요청을 보낼 때, 응답을 기다리는 시간과 함께 연결하는 시간이 들어가게 된다. 이러한 `HTTP 통신`은 실시간 연결이 아닌, **필요한 경우에만 `Server`로 접근하는 콘텐츠 위주의 데이터를 사용할 때 용이**하다.

만약 이러한 경우에 Socket 통신을 사용하게 되면 게시물을 받은 후에도 계속 통신을 위한 연결이 성립되어 있어 부하가 걸리게 된다. 그렇기 때문에 정보가 필요할 때마다 `Server`에게 요청할 수 있는 `HTTP 통신`이 좋다.

즉, 서버의 부하를 줄여서 다른 접속을 원활하게 처리하기 위해 이 방식을 사용한다.

## HTTP 통신의 특징
- `Client`가 요청을 보내는 경우에만 `Server`가 응답하는 **단방향 통신**이다.
- `Server`로부터 응답을 받은 후에는 연결이 바로 종료된다.
- 실시간 연결이 아니고, 필요한 경우에만 `Server`로 요청을 보내는 상황에 유용하다.
- 요청을 보내 `Server`의 응답을 기다리는 어플리케이션(Android or los)의 개발에 주로 사용된다.

# Socket 통신
`Socket 통신`은 `HTTP 통신`과 달리 `Server`와 `Client`가 특정 `Port`를 통해 연결을 성립하고 있어 **실시간으로 양방향 통신**을 하는 방식이다.

<img width="779" alt="socket 통신" src="https://user-images.githubusercontent.com/43868540/96217485-a5cf6480-0fbd-11eb-80a6-ab78ee9e470f.png">

> [출처 dentuniverse.tistory](https://dentuniverse.tistory.com/22)

필요한 경우에 `Client`만 요청을 보낼 수 있는 `HTTP 통신`과 달리 `Socket 통신`은 `Server` 역시 `Client`로 요청을 보낼 수 있으며, 계속 연결을 유지하는 **연결지향형 통신**이기 때문에 실시간 통신이 필요한 경우에 자주 사용된다.

실시간 통신을 할 수 있다는 특성때문에 실시간 Streaming 중계나 실시간 채팅과 같이 즉각적으로 정보를 주고받는 경우에 사용된다.

만약 이러한 상황에 `Socket 통신`이 아닌 `HTTP 통신`으로 정보를 주고 받는다면 동영상이 종료되는 순간까지 계속해서 `HTTP 통신`을 보내야 하고 이러한 구조는 계속 요청을 하기 때문에 부하가 걸리게 된다.

그러므로 동영상같이 정보를 계속해서 요청해야하는 경우에는 `Socket`을 통해 구현하는 것이 적합하다.

## Socket 통신의 특징
- `Server`와 `Client`가 계속 연결을 유지하는 **양방향 통신**이다.
- `Server`와 `Client`가 실시간으로 데이터를 주고받는 상황이 필요한 경우에 사용된다.
- 실시간 동영상 Streaming이나 온라인 게임 등과 같은 경우에 자주 사용된다.


----
#### Reference
- [HTTP vs Socket](https://mangkyu.tistory.com/48?category=762469)
