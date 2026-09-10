# luna-plugin

LUNA Lab 팀 표준 도구를 배포하는 플러그인 마켓플레이스.

- 매장(marketplace): `luna` — `.claude-plugin/marketplace.json`
- 상품(plugin): `luna-toolkit` v0.2.1 — `luna-toolkit/.claude-plugin/plugin.json`

## 설치 안내

Claude Code 프롬프트에 두 줄 입력한다.

```
/plugin marketplace add Tlarkdus/luna-plugin
/plugin install luna-toolkit@luna
```

첫 줄이 매장을 등록하고, 둘째 줄이 그 매장의 상품을 설치한다.
설치 후 `/help`에 도구가 뜨는지 확인한다. 훅은 새 세션부터 반영된다.

로컬 사본으로 붙이려면 첫 줄의 인자를 절대 경로로 바꾼다 (`/plugin marketplace add C:/Users/sgy46/luna-plugin`).

## 담긴 도구

| 종류 | 이름 | 내용 |
|---|---|---|
| 커맨드 | `/repo-grade` | 저장소를 AI-Ready 관점에서 100점 채점 |
| 스킬 | `repo-grade` | 채점 루브릭 5카테고리 × 20점 |
| 스킬 | `wiki-ingest` | raw 문서를 `_brain` 위키 노드로 정리 |
| 스킬 | `wiki-query` | `_brain`에서 출처와 함께 답 찾기 |
| 스킬 | `wiki-lint` | 깨진 링크·고아 노드·방치된 draft 검진 |
| 스킬 | `lab-onboard` | `.claude/ci/sources.yaml` 기준 지식 지도 생성 |
| 훅 | `PreToolUse` | Edit/Write는 TDD 가드, Bash는 위험 명령 차단(exit 2) |
| 훅 | `PostToolUse` | Bash 명령을 `.claude/audit.log`에 append |
| 스크립트 | `tdd-guard.sh` | 훅이 부른다 |

훅은 새 세션부터 반영된다.
`wiki-*`와 `lab-onboard`는 대상 저장소에 `_brain/`·`.claude/ci/sources.yaml`이 있어야 의미가 있다.

## 갱신

팀 규칙 — **매주 수요일 수업 시작 = update 타임.**

```
/plugin marketplace update luna
```

## changelog

- **v0.2.1** — `plugin.json`에 `hooks` 선언 추가 (파일만 있으면 훅이 로드되지 않았다)
- **v0.2.0** — wiki 3종·lab-onboard 스킬 이식, audit log 훅(PostToolUse) 추가
- **v0.1.2** — 커맨드가 `${CLAUDE_PLUGIN_ROOT}`로 루브릭을 짚도록 수정
- **v0.1.1** — repo-grade 출력 표에 총평 행 규칙 추가
- **v0.1.0** — marketplace 뼈대, repo-grade 커맨드+스킬, 가드 훅 2종

---

경로는 항상 `${CLAUDE_PLUGIN_ROOT}` 기준으로 쓴다. 설치 위치가 저장소마다 달라 상대·절대경로는 깨진다.
