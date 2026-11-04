# Completion checklist

Use this with [the task](INSTRUCTIONS.md) for a **3–4-hour prototype, capped at 5 hours**. It records the requested minimum, separately from the hiring judgement. The interview's technical defence and prioritised next steps carry **65%** of the assessment; a polished application is not the goal.

| ID | Requirement | Observable completion evidence |
|---|---|---|
| AC1 | R1 — Sources | The README identifies 1–2 relevant public English documents, their URLs, publisher, access date, edition/date if shown, selected sections and reuse basis. One publisher is enough. Permitted excerpts or clear acquisition steps make the material inspectable. |
| AC2 | R2 — Live AI flow | A local web frontend calls a local backend API; the backend uses the selected material with a remote model API and returns an answer. The application accepts new questions. At least one answerable case produces a useful, supported answer. A CLI-only, API-only or canned demo is insufficient. |
| AC3 | R3 — Evidence | Claims in that answer connect to passages readable or accessible from the frontend, with source IDs and usable locations. The reviewer can check the original text. |
| AC4 | R4 — Evidence gaps | The absent-information case reports the gap in the frontend without fabricating an answer. The collection's scope is stated; no vessel-readiness certification is claimed. A separate partial-answer case is unnecessary. |
| AC5 | R5 — Error feedback | The model-call path has basic error handling, a frontend error message and a finite timeout. This can be inspected in code; a separate fault simulation, report or structured log is unnecessary. No credentials appear in the repository, browser, outputs or logs. |
| AC6 | R6 — Verification | Two executed cases cover one answerable and one absent-information question. Each records expectation, actual output and a reasoned judgement, with a source passage where relevant. Model/configuration and repeat steps are identified. One limitation or uncertainty and a proposed next check are stated. |
| AC7 | R7 — Reproduction | Brief instructions, dependencies and configuration placeholders let a reviewer start both components with a team-owned key held only in the backend. Preparation, storage, retrieval and diagnostics are local. The only remote application service is model inference; any remote embeddings or model-based evaluation share the LLM provider/key. The provider/models and rough EUR 5 review-cost estimate are explicit. |
| AC8 | R8 — Decision notes | The README contains 5–8 concise bullets on the flow, a trade-off/alternative, a concrete limitation, three prioritised next steps and how to check them, time spent, unfinished work and verification of AI-assisted work. A separate design report or slides are unnecessary. |

The page/word guide is a sizing aid, not a quota or hidden rejection rule. One or two documents and two cases are enough. Reuse the same outputs and notes across this checklist; duplicate reports are unnecessary.

There is no minimum accuracy percentage, performance target, automated-test coverage or hidden maritime quiz. Automated ingestion, a vector database, a failure-test harness, detailed telemetry and production infrastructure are not required.

Stop at five hours and mark unfinished items honestly. A missing requirement stays visible; it does not trigger an automatic rejection or a second penalty beyond its relevant scoring dimension. In the interview, explain the consequence, likely cause and next check. Excellent reasoning must be supported by evidence; fluency alone does not establish technical understanding.

Prepare a 10-minute repository walkthrough within the 60-minute interview. Expect questions about your code, results, choices and next steps, with no required live coding task.
