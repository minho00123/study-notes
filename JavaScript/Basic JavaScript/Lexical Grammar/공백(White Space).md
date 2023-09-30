---
Created: 2023-09-24 09:59
Modified: 2023-09-24 09:48
---

# 공백(White Space)
---
## Description
- 코드의 가독성을 향상시키고 [[토큰(Token)]]을 서로 구분하는 데 자주 사용된다.
- 일반적으로 코드 기능에는 필요하지 않다.
- White Space 문자와 사용법은 컴퓨터 언어마다 다르다.
## Examples
<table>
  <thead>
    <tr>
      <th>Code point</th>
      <th>Name</th>
      <th>Abbreviation</th>
      <th>Description</th>
      <th>Escape sequence</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>U+0009</td>
      <td>Character tabulation</td>
      <td>&lt;TAB&gt;</td>
      <td>Horizontal tabulation</td>
      <td>\t</td>
    </tr>
    <tr>
      <td>U+000B</td>
      <td>Line tabulation</td>
      <td>&lt;VT&gt;</td>
      <td>Vertical tabulation</td>
      <td>\v</td>
    </tr>
    <tr>
      <td>U+000C</td>
      <td>Form feed</td>
      <td>&lt;FF&gt;</td>
      <td>Page breaking control character (<a href="https://en.wikipedia.org/wiki/Page_break#Form_feed" class="external" target="_blank">Wikipedia</a>).</td>
      <td>\f</td>
    </tr>
    <tr>
      <td>U+0020</td>
      <td>Space</td>
      <td>&lt;SP&gt;</td>
      <td>Normal space</td>
      <td></td>
    </tr>
    <tr>
      <td>U+00A0</td>
      <td>No-break space</td>
      <td>&lt;NBSP&gt;</td>
      <td>Normal space, but no point at which a line may break</td>
      <td></td>
    </tr>
    <tr>
      <td>U+FEFF</td>
      <td>Zero-width no-break space</td>
      <td>&lt;ZWNBSP&gt;</td>
      <td>When not at the start of a script, the BOM marker is a normal whitespace character.</td>
      <td></td>
    </tr>
    <tr>
      <td>Others</td>
      <td>Other Unicode space characters</td>
      <td>&lt;USP&gt;</td>
      <td><a href="https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5Cp%7BGeneral_Category%3DSpace_Separator%7D" class="external" target="_blank">Characters in the "Space_Separator" general category</a></td>
      <td></td>
    </tr>
  </tbody>
</table>
## Reference
- https://developer.mozilla.org/en-US/docs/Glossary/Whitespace
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators
[[Lexical Grammar|]]