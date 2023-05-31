# URI, URL, URN 이스케이프 처리

## URI(Uniform Resource Identifier)
- 인터넷에 있는 자원을 나타내는 유일한 주소

 URI, URL(Uniform Resource Locator), URN(Uniform Resource Name)의 차이는 아래 그림 참고
![다운로드](https://github.com/minhyeonhong/algorithm/assets/90454621/d944793d-732d-4201-ae03-1329910e44eb)
 
 <br/>

 연관된 개념인 Scheme(Protocol), Host(Domain), Port, Path, Query String, Search, Fragment는 아래 그림 참고
![다운로드 (1)](https://github.com/minhyeonhong/algorithm/assets/90454621/66c6508e-8d6a-4215-ac8b-6599b9c5b030)

 <br/>

 ## 이스케이프 처리
 - 어떤 시스템에서도 읽을 수 있는 아스키(ASCII) 문자셋으로 변환하는 것

 ## URI 인코딩
 - 네트워크 등를 통해 정보를 공유할 때, 어떤 시스템에서도 읽을 수 있도록 URI의 문자들을 ASCII 문자셋으로 변환하는 것이다.
- 예를들어, UTF-8 한글의 '가'는 3바이트의 아스키 문자셋 %EC %92 E%90 등으로 인코딩된다.

## URI 디코딩
 - 디코딩은 반대로 인코딩된 아스키문자셋 %EC %92 E%90를 해석하여 한글 "가"로 되돌리는 것이다.

 <br/>

 ## Javacript의 인코딩/디코딩 함수
 자바스크립트는 빌트인(내장) 전역 함수로 URI 문자열을 인코딩하고, 다시 디코딩하는 함수를 제공한다.

### [encodeURI()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/encodeURI) / [decodeURI()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/decodeURI)

- 보통 URI에서 의미가 있는 . : / ? = &, 영어 등은 그대로 남겨두고 인코딩한다.
    -  encodeURI('인코딩 이전 URI')  => 이스케이프 처리된 URI
    -  decodeURI('인코딩 완료 URI')  => 이스케이프 처리 이전 URI

```
 const test = () => {
    const URI = 'https://mhhtest.com/user?name=테스트';
    const encode = encodeURI(URI);
    const decode = decodeURI(encode);

    console.log("encode", encode);
    console.log("decode", decode);    
}

// encode https://mhhtest.com/user?name=%ED%85%8C%EC%8A%A4%ED%8A%B8
// decode https://mhhtest.com/user?name=테스트
```

### [encodeURIComponent()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent) / [decodeURIComponent()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent)
-  . : / ? = &  등 조차 모두 인코딩한다.(영어는 남겨둔다.)
    -  encodeURIComponent('인코딩 이전 URI')  => 이스케이프 처리된 URI
    -  decodeURIComponent('인코딩 완료 URI')  => 이스케이프 처리 이전 URI

 ```
 const test = () => {
    const URI = 'https://mhhtest.com/user?name=테스트';
    const encodeComponent = encodeURIComponent(URI);
    const dncodeComponent = decodeURIComponent(encodeComponent);

    console.log("encodeComponent", encodeComponent);
    console.log("dncodeComponent", dncodeComponent);
}

// encodeComponent https%3A%2F%2Fmhhtest.com%2Fuser%3Fname%3D%ED%85%8C%EC%8A%A4%ED%8A%B8
// dncodeComponent https://mhhtest.com/user?name=테스트
```

## 참고
https://curryyou.tistory.com/347