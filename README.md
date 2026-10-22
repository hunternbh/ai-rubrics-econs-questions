# AI Rubrics and Economics Examination Questions

Data for *Do Assessment Rubrics Improve Large Language Model Performance?* by Hunter Ng and Shou-Ming Chang.

The dataset compares generated economics explanations under no, rough, and detailed assessment rubrics. It contains the saved answers, evaluated answers, criterion-level grades and explanations, question-level scores, model settings, and token costs used in the manuscript.

## Contents

| Setting | Questions | Models | Answers |
| --- | ---: | ---: | ---: |
| MIT microeconomics, 2010, 2018 and 2023 | 31 collected; 30 primary | 10 | 930 |
| AP Microeconomics and Macroeconomics long questions, 2021–2026 | 22 | 7 | 462 |

`index.json` links each question file. `data/mit/questions/` and `data/ap/questions/` contain one file per question, with models and conditions nested inside it. Flat question scores and criterion grades are also provided. `data/analysis/` contains comparisons, regressions, token costs, influence checks and other sample checks. `settings/`, `prompts/` and `sources/` document the model configuration, common instructions and source materials.

`data/ap/assessment_conditions/` contains the separate scoring-criteria disclosure, point-reallocation and criterion-omission comparisons in the online appendix: 66 released AP questions and 12 explicitly identified researcher-constructed questions, with 3,150 scored configurations. These conditions differ from the main rubric-detail comparison. Constructed questions are not official examination releases. A shared `response_id` identifies the same answer where a configuration uses an identical completion.

## Measures

Economic correctness is the percentage of eligible criteria fully satisfied. Written economic reasoning requires demonstration of the relevant concept, economic consistency and absence of an explicit economic error. Coverage records an attempt to address a criterion. Primary scores weight criteria equally within a question and questions equally within a setting. MIT source-ambiguity flags identify the excluded criteria and the block with no primary-eligible criteria. All collected MIT answers remain available. AP incomplete-output flags identify four partial answers retained in the main comparison.

Grades are automated model assessments, not student outcomes or human expert ratings. Written-attention measures are evaluator estimates of the observable answer, not internal model reasoning. Costs use the study's recorded token quantities and standard uncached rates; they exclude unmeasured rubric-preparation and human-review time.

## Source materials

MIT question text and source-derived criteria are attributed to MIT OpenCourseWare and the credited course contributors under [CC BY-NC-SA](https://ocw.mit.edu/pages/privacy-and-terms-of-use/). The 2010 examinations are hosted in the Fall 2011 course release. Original and archived retrieval links are distinguished in `sources/examination_sources.json`. Transcribed text and researcher-prepared criteria are identified as adaptations; source notes preserve material ambiguities.

College Board question wording, original question images, official scoring guides and task-specific rubric text are linked rather than redistributed. AP JSON files retain identifiers, source links, assessment-point metadata, generated answers and grading results. This repository is not endorsed by MIT or College Board.

## Load the data

```python
import json
from pathlib import Path

root = Path('.')
index = json.loads((root / 'index.json').read_text(encoding='utf-8'))
question = json.loads((root / index['rubric_detail_questions'][0]['file']).read_text(encoding='utf-8'))
scores = json.loads((root / 'data/mit/question_scores.json').read_text(encoding='utf-8'))
```

See `DATA_DICTIONARY.md` for field definitions and `LICENSE.md` for attribution and reuse terms. No API calls are needed to read these files.
