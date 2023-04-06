# react-native_baic_nomad

- (basic) Nomad - 왕초보를 위한 React Native 101
- https://nomadcoders.co/react-native-for-beginners

# 1. INTRODUCTION

- React-Native 셋업은 복잡하므로 expo 활용 할 예정
- Expo : 셋업 할 필요 없이 코드의 결과를 앱에서 즉시 확인할 수 있음
- **Expo 설치**

  1. npm install --global expo-cli
  2. 핸드폰에서 expo 앱 설치

- React-Native 동작 방식

  - Native(ios / android) <-> Bridge <-> JavaScript

- **Expo 만들기**
  - (1) Create a new app
    - npx create-expo-app (name)
    - cd (name)
  - (2) Login - npx expo login
  - (3) Starting the development server - expo start

# 2. WEATHER APP

- **React-Native Rule**
  - (1) 태그의 차이점이 있다.
    - div -> View
    - span, p -> Text
  - (2) 일부 style property를 사용 할 수 없다.
    - border X
  - (3) style object 만들어서 활용 가능
    - `const style = StyleSheet.cerate({});`
    - css 자동완성 기능 제공
  - (4) 일부 component는 화면에 표시되지 않는다.
    - ios, android 운영 체제와 소통하는 컴포넌트 존재
    - `<StatusBar style="light"/>`

---

- **Third Pary Packages**
  - React Native 버전에 따라 Core Component 지원하는 규모가 다르다.
  - 버전 업그레이드 마다 버그를 줄이기 위해 지원 하는 Component 서비스 규모를 줄임
  - [React Native Doc](https://reactnative.dev/docs/0.60/components-and-apis)
  - [React Native Directory](https://reactnative.directory/)
    - 커뮤니티에서 유저들이 만든 패키지
  - [Expo Doc](https://docs.expo.dev/versions/latest/)
    - Expo SDK : Expo 에서 자체적으로 만든 패키지
  - Expo와 ReactNative 의 StatusBar 차이점
    - 만들어진 코드가 다르고, props 또한 다를 수 있음

---

- **Layout System**

  - Flexbox Default 차이점
    - Web은 Flex Direction : row
    - App은 Flex Direction : column
  - View 태그 : Flex Container 기본값 column
  - 레이아웃 시스템 이해하기

    - 스크린 사이즈가 다양하기에 width/height 사용하지 않음
    - (1) Flex 부모에 flex 설정
    - (2) Flex 자식에 비율 설정

    ```js
    import { View } from "react-native";

    export default function App() {
      return (
        <View style={{ flex: 1, flexDirection: "row" }}>
          <View sytle={{ flex: 1, backgroundColor: "tomato" }}></View>
          <View sytle={{ flex: 1, backgroundColor: "teal" }}></View>
          <View sytle={{ flex: 1, backgroundColor: "orange" }}></View>
        </View>
      );
    }
    ```

---

- ScrollView 태그

  - 화면의 스크롤을 사용할 때 쓰는 컴포넌트
  - ScrollView에서 style을 만들고 싶으면, props 사용이 제한되기에 contentContainerStyle 사용
    - contentContainerStyle={styles.weather}
  - props
    - horizontal
    - pagingEnabled
    - showsHorizontalScrollIndicator={false}

- Dimension

  - 화면 크기 width, height 가져오는 API

    ```js
    const { width: SCREEN_WIDTH } = Dimensions.get("window");
    ```
