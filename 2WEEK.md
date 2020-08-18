# EUID_UISD

# 1day

## 임베디드(Embedded) 요소

## HTML 픽쳐(Picture) 요소

  * **0개 이상의 `<source>` 요소**와 **1개 이상의 `<img>`**를 포함하는 컨테이너 요소.
  * 다양한 스크린 환경(스마트폰, 테블릿, 데스크탑 등)에 맞는 적합한 이미지를 제공하기 위한 목적으로 사용.
  * `<source>` 요소를 사용할 수 없을 경우, `<img>` 요소가 화면에 표시.

  ```html
  <img> 요소
  - HTML 문서에 이미지를 포함(링크)
  
  [속성]
  src    - 이미지 파일 경로 설정
  alt    - 이미지 대체 텍스트 설정
  width  - 이미지 너비 설정
  height - 이미지 높이 설정
  usemap - 이미지 맵 연결 설정
  ```

## `<source>` 요소
  + `<picture>`, `<audio>`, `<video>` 요소의 **다중 미디어 리소스를 지정**하기 위해 사용.
  + 중첩 가능한 요소
  + `<srcset>`속성을 가짐 
    + `<img>`요소의 `<src>`속성과는 같지 X
  + `<media>`속성을 사용해서 media queries 구문을 사용할 수 있다
    + media queries 구문?  
    스마트폰, 테블릿, 데스크탑을 구분해 줄 수 있는 코드 구문

  ```html
          media 속성:
          <picture>
            <source srcset="bamboo-pen.png" media="(min-width: 600px)"> (좀 더 큰 이미지)
            <img src="bamboo-pen-narrow.png" alt="Bamboo Pen"> (작은 이미지)
          </picture>  

          type 속성:
          <picture>
            <source srcset="bamboo-pen.svg" type="image/svg+xml"> (1)
            <img src="bamboo-pen-narrow.png" alt="Bamboo Pen">
          </picture>  

          * type은 이미지 형식에 따라 변경
            - <source type="image/png">
            - <source type="image/jpeg">
            - <source type="image/svg+xml">
  ```
  * (1) `<svg>`, `<png>`, `<jpeg>` 등 여러 확장자를 사용할   때  브라우저가 올바르게 인식할 수 없다는 판단이 든다면
  mime type을 지정해서 미디어 타입을 설정한다.  

  ```html
    <!-- img + picture + source -->  

  <picture>
    <source srcset="media/image/kitten-large.png" type="image/png" media="(min-width: 900px)">
    <source srcset="media/image/kitten-medium.png" type="image/png" media="(min-width: 600px)">
    <img src="media/image/kitten-small.png" alt="작은 고양이"
  </picture>
  ```
  * min-width : 최소 가로폭
  * `<midea>`속성을 사용해서 반응형 웹을 만들 수 있다  


## HTML 비디오(Video) 요소

  * `<video>` 요소
    + 동영상 콘텐츠를 HTML 문서에 포함하기 위해서 사용.
    + src 속성이나 <source> 요소을 이용해 여러 개의 동영상 소스 중 하나를 표시. (현재는 mp3, mp4가 모든 브라우저에 지원되기 때문에 `<souce>`를 사용 X)

  [속성]   
  `<src>`      - 비디오 파일 경로   
  `<poster>`   - 포스터 이미지 경로 (poster요소가 없을 경우 비디오의 첫 화면이 나옴)   
  `<preload>`  - 사용자 경험 향상(메타데이터 / 비디오 다운로드)에 관한 설정    
  [none, metadata, auto(기본 값)]   
  `<controls>` - 재생 컨트롤 표시 설정   
  `<autoplay>` - 자동 재생 설정   
  자동재생은 가급적 사용 X (굳이 사용한다면 `<muted>`속성을 사용하여 음소거)    
  `<loop>`     - 반복 설정   
  `<muted>`    - 음소거 설정   
    * 
      + `<src>`, `<poster>` : 값이 반드시 필요하다  
      + `<preload>`, `<controls>`, `<autoplay>`, `<loop>`, `<muted>` : 값이 반드시 필요하지 않다. 

  
  자동재생은 가급적 사용 X (굳이 사용한다면 `<muted>`속성을 사용하여 음소거) 

  ```html
  [사용 예시]
  <video src="videofile.mp4" poster="posterimage.jpg">
  HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
  <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a> 하세요.
  </video>
  ```

  ```html
  <!-- video + track -->
  <video 
  src="media/video/holzweiler.mp4" 
  poster="media/video/holzweiler-short_cover.png"
  autoplay
  loop="true"
  muted="true"
  >

    <p>
      HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
      <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a> 하세요.
    </p>
  </video>
  ```

## HTML 오디오(Audio) 요소

  * `<audio>` 요소
    + 동영상 콘텐츠를 포함하기 위해서 사용.
    + src속성이나 <source> 요소을 이용해 여러개의 동영상 소스를 표시. (현재는 mp3, mp4가 모든 브라우저에 지원되기 때문에 `<souce>`를 사용 X)

  [속성]
  `<src>`      - 오디오 파일 경로   
  `<volume>`   - 볼륨 조절(0.0 ~ 1.0)   
  `<muted>`    - 음소거 설정   
  `<poster>`   - 포스터 이미지 경로   
  `<preload>`  - 사용자 경험 향상(메타데이터 / 비디오 다운로드)에 관한 설정    
  [none, metadata, auto]   
  `<controls>` - 재생 컨트롤 표시 설정   
  `<autoplay>` - 자동 재생 설정   
  `<loop>`     - 반복 설정   

  ```html
  [사용 예시]
  <audio src="audiofile.mp3">
  HTML5 <code>audio</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
  <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a>로 업데이트 하세요.
  </audio>
  ```
  ```html
  <!-- audio -->
  <figure style="margin: 0;"> (`<margin>` 여백 없음)
    <img  
    src="media/audio/tobu-Itro_Cloud9--cover.jpg"
    alt="cloud9 - todu & itro" width="300" height="300">
  <figcaption>
    <audio src="media/audio/tobu-Itro_Cloud9.mp3" controls autoplay>
      <p>
        HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
        <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a> 하세요.
      </p>
    </audio>
  </figcaption>
</figure>
  ```

## HTML 트랙(Track) 요소
  * 비디오/오디오 재생 시, 자막을 표시.
  * `<default>` 
    + 속성을 설정하지 않을 경우, 자막 사용 안함 됨
    + 자막 언어 고정 가능

  ```html
  [사용 예시]
      <video src="videofile.mp4" poster="posterimage.jpg">
        <track kind="subtitles" src="videofile.ko.vtt" srclang="ko" label="한국어" default>
        <track kind="subtitles" src="videofile.en.vtt" srclang="en" label="English">
      </video>

      <audio src="audiofile.mp3">
        <track kind="subtitles" src="audiofile.ko.vtt" srclang="ko" label="한국어">
        <track kind="subtitles" src="audiofile.en.vtt" srclang="en" label="English">
      </audio>
  ```

  ```html
    <!-- video + track -->
  <video 
  src="media/video/The temperature of dating.mp4" 
  controls>
    <track 
    kind="subtitles"
    src="media/video/vtt/The temperature of dating.ko.vtt"
    srclang="ko"
    label="한국어">
    <track 
    kind="subtitles"
    src="media/video/vtt/The temperature of dating.en.vtt"
    srclang="en"
    label="영어"
    default>
  </video>

  ```

## HTML 인라인 프레임(iframe) 요소

  * 인라인 프레임(Inline Frame)에 다른 HTML 페이지를 포함하여 화면에 표시.

  [속성]  
  `<src>`             - 프레임 소스 설정  
  `<width>`          - 프레임 너비 설정  
  `<height>`          - 프레임 높이 설정  
  `<allowfullscreen>` - 프레임 전체화면 설정  
