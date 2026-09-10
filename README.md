# luna-plugin

LUNA Lab 팀 표준 도구를 배포하는 플러그인 마켓플레이스.

- 매장(marketplace): `luna` — `.claude-plugin/marketplace.json`
- 상품(plugin): `luna-toolkit` v0.1.0 — `luna-toolkit/.claude-plugin/plugin.json`

## 설치 안내

Claude Code 프롬프트에 두 줄 입력한다.

```
/plugin marketplace add C:/Users/sgy46/luna-plugin
/plugin install luna-toolkit@luna
```

첫 줄이 매장을 등록하고, 둘째 줄이 그 매장의 상품을 설치한다.
설치 후 `/help`에 도구가 뜨는지 확인한다. 훅은 새 세션부터 반영된다.

## 담긴 도구

| 종류 | 이름 | 상태 |
|---|---|---|
| 커맨드 | — | 준비 중 |
| 스킬 | — | 준비 중 |
| 훅 | — | 준비 중 |
| 스크립트 | — | 준비 중 |

경로는 항상 `${CLAUDE_PLUGIN_ROOT}` 기준으로 쓴다. 설치 위치가 저장소마다 달라 상대·절대경로는 깨진다.
