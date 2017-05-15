**Front-End School 3**

# Day7

## HTML5 Content Models

> Content Model이란 요소의 내용이 가지리라 기대되는 것에 대한 설명이다.



### 종류

- **Metadata content**  

  > Metadata content is content that sets up the presentation or behavior of the rest of the content, or that sets up the relationship of the document with other documents, or that conveys other "out of band" information.  

  메타데이터는 나머지 내용의 표현이나 행동을 설정하거나, 또는 현재 문서와 다른 문서의 관계를 설정하거나, 혹은 미분류 정보들을 포함합니다.  

  ​

- **Flow content**  

  > Most elements that are used in the body of documents and applications are categorized as flow content.  

  문서 바디와 응용프로그램에서 사용되는 요소 대부분은 플로우 컨텐츠로 분류됩니다.    


- **Sectioning content**  

  > Sectioning content is content that defines the scope of [headings](http://html5.clearboth.org/content-models.html#heading-content) and [footers](http://html5.clearboth.org/sections.html#the-footer-element).  

  섹션 컨텐츠 (article, aside, nav, section) 는 [헤딩](http://html5.clearboth.org/content-models.html#heading-content)과 [푸터](http://html5.clearboth.org/sections.html#the-footer-element)의 유효범위를 정의합니다.  

  각각의 [섹션 컨텐츠](http://html5.clearboth.org/content-models.html#sectioning-content)는 헤딩과 [개요](http://html5.clearboth.org/sections.html#outline)를 가질 가능성이 있습니다. 이에 관해서는 [헤딩과 섹션에 관한 섹션](http://html5.clearboth.org/sections.html#headings-and-sections)을 참조하십시오.  

  ​

- **Heading content**  

  > Heading content defines the header of a section (whether explicitly marked up using [sectioning content](http://html5.clearboth.org/content-models.html#sectioning-content) elements, or implied by the heading content itself).  

  제목 컨텐츠(h1 ~ h6, hgroup)는 섹션(섹션 컨텐츠를 이용해 명시적으로 마크업 했거나, 또는 [제목 컨텐츠](http://html5.clearboth.org/content-models.html#sectioning-content)에 의해 암시적으로 마크업 된)의 헤더를 정의합니다.    

  ​

- **Phrasing content**  

  > Phrasing content is the text of the document, as well as elements that mark up that text at the intra-paragraph level. Runs of [phrasing content](http://html5.clearboth.org/content-models.html#phrasing-content) form [paragraphs](http://html5.clearboth.org/content-models.html#paragraph).  

  구문 컨텐츠는 문서의 텍스트이고, 또한 그 텍스트를 문단 내부 레벨로 마크업 하는 요소들입니다. [구문 컨텐츠](http://html5.clearboth.org/content-models.html#phrasing-content)가 모여서 [문단](http://html5.clearboth.org/content-models.html#paragraph)을 구성합니다.  

  ​

- **Embedded content**  

  > Embedded content is content that imports another resource into the document, or content from another vocabulary that is inserted into the document.  

  포함된embedded 컨텐츠란 다른 자원을 문서에 삽입하는 컨텐츠, 또는 문서에 삽입된 다른 사전에서 유래한 컨텐츠를 말합니다.  (audio, canvas, embed, iframe, img, math, object, svg, video)

  ​

- **Interactive content**  

  > Interactive content is content that is specifically intended for user interaction.  

  대화형 컨텐츠는 사용자의 상호작용을 위해 특별히 의도된 내용입니다.  



**참고** [W3C](http://html5.clearboth.org/content-models.html)



