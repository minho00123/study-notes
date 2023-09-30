---
Created: 2023-09-24 09:51
Modified: 2023-09-24 09:51
---

# Line Terminator
---
## Description
- Source Text의 가독성을 높이기 위해 사용된다.
- Line Terminator가 금지된 곳이 있기 때문에 JavaScript 코드 실행에 영향을 줄 수 있다.
- Line Terminator는 세미콜론 자동 삽입 기능에도 영향을 준다.
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
      <td>U+000A</td>
      <td>Line Feed</td>
      <td>&lt;LF&gt;</td>
      <td>New line character in UNIX systems.</td>
      <td>\n</td>
    </tr>
    <tr>
      <td>U+000D</td>
      <td>Carriage Return</td>
      <td>&lt;CR&gt;</td>
      <td>New line character in Commodore and early Mac systems.</td>
      <td>\r</td>
    </tr>
    <tr>
      <td>U+2028</td>
      <td>Line Separator</td>
      <td>&lt;LS&gt;</td>
      <td><a href="https://en.wikipedia.org/wiki/Newline" class="external" target="_blank">Wikipedia</a></td>
      <td></td>
    </tr>
    <tr>
      <td>U+2029</td>
      <td>Paragraph Separator</td>
      <td>&lt;PS&gt;</td>
      <td><a href="https://en.wikipedia.org/wiki/Newline" class="external" target="_blank">Wikipedia</a></td>
      <td></td>
    </tr>
  </tbody>
</table>

## Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators