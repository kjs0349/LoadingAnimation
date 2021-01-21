# LoadingAnimation
CSS와 HTML을 이용해 로딩 애니메이션을 만들어 보았습니다.

![LoadingAnimation2](https://user-images.githubusercontent.com/61913417/105387904-5d2ce480-5c59-11eb-896a-1b27100a964b.gif)

- 구상 과정과 구현
1. 원을 3등분으로 나눠 다른 색을 나오게 하고 싶다.
	- border-radius: 50% 로 원을 만들어 준다.
    - border-top 값으로 윗 부분에만 값을 준다.
    - 가상요소 선택자 after와 befor로 똑같이 만들어 주고 position: absolute; top: -7px; left: 0;로 부모와 같은 위치에 위치시킨다.  
    --> top에 -7px 값을 주는 이유는 .loading 의 border-top 값에 7px 를 주었으므로 일치시키기 위해 주었습니다.
    - after와 befor에 transform: rotate(); 로 각각 120도와 -120도로 돌려줘서 원의 형태를 만들어 준다.
    - .loading과 .loading::after, .loading::before에 각각 다른 색 값을 준다.
    
2. Loading... 이라는 문구를 로딩 이미지 가운데에 위치시키고 싶다.
	- position: absolute를 이용해 부모 너비와 동일하게 만들어 준다.
    	- 인라인 요소 span에 크기를 줄 수 있는 이유!
        position: absolute를 주었으므로 부모 영역의 값을 사용할 수 있다. 따라서 인라인 요소여도 크기 값을 지정해 줄 수 있다!
    - text-align: center 와 line-height를 요소의 크기만큼 주어 가운데 위치 시킨다.
    
3. 로딩 이미지 처럼 보이게 하기 위해 돌아가게 만들고 싶다.
	- @keyframes 를 이용해 transform: rotate(360deg) 값을 줘서 360도 돌아가게 만들어 준다.  
    	--> 여기서 to는 100%를 의미한다(from은 0%를 의미한다.)
    - animation의 infinite 속성을 이용해 무한으로 돌아가게 한다.
    
    > #### 여기서 문제!
    >이렇게 코딩하면 Loading... 이라는 글씨도 같이 360도 돌아버리게 된다.  
    >그러므로 transform: rotate(-360deg) 값을 주는 @keyframes를 하나 더 생성해 span 태그에 준다.  
    >이렇게 해주면 돌아가지 않는 것과 동일한 효과를 줄 수 있다.  
    >하지만 여기서 Loading... 이 움직이는 이유는 top: -7px 로 부모의 위치와 맞춰주지 않았기 때문에 돌아가는 것이다.   
    >top: -7px를 주면  
    >![](https://images.velog.io/images/kjs0349/post/cf4d205f-6e78-42b2-9227-8b924f95d759/LoadingAnimation3.gif)  
    >이렇게 만들 수 있다.
