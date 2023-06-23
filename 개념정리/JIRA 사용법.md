JIRA 사용법
===========

# 진행 순서

- 진행할 수 있는 카드가 있는지 확인한다.
    - 작업해도 되는 카드 : BackLog, Ready To Develop, ReOpened
    - Ready To Develop 카드가 있다면 먼저 진행한다. Ready To Develop 상태의 코드를 모두 완료했을 경우 BackLog에 있는 카드를 진행해도 좋다.
- 진행 가능한 카드 중 진행하고자 하는 카드(ex. HGP-0)의 상태를 In Progress로 변경한다.
- 해당 카드(HGP-0)를 진행중인 Repository에서 카드 번호(HGP-0)를 이름으로 브랜치를 생성한다.
- HGP-0 브랜치에서 카드 내용에 해당하는 작업을 수행한다.
- 작업이 완료되면 카드를 In Review 상태로 변경하고 Pull Request(PR)을 만든다.
    - 기본으로 main <- HGP-0 으로 합쳐지도록 설정되어있다.
    - 필요시 합치고자하는 목적지/출발지 브랜치를 변경한다.
- PR의 제목과 내용은 아래와 같은 형식으로 작성한다.

```
// HGP-20 카드 예시
HGP-20: [Feat] Branch를 만들어본다.

- [HGP-20](https://jytutoring.atlassian.net/browse/HGP-20)
```

- PR 오른쪽의 Reviewer를 지정하여 리뷰를 요청한다.
    - 리뷰어가 수정이 필요하거나 질문이 있을 경우 코멘트를 남깁니다.
    - 수정이 필요하다는 내용이 적혀있다면 해당 브랜치에 수정사항을 담아 commit을 한 후, 수정 완료가 되었다는 코멘트를 남깁니다.
    - 질문이 있을 경우, 질문에 대한 답변을 작성해주세요.
    - (질문자가 문제가 해결됬을 경우 Resolve Conversation을 눌러 해결되었음을 표시합니다.)
- 수정사항이 더이상 없을 경우 리뷰어가 Approve(승인) 처리를 합니다.
    - Reviewer 옆에 초록색 체크 표시가 보입니다.
- Reviewer가 브랜치를 merge 한 후 삭제합니다.
- Reviewer가 카드의 상태를 Done으로 변경합니다.
