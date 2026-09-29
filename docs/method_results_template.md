# Method–Results Template (v0.1.0)

> **Phase 2 Step 2b (권장).** `analysis_plan.md` 승인 **후**, 분석 실행 **전**에 이 파일을 복사해 Methods와 Results의 골격을 먼저 고정한다.
> 복사 위치: `drafts/method_results_template.md` (multi-paper: `drafts/paper{N}_xxx/method_results_template.md`).
>
> **목적:** 결과를 보기 전에 "무엇을, 어떻게, 어디에 보고할지"를 확정한다 — 결과를 본 뒤 분석을 바꾸는 일(outcome switching)을 막고, `results/*.csv` 출력 schema를 미리 정해 Phase 4 수치 게이트(`check_numbers.py`)와 곧바로 연결한다.

## 사용 규칙

- **계획 산출물이지 원고 섹션이 아니다.** 파일명에 섹션 번호(`0N_`)를 붙이지 않는다 — `04_methods.md`/`05_results.md`는 Rule 8 훅이 승인된 `draft_plan.md` 없이 차단한다. 이 템플릿은 차단 대상이 아니다.
- **수치 금지.** Results 골격은 빈칸(`[N]`, `[estimate]`, `95% CI [___, ___]`, `p = [___]`)으로만 둔다. 실제 수치는 Phase 4에서 `results/*.csv` 값으로만 채운다 (Rule 9 수치 grounding).
- **미확정은 미확정으로.** 알 수 없는 파라미터는 `[TO CONFIRM: ...]`로 남기고 관례값으로 메우지 않는다. 각 결정에 상태를 단다: `CONFIRMED` / `PROVISIONAL` / `UNRESOLVED` / `NOT AVAILABLE`.
- **analysis_plan.md에 합치지 않는다.** 승인된 plan은 승인 해시에 묶여 있어 템플릿을 고칠 때마다 승인이 stale이 된다. 분석 위계·검정법이 바뀌면 analysis_plan을 먼저 개정·재승인하고 템플릿을 따라 고친다.
- **인용은 `[EVID:id]`만.** `knowledge/evidence.md`에 없는 근거는 G의 "필요 근거"로 적고 Phase 1로 돌아간다.
- **최소주의.** 연구 질문에 답하는 데 필요한 분석·Table·Figure만 둔다. 제거해도 논증이 약해지지 않는 분석은 뺀다.

---

## A. Analytic Architecture

| ID | Level | Scientific question | analysis_plan 근거 절 |
|----|-------|---------------------|-----------------------|
| P1 | Primary | [TO CONFIRM: ...] | |
| S1 | Secondary | | |
| SEN1 | Sensitivity (P1 가정 변경) | | |
| E1 | Exploratory (해당 시에만) | | |

> Sensitivity는 "합리적 가정을 바꿔도 1차 결론이 유지되는가"만 답한다. 새로운 질문은 Sensitivity가 아니다.

## B. Methods Skeleton

> 연구 설계에 맞게 소절을 삭제·추가한다. 확정된 내용은 원고용 문장으로, 미확정은 `[TO CONFIRM: ...]`.

- **Participants** — 선정/제외 기준, 최종 분석 N의 산출 경로
- **Procedure / Data acquisition** — 실제 프로토콜만 (관례로 추정 금지)
- **Data processing / Quality control** — 단계별 `STEP / PARAMETER / RATIONALE / STATUS`
- **Variables / Feature definitions** — outcome·exposure·covariate의 조작적 정의
- **Primary analysis (P1)** — 종속변수, 독립변수, 공변량, 모형, 효과추정치, 95% CI
- **Secondary analysis (S1)**
- **Sensitivity analyses (SEN*)**
- **Statistical analysis** — 다중비교 전략, 유의수준, 결측 처리, 소프트웨어/버전

## C. Matched Results Skeleton

> B와 같은 순서·같은 ID. Methods에 없는 분석이 Results에 처음 등장하지 않는다. "significant"는 실제 결과로 확인되기 전에 쓰지 않는다.

- **Participant characteristics and data availability** — "Of [N] participants screened, [N] were included in the primary analysis (Table 1)."
- **Quality control and retained data** — "[n] of [N] recordings/records were retained after quality control."
- **P1** — "The estimated [effect] was [estimate] (95% CI [___, ___]; *p* = [___])."
- **S1**
- **SEN*** — "Results were [consistent / not consistent] with the primary analysis (Supplementary Table [__])."

## D. Method–Result Crosswalk

| ID | Question | Methods § | Results § | Table/Figure | results CSV |
|----|----------|-----------|-----------|--------------|-------------|
| P1 | | | | | |

## E. Results CSV Schema

> Phase 2 분석 스크립트가 내보낼 `results/*.csv`의 열을 분석 ID별로 미리 정한다. 원고의 모든 보고 수치는 여기 정의된 열에서 나와야 한다.

| CSV file | ID | Required columns |
|----------|----|------------------|
| `results/[file].csv` | P1 | analysis_id, group/contrast, n, estimate, ci_low, ci_high, p, p_adj |

## F. Table / Figure Plan

| Output | ID(s) | 답하는 질문 | Main / Supplement |
|--------|-------|-------------|-------------------|
| Table 1 | — | Participant characteristics | Main |

> 같은 데이터를 Text + Table + Figure 세 곳에 모두 넣지 않는다 (Rule 2).

## G. Reference Justification Map

| Methodological decision | [EVID:id] | Exact support | Applicability / limitation |
|-------------------------|-----------|---------------|----------------------------|
| | | | |

> 일반 방법을 지지하는 문헌이 우리 파라미터 선택까지 지지하는 것은 아니다. 없으면 "필요 근거"로 적는다.

## H. Unresolved Decisions

| Decision | Status | Why it matters | Options | Next step (data / protocol / literature / statistics / supervisor) |
|----------|--------|----------------|---------|-------------------------------------------------------------------|
| | | | | |

## I. Self-Audit (분석 실행 전)

- [ ] 1차 분석이 하나의 명확한 질문으로 정의되었다
- [ ] Methods의 모든 분석이 Results 위치(D)를 가진다, 그 역도 성립한다
- [ ] 모든 보고 수치의 출처 CSV 열(E)이 정의되었다
- [ ] 다중비교의 원천(outcome·그룹·시점·변수 수)을 열거하고, 불필요한 분석을 먼저 줄였다
- [ ] 실제 데이터로 확인되지 않은 파라미터를 관례값으로 채우지 않았다
- [ ] Table/Figure가 각각 하나의 질문에 답한다

발견된 문제는 **CRITICAL**(과학적 타당성·해석에 영향) / **MAJOR**(방법·결론에 실질적 영향) / **MINOR**(보고·명료성)로 분류하고, CRITICAL은 분석 실행 전에 해결한다.

---

**다음 단계:** Phase 2 분석 실행 → E의 schema로 `results/*.csv` 출력 → Phase 3 `draft_plan.md`의 Table/Figure plan(항목 5)과 Methods rationale claim(항목 10)을 F·G에서 가져온다 → Phase 4에서 B·C를 `04_methods.md`/`05_results.md`로 옮겨 CSV 값으로 채운다.
