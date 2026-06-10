# agent-config-starter

> **Production-grade `CLAUDE.md` / `AGENTS.md` / skills starter for backend & infra teams.**
> 바이브코딩 말고 실서비스 — 현업에서 AI 코딩 에이전트를 제대로 굴리기 위한 설정 스타터킷.

대부분의 "에이전트가 멍청해진다"는 모델 문제가 아니라 **컨텍스트 규율(discipline) 문제**입니다.
이 스타터킷은 실서비스에서 코딩 에이전트를 굴릴 때 바로 쓰는, 토큰 예산을 의식한 설정 템플릿 모음입니다.

## 왜 (Why)

- LLM이 자동 생성한 컨텍스트 파일은 작업 성공률을 오히려 깎고 비용을 늘린다는 연구(ETH Zürich, 2026)가 있습니다.
- 항상 로드되는 설정은 "항상 켜진 비용"입니다. 얇고 정확할수록 매 요청이 싸지고 또렷해집니다.
- 핵심은 capability가 아니라 **clean context**.

## 무엇이 들어있나 (What's inside)

| 파일 | 역할 |
|---|---|
| [`AGENTS.md`](./AGENTS.md) | 크로스툴 표준 단일 출처 — 빌드/테스트·코드 스타일·아키텍처 경계 |
| [`CLAUDE.md`](./CLAUDE.md) | 얇은 프로젝트 컨텍스트 (AGENTS.md를 가리킴) |
| [`skills/`](./skills) | on-demand 스킬 예시 (워크플로는 항상 로드하지 말 것) |
| [`.claudeignore`](./.claudeignore) | 컨텍스트 위생 — 노이즈 제외 |
| [`CONTEXT-BUDGET.md`](./CONTEXT-BUDGET.md) | 토큰 예산·죽은 무게 제거·Context Rot 임계 가이드 |

## 원칙 (Production discipline)

1. **CLAUDE.md는 얇게.** 항상 필요한 최소만. 워크플로는 스킬로 내린다.
2. **워크플로 = 스킬(on-demand).** 필요할 때만 로드되게 한다.
3. **AGENTS.md = 단일 출처.** 모순되는 규칙이 에이전트를 갈팡질팡하게 만든다.
4. **설정은 영어로.** 항상 로드되는 파일은 영어가 토큰을 2~3배 아낀다.
5. **예산을 측정하라.** `/context`로 시작 전 점유율을 보고, 안 쓰는 건 지운다.

## 빠른 시작 (Quick start)

```bash
# 1) 템플릿 복사
cp AGENTS.md CLAUDE.md .claudeignore /path/to/your/repo/

# 2) AGENTS.md를 프로젝트에 맞게 채운다 (빌드/테스트/경계)
# 3) Claude Code에서 /context 로 시작 점유율을 확인한다
# 4) 안 쓰는 스킬/섹션을 제거하고 다시 측정한다
```

## 더 보기

실서비스에서 AI 코딩 에이전트 쓰는 법을 기록합니다.

GitHub: [@purewater02](https://github.com/purewater02)
<!-- TODO: 런칭 시 X / YouTube 핸들 추가 -->

## License

MIT — see [LICENSE](./LICENSE).
