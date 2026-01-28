# EEG Brainwave Research - External Repository Analysis

This document analyzes the [Hiurge/eeg_brainwave_research](https://github.com/Hiurge/eeg_brainwave_research) repository and its potential relevance to RF/Havana Syndrome research.

---

## Table of Contents

1. [Repository Overview](#repository-overview)
2. [Project Goal](#project-goal)
3. [Data Source](#data-source)
4. [Technical Implementation](#technical-implementation)
5. [Sample Selection Criteria](#sample-selection-criteria)
6. [Code Analysis](#code-analysis)
7. [Relevance to RF Research](#relevance-to-rf-research)
8. [Key Takeaways](#key-takeaways)
9. [Potential Applications](#potential-applications)

---

<a id="repository-overview"></a>
## Repository Overview

| Attribute | Value |
|-----------|-------|
| **Repository** | [Hiurge/eeg_brainwave_research](https://github.com/Hiurge/eeg_brainwave_research) |
| **Owner** | Hiurge (Łukasz M. Pintal) |
| **Contributor** | robscott95 (Robert Kuśka) |
| **Created** | October 20, 2019 |
| **Last Updated** | October 25, 2019 |
| **Status** | Abandoned (5+ years inactive) |
| **Language** | Python (Jupyter Notebooks) |

### Repository Structure

```
eeg_brainwave_research/
├── .gitignore
├── readme.md
├── scrapping_eeg_data_with_descriptions.ipynb   # Data collection
└── database_exploration_and_picking_samples.ipynb # Sample selection
```

---

<a id="project-goal"></a>
## Project Goal

> "Create a machine/deep learning based model which will successfully predict if a 20-minute baseline EEG session is that of a schizophrenic."

### Clinical Use Case

- **Setting**: Emergency Room triage
- **Purpose**: Quick psychiatric diagnosis
- **Team Size**: 3-4 researchers

### Why This Matters for RF Research

While the project focuses on schizophrenia, the methodology for:
1. Filtering clinical EEG records
2. Identifying "clean" baseline recordings
3. Excluding confounding conditions

...could be applied to studying **RF-exposed individuals**.

---

<a id="data-source"></a>
## Data Source

### TUH EEG Corpus v1.1.0

| Statistic | Value |
|-----------|-------|
| Total patients | 13,539 |
| Total sessions | 23,002 |
| Sessions/patient | 1.70 avg |
| EDF files | 53,506 |
| Total duration | 15,757 hours |
| Sample frequencies | 250 Hz - 1024 Hz |
| 10-20 standard | 95% of data |

**Source**: Temple University Hospital (TUH) EEG Corpus
**Access**: Restricted (requires credentials)
**URL**: https://isip.piconepress.com/projects/tuh_eeg/

### Data Structure

Each session contains:
- `.edf` files - Raw EEG signal data
- `.txt` files - Clinical reports (semi-structured text)

---

<a id="technical-implementation"></a>
## Technical Implementation

### Phase 1: Data Scraping

Two implementations:

| Version | Method | Time |
|---------|--------|------|
| Sync | `requests` library | 1-1.5 hours |
| Async | `aiohttp` + `asyncio` | ~15 minutes |

**Key Algorithm**: Depth-First Search (DFS) web crawler

```python
# Core data structure
EDFData = namedtuple("EDFData", ["url", "readme"])

# Crawling logic
def crawl(init_link):
    to_crawl = [init_link]
    while to_crawl:
        current_url = to_crawl.pop(-1)  # DFS
        # Parse directory listing
        # Yield EDFData tuples
```

### Phase 2: Format Classification

Clinical reports have inconsistent formatting. Solution: classify by capitalization.

```python
def repport_type(text):
    first = str(text).strip().split()[0]
    if first.isupper():
        return 'standard_1'    # "CLINICAL HISTORY..."
    elif first.title():
        return 'standard_2'    # "History..."
```

**Results**:

| Format | Count | % |
|--------|-------|---|
| standard_1 | 18,611 | 80.9% |
| standard_2 | 4,390 | 19.1% |
| unclassified | 1 | 0.004% |

### Phase 3: Schema Normalization

**Unified schema** (11 fields):

| Field | Purpose |
|-------|---------|
| clinical_history | Patient background |
| age | Patient age |
| sex | Patient sex |
| medications | Current medications |
| sedation | Sedation status |
| eeg_type | Recording type |
| technique | Recording method |
| study_details | Technical details |
| impression | Clinician interpretation |
| correlations | Clinical correlations |
| others | Unclassified |

### Phase 4: Feature Extraction

**12 derived features** from raw text:

| Feature | Method |
|---------|--------|
| `age` | 15+ pattern matching rules |
| `sex` | Keyword detection (man, woman, male, female, etc.) |
| `system` | String search for "10-20" |
| `eeg_norm_abnorm` | Keyword search (NORMAL/ABNORMAL EEG) |
| `is_awake` | Boolean flag |
| `not_asleep` | Boolean flag |
| `medications` | Text cleaning pipeline |
| `cond_flags` | Lemmatization + keyword matching |

**Age Extraction Example** (handles 15+ formats):
- "52-year-old"
- "52 yr"
- "52yo"
- "52 y.o."
- "52 y/o"

---

<a id="sample-selection-criteria"></a>
## Sample Selection Criteria

### 5 Filtering Conditions

| # | Criterion | Code | Purpose |
|---|-----------|------|---------|
| 1 | 10/20 electrode system | `system == '10/20'` | Standard placement |
| 2 | Normal EEG | `eeg_norm_abnorm == 'Normal'` | Control group |
| 3 | Not asleep | `not_asleep == 1` | Consistent brain state |
| 4 | No medications | `medications == ''` | Avoid drug artifacts |
| 5 | No neurological conditions | `cond_flags == ''` | Clean controls |

### Excluded Conditions (18 total)

| Category | Conditions |
|----------|------------|
| Neurodevelopmental | Autism, ADHD |
| Psychotic | Schizophrenia |
| Mood | Depression, Mania |
| Anxiety | Anxiety, OCD |
| Neurodegenerative | Dementia, Parkinson's |
| Sleep | Narcolepsy, Parasomnias |
| Substance | Alcoholism |
| Metabolic | Diabetes |
| Connective tissue | Ehlers-Danlos, Arthritis |
| Cardiovascular | Tachycardia |
| Seizure | Epilepsy |

### Filtering Results

| Filter Stage | Remaining | % of Total |
|--------------|-----------|------------|
| Start | 23,002 | 100% |
| Normal EEG | 3,933 | 17.1% |
| + Not asleep | ~3,800 | ~16.5% |
| + No meds | ~400 | ~1.7% |
| + 10/20 system | 365 | 1.6% |
| + No conditions | **94** | **0.4%** |

### Final Sample Groups

| Group | Criteria | Count |
|-------|----------|-------|
| A | Criteria 1-4 | 365 |
| B | All 5 criteria | 94 |

---

<a id="code-analysis"></a>
## Code Analysis

### Strengths

| Aspect | Evidence |
|--------|----------|
| Modular design | Separate functions for each transformation |
| Performance | 6x speedup with async implementation |
| Documentation | Markdown cells explain methodology |
| Collaboration | PR workflow with external contributor |

### Weaknesses

| Issue | Impact |
|-------|--------|
| No unit tests | Parsing errors may propagate |
| No validation | Parsing accuracy unknown |
| Abandoned | ML model never implemented |
| Data restricted | Requires TUH credentials |

### Critical Bug Fix (PR #2)

**Original (broken)**:
```python
if 'NORMAL EEG' in text:      # Matches "ABNORMAL EEG" too!
    return 'Normal'
elif 'ABNORMAL EEG' in text:
    return 'Abnormal'
```

**Fixed**:
```python
if 'ABNORMAL EEG' in text:    # Check ABNORMAL first
    return 'Abnormal'
elif 'NORMAL EEG' in text:
    return 'Normal'
```

---

<a id="relevance-to-rf-research"></a>
## Relevance to RF Research

### Direct Overlap

| Aspect | Overlap Level | Notes |
|--------|---------------|-------|
| Domain | Low | Psychiatry vs. RF effects |
| Technology | Medium | EEG analysis applicable to both |
| Methods | High | Data filtering, feature extraction |
| Code | High | Reusable Python pipeline |

### How This Relates to Havana Syndrome

McLean's research predicts RF exposure causes:
1. Neural threshold changes
2. Spike rate alterations
3. Network-level errors

**EEG could detect these effects** via:
- Alpha/beta/gamma band power changes
- Event-related potential (ERP) alterations
- Connectivity metric changes

### EEG Biomarkers of RF Exposure (Literature)

| Study | Finding |
|-------|---------|
| Hinrikus et al. (2005) | Microwave exposure altered EEG alpha rhythms |
| Hinrikus et al. (2008) | Modulated microwave affected cognitive processes |
| Croft et al. (2002) | Mobile phone RF altered EEG during sleep |

These studies are cited in McLean's Book 1 references [20], [21].

---

<a id="key-takeaways"></a>
## Key Takeaways

### What This Project Achieved

1. ✅ Web scraper for 23,000 EEG records
2. ✅ Multi-format text parser
3. ✅ Feature extraction pipeline
4. ✅ Clean sample identification (94 controls)

### What's Missing

1. ❌ Schizophrenia sample identification
2. ❌ EEG signal preprocessing
3. ❌ Feature extraction from signals
4. ❌ ML model training
5. ❌ Validation

### Lessons Learned

1. **Clinical data is messy** - Multiple formats require robust parsing
2. **Filtering is aggressive** - Only 0.4% of data meets strict criteria
3. **Async scraping essential** - 6x speedup for large datasets
4. **Bug testing critical** - String matching order matters (ABNORMAL/NORMAL)

---

<a id="potential-applications"></a>
## Potential Applications

### For RF/Havana Syndrome Research

If you wanted to study **EEG changes in RF-exposed individuals**, this pipeline could:

1. **Identify baseline samples** - Find clean pre-exposure EEGs
2. **Filter by demographics** - Match age/sex across groups
3. **Exclude confounders** - Remove subjects with neurological conditions
4. **Extract metadata** - Parse clinical reports for relevant info

### Proposed Study Design

```
1. Obtain TUH EEG access
2. Use Hiurge pipeline to identify clean baselines
3. Apply McLean's frequency predictions (400-500 MHz)
4. Design RF exposure experiment (within safety limits)
5. Compare pre/post exposure EEG
6. Train classifier on exposed vs. unexposed
```

### Technical Stack for Continuation

```python
# Recommended libraries
mne           # EEG signal processing
scipy         # Spectral analysis
scikit-learn  # ML models
tensorflow    # Deep learning
pandas        # Data manipulation
numpy         # Numerical computing
matplotlib    # Visualization
```

### EEG Features to Extract

| Category | Features |
|----------|----------|
| Spectral | Power in delta, theta, alpha, beta, gamma bands |
| Temporal | ERP components (P300, N100, etc.) |
| Connectivity | Coherence, phase-locking value |
| Complexity | Entropy measures |

---

## Summary

The Hiurge/eeg_brainwave_research repository provides a **well-engineered but incomplete** data pipeline for clinical EEG analysis. While focused on schizophrenia, the methodology is directly applicable to studying RF-induced neural effects.

The key value lies in:
1. **Proven web scraping** for large EEG datasets
2. **Robust text parsing** for clinical reports
3. **Rigorous filtering** criteria for clean samples
4. **Reusable Python code** under permissive license

For Havana Syndrome research, this represents a starting point for **EEG-based validation** of McLean's theoretical predictions about RF effects on neural signaling.

---

## References

- [Hiurge/eeg_brainwave_research](https://github.com/Hiurge/eeg_brainwave_research) - GitHub Repository
- [TUH EEG Corpus](https://isip.piconepress.com/projects/tuh_eeg/) - Data Source
- [MNE-Python](https://mne.tools/) - EEG Processing Library
- Hinrikus et al. (2005) - "Non-thermal effect of microwave radiation on human brain"
- Hinrikus et al. (2008) - "Effect of modulated microwave radiation on EEG rhythms"

---

*Document created: January 2025*
*Part of the McLean-Books Research Repository*
