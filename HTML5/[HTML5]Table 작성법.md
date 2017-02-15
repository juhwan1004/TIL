[HTML] Table 작성 시 고려 사항				

# Table 작성  
Tip. e-mail 작성 시(e.g. g-mail) 제대로된 CSS를 지원 못하므로 table을 사용하여 form 형식을 만들어 보내주는 것이 좋다.

##  1. <caption> 태그 작성 (필수)  

table 작성 시 제목 역할을 하는 caption을 반드시 써주자 !!!   

**1.1 간단한 테이블 (one header)의 경우**  

table에 대한 설명(summary) 생략가능 

```html
<table>
  <caption>Teddy bear collectors:</caption>
  <tr>
    <th scope="col">Last Name</th>
    <th scope="col">First Name</th>
  </tr>
  <tr>
    <td>Phoenix</td>
    <td>Imari</td>
    <td>Henry</td>
  </tr>
  <tr>
    <td>Zeki</td>
    <td>Rome</td>
    <td>Min</td>
  </tr>
</table> 
```

**1.2 Two headers 이상의 복잡한 테이블의 경우**  

caption과 함께 테이블에 대한 summary(aria-describedby, figure 권장) 작성 필요

**1.2.1 caption + span**

```html
<caption>Availability of holiday accommodation <br>
  <span>Column one has the location and size of accommodation, other columns show the type and number of properties available</span>
</caption>
```

**1.2.2 aria-describedby**

```html
<p id="tblDesc">Column one has the location and size of accommodation, other columns show the type and number of properties available.</p>
<table aria-describedby="tblDesc">
```

**1.2.3 figure + figcaption**

```html
<figure>
  <figcaption>
    <strong>Paris: Availability of holiday accommodation</strong><br>
    <span>Column one has the location and size of accommodation, other columns show the type and number of properties available.</span>
  </figcaption>
  <table>
[…]
  </table>
</figure>
```

## 2. Multi-level Headers, 큰 `<th>`안에 또 하위 `<th>`가 있는 경우(headers 작성)

`headers` 속성을 통해 해당 `<td>`가 속해있는 `<th>`가 읽혀질 순서를 지정해줘야 한다.

```html
<td headers="par pbed1 stud">11</td>
<td headers="par pbed1 apt"> 20</td>
```

## 3. scope 속성 사용 

**3.1 Two headers 이상의 table의 경우 `<th>`가 읽혀질 방향을 나타내기 위해 작성한다.**

Delivery slots:

|               | Monday | Tuesday | Wednesday | Thursday | Friday |
| ------------- | ------ | ------- | --------- | -------- | ------ |
| 09:00 - 11:00 | Closed | Open    | Open      | Closed   | Closed |
| 11:00 - 13:00 | Open   | Open    | Closed    | Closed   | Closed |
| 13:00 - 15:00 | Open   | Open    | Open      | Closed   | Closed |
| 15:00 - 17:00 | Closed | Closed  | Closed    | Open     | Open   |

```html
<table>
  <caption>Delivery slots:</caption>
  <tr>
    <td></td>
    <th scope="col">Monday</th>
    <th scope="col">Tuesday</th>
    <th scope="col">Wednesday</th>
    <th scope="col">Thursday</th>
    <th scope="col">Friday</th>
  </tr>
  <tr>
    <th scope="row">09:00 - 11:00</th>
    <td>Closed</td>
    <td>Open</td>
    <td>Open</td>
    <td>Closed</td>
    <td>Closed</td>
  </tr>
</table>
```

**3.2 rowspan`, `colspan`작성 시 scope= [ colgroup | rowgroup ]**

```html
<table>
   <tr>
    <th colspan="2" scope="colgroup">Mars</th>
    <th rowspan="2" scope="rowgroup">Venus</th>
  </tr>
</table>
```

## 4. 하나의 `<td>`안에 여러 문장을 작성 할 경우

**4.1 서로 연관된 내용**

`<td>`안에 `<ul>`(List)로 작성

```html
<th>포인트 사용 안내</th>
<td>
  <ul>
    <li>500 포인트 이상일 때 사용하세요</li>
    <li>10000 포인트 부터 사용가능해요</li>
    <li>포인트는 연말에 초기화 됩니다.</li>
  </ul>
</td>
```

**4.2 연관 없는 내용**

각각 `<td>`로 구분하여 한 줄 씩 작성

```html
<th>table headers</th>
<td>
	<tr>
      <td>웹의 어머니 마더 데레사</td>
  	</tr>
  	<tr>
      <td>오늘 점심은 고추장 삼겹살</td>
  	</tr>
  	<tr>
      <td>삼성 노트북</td>
  	</tr>
</td>
```
**참고:** [w3g](https://www.w3.org/WAI/tutorials/tables/)
