# Version 1.5 Release Notes

## Overview

Version 1.5 represents a major milestone for the Human Evaluation Workshop, with **43 commits** since December 2025. The release focuses on four key feature areas that were aligned on by the team:

1. **Judge Builder UI Widgets** (free-form + binary labeling)
2. **Discovery → Rubric Creation** (reduce facilitator load)
3. **Align() + Judge Integration** (Likert + Binary/FuJ)
4. **Quality / Tech Debt** (test coverage, DB migration, infra)

---

## 1. Judge Builder UI Widgets (Free-form + Binary Labeling)

### What Changed

Added full support for binary (Pass/Fail) evaluation alongside the existing Likert scale, plus free-form text responses.

### Features Added

#### Binary Scale Support
- **New JudgeTypeSelector component** (`client/src/components/JudgeTypeSelector.tsx`)
  - UI for selecting between Likert (1-5) and Binary (Pass/Fail) judge types
  - Custom binary label configuration (e.g., "Good/Bad", "Pass/Fail")
  - Default prompt templates for each judge type

#### Annotation UI Updates (`client/src/pages/AnnotationDemo.tsx`)
- Binary rating buttons (Pass/Fail) alongside Likert scale
- Free-form text response fields for qualitative feedback
- Visual distinction between rating types
- Smart detection of which rating type is being used

#### Judge Tuning Updates (`client/src/pages/JudgeTuningPage.tsx`)
- Mode indicator badge now shows: Demo, Simple, or MLflow
- Binary scale prompt templates with 0/1 rating format
- Evaluation results display adapted for binary ratings
- Fixed mode toggle to correctly reflect MLflow vs Simple Model Serving

### Key Commits
- `e23a6c0` - Added binary scale, freeform text
- `579f7dd` - Added binary scale, freeform text
- `90326ec` - Updated judge tuning with binary scale
- `cefc182` - Updated judge tuning with binary scale
- `df777f8` - Updated judge tuning with binary scale
- `414fdf9` - Fix the mode toggle for judge tuning

### Files Changed
- `client/src/components/JudgeTypeSelector.tsx` (NEW - 215 lines)
- `client/src/pages/AnnotationDemo.tsx` (788+ lines changed)
- `client/src/pages/JudgeTuningPage.tsx` (633+ lines changed)
- `client/src/utils/rubricUtils.ts` (32+ lines changed)
- `server/models.py` (33+ lines changed)
- `server/database.py` (40+ lines changed)

---

## 2. Discovery → Rubric Creation (Reduce Facilitator Load)

### What Changed

Streamlined the flow from discovery to rubric creation, reducing manual steps for facilitators and making onboarding easier.

### Features Added

#### Auto-Derived Judge Name
- Judge name is now automatically derived from the rubric question
- Moved judge name input to Annotation Phase dashboard
- Reduces configuration steps during workshop setup

#### Rubric Creation Improvements (`client/src/pages/RubricCreationDemo.tsx`)
- Improved rubric parsing with `|||QUESTION_SEPARATOR|||` delimiter
- Support for multiple evaluation criteria per rubric
- Judge type metadata embedded in rubric format
- Binary labels stored with rubric configuration

#### Facilitator Dashboard Enhancements (`client/src/components/FacilitatorDashboard.tsx`)
- Better progress tracking across phases
- Clearer status indicators for each workflow phase
- Improved user management interface

### Key Commits
- `563472b` - Auto-derive judge name from rubric and move input to annotation phase
- `77dacde` - Fix Judge Tuning save functionality and remove proceed button
- Various rubric parsing improvements across multiple commits

### Files Changed
- `client/src/pages/RubricCreationDemo.tsx` (406+ lines changed)
- `client/src/components/FacilitatorDashboard.tsx` (119+ lines changed)
- `client/src/components/FacilitatorUserManager.tsx` (111+ lines changed)
- `client/src/components/PhaseControlButton.tsx` (20+ lines changed)

---

## 3. Align() + Judge Integration (Likert + Binary/FuJ)

### What Changed

Extended the MLflow judge alignment system to support both Likert scale and Binary (Pass/Fail) judges, with proper SIMBA optimizer integration.

### Features Added

#### Binary SIMBA Optimizer (`server/services/alignment_service.py`)
- **LikertSIMBAAlignmentOptimizer** - Custom optimizer for 1-5 scale judges
- **Binary judge support** - Uses MLflow's default SIMBAAlignmentOptimizer
- Automatic detection of judge type from rubric
- Proper feedback aggregation for both rating types

