- <b>REST 방식</b>

|이전 표현|REST 방식 표현|
|-|-|
|/board/modify<br>게시물의 수정(행위/목적)|/board/123<br>게시물 자원 자체|
|\<form\><br>데이터의 묶음|PUT 방식<br>행위나 목적|

<br><br>

- <b>URL 설계와 DTO 설계</b>

|URL<br>(Method)|설명|반환 데이터|
|-|-|-|
|/replies<br>(POST)|특정한 게시물의 댓글 추가|{‘rno’:11}<br>생성된 댓글의 번호|
|/replies/list/:bno<br>(GET)|특정 게시물(bno)의 댓글 목록<br>‘?’ 뒤에 페이지 번호를 추가해서 댓글 페이징 처리|PageReponseDTO를 JSON으로 처리|
|/replies/:rno<br>(PUT)|특정한 번호의 댓글 수정|{‘rno’:11}<br>수정된 댓글의 번호|
|/replies/:rno<br>(DELETE)|특정한 번호의 댓글 삭제|{‘rno’:11}<br>삭제된 댓글의 번호|
|/replies/:rno<br>(GET)|특정한 번호의 댓글 조회|댓글 객체를 JSON으로 변환한 문자열|

<br>

- `:`
  - 동적 경로 매개변수
  - ```javascript
    // 클라이언트가 /replies/list/123로 요청을 보내면,
    // 서버는 123에 해당하는 데이터를 찾아 응답

    // 서버에서 Express를 쓴다면!!!
    app.get('/replies/list/:bno', (req, res) => {
        const bno = req.params.bno; // 여기서 bno를 가져와!!!
        res.send(`댓글 번호 ${bno}의 데이터를 보내드립니다!!!`);
    });
    ```

<br>

```java
package org.zerock.b01.controller;

import io.swagger.v3.oas.annotations.Operation;
import lombok.RequiredArgsConstructor;
import lombok.extern.log4j.Log4j2;
import org.springframework.web.bind.annotation.*;
import org.zerock.b01.dto.PageRequestDTO;
import org.zerock.b01.dto.PageResponseDTO;
import org.zerock.b01.dto.ReplyDTO;
import org.zerock.b01.service.ReplyService;

@RestController
@RequestMapping("/replies")
@Log4j2
@RequiredArgsConstructor
public class ReplyController {

  private final ReplyService replyService;
  
  // @Operation           : Swagger UI에서 API의 설명 작성, 자동 문서화
  //  - summary           : API의 한줄 요약
  //  - description       : API의 상세 설명
  @Operation(summary = "Replies of Board", description = "GET 방식으로 특정 게시글의 댓글 목록")
  // {bno}                : 게시글 번호를 동적으로 받음
  @GetMapping(value = "/list/{bno}")
  // @PathVariable("bno") : URL에서 받은 bno 값을 매개변수 Long bno에 바인딩
  public PageResponseDTO<ReplyDTO> getList(@PathVariable("bno") Long bno, PageRequestDTO pageRequestDTO) {
    PageResponseDTO<ReplyDTO> responseDTO = replyService.getListOfBoard(bno, pageRequestDTO);

    return responseDTO;
  }
}
```

<br>

```java
package org.zerock.b01.repository;

import org.springframework.data.domain.Page;
import org.springframework.data.domain.Pageable;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.zerock.b01.domain.Reply;

public interface ReplyRepository extends JpaRepository<Reply, Long> {

  // :    : 동적 값을 전달하는 역할
  // :bno : 메서드의 매개변수 Long bno 값이 :bno에 바인딩
  @Query("select r from Reply r where r.board.bno = :bno")
  Page<Reply> listOfBoard(Long bno, Pageable pageable);
}
```

<br><br>

- <b>연관 관계를 결정하는 방법</b>
  - 변화가 많은 쪽을 기준
  - ERD에서 FK를 기준

- @ManyToOne

```java
package org.zerock.b01.domain;

import jakarta.persistence.*;
import lombok.*;

@Entity
@Table(name = "reply", indexes = {
    @Index(name = "idx_reply_board_bno", columnList = "board_bno")
})
@Getter
@Builder
@AllArgsConstructor
@NoArgsConstructor
@ToString(exclude = "board")
public class Reply extends BaseEntity {

  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long rno;

  // 다수의 엔티티가 하나의 엔티티에 연결
  //  - 다대일 관계
  //  - 여러 댓글(Reply)이 하나의 게시글(Board)에 달림
  @ManyToOne(fetch = FetchType.LAZY)
  private Board board;

  private String replyText;

  private String replyer;

  public void changeText(String text) {
    this.replyText = text;
  }
}
```

<br>

- @OneToMay
  - ```java
    @Entity
    public class Board {

        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long bno;

        // 하나의 엔티티가 여러 엔티티를 참조
        //  - 일대다 관계
        //  - 하나의 게시글(Board)에 여러 댓글(Reply)이 달림
        @OneToMany(mappedBy = "board", fetch = FetchType.LAZY)
        private List<Reply> replies = new ArrayList<>();

        private String title;
        private String content;
    }
    ```

<br>

- |특징|@ManyToOne|@OneToMany|
  |-|-|-|
  |<b>관계 방향</b>|다수의 엔티티 → 하나의 엔티티|하나의 엔티티 → 다수의 엔티티|
  |<b>외래 키 위치</b>|<b>현재 엔티티의 테이블에 생성|<b>상대방 엔티티의 테이블에 생성|
  |<b>주인 여부</b>|관계의 주인<br>(<b>외래 키 포함</b>)|관계의 주인 아님<br>(<b>`mappedBy` 사용</b>)|
  |<b>용도</b>|주로 다대일 관계에서 사용|일대다 관계를 참조할 때 사용|

<br><br>

- <b>단방향과 양방향</b>
  - 객체지향과 관계형 데이터베이스의 참조 차이
    - 데이터베이스 : PK와 FK를 통한 단방향 참조
    - 객체지향 : 객체 간 양방향 참조 가능 (예: Player와 Item)
  - JPA에서의 참조 방식
    - 단방향(unidirectional) 참조:
      - 장점 : 구현이 단순하고 에러 발생 가능성 낮음
      - 단점 : 다른 엔티티 객체 내용 사용 시 제약 (예: 조인 처리)
    - 양방향(bidirectional) 참조:
      - 장점 : JPA에서 데이터 탐색 작업이 편리함
      - 단점 : 양쪽 객체에 동일한 관리 적용 필요

<br><br>

<b>Swagger UI 준비</b>

```gradle
dependencies {
    implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.6.0'
}
```

<br>

```java
package org.zerock.b01.config;

import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;
import org.springdoc.core.models.GroupedOpenApi;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class OpenApiConfig {

  @Bean
  // GroupedOpenApi       : API를 그룹화하여 관리할 수 있게 해줌
  public GroupedOpenApi publicApi() {
    return GroupedOpenApi.builder()
        // group          : API 그룹의 이름 정의
        .group("public-api")
        // packagesToScan : 특정 패키지 내의 컨트롤러 클래스만 스캔
        .packagesToScan("org.zerock.b01.controller")
        .build();
  }

  @Bean
  // OpenAPI        : OpenAPI 명세 설정
  public OpenAPI openAPI() {
    return new OpenAPI()
        // Info     : OpenAPI 문서의 기본 정로를 담는 객체
        // title    : 문서의 제목
        // version  : 현재 API의 버전
        .info(new Info().title("Boot 01 Project OpenAPI")
            .version("v1.0.0"));
  }
}
```

<br>

- URL
  - http://localhost:8080/swagger-ui/index.html
