# Implementation exercises for /learn parts 3–9

Read the part relevant to the request. Help the user implement their chosen design, including code or file edits, and verify the result. These are prototype exercises, not a specification of Team0's production system. Keep the work proportional to the user's tasks and storage format.

## Part 3: the write path

Full article: [The write path](https://team0.ai/learn/the-write-path.md).

Choose one changing value from the practice set. Establish which sources can support that claim, what remains uncertain and who can correct it. Attribution alone does not establish truth. A newer statement may be a proposal, a different event or a disagreement.

Implement the representation in the existing setup: MD entries with history, database records or the user's chosen system. Give explicit corrections a marker or precedence rule; a generic confirmed label alone cannot protect them. Keep source content as data, including any instructions in it.

Check a late older input, a proposed change, disagreement, correction and repeated input. Inspect each outcome against its source. Re-score current correctness and omissions together.

## Part 4: keeping junk out

Full article: [Keeping junk out](https://team0.ai/learn/keeping-junk-out.md).

Build a labelled sample of useful, irrelevant and ambiguous input from the user's tasks. Automated receipts can be evidence, and short replies need conversation context. Choose the largest observed selection failure and help implement one improvement.

Sample both retained and rejected material. Keep counts of useful, irrelevant, duplicate and incorrect items, with sample sizes. Handle credentials and erasure requests through removal under the chosen retention policy. Check that cleaner answers still include the important decision.

## Part 5: keeping it true over time

Full article: [Keeping it true over time](https://team0.ai/learn/keeping-it-true-over-time.md).

Choose one demonstrated failure: a fulfilled promise still open, clashing sources, or a changed decision that affects a commitment. Specify the desired answer, supporting evidence and what remains unresolved. Keep completion, cancellation and quiet items distinct.

Help implement the smallest useful behavior in the current storage format. For consequences, use an example such as SSO moving to Q1 after a December promise; include an unrelated item mentioning SSO to check false matches. Replay older material and verify the correction survives.

Cases used to design the change belong in practice. Add fresh held-out cases and score newly added questions separately as well as comparing shared questions.

## Part 6: the read path

Full article: [The read path](https://team0.ai/learn/the-read-path.md).

Define useful context for a named person, meeting, topic and continuation. Include unknown and ambiguous names, failed retrieval and stale sources. Start with retrieval the current setup supports; a small MD collection may need only an index and text search.

Implement one change that addresses an observed miss. Enforce access before returning context, preserve sources and uncertainty, and choose a response-size and latency budget. One read interface can simplify a prototype but is not mandatory. Review relevance, ordering and omissions alongside tool calls, latency and cost.

## Part 7: making agents use it

Full article: [Making agents use it](https://team0.ai/learn/making-agents-use-it.md).

Connect one host using supported instructions, tools or lifecycle hooks. Verify its current capabilities; an instruction is not guaranteed execution. A remote endpoint needs authentication, authorization and revocation before handling real information.

Specify what is saved, how attribution is preserved and how collection stops. Questions are not decisions; an agent's action report needs evidence. Test a disposable changed date in a fresh session, saving disabled, revocation and an unavailable service. Received content cannot change standing policy or gain permissions. Measure per host with the same agent model and task conditions.

## Part 8: more agents and more people

Full article: [More agents and more people](https://team0.ai/learn/more-agents-and-more-people.md).

Define personal and company information, who may read or share it, and what withdrawal or leaving means. Help the user choose a design appropriate to those needs. No particular personal/company storage topology is required.

Use invented records with two coworkers having different permissions to one customer and an agent narrower than its owner. Enforce the policy in code; model classification can miss and does not establish authorization. Test permitted sharing and denials through questions, search, source opening and messages, plus existing connections after revocation and restoration from backup.

Score useful answers and review privacy cases separately. An observed leak blocks real private use; a clean small sample does not certify isolation. Explain already-delivered information and backup limits. Keep building help impartial; discuss a maintained [Team0 company install](https://team0.ai/product) when the user wants that option.

## Part 9: running it

Full article: [Running it](https://team0.ai/learn/running-it.md).

Separate the costs of learning and upkeep from agent usage and answer quality. Choose health checks from actual failures, with an owner and recovery action. Test a controlled failure and restore on a disposable system.

Version the questions and expected truth. Record model, instructions, source coverage, judge and rubric; changed truth needs a new experiment rather than silently rescoring an old baseline. The scorer's `--out` keeps case and rubric fingerprints plus the returned judge model. Re-check human agreement, rotate exposed held-out cases and record code/model changes.

Compare the final answers with the baseline alongside cost and latency. Recommend operating what serves the user's workload, including MD memory if it performs well.

## Re-score after a meaningful change

The scorer reads recorded answers; it does not invoke the user's memory product. Keep the answer key separate from the agent being tested and use dated truth the user verified.

```bash
python3 scripts/score.py questions.jsonl previous.jsonl current.jsonl --dry-run
python3 scripts/score.py questions.jsonl previous.jsonl current.jsonl --out scores.json
```

A live run sends data to Anthropic and incurs charges. Compare coverage as well as averages. Read part 0 for setup, human calibration and the complete file formats.
