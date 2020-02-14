# weather_app_basic
Basic weather app made with React Native

## expo app 설치 후에 QR code를 스캔해주세요.

- [play store](https://play.google.com/store/apps/details?id=host.exp.exponent)

- [app store](https://apps.apple.com/kr/app/expo-client/id982107779)

![qrcode](./app-qrcode.png)


```javascript
expo
create-react-app 과 같다.
리엑트 네이티브를 위한 설정 파일 같은 것들이 없는 방식으로, 모든 것이 셋업되어 있다.

프로젝트 시작

expo init 프로젝트명

- 장점 
  휴대폰에서 테스트가 가능하다는 점
  building process : IOS와 안드로이드를 위한 앱을 알아서 빌드해줌(윈도우에서 IOS앱을 빌드할 수 있다.)
  live reloading : 내가 저장하면, 자동으로 리프레쉬 되고, 변경될걸 바로 확인 가능하다
  hot reloading

- 단점
  native files들을 크게 제어할 수 없다는 점


- native files들을 더 많이 컨트롤 하고싶을때는 react native CLI 방식을 사용

완전 native : Swift or object-c로 IOS 앱을 만드는 것, Java or 코클린을 가지고 만드는 Android 앱, 프로그래밍 언어도 다르고 매우 다르다
하나는 Xcode 하나는 Android studio 이게 네이티브 방식

- 다른 하나는 앱 기반 웹뷰를 만드는 것

앱안에서 작동하는 웹사이트( 하이브리드 )

정말 간단하고 매우매우 심플한 앱을 만들고, 예를 들어 Cordova or PhoneGap 이용해서..

그리고 그 안에 그냥 HTML, CSS를 넣는 것, 앱을 실행하면 웹사이트처럼 HTML, CSS, Jvascript 를 보여준다.

native쪽에 많은 예산이 없는 회사들이 사용하거나 휼륭한 반은형 웹사이트를 가지고 있고, 몇개의 네이티브 기능들이 필요할 때 사용한다

예를 들어 알림 푸쉬같은 것들... 그래서 전체 웹사이트를 앱안에 넣어서 유저가 앱 실행시에 반응형 웹사이트를 보도록(아마존앱처럼)

리엑트 네이티브 방식은 기본적으로 안드로이드, ios 둘다 자바스크립트 엔진을 가지고 있기 때문에 자바스크립트를 실행 할 수 있어 가능하다.

리엑트 네이티브가 하는 일은, 자바스크립트를 이용해서 ios 또는 안드로이드 네이티브 엔진에게(JS를 이용한) 메세지를 보내는 것 
연결을 이어주는 브릿지처럼

react-native 에서 import하는 것들이 모두 브릿지

컴포넌트 안에 브릿지가 있다.

누군가가 작성해 놓은 Swift code나 Java code로 아이폰, 안드로이드가 이 컴포넌트를 이해하도록 만들려고 항상 브릿지가 존재함

페이스북도 자바스크립트와 ios, 안드로이드 사이에서 서로를 이해하기 위한 사이의 브릿지를 만든다.

사람들이 리엑트 네이티브를 좋아하기도 하지만 싫어하기도 하는 이유가 네이티브기는 한데 실제로 아이폰의 core로 가고 안드로이드의 core로 가지만
자바스크립트와 폰 사이의 커뮤니케이션을 위해서 항상 브릿지가 필요하게 되기 때문이다.
그래서 그게 느린 성능을 유발 할 수도 있다 왜냐면 브릿지로 많은 데이터를 보내면 브릿지에 교통체중처럼 부하가 걸리기 때문이다.

그래서 리엑트네이티브는 컨텐츠만 다루는 애플리케이션 만들기에는 퍼팩트하다.
예를 들자면 인스타그램, 데이팅 앱 같은 것들.

근데 만약에 3D 비디오 게임 같은 것을 만든다면 리엑트 네이티브가 좋은 선택은 아니다.
왜냐면 브릿지가 느려지지 않도록 코드를 최적화 하는데 많은 시간을 써야 할테니까. 

비디오 게임 코드를 작성하거나, 3D 증강 현실 앱을 작성하길 원하는 경우에는 폰 카메라나 뭐 그런 것들을 가지고 개발하는 것은 
리엑트 네이티브는 별로다. 왜냐면 그런 것을 목적으로 만들어진게 아니고 자바스크립트와 폰의 코드 사이의 커뮤니케이션을 쉽게 하려고 만들어진 것이다.

- 리엑트 네이티브가 작동하는 규칙

<div>, <span> 을 사용하지 않고 <View>, <Text>를 사용한다.

view안에 모든 것이 들러가야 한다.

모든 텍스트는 <Text></Text> 컴포넌트 안에 있어야 한다.


이런 룰이 존재하는 이유는 브릿지 때문이다.


## Logic
리엑트 네이티브 레이아웃 규칙

리엑트 네이티브의 모든 flex box의 디폴트는 
flexDirection: column이다.
웹사이트에 모든 flex box의 디폴트는 row이고 flexDirection이 column이다.
왜냐하면 모바일 폰에서는 대게 모든게 서로 아래에 있으니까
그래서 flexDirection 기본값이 column이다. 바꿀 수는 있다.

웹사이트에서는 flex: 1 or flex: 2 이렇게 안한다.

<View>는 리엑트 네이티브에서 <div>와 같은 것이다.

style을 주는 방법
export default function App() {
  return (
    <View style={styles.container}>
      <View style={styles.yellowView} />
      <View style={{flex: 3, backgroundColor: "blue"}} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1
  },
  yellowView: {
    flex: 1,
    backgroundColor: "yellow"
  }
});


flex: 1 은 모든 공간 사용 가능하다라는 의미, 전체공간을 다 사용하고 싶을 떄 사용

container안에 두개의 View가 각각 flex를 1, 3으로 지정되 있는데 이경우엔
각각 4분의 1, 4분의 3의 공간을 차지한다.

웹사이트에는 없는 css인데, 리엑트 네이티브에 쓴다.
paddingHorizontal: paddingLeft
paddingVertical: paddingBottom


GeoLocation은 사용자 IP 기반 위치 정보를 제공하는 서비스

openweathermap API

expo-location, axios, expo-linear-gradient 추가

### flex 

- justifyContent

justify-content 속성은 플렉스 요소의 수평 방향 정렬 방식을 설정합니다.
이 속성은 다음과 같은 속성값을 가질 수 있습니다.

1. flex-start : 기본 설정으로, 플렉스 요소는 플렉스 컨테이너의 앞쪽에서부터 배치됩니다.

2. flex-end : 플렉스 요소는 플렉스 컨테이너의 뒤쪽에서부터 배치됩니다.

3. center : 플렉스 요소는 플렉스 컨테이너의 가운데에서부터 배치됩니다.

4. space-between : 플렉스 요소는 요소들 사이에만 여유 공간을 두고 배치됩니다.

5. space-around : 플렉스 요소는 앞, 뒤, 그리고 요소들 사이에도 모두 여유 공간을 두고 배치됩니다.

- alignItems

align-items 속성은 플렉스 요소의 수직 방향 정렬 방식을 설정합니다.
이 속성은 한 줄만을 가지는 플렉스 박스에서는 효과가 없으며, 두 줄 이상을 가지는 플렉스 박스에서만 효과가 있습니다.
이 속성은 다음과 같은 속성값을 가질 수 있습니다.

1. stretch : 기본 설정으로, 플렉스 요소의 높이가 플렉스 컨테이너의 높이와 같게 변경된 뒤 연이어 배치됩니다.

2. flex-start : 플렉스 요소는 플렉스 컨테이너의 위쪽에 배치됩니다.

3. flex-end : 플렉스 요소는 플렉스 컨테이너의 아래쪽에 배치됩니다.

4. center : 플렉스 요소는 플렉스 컨테이너의 가운데에 배치됩니다.

5. baseline : 플렉스 요소는 플렉스 컨테이너의 기준선(baseline)에 배치됩니다.


- tatusBar 추가( 리엑트 네이티브 )

  앱 상태 표시 줄을 제어하는 ​​구성 요소
  
  barStyle: 상태 표시 줄 텍스트의 색상을 설정합니다.

uigradients에서 색상검색




## PropTypes의 종류

array	배열
bool :	true/false
func :	함수
number :	숫자
object :	객체
string :	문자열
symbol :	심벌 개체(ES6)
node :	렌더링 가능한 모든것(number, string, element, 또는 그것들이 포함된 array/fragment)
element :	React element
instanceOf(ClassName) :	JS에서 instanceof로 정의 가능한 클래스 인스턴스
oneOf([…Value]) :	포함된 값들중 하나.(ex: oneOf([‘남자’,’여자’]))
oneOfType([…PropTypes]) :	포함된 PropTypes들중 하나. (ex: oneOfType([PropTypes.string, PropTypes.instanceOf(MyClass)]))
arrayOf(PropTypes) :	해당 PropTypes으로 구성된 배열
objectOf(PropTypes) :	주어진 종류의 값을 가진 객체
shape({key:PropTypes}) :	해당 스키마를 가진 객체.(ex:shape({name:PropTypes.string,age:PropTypes.number}))
exact({key:PropTypes}) :	명확하게 해당 스키마만 존재해야함.

