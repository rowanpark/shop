# shop

- 개인 **스터디** & **mini 프로젝트**
- 참고 도서 : 백견불여일타 이젠 프로젝트다! 스프링 부트 쇼핑몰 프로젝트 with JPA / 변구훈 / 로드북<br/><br/>
- 기술 스택 :<br/>
`Spring Boot`, `Spring Data JPA`, `Spring Security`, `Maven`, `Thymeleaf`, `Bootstrap`,<br/>
`Java`, `JavaScript`, `JQuery`, `HTML5`, `CSS3`, `MySQL`
- 사용 툴 : `IntelliJ`, `MySQLWorkbench`, `Mac Terminal`<br/><br/>

### 히스토리<br/>
- 230323 : html img 태그의 src 속성 값(url)에는 로컬 경로가 포함되면 안된다. 웹 브라우저는 로컬 파일 시스템에 직접 접근할 수 없기 때문이다.<br/>
`/Users/rowan/Dev/images/shop/item/` 대신에 `/images/shop/item/` 사용<br/>

- 230330 : `templates/item/itemMng.html`에서 `thymeleaf parsing error`가 발생하였다.
ShopApplication을 올리고나서 한동안은 `itemMng.html`이 떴다가 일정 시간이 지나면 콘솔에 아래와 같은 메세지가 뜨면서 `Whitelabel Error Page(status=500)` 페이지가 화면에 로드됐다.
해결방안을 못 찾고 있다가 `com.shop.constant.ItemSellStatus.java` `enum 파일`을 삭제했다 다시 생성하니 오류가 발생하지 않았다.
찾지 못한 오타나 공백이 포함되어 있을 것으로 추정 중이나 정확한 원인은 파악하지 못했다.
  > 2023-03-27 14:46:48.459 ERROR 29710 --- [-nio-80-exec-10] org.thymeleaf.TemplateEngine             : [THYMELEAF][http-nio-80-exec-10] Exception processing template "item/itemMng": An error happened during template parsing (template: "class path resource [templates/item/itemMng.html]")

  > Caused by: org.attoparser.ParseException: Exception evaluating SpringEL expression: "item.itemSellStatus == T(com.shop.constant.ItemSellStatus).SELL" (template: "item/itemMng" - line 62, col 21)

  > Caused by: org.thymeleaf.exceptions.TemplateProcessingException: Exception evaluating SpringEL expression: "item.itemSellStatus == T(com.shop.constant.ItemSellStatus).SELL" (template: "item/itemMng" - line 62, col 21)

  > Caused by: org.springframework.expression.spel.SpelEvaluationException: EL1013E: Cannot compare instances of class com.shop.constant.ItemSellStatus and class com.shop.constant.ItemSellStatus

  > 2023-03-27 14:46:48.461 ERROR 29710 --- [-nio-80-exec-10] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed; nested exception is org.thymeleaf.exceptions.TemplateInputException: An error happened during template parsing (template: "class path resource [templates/item/itemMng.html]")] with root cause