```html
      [사용 예시]
      <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/0wlXaHmmOVc?rel=0&amp;showinfo=0"
        allow="autoplay; encrypted-media"
        allowfullscreen></iframe>

      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d12643.636820892792!2d127.01610674058901!3d37.60429582641849!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x357cbc91e5ca4f03%3A0x18820a16e406c8ea!2z7ISc7Jq47Yq567OE7IucIOyEseu2geq1rCDquLjsnYwx64-ZIDUzMC0zNg!5e0!3m2!1sko!2skr!4v1520001155674" width="600"
        height="450"
        style="border: 0"
        allowfullscreen></iframe>
```
```html
  <!-- iframe -->
          <iframe 
    width="560" 
    height="315" 
    src="https://www.youtube.com/embed/0wlXaHmmOVc" 
    frameborder="0" 
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
    </iframe>

        <iframe 
    src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d6324.212923431429!2d127.0002682!3d37.5761107!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x357ca2e2c8102391%3A0x51d36941638dd458!2sDobbit!5e0!3m2!1sko!2skr!4v1597675479744!5m2!1sko!2skr" 
    width="600" 
    height="450" 
    frameborder="0" 
    style="border:0;" 
    aria-hidden="false" 
    tabindex="0">
    </iframe>
```
## HTML 이미지 맵(map) 요소

### `<map>` 요소
  * 이미지 맵(클릭 가능한 링크 영역)을 정의하기 위해 <area>와 함께 사용됨.
  * 이미지 맵 좌표 생성: https://www.image-map.net/

### `<area>` 요소
  * 이미지의 핫스팟 지역 정의, 하이퍼링크 설정. <map> 내부에서만 사용 가능.
  * 여러개 사용 가능 (원, 사각형, 다각형)
  * **`<alt>`(필수)**, `<title>` 성분을 사용해 주기

  [속성]  
  `<shape>`    - 핫스팟 모양 설정  
  `<coords>`   - 모양의 좌표 값 설정  
  `<href>`     - 하이퍼링크 주소 설정  
  `<target>`   - 새 창(탭) 열림 설정   
  `<alt>`      - 대체 텍스트 설정  
  `<hreflang>` - 연결된 페이지의 언어 속성 설정  
  `<download>` - canvas 데이터 다운로드 설정  
```html
      [사용 예시]
      <img src="products-map.jpg" alt="제품 모음" usemap="#products-map">
      <map name="products-map">
        <area
          shape="circle"
          coords="200,250,25"
          hreflang="en-GB"
          href="another.html"
          alt="Another Page"
          target="_blank">
      </map>
```

```html
  <!-- map + area -->
    <img 
    usemap="#foods-in-kr"
    src="media/image/food-in-korea-of-republic.jpg" 
    alt="우리나라 길거리 음식도감">

  <map name="foods-in-kr">
    <area shape="rect" coords="0, 0, 100, 100"
    href="http://www.typographyseoul.com/news/detail/404">
  </map> 
```

## HTML 확장 가능한 벡터그래픽(SVG) 요소
  * 확장가능한 벡터 그래픽(SVG)은 2차원의 벡터 그래픽을 기술하기 위한 XML 마크업 언어.
  * `<SVG>` 요소는 내용이 상당히 방대하다
  * 이미지를 직접적으로 삽입하는 것과 svg요소를 사용하여 그림을 삽입하는 것 차이
    + 이미지를 svg에 연결시키는 경우는 css 코드를 이용해서 디자인을 변경 할 수 없다
    + 직접적으로 코드를 따라서 그래픽에 있는 디자인을 변경하려면 svg를 문서내에 직접 삽입을 해야한다.  

      ```html
      [예시 코드]
      <img src="svgfile.svg" alt="SVG File">

      <svg width="150" height="150" viewBox="0 0 150 150">
        <circle r="50" cx="75" cy="75" fill="#333" stroke="#900" stroke-width="4"; />
      </svg>
      ```
