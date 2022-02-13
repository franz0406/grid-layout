#### CSS Grid 그리드에서 벗어나 자유롭게 레아아웃! [예제 사이트 보기](https://franz0406.github.io/grid-layout/)

#### Grid Basic
```css
grid-template-columns:100px 200px 1fr;
/* 그리드의 '행의 개수와 크기' 를 각각 지정 */

grid-template-rows: 100px 100px 1fr;
/* 그리드의 '열의 수' 를 각각 지정 */

grid-template:100px 200px 1fr/100px 100px 1fr;
/* 축약형 grid-template: rows / columns */

grid-auto-rows: 100px 200px;
/* 그리드 열의 수가 몇개던 100px 200px 반복 */

grid-auto-flow: dense;
/* 그리드 셀간의 빈공간을 최대한 채워주는 속성 */

```
#### Fraction
![fraction](https://user-images.githubusercontent.com/80723523/153728750-97da29de-1b67-491b-ad4c-fc6d9d0106a7.jpg)

#### repeat( count, size )
```css
grid-template-columns: repeat(3, 1fr);
grid-template-rows: repeat(2, 100px);
```

#### auto-fit & minmax( min-size, max-size )
```css
grid-template-columns: repeat(auto-fit, 300px);

grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
```

##### gap
```css
grid-gap:10px;         /* 행과 열 사이 간격 */
grid-row-gap:10px;     /* 행 사이 간격 */
grid-column-gap:10px;  /* 열 사이 간격 */
```
![grid_gap](https://user-images.githubusercontent.com/80723523/153727454-6a77e962-4cdf-4d3c-b04d-1ff9046198d7.jpg)

#### 자식요소 그리드 포지셔닝 속성
##### 그리드 Line 기준
```
- grid-column-start:1; 행 시작 포인트
- grid-column-end:3;   행 끝 포인트
- grid-column:1/3;     축약형 시작/끝

- grid-row-start:1;    열 시작 포인트
- grid-row-end:3;      열 끝 포인트
- grid-row:1/3;        축약형 시작/끝
- grid-column:1/-1;    -1 은 맨끝지점
```
##### 그리드 Cell 기준
```
- grid-column:auto/span 3;  자기 위치기준 몇 컬럼 사용할지 정의
- grid-column:span 3;       auto 속성 생략 가능함.

- justify-self:;  flex의 justify-content 속성과 동일
- align-self:;    flex의 align-items 속성과 동일
```

##### Gris Template areas - 그리드 커스텀
```html
<div>
    <div class="header">H</div>
    <div class="aside">A</div>
    <div class="content">C</div>
    <div class="footer">F</div>
</div>
```
```css
div {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: 50px 200px 50px;
    grid-gap:5px;

    grid-template-areas: 
        "h h h h h h h h h h h h"
        "a a a c c c c c c c c c"
        "f f f f f f f f f f f f"    
    ;
    /*  . 점 사용시 해당 영역은 비워짐
        ex) grid-template-areas: 
            ". . h h h h h h h h h h"
            ". . a c c c c c c c c c"
            ". . f f f f f f f f f f"    
    */
}
div > .header { grid-area:h; }
div > .aside { grid-area:a; }
div > .content { grid-area:c; }
div > .footer { grid-area:f; }
```
![template_areas](https://user-images.githubusercontent.com/80723523/153732452-65a675cf-cab8-446e-b689-354567552b87.jpg)



