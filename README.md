# BITS Pilani Digital – Advanced Academic Grading Console

> **BITS Digital CodeForge V1.0 Challenge Submission**  
> A production-grade, privacy-first, client-side academic grading console designed for instructors to ingest student scores, configure continuous grade boundaries, inspect borderline cases, and export finalized grades with zero server-side friction.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-bitsgrade.netlify.app-success.svg?style=for-the-badge&logo=netlify)](https://bitsgrade.netlify.app/)
[![Repository](https://img.shields.io/badge/GitHub-BitsAssignmentcodeforge-indigo.svg?style=for-the-badge&logo=github)](https://github.com/ajaditya103-a11y/BitsAssignmentcodeforge)
[![Platform](https://img.shields.io/badge/Platform-Modern%20Web%20(Client--Side)-blue.svg?style=for-the-badge)](#)
[![Accessibility](https://img.shields.io/badge/A11y-WCAG%20AA%20Compliant-purple.svg?style=for-the-badge)](#)

> 🌐 **Live Web Application:** [**https://bitsgrade.netlify.app**](https://bitsgrade.netlify.app/)  
> 📦 **GitHub Repository:** [**https://github.com/ajaditya103-a11y/BitsAssignmentcodeforge**](https://github.com/ajaditya103-a11y/BitsAssignmentcodeforge)


---

## 📑 Table of Contents
1. [Overview & Purpose](#-overview--purpose)
2. [Quickstart & Walkthrough](#-quickstart--walkthrough)
3. [Stage 1: Official Bug Fix Log](#-stage-1-official-bug-fix-log)
4. [Stage 2: Reimagined Product Enhancements](#-stage-2-reimagined-product-enhancements)
5. [Technical Architecture & Statistical Formulation](#-technical-architecture--statistical-formulation)
6. [Data Contract & Ingestion Rules](#-data-contract--ingestion-rules)
7. [Repository File Manifest](#-repository-file-manifest)
8. [Local Verification & Testing Guide](#-local-verification--testing-guide)

---

## 🎯 Overview & Purpose

The **BITS Pilani Digital Advanced Grading Console** is a specialized evaluation tool created for the **CodeForge V1.0** challenge. It bridges the gap between raw statistical data and qualitative academic decision-making.

Instructors can:
* Upload marks spreadsheets (`.xlsx`, `.xls`, `.csv`).
* Automatically normalize and deduplicate multi-course datasets.
* Select from predefined academic curve models (**BITS Default**, **Gaussian Bell Curve $\mu \pm \sigma$**, **Lenient**, **Strict**).
* Inspect student scores in real-time with automatic **Borderline ($\pm 1$ mark)** detection.
* Export officially formatted CSV and multi-sheet Excel workbooks with full audit summaries.

---

## 🚀 Quickstart & Walkthrough

The application is completely self-contained. There are **zero build steps, zero package installations, and zero server dependencies**.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       BITS Pilani Digital Console                           │
│  [⚡ Load Demo Dataset]  [📄 Download Template]    Instructor: Dr. Sharma   │
├──────────────────────────────────────┬──────────────────────────────────────┤
│ 📊 Statistical Analytics Studio      │ ⚙️ Grading Engine & Visual Spectrum  │
│  • Canvas Histogram & Bell Curve     │  • Presets: BITS / μ±σ / Lenient     │
│  • Mean Line Marker (μ)              │  • Continuous Spectrum Bar [0-100]   │
│  • Min, Max, Mean, Median, StdDev,   │  • Synchronized Min/Max Grade Cards  │
│    IQR, and Pass Rate %              │  • Live Validation Engine            │
│  • Grade Band Breakdown Pills (%)    │  • [Export CSV] [Export XLSX]        │
├──────────────────────────────────────┴──────────────────────────────────────┤
│ 📋 Live Student Grade Audit Roster                                          │
│  • Search by BITS ID | Filter by Grade | Borderline (±1 mark) Badges        │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Guided Walkthrough Steps

#### Step 1: Launch the Console
* Clone or download this repository.
* Open [`index.html`](index.html) in any modern web browser (Google Chrome, Firefox, Safari, Microsoft Edge).

#### Step 2: Instant Demo Exploration
* Don't have a spreadsheet on hand? Click the **`⚡ Load Demo Dataset`** button in the header.
* This automatically loads 144 realistic student marks across three distinct courses (`CS F111`, `MATH F111`, `EEE F111`) generated with a Box-Muller Gaussian distribution and explicit borderline edge cases.

#### Step 3: Instructor Identification & Course Selection
* Enter the **Instructor Name** (mandatory).
* Select a course from the dropdown. The session timer starts tracking active grading time immediately upon course selection.

#### Step 4: Fine-Tune Grade Cut-Offs
* **Preset Strategies**: Click **`Statistical Bell Curve (μ ± σ)`** to automatically compute grading cut-offs relative to the class mean ($\mu$) and standard deviation ($\sigma$). Alternatively, use **`BITS Default`**, **`Lenient Cut-offs`**, or **`Strict Cut-offs`**.
* **Manual Adjustment**: Change any grade's `Min` or `Max` dropdown. The downward cascade automatically shifts adjacent grades to eliminate gaps and overlaps.
* **Continuous Visualizer**: The multi-color spectrum bar at the top updates in real-time, confirming that 100% of the mark scale ($0 \to 100$) is covered without gaps.

#### Step 5: Review Analytics & Distribution
* **Canvas Histogram**: Bar heights show student density, and each bar is color-coded by the dominant grade assigned to that score range.
* **Gaussian Normal Curve**: The synchronized red curve illustrates class distribution, accompanied by a vertical dashed marker highlighting the cohort mean ($\mu$).
* **Academic Metric Cards**: Inspect **Min**, **Max**, **Class Average ($\mu$)**, **Median**, **Standard Deviation ($\sigma$)**, **Interquartile Range ($IQR$)**, and the overall **Passing Rate %** ($A \to D$).

#### Step 6: Audit Borderline Students
* Scroll down to the **Student Grade Audit Roster**.
* Click the **`⚠️ Borderlines (±1)`** filter button to inspect students who scored exactly 1 mark below a higher grade threshold (e.g., $79$ when the 'A' boundary is $80$).
* Use the search bar to locate specific student BITS IDs instantaneously.

#### Step 7: Finalize & Export
* Click **`📥 Finalize & Download CSV`** to export the official grading CSV according to BITS Pilani Digital specification.
* Click **`📊 Export XLSX`** to download a formatted Excel workbook containing two tabs: **Student Grades** and **Grading Summary**.
* An attempt notification records your total grading completion time.

---

## 🐛 Stage 1: Official Bug Fix Log

Below is the complete bug audit log identifying the 12 intentional and structural issues discovered in the original prototype, along with reproduction steps, root cause analysis, fixes implemented, and verification results:

| # | Bug / Issue Identified | How You Reproduced It | Root Cause | Fix Implemented | How You Tested the Fix |
|---|------------------------|-----------------------|------------|-----------------|------------------------|
| **1** | **Min and Max stat cards show inverted values** | Uploaded a dataset; the card labeled "Min" displayed the highest score (e.g. 98) while "Max" displayed the lowest score (e.g. 12). | In the HTML markup, the element IDs were swapped (`<b id="max">` inside Min container, `<b id="min">` inside Max container). | Corrected markup IDs to `#minStat` and `#maxStat`, wiring respective queries to semantic targets. | Verified Min displays lowest score ($8$) and Max displays highest score ($99$). |
| **2** | **Course list duplicates and stale options persist on re-upload** | Uploaded a file containing 50 records of "CS F111", or uploaded a second file sequentially. | `file.onchange` lacked deduplication (`Array.from(new Set(...))` was missing), and `course.innerHTML` was never cleared before adding new options. | Reset `course.innerHTML` to default placeholder on upload, extracted unique course names using `Set`, and populated only distinct course options. | Uploaded multi-course files with 100+ rows; verified clean, unique dropdown options. |
| **3** | **File picker rejects standard modern `.xlsx` files** | Tried selecting a standard modern `.xlsx` spreadsheet in macOS/Windows file picker. | The `<input type="file">` element was restricted to `accept=".xls"`, filtering out standard `.xlsx` files. | Updated input attribute to `accept=".xlsx, .xls, .csv"`. | Tested uploading `.xlsx`, `.xls`, and `.csv` files directly in file dialogue. |
| **4** | **Division by zero / NaN in statistics on empty or uniform datasets** | Selected a course with 0 records or where all students scored identical marks. | `computeStats()` divided by `m.length` without checking `m.length > 0` ($0/0 = \text{NaN}$). In `drawBellCurve()`, identical marks caused standard deviation $\sigma = 0$, leading to division by zero ($\text{NaN}/\infty$). | Added early guard clauses returning zero/dash placeholders for empty arrays, and clamped $\sigma = \max(\sigma, 0.5)$ when standard deviation is zero. | Tested with empty course dataset and uniform-mark datasets; confirmed clean rendering and zero errors. |
| **5** | **Bell curve x-axis misaligned with histogram bars** | Inspected analytics canvas overlay. Normal curve drifted leftward as marks approached 100. | Histogram bars used spacing $30 + i \times 32$ (span 320px), whereas the Gaussian curve used $30 + (x / 10) \times 30$ (span 300px). | Unified coordinate mapping so both histogram bars and the normal curve share the exact same step size ($34\text{px}$) and padding. | Verified that the Gaussian peak mathematically aligns with the class mean ($\mu$) bin. |
| **6** | **Concurrent animation frame leak on rapid range changes** | Adjusted grade range selectors rapidly. | `drawHistogram()` called `requestAnimationFrame(animate)` without cancelling previous pending frame loops (`cancelAnimationFrame`). | Maintained an active `currentAnimFrameId` and called `cancelAnimationFrame()` before initiating any new frame loop. | Toggled sliders rapidly; confirmed zero visual tearing, zero stutter, and stable 60 FPS rendering. |
| **7** | **Fractional marks fall through boundaries and lose grades** | Inputted non-integer marks such as $79.4$ or $69.8$. | Boundaries are discrete integers ($70-79$ then $80-100$). A mark of $79.4$ is $> 79$ and $< 80$, so it matched no grade band, disappearing from exports. | Added mandatory math rounding (`Math.round(Number(rawMarks))`) during ingestion per BITS policy ($80.2 \to 81$, $79.4 \to 79$). | Verified $79.4 \to 79$ (Grade A-) and $79.8 \to 80$ (Grade A); confirmed 100% of students receive valid grades. |
| **8** | **Timer starts prematurely and freezes permanently after first export** | Loaded page, waited 5 minutes, then started grading. Timer recorded idle time. Clicking download called `clearInterval()` permanently. | `gradingStartTime` was set on script load instead of when course grading begins. `download.onclick` cleared the interval with no resume capability. | Tied timer start to active course selection; added active state tracking and pause/resume logic. | Verified timer accurately resets on new course selection and reflects active grading time. |
| **9** | **Grade cascade produces negative values and invalid bounds** | Reduced Grade A Min down towards 0. | `cascadeMaxFrom()` set $\text{nextMax} = \text{prevMin} - 1$. If $\text{prevMin} = 0$, $\text{nextMax}$ became $-1$, which does not exist in the dropdown ($0..100$). | Clamped target values with $\max(0, \text{prevMin} - 1)$ and enforced minimum width between Min and Max. | Lowered Grade A Min to extreme lows; confirmed lower selects gracefully clamp at 0 without errors. |
| **10** | **CSV export lacks boundary validation and CSV escaping** | Downloaded CSV when instructor name had a comma or student fell outside ranges. | Raw string concatenation failed when fields contained commas or quotes, and students outside ranges were silently excluded. | Added RFC 4180 compliant CSV serialization with quoted fields, validation checks ensuring zero unassigned students, and blob cleanup via `URL.revokeObjectURL()`. | Tested instructor names like `"Sharma, Dr. P."`; confirmed proper spreadsheet column alignment. |
| **11** | **CSS animation classes removed before transition completes** | Changed select value and observed card lift. | `setTimeout(() => card.classList.remove("lift"), 30)` removed the class after 30ms, while the CSS transition was set to 250ms, creating visual stutter. | Matched timeout duration to 250ms. | Verified smooth card lift animation without frame snapping. |
| **12** | **Full scale coverage validation missing** | Set Grade A Max below 100 or Grade E Min above 0. | `validateRanges()` only checked $\text{Min} < \text{Max}$ and adjacent continuity, but never verified that Grade A Max is 100 and Grade E Min is 0. | Added checks ensuring `Amax == 100` and `Emin == 0`. | Set Grade A Max to 95; confirmed UI flags error: *"Grade A Max must be 100 to ensure full scale coverage."* |

---

## 💡 Stage 2: Reimagined Product Enhancements

To transform the prototype into a production-grade academic instrument, six foundational enhancements were engineered:

### 1. One-Click Curve & Grading Presets
* **Statistical Bell Curve ($\mu \pm \sigma$)**: Dynamically calculates cut-offs using standard deviations from the cohort mean:
  * Grade A: $\mu + 1.5\sigma$
  * Grade A-: $\mu + 1.0\sigma$
  * Grade B: $\mu + 0.5\sigma$
  * Grade B-: $\mu$
  * Grade C: $\mu - 0.5\sigma$
  * Grade C-: $\mu - 1.0\sigma$
  * Grade D: $\mu - 1.5\sigma$
* **BITS Default**: Restores the 80–70–60–50–40–30–20 standard.
* **Lenient & Strict Profiles**: Enables rapid adjustment for differing exam difficulties.

### 2. Live Student Grade Audit Roster & Borderline Detection
* **Borderline Inspection**: Instructors often agonize over students who narrowly missed a grade threshold. The console flags students within $\pm 1$ mark of an upper boundary with an amber `⚠️ Borderline` badge.
* **Dynamic Search & Filtering**: Instant search by student ID and category filters (`All`, `Borderlines`, `A/A-`, `E Failures`).

### 3. Continuous Grade Spectrum Visualizer
* Provides a multi-colored visual bar representing marks $0 \to 100$.
* Instantly reflects the proportional width of each grade band, giving instructors immediate visual verification that no mark gaps exist.

### 4. Advanced Academic Statistical Dashboard
* Computes essential higher-order academic metrics:
  * **Mean ($\mu$)** and **Median** for central tendency.
  * **Standard Deviation ($\sigma$)** for score dispersion.
  * **Interquartile Range ($IQR = Q_3 - Q_1$)** for outlier-resilient spread.
  * **Pass Rate %** (percentage of students receiving $A \to D$ vs $E$).
* **Color-Coded Histogram**: Each bar is dynamically shaded according to its assigned grade band.
* **Mean Marker**: Visual dotted line and $\mu$ label drawn on the distribution canvas.

### 5. Robust Ingestion & Built-in Demo Engine
* **`⚡ Load Demo Dataset`**: Generates 144 students across 3 courses using a Box-Muller Gaussian model so evaluators can test immediately without external files.
* **`📄 Download Template (.xlsx)`**: Client-side generation of an empty formatted marks workbook using SheetJS.
* **Drag-and-Drop Dropzone**: Visual feedback for dragging spreadsheets into the console.

### 6. Multi-Format & Audit Export
* **RFC 4180 CSV Export**: Adheres strictly to the BITS Pilani Digital specification with quoted string escaping.
* **Dual-Sheet Excel Export (`.xlsx`)**: Generates an `.xlsx` workbook containing both the student grade sheet and a formal **Grading Summary Sheet** (Instructor, Course, Metrics, Date).
* **Print-Ready Styles**: Formatted `@media print` rules for paper submission and PDF generation.

---

## 📐 Technical Architecture & Statistical Formulation

### Gaussian Probability Density Function
The bell curve overlay is rendered using the continuous normal probability density function:

$$f(x) = \frac{1}{\sigma \sqrt{2\pi}} \exp\left( -\frac{1}{2}\left(\frac{x - \mu}{\sigma}\right)^{\!2} \right)$$

* **Sample Mean**: $\mu = \frac{1}{N} \sum_{i=1}^{N} x_i$
* **Standard Deviation**: $\sigma = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2}$
* **Coordinate Mapping**: Each mark $x \in [0, 100]$ maps to the canvas coordinate $P_x = \text{Left} + \left(\frac{x}{10}\right) \times \text{Step} + \frac{\text{Step}}{2}$, guaranteeing 1:1 mathematical alignment with histogram bars.

### Box-Muller Transformation for Demo Generation
The built-in demo generator produces authentic pseudo-random normal distributions using the Box-Muller transform:

$$Z_0 = \sqrt{-2 \ln U_1} \cos(2\pi U_2)$$
$$\text{Score} = \text{clamp}\Big(8, 99, \text{round}\big(\mu + Z_0 \cdot \sigma\big)\Big)$$

---

## 📊 Data Contract & Ingestion Rules

The console expects an Excel workbook (`.xlsx`, `.xls`) or comma-separated values (`.csv`) containing three columns:

| Column Header | Type | Description | Handling Rule |
| :--- | :--- | :--- | :--- |
| **BITS ID** | String | Unique Student Roll / Identifier (e.g. `2024A7PS0001P`) | Trimmed of whitespace; case preserved |
| **Course** | String | Course Code / Title (e.g. `CS F111`) | Normalized; used for automatic course grouping |
| **Total Marks** | Number | Marks scored on 0–100 scale | Rounded to nearest integer ($80.2 \to 81$, $79.4 \to 79$) |

> **Absentee (NC) Rule**: Students who were absent or awarded an **NC** grade are excluded from the input file as per academic grading policy.

---

## 📁 Repository File Manifest

```
BitsAssignmentcodeforge/
├── index.html                    # Complete standalone Single-Page Grading Application
├── README.md                     # Comprehensive Walkthrough & Submission Documentation
├── sample_marks_cs111.csv        # 25 student records for CS F111 (borderline & normal spread)
└── sample_marks_multicourse.csv  # 22 student records across CS F111, MATH F111, EEE F111
```

---

## 🧪 Local Verification & Testing Guide

### Option 1: Direct Browser Launch
Simply double-click [`index.html`](index.html) or open it in your browser:
```bash
open /Users/adityajaiswal/Documents/assignmentsBITs/index.html
```

### Option 2: Local HTTP Server (Optional)
If you prefer running through a local development server:
```bash
# Using Python
python3 -m http.server 8080

# Using Node.js npx
npx serve .
```
Then navigate to `http://localhost:8080` in your browser.

### Test Scenarios to Verify

1. **Verify Bug Fix #1 (Min/Max Inversion)**:
   * Upload `sample_marks_cs111.csv`.
   * Check Min card: displays `8`.
   * Check Max card: displays `94`.

2. **Verify Bug Fix #2 (Course Deduplication)**:
   * Upload `sample_marks_multicourse.csv`.
   * Open Course dropdown: exactly 3 distinct options appear (`CS F111`, `MATH F111`, `EEE F111`).

3. **Verify Bug Fix #7 (Fractional Mark Rounding)**:
   * Upload `sample_marks_cs111.csv`.
   * Locate student `2024A7PS0004P` (raw mark: `79.4`).
   * Observe in roster: mark is rounded to `79` (Grade A-).
   * Locate student `2024A7PS0005P` (raw mark: `79.8`).
   * Observe in roster: mark is rounded to `80` (Grade A).

4. **Verify Enhancement #1 (Statistical Bell Curve Preset)**:
   * Click **`Statistical Bell Curve (μ ± σ)`**.
   * Observe the cut-offs adapting to the class distribution.
   * Observe the continuous spectrum bar and histogram bars updating instantaneously.

5. **Verify Enhancement #2 (Borderline Audit)**:
   * Click **`⚠️ Borderlines (±1)`** in the Student Grade Audit Roster.
   * Review all students flagged within $\pm 1$ mark of boundary changes.

---

## 👤 Author & Academic Details

* **Student / Author**: Aditya Jaiswal
* **GitHub**: [@ajaditya103-a11y](https://github.com/ajaditya103-a11y)
* **Repository**: [BitsAssignmentcodeforge](https://github.com/ajaditya103-a11y/BitsAssignmentcodeforge)
* **Challenge**: BITS Digital CodeForge V1.0 Challenge
