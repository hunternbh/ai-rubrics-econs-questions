# Data dictionary

## Main rubric-detail comparison

- `dataset`, `year`, `exam`, `question_id`, `subject`: examination identifiers.
- `question_origin`: released examination or explicitly researcher-constructed task.
- `primary_eligible`, `eligible_criterion_groups`: eligibility for the reported primary score. Excluded source-ambiguous criteria remain available.
- `question.wording`: source question text for licensed MIT materials. AP source text is accessed through the source links.
- `question.criteria`: source-based research criteria for MIT; criterion IDs, point maxima and task categories for AP.
- `model_answers`: records grouped by answering model.
- `rubrics_shown`: exact researcher-prepared MIT rough and detailed rubrics; `none` is null. AP task-specific source text is accessed through the source links.
- `responses.condition`: `none`, `rough`, or `detailed`.
- `response_id`: stable answer identifier used to join scores, grades and costs.
- `full_answer`, `evaluated_answer`: complete received answer and the version evaluated under the finite written allowance. Diagram definitions remain embedded as structured arrays. Some source records provide the same answer in both fields.
- `settings`: saved model identifier, requested temperature, optional reasoning/thinking setting, output-token ceiling and common-instruction template ID. Null means that a value is absent from the particular saved request; it is not an invented default.
- `processing`: written/raw word counts, finite-prose truncation and diagram-format metadata.
- `criterion_grades`: the grader's criterion flags, point awards, evidence and explanations.
- `scores`: saved aggregate outcomes. MIT `primary_*` fields use eligible criteria; `all_items_*` fields include the source-ambiguous groups. AP `original_score` uses official raw-point weights, expressed as a percentage.
- `partial_output_retained`: a received incomplete answer is included as flagged; missing diagrams are not reconstructed.

## Flat scores and criterion grades

Percentages and point awards retain the saved numeric values. `task_correct` records full task satisfaction; `reasoning_correct_derived` combines concept demonstration, consistency and absence of explicit error. `word_share` is evaluator-estimated written attention. Evidence and explanations are preserved as saved text. The AP scoring-incentive tables originated as CSV fields and retain those field strings in JSON; blank strings remain blank.

## AP assessment conditions

Conditions A–F distinguish no guidance, generic guidance, criteria without points, original point weights, reallocated points and an omitted criterion. `specification` distinguishes the requested response format or other experimental condition. `word_limit` records the evaluated written allowance. Question IDs marked `researcher_constructed` identify the additional questions. Recognition fields are model self-reports, not verified training-data exposure.

## Analysis and usage

Generation costs retain both accepted-response and received-attempt totals. The distinction matters when a technical retry was received. Cached quantities, output tokens, optional reasoning-token counters and historical prices are billing fields, not measurements of internal reasoning. Family comparisons use paired question blocks and separate outcome-specific Holm families. Influence checks retain every omission, and headroom checks preserve their stated equivalence margins. No response is selected for publication based on whether its results favor the paper's hypothesis.
