# Spec Test Coverage Map

**Generated**: 2026-01-20 11:27:33

This report shows which tests cover each specification.
Tests are tagged using framework-specific conventions:

- **pytest**: `@pytest.mark.spec("SPEC_NAME")`
- **Playwright**: `{ tag: ['@spec:SPEC_NAME'] }` or `@spec:SPEC_NAME` in test title
- **Vitest**: `// @spec SPEC_NAME` comment or `describe('@spec:SPEC_NAME', ...)`

---

## Coverage Summary

| Spec | pytest | Playwright | Vitest | Total | Status |
|------|--------|------------|--------|-------|--------|
| [ANNOTATION_SPEC](#annotation-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [AUTHENTICATION_SPEC](#authentication-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [BUILD_AND_DEPLOY_SPEC](#build-and-deploy-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [DATASETS_SPEC](#datasets-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [DESIGN_SYSTEM_SPEC](#design-system-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [DISCOVERY_TRACE_ASSIGNMENT_SPEC](#discovery-trace-assignment-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |
| [JUDGE_EVALUATION_SPEC](#judge-evaluation-spec) | 2 | 0 | 0 | 2 | 🟡 Partial |
| [RUBRIC_SPEC](#rubric-spec) | 0 | 1 | 1 | 2 | 🟡 Partial |
| [UI_COMPONENTS_SPEC](#ui-components-spec) | 0 | 0 | 0 | 0 | ❌ Uncovered |

**Coverage**: 2/9 specs (22%)

---

## ANNOTATION_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("ANNOTATION_SPEC")`
- Playwright: `{ tag: ['@spec:ANNOTATION_SPEC'] }`
- Vitest: `// @spec ANNOTATION_SPEC`

## AUTHENTICATION_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("AUTHENTICATION_SPEC")`
- Playwright: `{ tag: ['@spec:AUTHENTICATION_SPEC'] }`
- Vitest: `// @spec AUTHENTICATION_SPEC`

## BUILD_AND_DEPLOY_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("BUILD_AND_DEPLOY_SPEC")`
- Playwright: `{ tag: ['@spec:BUILD_AND_DEPLOY_SPEC'] }`
- Vitest: `// @spec BUILD_AND_DEPLOY_SPEC`

## DATASETS_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("DATASETS_SPEC")`
- Playwright: `{ tag: ['@spec:DATASETS_SPEC'] }`
- Vitest: `// @spec DATASETS_SPEC`

## DESIGN_SYSTEM_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("DESIGN_SYSTEM_SPEC")`
- Playwright: `{ tag: ['@spec:DESIGN_SYSTEM_SPEC'] }`
- Vitest: `// @spec DESIGN_SYSTEM_SPEC`

## DISCOVERY_TRACE_ASSIGNMENT_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("DISCOVERY_TRACE_ASSIGNMENT_SPEC")`
- Playwright: `{ tag: ['@spec:DISCOVERY_TRACE_ASSIGNMENT_SPEC'] }`
- Vitest: `// @spec DISCOVERY_TRACE_ASSIGNMENT_SPEC`

## JUDGE_EVALUATION_SPEC

### pytest

- `tests/unit/services/test_alignment_service.py` (test_normalize_judge_prompt_converts_placeholders_to_mlflow_style)
- `tests/unit/services/test_alignment_service.py` (test_likert_agreement_metric_from_store_is_one_when_equal)

## RUBRIC_SPEC

### Playwright (E2E)

- `client/tests/e2e/rubric-creation.spec.ts`

### Vitest (Unit)

- `client/src/utils/rubricUtils.test.ts`

## UI_COMPONENTS_SPEC

❌ **No tests tagged for this spec**

To add coverage, tag tests with:
- pytest: `@pytest.mark.spec("UI_COMPONENTS_SPEC")`
- Playwright: `{ tag: ['@spec:UI_COMPONENTS_SPEC'] }`
- Vitest: `// @spec UI_COMPONENTS_SPEC`
