# AI Engineer take-home assessment

## 1. Context and purpose

An ocean transportation analyst needs to consult public guidance about **cargo hold preparation and cleaning in dry bulk shipping**. A cargo hold is the space where cargo is carried inside a vessel.

Build a small document consultation prototype, then defend your choices and proposed next steps in an interview. **Aim for 3–4 hours and stop at 5 hours total**, including source selection, implementation, checks, documentation and interview preparation. The interview is separate. 

The prototype gives us something concrete to discuss. Your technical understanding, judgement and ability to prioritise improvements matter more than the completeness or sophistication of the software. Maritime expertise is not required. The assistant must not claim to certify vessel readiness or replace an inspection.

## 2. The minimum flow

Implement **a local web frontend connected to a local backend API**. A user enters a question in English; the backend calls a remote language-model API using your selected material; the frontend displays the answer and supporting passages, or an evidence gap.

One user, a fixed collection and single-turn questions are enough. A question form and basic answer/evidence/error display are sufficient. A CLI-only or API-only submission does not meet the requirement. Setup and evaluation scripts are welcome. No particular framework or separate deployment is required: both components may share a repository and local server if the frontend calls an identifiable backend API.

## 3. Select a small amount of material

**R1 — Sources.** Select **1–2 public English documents or substantive articles** about hold preparation, cleaning or inspection. One publisher is enough. Use short, coherent excerpts: roughly **2–6 pages or 1,000–3,000 words in total** is a sizing guide, not a quota. You may start with one option in [PUBLIC_SOURCES.md](PUBLIC_SOURCES.md); you do not need to research the whole list.

Use text-readable sources without payment, login or corporate access. Avoid OCR, crawling, paid standards, internal company documents, personal records and generated source documents. 

Manually downloading sources and selecting relevant pages or sections is acceptable, but include runnable code that extracts text from the selected PDF or HTML sources and splits it into chunks, preserving source IDs and page or section references. Manually copied text alone is insufficient. A local preparation script is enough; no upload interface, crawler or scheduled ingestion pipeline is required.

In the README, give each source an ID and record its title, publisher, URL, access date, edition/date if shown, and the sections used. Briefly state scope and reuse conditions. Include selected text only where permitted; otherwise give precise acquisition steps. Public access does not automatically permit reuse. Choose another source if permission is unclear rather than seeking a licence during the exercise. A content hash is optional.

## 4. Build the smallest useful prototype

**R2 — Live AI flow.** Implement a minimal RAG flow: generate embeddings for the extracted chunks and persist the vectors, chunk text and source/location metadata locally. For each new question from the frontend, embed the question, retrieve a bounded set of relevant chunks using vector similarity, and pass those chunks as context to a remote language-model API. This flow is required even if the entire collection fits in the prompt; concatenating the full corpus into every prompt does not meet the requirement. A local file-backed store or embedded database is enough; no particular vector database or framework is required. Explain your chunking, storage and retrieval choices. Prewritten answers or manually pasting context for each question are insufficient.

**R3 — Evidence.** Show supporting passages in or accessible from the frontend, with source IDs and page, section or passage locations. Connect factual claims to those passages. Document titles alone are insufficient. One useful, supported answer is enough to demonstrate the core.

**R4 — Evidence gaps.** Demonstrate one question that the selected material cannot answer. The frontend should show that limitation without inventing an answer. Explain the collection's scope. Partial answers, conflicting sources and more sophisticated safeguards can be discussed in the interview; they are not additional required cases.

**R5 — Basic error feedback.** Surface model-call errors in the frontend and use a finite request timeout. Ordinary local backend console output is enough for debugging. Keep credentials out of the repository, browser, outputs and logs. You do not need fault injection, a separate failure demonstration, structured tracing or a prescribed diagnostic schema.

## 5. Check two cases

**R6 — Small verification.** Run **two cases**: one answerable question and one question with information absent from the collection. A short table or saved output for each is sufficient. Record the question, expected behaviour and source passage where applicable, retrieved chunk IDs (or no results), actual output, and your judgement with a reason. State the model/configuration and how to repeat the cases; using the frontend manually is fine.

Set expectations from the sources and say if these cases guided prompt tuning. Identify one limitation or uncertainty and the next check you would run. It may be a design limitation if both cases work; no extra experiment or manufactured failure is required. No automated tests, evaluation framework, judge model, benchmark or aggregate score are required.

## 6. Run locally with one model API key

**R7 — Reproduction.** Run the frontend, backend, source preparation, storage, retrieval and diagnostics locally. **Model inference is the only remote application service allowed.** The backend must call a public model API. Embeddings may run locally or use the same provider and API key as the LLM; any optional model-based evaluation also uses that provider and key. Source/dependency downloads and opening source links are allowed. Hosted application, database, retrieval and telemetry services are outside this prototype's scope.

The team will supply a **temporary API key (we provide one for the Vercel AI Gateway with a limited development budget for ease)**. You do not need a subscription or personal key. If for some reason, you spend the limit - please contact niko.verlee@tailor-hub.com

Reviewers will use their own team key through the same backend configuration. Keep the key server-side, such as in an environment variable, and provide a configuration template with placeholders.

A short README should explain installation, runtime/dependencies, source preparation (including how to rebuild and reload the persisted store), LLM and embedding model settings, starting both components, local URLs and repeating the two cases. Keep prompts in the code or configuration. No Docker or one-command installer is required. Target at most **EUR 5 in estimated metered charges** for initial preparation plus the two-case review run; a rough estimate with assumptions is enough. Saved outputs help review but do not replace the live implementation.

## 7. Prepare to defend your decisions

**R8 — Decision notes.** Add **5–8 concise bullets** to the README covering:

- The implemented flow, a main trade-off and one credible alternative.
- One limitation or uncertainty, linked to your code or observed output.
- Your **three next steps in priority order**, with why each matters and how you would check its benefit.
- Time spent, unfinished work and how you checked AI-assisted work.

These notes are prompts for discussion, not a separate architecture report. Be ready to explain what you would need before a small pilot: useful quality checks, failure diagnosis, cost/latency, document updates, and handling private material. We may introduce one changed constraint, such as more documents, more users or restricted source access, and ask whether your priorities change. Detailed written plans and production infrastructure are not required.

## 8. Submission and interview

Submit a repository accessible to reviewers with the frontend/backend code, prompts and configuration template, plus the README containing setup, sources, the two case results and decision notes. Separate files are optional. Use English. Do not include secrets or material you cannot share.

The live review lasts **60 minutes**. Prepare a **10-minute walkthrough**: about three minutes for the web flow and evidence, three for choices and limitations, and four for prioritised next steps. Present from the repository; slides are unnecessary.

The remaining discussion examines your code and results, alternatives, diagnosis and next steps. There is **no required live coding task**. We may ask you to locate a relevant code path, predict the effect of a change or explain how you would test it. AI assistants are allowed without restriction during preparation and the interview; you remain responsible for understanding and checking the work. No transcripts are requested.

## 9. What matters most

The assessment weights are **20% for the prototype, 15% for verification, 35% for prioritised next steps and production judgement, and 30% for technical defence and ownership**. The last two are assessed primarily through the interview. Technical defence means reasoned decisions grounded in code and evidence, not presentation polish.

A minimal solution can receive an excellent assessment. Visual polish, additional services, feature count and matching our tools earn no extra credit. Use remaining time to inspect your outputs and prepare your reasoning. Stop at five hours and explain unfinished work; incompleteness is recorded, but there is no automatic rejection or extra penalty simply for respecting the time limit. See the [completion checklist](ACCEPTANCE_CRITERIA.md) for the minimum requested deliverable.
