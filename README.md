# McCodexalds

이 저장소는 요즘IT 글 [클로드 코드로 프로덕트 팀 바이브코딩 표준화한 방법(aka 맥도날드 시스템)](https://yozm.wishket.com/magazine/detail/3457/)에서 설명한 문제의식을, Codex에서 재사용 가능한 `AGENTS.md`와 `skills/` 구조로 옮겨 놓은 예시 저장소다.

핵심 아이디어는 단순하다. AI에게 많은 컨텍스트를 한 번에 밀어 넣는 대신, 항상 읽는 짧은 운영 가이드와 필요할 때만 읽는 작은 스킬 문서로 분리해서 컨텍스트를 통제한다.

## 이 저장소가 해결하려는 문제

위 글에서 반복해서 지적하는 문제는 대체로 아래에 모인다.

- 프로젝트가 커질수록 컨텍스트 과부하가 생기고, AI가 환각하거나 엉뚱한 구현을 만든다.
- 채팅창에서만 설명된 의도는 휘발되어, 시간이 지나면 "왜 이렇게 만들었는지"를 추적하기 어렵다.
- 기존 구현이나 API를 재사용할 수 있는데도, AI가 비슷한 경로를 새로 만들어 중복 로직이 생긴다.
- 규칙을 계속 덧붙이다 보면 단일 룰 파일이 비대해져, 일을 시작하기도 전에 컨텍스트를 과하게 소모한다.
- 비개발자나 새 참여자는 현재 상태와 의도를 파악하기 위해 결국 사람에게 다시 물어봐야 한다.

이 저장소는 그 문제를 다음 원칙으로 줄이려 한다.

- 항상 읽는 가이드는 짧고 명확하게 유지한다.
- 반복되는 워크플로우는 개별 스킬 문서로 분리한다.
- 중요한 의도, 결정, 우선순위는 채팅이 아니라 저장소에 남긴다.
- 작업마다 필요한 문서만 읽게 해서 컨텍스트 사용량을 줄인다.

## 시스템 프롬프트와 스킬을 어떻게 나눴나

엄밀히 말하면 이 저장소에는 Codex 제품 내부의 숨겨진 전체 시스템 프롬프트가 들어 있지 않다. 여기서 "시스템 프롬프트 역할"을 하는 것은 프로젝트 루트의 [`AGENTS.md`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\AGENTS.md)다.

역할 분리는 이렇게 된다.

- [`AGENTS.md`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\AGENTS.md): 항상 적용되는 공통 운영 원칙. 예를 들면 가정 명시, 재사용 우선, 단순성, 수술적 변경, 주석 원칙, 범위 통제, 성공 기준 정의 같은 규칙을 둔다.
- [`skills/`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills): 특정 상황에서만 읽는 작은 작업 매뉴얼. 예를 들면 PRD 작성, 구현 전 스펙 정리, 결정 로그 기록, 검증 기준 작성 같은 절차를 분리한다.

이 구조는 글에서 말한 "200줄 내외의 핵심 가이드 + 필요 시 appendix/세부 문서 참조" 전략을 그대로 따른다. 즉, 모든 절차를 거대한 한 파일에 넣지 않고, 기본 운영 원칙만 `AGENTS.md`에 두고 세부 실행법은 스킬로 라우팅한다.

## 어떻게 작동하나

실행 흐름은 아래와 같다.

1. 에이전트는 먼저 [`AGENTS.md`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\AGENTS.md)를 읽고 기본 원칙을 잡는다.
2. 작업 성격을 보고 필요한 스킬만 고른다.
3. 선택된 스킬의 `SKILL.md`를 읽어 해당 작업의 입력, 출력, 워크플로우, 가드레일을 따른다.
4. 결과물은 다시 저장소 안의 문서나 코드로 남긴다.
5. 세션이 끝나도 중요한 의도와 절차는 저장소에 남아 다음 작업의 컨텍스트가 된다.

이 방식의 목적은 "많이 아는 AI"를 만드는 것이 아니라 "필요한 순간에 필요한 매뉴얼만 꺼내 쓰는 AI"를 만드는 것이다.

## 포함한 스킬과 각 역할

현재 포함된 스킬은 모두 "큰 룰 파일을 쪼개고, 의도와 절차를 저장소에 남긴다"는 목적에 맞춰 골랐다.

- [`skills/commenting-intent-and-coupling`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\commenting-intent-and-coupling): 코드가 무엇을 하는지가 아니라 왜 존재하는지, 어떤 제약과 결합이 있는지를 주석에 남긴다.
- [`skills/decision-logging`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\decision-logging): 여러 선택지 중 왜 이 길을 택했는지 기록해 의도 상실을 줄인다.
- [`skills/domain-context-template`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\domain-context-template): DB, API, 페이지, 워크플로우 같은 반복 설명을 저장소 문서로 고정해 채팅 의존도를 낮춘다.
- [`skills/minimal-surgical-change`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\minimal-surgical-change): 버그 수정이나 핫픽스에서 AI가 괜히 범위를 넓히지 않도록 제한한다.
- [`skills/pr-guide`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\pr-guide): 작업 완료 후 무엇이 바뀌었고 왜 바뀌었는지, 어떤 리스크와 검증이 있었는지 남긴다.
- [`skills/prd-writing`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\prd-writing): 기능 개발 전에 Goal, Non-goals, Must/Should/Nice, 리스크와 검증을 정리해 막연한 요청을 줄인다.
- [`skills/repo-context-hygiene`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\repo-context-hygiene): 반복 설명을 채팅에 남기지 않고 저장소의 적절한 위치로 승격시킨다.
- [`skills/spec-before-implementation`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\spec-before-implementation): 바로 코딩하지 않고 짧은 실행 스펙으로 범위와 수용 기준을 먼저 고정한다.
- [`skills/verification-and-success-criteria`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\skills\verification-and-success-criteria): "될 것 같다" 대신 관찰 가능한 성공 기준과 검증 방법을 요구한다.

## 이 저장소에서의 라우팅 방식

[`AGENTS.md`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\AGENTS.md)의 `Skill Routing` 섹션은 어떤 상황에서 어떤 스킬을 읽을지 정한다.

예를 들면:

- 중간 이상 규모 작업이거나 요구가 모호하면 `prd-writing` 다음 `spec-before-implementation`
- 트레이드오프가 중요하면 `decision-logging`
- 프로젝트 지식이 반복되면 `repo-context-hygiene`, 필요하면 `domain-context-template`
- 버그픽스나 좁은 패치는 `minimal-surgical-change`와 `verification-and-success-criteria`
- 마무리 문서는 `pr-guide`

즉, `AGENTS.md`는 "언제 무엇을 불러올지"를 정하는 라우터이고, 각 스킬은 "그 상황에서 정확히 어떻게 일할지"를 정하는 작업 매뉴얼이다.

## 기사 내용과 이 저장소의 대응 관계

글의 문제의식과 이 저장소의 대응은 아래처럼 볼 수 있다.

- 거대한 단일 룰 파일 문제 -> 짧은 [`AGENTS.md`](C:\Users\B360M-PC\Documents\guthab\mccodexalds\AGENTS.md) + 분리된 `skills/`
- 의도 휘발 문제 -> PRD, decision log, PR guide, domain guide 같은 저장소 문서화 흐름
- 중복 구현 문제 -> `Reuse Before Creating`, `spec-before-implementation`
- 범위 폭주 문제 -> `Simplicity First`, `Scope Discipline`, `minimal-surgical-change`
- 검증 없는 낙관 문제 -> `Goal-Driven Execution`, `verification-and-success-criteria`

## 저장소 구조

```text
mccodexalds/
├─ AGENTS.md
├─ README.md
└─ skills/
   ├─ commenting-intent-and-coupling/
   ├─ decision-logging/
   ├─ domain-context-template/
   ├─ minimal-surgical-change/
   ├─ pr-guide/
   ├─ prd-writing/
   ├─ repo-context-hygiene/
   ├─ spec-before-implementation/
   └─ verification-and-success-criteria/
```

## 한 줄 요약

이 저장소는 "AI에게 모든 걸 한 번에 알려주는 방식" 대신, "짧은 상시 가이드와 상황별 스킬 문서를 조합해 팀의 의도와 워크플로우를 표준화하는 방식"을 실험하기 위한 베이스다.
