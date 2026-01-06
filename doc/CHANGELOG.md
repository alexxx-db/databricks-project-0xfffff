# Changelog

## v1.2.0 (January 5, 2026)

### New Features
- **Binary Scale Support**: Full support for Pass/Fail evaluation alongside Likert (1-5) scale
- **Free-form Text Responses**: Qualitative feedback in annotations
- **Binary SIMBA Optimizer**: Judge alignment for binary judges
- **Auto-refresh Annotations**: Judge Tuning now picks up new annotations automatically

### Improvements
- IRR recalculation uses `toast.promise()` for better UX (no duplicate toasts)
- MLflow locked to version 3.7 for compatibility
- Default annotation traces increased from 10 to 15
- Mode badge now correctly shows MLflow vs Simple Model Serving

### Bug Fixes
- Fixed IRR recalculation showing duplicate notifications
- Fixed Judge Tuning not recognizing new annotations after adding more traces

---

## v1.1.0 (December 8, 2025)

### New Features
- **Alignment Service**: New polling-based alignment with file job store
- **Judge Evaluation Persistence**: Results saved to database and reload in UI
- **Auto-derived Judge Name**: Judge name derived from rubric question
- **Automated Release Workflow**: GitHub Actions creates `project-with-build.zip`

### Improvements
- Judge name input moved to Annotation Phase dashboard
- Client build included in repository for easier deployment
- Login routing fixes

### Bug Fixes
- Fixed Judge Tuning save functionality
- Removed redundant proceed button
- Fixed user login routing issues
- Removed unnecessary auth sync

---

## v1.0.0 (December 5, 2025)

### Initial Release
- **Workshop Management**: Create and manage annotation workshops
- **Discovery Phase**: Users explore traces and identify patterns
- **Annotation Phase**: Rate traces based on custom rubrics
- **IRR Analysis**: Calculate inter-rater reliability (Krippendorff's Alpha, Cohen's Kappa)
- **MLflow Integration**: Import traces from MLflow experiments
- **Judge Tuning**: Create and evaluate AI judges
- **Pre-built Client**: Ready-to-deploy frontend

### Features
- Annotation editing with smart change detection
- Multi-line comment support
- Per-user randomized trace ordering
- CSV upload for trace import

---

## Unreleased (After v1.2.0)

### Bug Fixes
- Fixed Mode toggle in Judge Tuning to correctly show MLflow vs Simple

