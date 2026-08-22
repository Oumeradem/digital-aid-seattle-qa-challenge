# Test Report: Random Date Generator
**Tool:** https://codebeautify.org/generate-random-date  
**Tester:** Oumer Adem  
**Date:** August 21, 2026  
**Test Type:** Exploratory Testing / Manual Functional Testing  

---

## 1. Tool Overview

The Random Date Generator allows users to generate one or more random dates based on:
- Number of dates to generate
- Date output format (8 format options + custom)
- Start date (range boundary)
- End date (range boundary)

---

## 2. Test Scope

| Area | In Scope |
|------|----------|
| Date generation with default settings | ✅ |
| All date format options | ✅ |
| Custom date format | ✅ |
| Start date / End date range validation | ✅ |
| Boundary dates (Jan 1, Dec 31, Feb 29) | ✅ |
| Large quantity of dates | ✅ |
| Invalid / empty inputs | ✅ |
| Output accuracy | ✅ |

---

## 3. Test Environment

| Item | Details |
|------|---------|
| Browser | Google Chrome (latest) |
| OS | Windows 11 |
| Device | Desktop |
| Test URL | https://codebeautify.org/generate-random-date |
| Test Date | August 21, 2026 |

---

## 4. Test Summary

| Total Test Cases | Passed | Failed | Bugs Found |
|-----------------|--------|--------|------------|
| 12 | 10 | 2 | 1 |

---

## 5. Test Cases

### TC-001: Generate date with default settings
- **Steps:** Open the tool, click "Generate Random Date" without changing any settings
- **Expected:** One random date is generated in MM-DD-YYYY format
- **Actual:** One random date generated successfully in MM-DD-YYYY format
- **Status:** ✅ PASS

---

### TC-002: Generate multiple dates
- **Steps:** Set quantity to 10, click "Generate Random Date"
- **Expected:** Exactly 10 random dates are generated
- **Actual:** 10 dates generated successfully
- **Status:** ✅ PASS

---

### TC-003: Generate date in YYYY-MM-DD hh:mm:ss format
- **Steps:** Select "YYYY-MM-DD hh:mm:ss" format, click generate
- **Expected:** Date and time generated in correct format (e.g., 2024-07-15 14:32:01)
- **Actual:** Date and time generated correctly
- **Status:** ✅ PASS

---

### TC-004: Generate date in ISO 8601 format
- **Steps:** Select "ISO 8601" format, click generate
- **Expected:** Date generated in ISO 8601 format (e.g., 2024-07-15T14:32:01Z)
- **Actual:** ISO 8601 format generated correctly
- **Status:** ✅ PASS

---

### TC-005: Generate date using custom format
- **Steps:** Select "Custom date format", enter "DD/MM/YYYY", click generate
- **Expected:** Date generated in DD/MM/YYYY format (e.g., 15/07/2024)
- **Actual:** Custom format generated correctly
- **Status:** ✅ PASS

---

### TC-006: Generate date within a valid date range
- **Steps:** Set Start Date to 01-01-2020, End Date to 12-31-2020, click generate
- **Expected:** Generated date falls within 2020
- **Actual:** Generated date was within the specified 2020 range
- **Status:** ✅ PASS

---

### TC-007: Start date equals End date
- **Steps:** Set Start Date and End Date both to 07-04-2024, click generate
- **Expected:** Only 07-04-2024 is generated (only one possible date)
- **Actual:** 07-04-2024 generated correctly
- **Status:** ✅ PASS

---

### TC-008: Start date is AFTER End date (invalid range)
- **Steps:** Set Start Date to 12-31-2025, End Date to 01-01-2020, click generate
- **Expected:** Tool should display an error message: "Start date must be before End date"
- **Actual:** Tool generates a date anyway without any error or warning — the output date appears invalid or random with no relation to the input range
- **Status:** ❌ FAIL — See BUG-001

---

### TC-009: Generate boundary date — January 1st
- **Steps:** Set Start Date and End Date both to 01-01-2024, click generate
- **Expected:** 01-01-2024 is generated
- **Actual:** Generated correctly
- **Status:** ✅ PASS

---

### TC-010: Generate boundary date — December 31st
- **Steps:** Set Start Date and End Date both to 12-31-2024, click generate
- **Expected:** 12-31-2024 is generated
- **Actual:** Generated correctly
- **Status:** ✅ PASS

---

### TC-011: Generate dates including a leap year date (Feb 29)
- **Steps:** Set Start Date to 02-28-2024, End Date to 03-01-2024, generate 10 dates
- **Expected:** February 29, 2024 may appear as a valid date (2024 is a leap year)
- **Actual:** Feb 29 2024 appeared as a valid generated date
- **Status:** ✅ PASS

---

### TC-012: Generate large quantity of dates (100 dates)
- **Steps:** Set quantity to 100, click generate
- **Expected:** 100 dates generated without errors or performance issues
- **Actual:** 100 dates generated, however no option exists to download or copy all results at once — usability issue
- **Status:** ✅ PASS (functional) — See FI-001 (usability improvement)

---

## 6. Bugs and Improvements Found

See [BUG_REPORT.md](./BUG_REPORT.md)

---

## 7. Overall Assessment

The Random Date Generator handles standard use cases well. The primary functional defect is the lack of validation 
when the Start Date is set after the End Date, which can produce misleading output without any user feedback. 
Two usability improvements are recommended to improve the overall user experience.