#### Evaluation Improvements
- Cohen's Kappa calculation for binary ratings
- Krippendorff's Alpha updates for binary scale
- IRR calculation fixes for both rating types
- Better handling of edge cases (systematic disagreement, no variation)

#### MLflow Integration
- Full `mlflow.genai.evaluate()` integration
- `align()` function support for judge optimization
- Proper trace tagging for alignment inclusion
- Fixed MLflow 3.7 compatibility issues

### Key Commits
- `cfde44f` - Added binary SIMBAoptimizer for alignment
- `7fdd359` - Refactor alignment to use polling and file-based job store
- `d9d2d3a` - Persist judge evaluation results to database and reload in UI
- `1493328` - Lock MLflow to 3.7 and default annotation to 15 traces

### Files Changed
- `server/services/alignment_service.py` (632+ lines changed)
- `server/services/irr_service.py` (28+ lines changed)
- `server/services/irr_utils.py` (58+ lines changed)
- `server/services/krippendorff_alpha.py` (58+ lines changed)
- `server/routers/workshops.py` (510+ lines changed)

---

## 4. Quality / Tech Debt (Test Coverage, DB Migration, Infra)

### What Changed

Significant infrastructure improvements including database migrations, automated workflows, and better error handling.

### Features Added

#### Database Migrations (Alembic)
- **Automatic migrations on startup** - Database is created/updated automatically
- Alembic added to production dependencies
- Migration scripts in `migrations/versions/`
- Support for both new and existing databases
- Legacy database stamping to baseline

#### Automated Build & Release
- GitHub Actions workflow for automated releases
- `project-with-build.zip` generation with pre-built client
- Manual trigger support for testing
- Proper exclusions (node_modules, .git, *.db, etc.)

#### IRR Recalculation Fixes
- Fixed duplicate toast notifications
- Switched to `toast.promise()` for better UX
- Automatic annotation refresh when navigating pages
- Judge Tuning now auto-refreshes annotations

#### React Query Integration
- Replaced manual state management with React Query hooks
- `useFacilitatorAnnotations` hook for real-time updates
- Automatic cache invalidation on annotation changes
- Page visibility refresh for stale data

### Key Commits
- `49a790d` - Add alembic, migrations, commands for bootstrap db
- `3279f4a` - Move setup scripts into justfile
- `642d079` - Setup e2e tests
- `10a551f` - Fixed IRR recalculation and judge tuning adding more traces
- `4f5c79d` - Setup automated build workflow for releases

### Files Changed
- `server/app.py` - Automatic migration on startup
- `alembic.ini` - Alembic configuration
- `migrations/env.py` - Migration environment
- `migrations/versions/0001_baseline.py` - Baseline schema
- `migrations/versions/0002_legacy_schema_fixes.py` - Legacy fixes
- `.github/workflows/release.yml` - Automated releases
- `justfile` - Build and deployment commands
- `client/src/hooks/useWorkshopApi.ts` (42+ lines changed)

---

## Summary of Changes by Area

| Area | Commits | Key Files Changed |
|------|---------|-------------------|
| Judge Builder UI | 6 | JudgeTypeSelector, AnnotationDemo, JudgeTuningPage |
| Discovery → Rubric | 3 | RubricCreationDemo, FacilitatorDashboard |
| Align() + Judge | 5 | alignment_service, irr_service, workshops router |
| Quality / Tech Debt | 8 | app.py, migrations, release workflow, useWorkshopApi |
| Bug Fixes | 12 | Various across frontend and backend |
| Documentation | 5 | README, release notes, gitignore |
| Other | 4 | Cleanup, refactoring |

---

## Breaking Changes

1. **Rubric Format** - Rubrics now include judge type metadata using `|||JUDGE_TYPE|||` delimiter
2. **Database Schema** - New columns for binary labels, judge type in rubrics/prompts
3. **MLflow Version** - Locked to MLflow 3.7 for compatibility

---

## Migration Guide

### From v1.1 to v1.5

1. **Database**: Migrations run automatically on startup - no action needed
2. **Existing Rubrics**: Will default to Likert scale if no judge type specified
3. **MLflow**: Ensure MLflow 3.7 is installed (`mlflow[databricks,genai]==3.7`)

---

## Contributors

- Vivian Xie (vivian-xie-db) - Binary scale, judge tuning, alignment
- Wesley Pasfield - MLflow 3.7 lock, annotation defaults
- Forrest Murray - User login routing, MLflow deeplink fix
- Will Middlebrook - CSV upload feature

---

## Next Steps

- [ ] Add comprehensive test coverage for binary scale
- [ ] Performance optimization for large annotation sets
- [ ] Enhanced IRR visualization for binary ratings
- [ ] Documentation updates for new features