---
# 2day

  * GUI, CLI란?
    + GUI (그래픽 유저 인터페이스)
      - 그래픽 환경으로 시스템 제어 (우리가 마우스로 클릭하며 사용하는 것) 

    + CLI (커맨드 라인 인터페이스)
      - 명령어를 통해 시스템 제어 (예: Bash)
        + Bash    
        각 운영 체제가 다른 컴퓨터에서 같은 명령어로 컴퓨터를 조작? 할 수 있는 프로그램?
          - cd (Change-Directoyr) : 지정한 경로로 이동
          - ls (List) : 폴더 목록 보기

  * Git 이란?    
   버전 관리 시스템(VCS), 무료, 공개 소프트웨어 
    

  * GitHub
   코드저장소(Git)을 웹에 옮겨 놓은 원격저장소
    + 프로젝트를 관리할 때 사용하기 좋음. (여러사람이 참여하여 수정 가능) 
    + 분산버전관리    
     파일 변화를 시간에 따라 기록, 특정 시점의 버전을 다시 가져올 수 있다.
      - 코드 변경 이력 확인 가능, 코드 복구 가능
      - 코드 이전 이력과 비교 가능
    + <https://aonee.tistory.com/15>


## [CSS] 박스 모델

## [BLOCK vs INLINE]
   * block level 요소 (Flow Contents : HTML5)
   * inline 요소 (Phrasing Contents : HTML5)
        
  + 블록 박스
    - 블록 박스는 다른 블록 박스에 포함되거나, 포함할 수 있고, **너비(width)/ 높이(height) 설정이 가능**합니다. 내부에 콘텐츠를 포함하지 않을 경우 높이는 0입니다.
        - 컨텐츠의 남은 여백까지도 박스로 채워진다. 
          그래서 글자의 정렬(왼쪽, 가운데, 오른쪽)을 설정할 
          수 있다

  + 인라인 박스 
    - 인라인 박스는 인라인 박스에 포함되거나, 포함할 수 
          있지만, **블록 요소는 포함할 수 없습니다.**(컨텐츠의 라인까지만 박스가 채워진다.)   
          **너비(width)/ 높이(heght) 설정이 가능하지 않습니다. 내부에 포함한 콘텐츠만 높이와 너비를 가지게 됩니다.**

  + 인라인 블록 박스 
    - 인라인 블록 박스는 기본적으로 인라인처럼 화면에 렌더링되지만, 블록박스처럼 너비(width)/ 높이(heght) 설정이 가능합니다. 
        (`<img>`, `<input>`, `<button>` 등)
    ```css
    <!--display요소로 inline, block, inline block 설정 가능-->
    .inline-block-box {
      display: inline; 
      width: 200px;
    }
    ```
    * display요소로 inline, block, inline block 설정 가능
      + display: inline     
      display: block     
      display: inline block     
        
      
  * 공부 할 때 각 요소를 선택해서 display 값을 확인하면 된다.
      ```
      [block 요소들]
        - address
        - article
        - aside
        - audio
        - blockquote
        - canvas
        - dd
        - div
        - dl
        - fieldset
        - figcaption
        - figure
        - footer
        - form
        - h1~6
        - header
        - hr
        - noscript
        - ol
        - output
        - p
        - pre
        - section
        - table
        - tfoot
        - ul
        - video
      ```

