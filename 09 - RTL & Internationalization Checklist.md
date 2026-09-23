# Module 9: RTL & Internationalization (i18n) Checklist

This checklist defines the visual, structural, and functional requirements for testing Right-To-Left (RTL) layout switching and bi-lingual support across the WST Management System.

---

##  Layout & Mirroring Verification
- [ ] **UI Flipping:** Verify that switching language to Arabic mirrors the main layout (Sidebar shifts to right, main content to left).
- [ ] **Navigation & Controls:** Ensure navigation arrows (Back/Forward), collapse icons, and dropdown indicators invert direction appropriately.
- [ ] **Form Fields & Labels:** Confirm form labels align to the right and input placeholders align according to text direction.
- [ ] **Tables & Data Grids:** Verify table headers and data columns re-order smoothly from Right-to-Left without breaking borders or scrolling.

---

## LTR Enforcement Rules (Standard Identifiers)
*The following standardized fields must strictly maintain LTR (Left-To-Right) formatting regardless of the active interface language:*

- [ ] **Vehicle Identification Numbers (VIN):** Displayed strictly LTR (e.g., `1HGCR2F83HA123456`).
- [ ] **License Plate Numbers:** Alpha-numeric plate formats preserve correct LTR order (e.g., `ABC-1234`).
- [ ] **Part SKUs & Barcodes:** Stock codes remain LTR aligned for scanner compatibility (e.g., `OIL-FIL-01`).
- [ ] **Transaction & Record IDs:** Job Cards, Purchase Orders, and Invoice codes maintain LTR formatting (e.g., `JC-2026-001`, `INV-8802`).
- [ ] **Financial Figures & Units:** Currency symbols, percentages, and numerical quantities display in standard order (e.g., `$150.00`, `15%`).

---

## Typography & Localization Accuracy
- [ ] **Arabic Font Rendering:** Ensure typography (e.g., Cairo/Tajawal) renders crisply without text clipping or overlapping elements.
- [ ] **Missing Translation Keys:** Verify no raw key fallback strings (e.g., `ERR_JOB_NOT_FOUND` or `BUTTON_SUBMIT`) appear in the UI.
- [ ] **Dynamic Date & Time Formatting:** Confirm timestamps follow localized formats while preserving server UTC synchronization.