# Part 0: build a test set and score any memory

Full article: [Measure before you build](https://team0.ai/learn/measure-before-you-build.md).

Use this for the measurement exercise in /learn, including MD-based setups and comparisons with built-in memory, databases or graphs. The script evaluates saved answers and has no storage-format preference.

## Establish expected truth

Find about 20 questions from real tasks: changed values, identity across sources, decisions another agent missed, promises and unsupported claims. The user verifies what is true on the stated date and which obsolete values must not be used. Keep unresolved truth in a separate review list, outside scored cases.

Write one object per line in `questions.jsonl`:

```json
{"id":"q01","split":"practice","asked_on":"2026-11-02","question":"When does the pilot start?","true_now":["The pilot starts November 15"],"stale":["The pilot starts November 1"]}
```

Reserve about a third as `held_out`. Keep the answer key away from the agent and memory being tested. If you helped prepare it, collect answers through a separate agent context with no access to that key. Do not claim that you forgot information in the same session.

## Collect comparable answers

Use the real agent with its memory enabled as configured. Start a fresh session per question, without giving it the expected answer. Save one object per answer:

```json
{"id":"q01","tool_calls":3,"answer":"The pilot starts November 15."}
```

For before/after or cross-system comparisons, keep model, instructions, source snapshot, task permissions and tool budget comparable. Record configurations and deliberate differences. MD memory must receive the same opportunity to answer; do not score database structure or graph features as quality by themselves.

## Run the scorer

`scripts/examples/` contains synthetic questions, before/after answers and human labels. No provider call is needed to validate them:

```bash
python3 scripts/score.py scripts/examples/questions.jsonl scripts/examples/before.jsonl --dry-run
```

Install `anthropic>=2.3,<3` and `pydantic>=2,<3` for a live run and set `ANTHROPIC_API_KEY` in the user's own environment. The call sends the question, expected truth and answer to Anthropic and costs money; use appropriate redaction or permission.

```bash
python3 scripts/score.py questions.jsonl before.jsonl after.jsonl --out scores.json
python3 scripts/score.py questions.jsonl before.jsonl --labels my_labels.jsonl --out calibrated.json
```

The comparison uses only questions both runs answered. Missing answers are reported before paid calls. Check the coverage as well as the average. With two runs, human labels check the first run.

## Interpret carefully

Higher is better for all five measures, including `missed` (1 means nothing important missing). Review correctness and omissions together, relevance and ordering, and whether enough context remains to act. Compare cost, latency and tool calls separately.

Have the user label a sample; a mean gap above 0.2 is flagged for review. A model judge is fallible, and a small held-out set is diagnostic. Version the expected truth and record the model and rubric. After tuning on a held-out failure, move it to practice and add an unseen case. Check access and privacy separately from answer quality.
