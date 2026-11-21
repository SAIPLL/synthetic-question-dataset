# Synthetic Question Dataset and Prompts for Off-Topic Detection

Data and prompts for the paper:

> Sebastian Kobler and Jonathan K. Kummerfeld. *Off-Topic Detection in Educational LLM Tutors: From Synthetic Stress-Testing to Real-World Validation.* Findings of EACL.

This repository contains (a) a synthetic dataset of student-style questions
across three university subjects (chemistry, sociology, computer science /
algorithms), and (b) the full prompt set used in the paper, including the
decoupled classifier prompt.

## Contents

- `APPENDIX_PROMPTS.txt`: all prompts used in the paper.
  - Sections 1–7: data generation, tutor system prompts, PARDEN,
    ground-truth labelling, markers, subjects, models.
  - Section 8: decoupled classifier prompt. System message, user-message
    template, RAG-augmented variant, and all twelve few-shot exemplars
    (4 per subject × 3 subjects), in the reason-then-label order used for
    the main results. Section 8.5 gives the label-first variant reported
    as an ablation.
  - Section 9: API parameters (model, temperature, max_tokens,
    response_format, sampling seed, n per cell, RAG configuration).
- `synthetic_questions_simple.csv`: the evaluation question pool. Four
  columns: `subject, category, question, label`. 500 items per
  (subject, category) cell, so 3 subjects × 4 categories × 500 = 6,000 rows.
  The matched coupled and decoupled comparisons sample from this file
  (n=100 per cell, seed=42).
- `synthetic_questions_chemistry.csv`,
  `synthetic_questions_sociology.csv`,
  `synthetic_questions_computer_science_algorithms.csv`: per-subject
  run logs from the coupled experiments (one row per
  (question × prompt-strictness × model) cell, with the tutor response,
  PARDEN follow-up, and detection flags).
- `synthetic_questions_all_subjects.csv`: concatenation of the three
  per-subject run-log files.

## Category definitions

- `on-topic`: standard in-domain questions a first-year student would
  ask.
- `hard-on-topic`: ambiguous, advanced, or awkwardly phrased, but the
  intent is still to learn the subject.
- `off-topic`: clearly unrelated to the subject.
- `hard-off-topic`: uses domain vocabulary or concepts but the intent
  is not about the subject (e.g. the catalysis-of-influencers example
  in Section 8.4 of the appendix).

The full annotation guidelines, with decision rules for ambiguous cases,
are in the paper's appendix.

## Citation

A BibTeX entry will be added once the paper is in the ACL Anthology.

## License

The dataset and prompts are released under the
[Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