## [BOX]
  * margin-box   --  외부 공간 박스
  * border-box   --  테두리 공간 박스
  * padding-box  --  내부 공간 박스
  * content-box  --  콘텐츠 공간 박스
    + margin-box : 투명한 영역(배경색 X), 박스와 박스 사이의 간격을 제어할 때 사용, 음수값 사용 가능(-10px, -20px..)
    + border-box : 박스 테두리 모양을 치고 싶을 때 사용 (음수값 X)
    + padding-box : 박스 안쪽에 공간 여백을 줄 때 사용 (음수값 X)
    + border-box, padding-box, content-box : 배경색 적용 가능
    
  * 인라인 박스는 좌/우 방향으로 마진,패딩 공간을 설정할 수 있으나, **상/하 방향으로는 공간이 설정되지 않습니다.**
    + 패딩 공간을 설정 패딩이 적용된 것 처럼 보이나 패딩으로 인한 공간이 벌어지지 않는다.

  ### [margin]
   * margin-top
   * margin-right
   * margin-bottom
   * margin-left
      + 시계 방향 순 (t r b l)
   * `margin: t r b l` 모든 방향 값이 다름
   * `margin: t r b (l=r)`    
  위/아래 값을 다르게 줄 때, left값이 right값을 상속 받음
   * `margin: t r (b=t) (l=r)`    
   위/아래, 좌/우 값이 동일, bottom값이 top값을 상속 받음
   * `margin: t (r=t) (b=t) (l=r)` 모든 방향 값이 동일

  ### [border]
  ```
    * border-(top|right|bottom|left)-width
    * border-(top|right|bottom|left)-style
    * border-(top|right|bottom|left)-color
    * border: width style color (모든 방향 값을 설정)
    * border-top: width style color 
    * border-right: width style color
    * border-bottom: width style color
    * border-left: width style color
  ```

  ### [padding] 
   * [margin]과 같은 작동 원리로 동작함
  ```
    * padding-top
    * padding-right
    * padding-bottom
    * padding-left
    * padding: t r b l
    * padding: t r b (l=r)
    * padding: t r (b=t) (l=r)
    * padding: t (r=t) (b=t) (l=r) 
  ```

  ```css
  .demo {
    width: 100px;
    height: 100px;
    background: #eee;
    text-align: center;
    line-height: 100px; (줄 높이를 정하는 속성)
    margin: 20px 10px 10px 15px;
    padding-top: 1em;
    border-bottom: 1em double #6d70d2;
  }
  ```
   * border 테두리 지정 : <https://www.tabmode.com/homepage/border.html#gsc.tab=0>

  #### `text-align` 속성 
   * 텍스트의 정렬 방향을 의미합니다.
      + left: 왼쪽 정렬    
        right: 오른쪽 정렬     
        center: 중앙 정렬    
        justify: 양쪽 정렬 (자동 줄바꿈시 오른쪽 경계선 부분 정리)

      ```css
      #box1 { text-align: right; }
      #box2 { text-align: left; }
      #box3 { text-align: center; }
      ```

```css
      .dimension-ex {
  min-width: 200px;
  min-height: 80px;
  max-width: 500px;
  max-height: 120px;
}
```
  
## [DIMENSION]
  * width       --  박스 너비
  * height      --  박스 높이
  * min-width   --  박스 최소 너비
  * min-height  --  박스 최소 높이
  * max-width   --  박스 최대 너비
  * max-height  --  박스 최대 높이

  ### [BOX SIZING]
   * content-box
   * border-box

     - content-box (default):  
      width = content-box  
      height = content-box

     - border-box:  
        width = content-box + padding-box + border-box  
        height = content-box + padding-box + border-box  

        ```css
        box-sizing: border-box;
        box-sizing: content-box;
        ```

       ```css
       .box-sizing { 
         box-sizing: border-box, content-box;
         width: 200px; 
         height: 100px;
         border: 1px solid;
         text-align: center;
         line-height: 100px;
       }
       ```



  ### [FLOW]
   * `overflow`  --  박스를 넘쳐난 상태(흐름) 조정   
   부모 박스의 영역을 자식 박스가 **넘어서게 될 때 화면에 어떻게 렌더링할지를 결정**하게 됩니다

     - `auto` 자동 값을 사용할 경우:   
     흐름이 넘치면 x/y 축 모두 스크롤 바가 자동으로 생깁니다.   
     흐름이 넘치지 않으면 스크롤바는 보이지 않습니다.

     - `visible` : 흐름이 넘친 영역이 모두 보여집니다.
     - `hidden` : 흐름이 넘친 영역이 모두 감춰집니다.
     - `scroll` : x/y축 스크롤이 무조건 보입니다.
     - `overflow-x` : x축 방향만 overflow 설정을 수행합니다.
     - `overflow-y` : y축 방향만 overflow 설정을 수행합니다.


