# 14 — Visual Quality Inspector

- **Application:** Computer vision inspection
- **Portfolio project:** 14 of 15
- **Status:** Source-derived CSV data is committed. ML models, the application and MLOps remain to be implemented.

Part of [Tomas Ferrer's DS/ML portfolio](https://tomasferrer.com/).

## Committed CSV dataset

**Dataset:** MVTec AD bottle category, Voxel51 mirror

**Coverage:** 60 source training-normal bottle images plus all 83 published bottle test images; original split/defect labels preserved. Full-source PNG images and available masks are included for this subset.

| CSV file | Rows |
|---|---:|
| [bottle_index.csv](data/raw/bottle_index.csv) | 143 |
| [bottle_grayscale32.csv](data/raw/bottle_grayscale32.csv) | 143 |

These are actual published observations or documented format conversions. See [source, license and limitations](data/DATASET.md) and [CSV schemas/checksums](data/csv-manifest.json).

The repository also includes 206 supporting image/mask assets referenced by the CSV data. Image-based work uses those assets; the CSV is not presented as a replacement for image content.

## Project prompt

Build an end-to-end computer vision inspection application that turns a published online dataset into a useful business decision. Implement the analysis, a trained machine learning component, a deployed application, its MLOps lifecycle, and a presentation. The learned model must influence the application's output. Begin with the dataset and adapt the scope to the evidence it actually contains.

### Business question and application

**Decision:** Which product images should a quality-control operator inspect?

**Application to build:** Inspect sample images, anomaly scores, and heatmaps; vary the threshold and compare missed defects with review workload.

Write a short project charter defining the user, current baseline, primary business KPI, guardrails, prediction time, and measurable success criteria before selecting a model. Explain which decision the model changes and the costs of incorrect decisions.

### Published dataset and raw data

The committed source is **MVTec AD bottle category, Voxel51 mirror**. 60 source training-normal bottle images plus all 83 published bottle test images; original split/defect labels preserved. Full-source PNG images and available masks are included for this subset. See [dataset documentation](data/DATASET.md) for original links, attribution, usage terms and limitations.

Acquire a pinned source release into `data/raw/` and preserve the original bytes. Add a repeatable acquisition script and a manifest containing source URL, release/version, retrieval time, citation, terms, file sizes and SHA-256 checksums. Keep cleaned data in `data/interim/` and model-ready features/split assignments in `data/processed/`. Redistributable CSV exports and the documented supporting assets are committed; large source archives remain excluded from Git.

Audit labels, decision-time feature availability, duplicates, missingness, class balance, and temporal/group structure. If the candidate cannot support the task or intended use, find another suitable published dataset or narrow the question. Generated fixtures and economic scenarios are supplementary, clearly labeled artifacts.

### Machine learning component

**Required fitted component:** Fitted anomaly detector over image features.

A simple image-feature baseline versus a fitted anomaly detector on pretrained image features. Learn the normal feature distribution from permitted training images, save that fitted state, and calibrate thresholds without test labels. A pretrained backbone alone is not the project's trained ML contribution.

Produce a reproducible training command and save the fitted preprocessing, model and decision policy together where appropriate. Compare the learned approach with a simple baseline. Pretrained models may support the solution, but a pretrained API call or prompt alone does not fulfill the trained-component requirement.

### Evaluation and business impact

Image-level AUROC and PR-AUC, defect recall at a fixed false-alarm rate, and a clearly described localization metric where heatmaps are evaluated.

Separate development/model selection from final evaluation. Fit transformations on training data only and compare candidate and incumbent on the same evaluation protocol. Save metrics, uncertainty/robustness checks, and representative failure cases with code/data/model identifiers.

Connect model metrics to the business KPI, with explicit denominators, comparator, population and period. Distinguish measured service performance, offline evaluation, simulated policy value and outcomes that require a real rollout. Never invent company impact or actual stakeholder buy-in.

### MLOps requirements

**Project-specific operational evidence:** Version backbone, normal-feature distribution and threshold; monitor image quality and anomaly-score drift; gate recall/false alarms before replacement.

Implement and demonstrate:

1. Data/schema validation and versioned acquisition, features, splits and configuration.
2. Reproducible training with MLflow experiment tracking and saved metrics/artifacts.
3. Model registration with code/data lineage, exact versions, candidate/incumbent comparison and promotion gates.
4. Production inference with validated inputs and meaningful tests, including consistency with the evaluated model.
5. Containerized deployment and GitHub Actions CI/CD, with a pinned model/image, health check, inference smoke test and release identifier.
6. Service telemetry and task-specific input/prediction/quality monitoring, alert criteria and a response runbook. Identify replayed quality reports separately when real outcome labels are unavailable.
7. A runnable data-refresh/retraining workflow that evaluates the replacement before promotion.
8. A demonstrated rollback to the previous model/application release and a successful post-rollback inference check.

Use the smallest architecture that completes this lifecycle. Select real-time or batch inference according to the decision; shared managed services are acceptable, while the repository remains independently reproducible.

### Communication and portfolio deliverables

- A readable README with setup, actual results, architecture, limitations, and links to the released demo/case study/slides.
- Purpose-specific notebooks and short executive summaries documenting important experiments and decisions.
- A stakeholder decision memo covering the recommendation, evidence, tradeoffs and proposed rollout.
- A personal ownership statement and dated operating record identifying what was implemented, actual service usage, model changes, and incident/rollback exercises.
- A working public demo with source-derived examples where permitted, plus screenshots or a short recorded fallback.
- An original 10–12 slide presentation: editable `presentation/slides.pptx`, reviewed `presentation/slides.pdf`, speaker notes and underlying figures. Include model evaluation, business implications, MLOps architecture and operational evidence.
- A case study prepared for `tomasferrer.com`, linking the repository, demo and presentation.

**Presentation story:** The inspection threshold determines the balance between missed defects and unnecessary manual review.

## Completion checklist

- [x] Published source acquired, checksum verified and provenance/profile recorded.
- [ ] Data audit, project charter, success criteria and evaluation protocol complete.
- [ ] Baseline and trained ML component evaluated; artifacts and failure analysis saved.
- [ ] Working application deployed with the exact evaluated model version.
- [ ] Tracking, registry, CI/CD, monitoring, retraining and rollback demonstrated.
- [ ] Stakeholder memo, ownership/operating record, case study and presentation complete.

## Current implementation

Published dataset observations, CSV exports, supporting assets where applicable, and provenance/checksum documentation are present. Models, application functionality and MLOps have not been implemented or evaluated yet.
