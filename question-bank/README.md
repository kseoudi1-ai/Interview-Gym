# Expanded Interview Question Bank — Draft Plan

## Scope
Expand Interview Gym beyond entry-level call-center interviews to cover the wider BPO and customer-operations career path.

Target size for the first complete release: **350 bilingual questions** (English and Arabic).

## Role tracks and target counts

| Track | Target questions |
|---|---:|
| Customer Service Agent | 50 |
| Technical Support | 40 |
| Sales & Retention | 35 |
| Team Leader | 45 |
| Operations Manager | 45 |
| Quality Assurance | 30 |
| Workforce Management | 30 |
| Training & Development | 25 |
| Recruitment & HR | 25 |
| Client Success / Account Management | 25 |
| **Total** | **350** |

## Question metadata

Every question should have:
- `id`: stable unique identifier
- `track`: one of the role tracks above
- `level`: beginner, intermediate, or advanced
- `type`: behavioral, situational, role_knowledge, or analytical
- `language`: English and Arabic text stored together
- `tags`: relevant skills, processes, or KPIs

Example record:

```json
{
  "id": "OPS-ADV-001",
  "track": "operations_manager",
  "level": "advanced",
  "type": "analytical",
  "tags": ["NPS", "AHT", "AICR", "recovery_plan"],
  "en": "Your account is missing its NPS, AICR, and attendance targets. How would you build a 30-day recovery plan?",
  "ar": "حسابك لا يحقق مستهدفات NPS وAICR والحضور. كيف تضع خطة تعافٍ لمدة 30 يومًا؟"
}
```

## Difficulty guidelines

- **Beginner:** fundamentals, clear definitions, basic customer interactions, and personal motivation.
- **Intermediate:** practical scenarios, prioritization, coaching, root-cause analysis, and handling escalations.
- **Advanced:** KPI trade-offs, capacity and staffing decisions, client governance, financial/operational impact, and multi-workstream recovery plans.

## Selection and repetition rules

1. Never repeat a question within one interview.
2. Prefer questions not used in the user's previous five completed interviews.
3. Select only from the chosen role track and compatible level.
4. Balance question types and tags so an interview is not dominated by one topic.
5. If the eligible pool is exhausted, relax the history exclusion gradually rather than returning too few questions.
6. Keep the existing 5/10-question interview options.

## Cost and compatibility constraints

- Questions are static content; do not call Gemini to generate them.
- Keep the existing Gemini evaluation flow and request format unchanged.
- Store question history locally in the browser for the first version; do not add a database dependency.
- Treat local history as a best-effort repetition reducer, not an identity or anti-abuse control.
- Preserve the current production site and Worker. All implementation and testing must happen on this feature branch and a preview deployment first.

## Acceptance checks

- Every record has a unique ID and both language strings.
- No question is duplicated by wording within the same track.
- Every role track has beginner, intermediate, and advanced coverage.
- 5-question and 10-question interviews both work.
- Existing interview evaluation still receives the same payload shape.
- Arabic and English selection show the matching question text.
- History exclusion is best-effort and safely falls back when the pool is small.
