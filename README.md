# Open Barlaman — Prompts and taxonomy

This repository publishes the prompts and classification taxonomy for analysing Moroccan parliamentary questions for Open Barlaman.

## Contents

| File | Purpose |
| --- | --- |
| [OCR prompt](prompts/parliamentary-ocr-v1.en.txt) | Instructions for transcribing a parliamentary document page as plain text, preserving its content and reading order. |
| [Question-analysis template](prompts/question-analysis-v2.1.template.ar.txt) | Arabic analysis instructions with placeholders for the allowed taxonomy codes and descriptions. |
| [Rendered question-analysis prompt](prompts/question-analysis-v2.1.rendered.ar.txt) | The complete Arabic analysis prompt with the taxonomy included. |
| [Classification taxonomy](taxonomy/ma-question-analysis-v2.1.json) | Allowed codes and Arabic descriptions for scopes, topics, problem types, request types, and population categories. |

## Question analysis

The taxonomy version is `ma_question_analysis_v2_1`.

The analysis prompt instructs the model to use only the supplied question text and return eight labelled lines in this order:

```text
SUMMARY:
SCOPE:
TOPICS:
PROBLEMS:
REQUESTS:
POPULATION_CATEGORIES:
PLACES:
PROGRAMS_ENTITIES:
```

The summary is a neutral Arabic sentence. Classification fields use the allowed English codes; places and public programmes or entities are extracted only when explicitly mentioned. The prompt specifies `NONE` for absent or inapplicable fields and comma-separated values where multiple entries are allowed. The scope must be one of `NATIONAL`, `LOCAL`, `DIASPORA`, or `INTERNATIONAL`.

Use the rendered prompt to inspect the complete instructions. The template contains `{{SCOPES}}`, `{{TOPICS}}`, `{{PROBLEM_TYPES}}`, `{{REQUEST_TYPES}}`, and `{{POPULATION_CATEGORIES}}` placeholders corresponding to the taxonomy sections.
