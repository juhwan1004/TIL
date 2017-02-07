먼저, font-face를 mixin으로 만들면 다양한 font-face 재사용이 편리하다.

Interpolation(보간법)을 사용하여 내부 값들을 변수화 해준다.

_mixins.scss파일에서

1. url을 interpolation로 변경해주기 #{font-path}
2. font-family 변수화 $font-name
3. font-style과 weight는 리스트로 필수 인자가 아닌 선택인자(기본값 설정)로 만들어 줌 -> 써도되고 안써도되고 그건 내맘

main.sass에서 @import "mixins"로 불러오고

@include하여 font-face mixin에 인자를 전달해주면 css에 전달한 인자값에 따른

font-face mixin이 만들어진다.

```css
@mixin font($font-path, $font-name, $font-options: normal normal) {
  @font-face {
    font-family: $font-name;
    font-weight: nth($font-options, 1);
    font-style: nth($font-options, 2);
    src: url('#{$font-path}.eot');
    src: url('#{$font-path}.eot?#iefix') format('embedded-opentype'),
         url('#{$font-path}.woff') format('woff')
  }
}
```

