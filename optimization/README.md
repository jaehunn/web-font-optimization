Critical Rendering Path 는 브라우저가 HTML 을 화면에 렌더링하는 과정이며, 6단계로 이루어져 있다.

1. HTML 을 파싱하여, DOM 트리를 생성한다.
2. CSS 를 파싱하여, CSSOM 트리를 생성한다.
3. JS 를 실행한다.
4. DOM 과 CSSOM 을 결합해 실질적으로 그려질 요소를 Render Tree 로 구성한다.
5. 화면에 자리잡을 요소를 계산한다. (Layouting)
6. 화면에 그린다. (Painting)

CSS 를 받고 CSSDOM 으로 만드는 과정에서 외부 웹 폰트를 받아오게 된다.
이 때, Painting 과정으로 넘어가도 웹 폰트 로드가 끝나지않았다면, 해당 웹 폰트를 사용하는 컨텐츠의 렌더링을 차단하는 현상이 발생한다.

다음과 같은 방식들로 웹 폰트 로드의 최적화를 도울 수 있다.

1. Font 사이즈 줄이기.

   1. Font Format (WOFF 2.0)
   2. Subset Font
   3. Dynamic Subset Font (Unicode Range)

2. Rendering Block 사용하기.

   1. Flash Of Invisible Text (FOIT)
   2. Flash Of Unstyled Text (FOUT)
   3. Font Face Observer Library
   4. CSS font-display Attribute
