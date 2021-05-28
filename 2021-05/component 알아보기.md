# Component in React-Native

## What is Component?
> 💡 컴포넌트란? 소프트웨어 시스템에서 독립적인 기능을 수행하는 모듈로 교채가 가능한 부품이다.

컴포넌트는 재사용이 가능한 조립 블록으로 화면에 나타나는 데이터, UI 요소를 말한다.

또한 단순히 UI역할을 하는 것 뿐만 아니라 부모로부터 받은 속성^(props) 또는 자신의 상태^(state)에 따라 표현이 달라지고 다양한 기능을 수행한다.

리액트 및 리액트 네이티브는 데이터와 UI 요소의 집합체인 **컴포넌트**를 이용하여 화면을 구성한다.

## 내장 컴포넌트
리액트 네이티브에는 다양한 내장 컴포넌트^(Core Components)가 제공된다.
- [**리액트 네이티브 컴포넌트**](https://reactnative.dev/docs/components-and-apis)

대표적인 리액크 네이티브 코어 컴포넌트로는 `Text`,`View`,`Button` 등이 있다. 

#### example
```javascript
const TestButton = () => {
  return (
    <View>
      <Button title="버튼" onPress={() => alert('Button Clicked!')} />
    </View>
  );
};

export default TestButton;
```

하지만 Button 컴포넌트의 스타일을 적용할 시 iOS와 Android가 다르게 나타나는 경우들이 있다.

ex) color

컴포넌트 별 플랫폼 호환 문제는 공식문서에서 확인 가능하지만 개발할 때마다 공식문서를 들여다 보고 있을 수는 없는 노릇이다.

따라서 플랫폼 별 기능 호환을 확인하기 위해서 iOS와 Android 모두를 확인하면서 개발하는 습관을 들여야한다.


## 커스텀 컴포넌트
리액트 네이티브에서 다양한 컴포넌트들을 제공하고 있으나, 프로젝트를 진행하다 보면 컴포넌트들을 커스텀 할 일이 많아진다.

앞에서 나온 Button 컴포넌트는 플랫폼 별로 다르게 렌더링 되는 단점이 있었다.

그 단점을 보완하기 위해 나온 Pressable 같은 내장 컴포넌트들을 이용하면 버튼의 기능을 유지함과 동시에 플랫폼 별로 같은 렌더링을 유지할 수 있다. 