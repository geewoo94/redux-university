# compose

## `compose(...functions)`

대단한 기능은 아닙니다. 함수형 프로그래밍 기법중 하나인 compose를 구현합니다. 오른쪽부터 왼쪽으로 함수를 평가합니다. redux에서는 enhancer에 여러가지 함수를 결합 사용할때 사용됩니다.

### compose를 간단하게 알아봅시다.

```javascript
function a(n) {
    return n + 1
}

function b(n) {
    return n * 2
}

const composed = compose(b, a); //결합된 함수

composed(10) //expected 22

/*
* 우측부터 함수를 평가합니다. 평가된 값은 좌측 함수의 인자로 전달됩니다.
* b(a(10)) 의 결과와 같습니다.
*/
```



