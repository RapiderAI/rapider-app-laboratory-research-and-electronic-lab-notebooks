<!-- Rapider Official App SOW & Specification | App #192: Laboratory Research & Electronic Lab Notebooks (laboratory-research-and-electronic-lab-notebooks) | Domain: IND -->

# #192 Laboratory Research & Electronic Lab Notebooks (`laboratory-research-and-electronic-lab-notebooks`) — Scope of Work (SOW)

- **App Number & Name:** `#192` — Laboratory Research & Electronic Lab Notebooks
- **Proposed App Key:** `laboratory-research-and-electronic-lab-notebooks`
- **Suite / Domain Key & Model Prefix:** `IND` (`Ind*`)
- **Representative Product (`P1`):** Benchling
- **Combined Feature Catalog:** [../combined-features/192-laboratory-research-and-electronic-lab-notebooks-features.md](../combined-features/192-laboratory-research-and-electronic-lab-notebooks-features.md)
- **Target Release Posture:** Scientific R&D Electronic Lab Notebook (ELN), Molecular/Chemical Entity Registry, Freezer/Plate Aliquot Lineage & FDA 21 CFR Part 11 Electronic Witnessing Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Business Problem Solved
Biotechnology, pharmaceutical, specialty chemical, materials science, food/ag-science, and industrial R&D laboratories suffer from irreproducible experiments, duplicate synthesis/cloning of already-registered molecules, mystery `-80°C` freezer cryovials with unknown freeze-thaw histories, manual plate-reader spreadsheet copy-paste errors, indefensible patent-priority records, and friction transferring lead candidates into commercial PLM/manufacturing. **Rapider Laboratory Research & Electronic Lab Notebooks (`laboratory-research-and-electronic-lab-notebooks`)** unifies structured ELN experiment entries, versioned SOP protocols, a canonical molecular/biological/chemical entity Registry, hierarchical freezer/box/96-384-well plate sample lineage, instrument result parsing, and FDA **21 CFR Part 11 / EU Annex 11** electronic witnessing with seamless graduation into canonical Rapider `plm`, `bom`, `quality`, `assets`, `maintenance`, `inventory`, and `apm` suites.

> **Explicit Scope Boundary vs. `#157 Clinical Diagnostic LIMS`:** App `#192` governs **scientific R&D, discovery, formulation, process development, IP witnessing, and research entity registration** (`Benchling` / `Revvity Signals` class). Clinical patient diagnostic specimen orders, HL7/FHIR hospital EHR interfaces, CLIA/CAP clinical pathology turnaround queues, and CPT insurance billing belong exclusively to `#157 Clinical Laboratory Information Management (LIMS)`.

### 1.2 Target Personas & Progressive Disclosure
- **SME Fast-Path Defaults (Biotech Startups, University Spinouts, Food/Materials R&D Labs, 5–40 Scientists):** Author structured ELN entries from reusable protocol templates in minutes, register unique sequence/compound IDs (`REG-*`), map `-80°C` / `-20°C` freezer boxes and vial balances, attach/parse CSV plate-reader results, and complete two-person IP patent witnessing in clicks.
- **Enterprise Progressive Disclosure (Biopharma, Global Chemical & Industrial R&D Organizations, 100–5,000+ Researchers):** Activate strict FDA 21 CFR Part 11 / GLP re-authenticated dual signatures (`Author` + `Witness` + `QA`) with SHA-256 lock digests and `reasonForChange` addenda, 96/384-well plate serial-dilution lineage, calibrated lab instrument (`OpsOperationsAsset`) readiness blocks, stealth pre-patent program ACLs, SAR candidate matrices, and governed tech-transfer graduation into `MfgProductRevision` (`plm`), `MfgBom` (`bom`), and `MfgQualityInspection` (`quality`).

### 1.3 Measurable Business Outcomes
- **100% Unbroken Entity-to-Freezer-to-Assay Lineage:** Every assay result traces back to the exact `IndLabSampleContainer` aliquot, freeze-thaw count, registered `IndResearchEntity` structure/sequence, and witnessed `IndElnEntry`.
- **Zero Duplicate Molecular / Chemical Registration:** Canonicalized sequence and SMILES/InChIKey checks prevent assigning duplicate corporate IDs to identical constructs or compounds.
- **100% Audit-Ready 21 CFR Part 11 & Patent Defense:** Cryptographically locked entries, enforced independent witnessing (`witnessUserId != authorUserId`), and append-only signed addenda withstand FDA GLP/IND and patent interference audits.

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the structured biology-first ELN, Registry, and freezer/plate lineage of **`P1` Benchling**, stoichiometry, SMILES chemistry, and 21 CFR Part 11 sign-and-lock rigor of **`P2` Revvity Signals Notebook**, plate transformations and scientific AI of **`P3` Sapio Sciences**, FDA/GLP project-experiment-step traceability of **`P4` SciNote**, calibrated instrument & analytical workbook controls of **`P5` BIOVIA Workbook**, and R&D-to-PLM/BOM/Quality tech-transfer graduation of **`P6` SAP Integrated Product Development**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. Structured ELN experiment entries (`IndElnEntry`) with stoichiometry/dilution math, inline `@`-entity/sample references, and versioned SOP protocols (`IndLabProtocol`).
2. Multi-modal scientific Entity Registry (`IndResearchEntity` — plasmids, antibodies, cell lines, oligos, small-molecule SMILES/InChIKey, polymers, formulations) with sequence/structure deduplication and parent-child lineage.
3. Cold-storage & lab hierarchy (`IndStorageHierarchy` — Room -> Freezer -> Rack -> Box) and barcoded container/plate tracking (`IndLabSampleContainer`) with volume drawdowns and `freezeThawCycles` guardrails.
4. Core-lab assay request `<rapider-kanban>` and normalized instrument result runs (`IndAssayResultRun`) linked to raw instrument files.
5. FDA 21 CFR Part 11 / IP electronic signatures (`IndNotebookSignature`), SHA-256 entry locking, append-only `reasonForChange` addenda, and candidate tech-transfer handoff to `plm`/`bom`/`quality`.

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Clinical patient diagnostic requisitions, PHI patient portals, HL7/FHIR clinical lab reporting, and CPT medical billing:** Owned exclusively by `#157 Clinical Diagnostic LIMS`.
- **Commercial manufacturing batch execution, MRP scheduling, and commercial QA release lot dispositions:** Owned by `plm` (`MfgProductRevision`), `bom` (`MfgBom`), `production` (`MfgOrder`), and `quality` (`MfgQualityInspection`).
- **Lab equipment fixed-asset depreciation and preventive calibration technician execution:** Owned by `assets` (`OpsOperationsAsset`) and `maintenance` (`MfgMaintenanceWorkOrder`).
- **Bulk warehouse purchase orders and vendor invoicing for lab glassware/solvents:** Owned by `inventory` (`OpsInventoryItem`) and `procurement` (`OpsPurchaseOrder`).
- **Standalone custom approval inbox:** Delegated strictly to Rapider Platform Home `WorkItem`s.

### 2.3 Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical Models) | Integration Contract with `laboratory-research-and-electronic-lab-notebooks` |
| :--- | :--- | :--- |
| **`laboratory-research-and-electronic-lab-notebooks` (`#192` — This App)** | `IndLabProtocol`, `IndElnEntry`, `IndResearchEntity`, `IndStorageHierarchy`, `IndLabSampleContainer`, `IndAssayResultRun`, `IndNotebookSignature` | Owns R&D notebooks, protocols, molecular/chemical registry, freezer/plate sample lineage, assay runs, and 21 CFR Part 11 signatures. |
| **`apm` (`APM` Suite)** | `ApmProject` | Every `IndElnEntry` and `IndAssayResultRun` links `studyProjectId -> ApmProject.id` for R&D program portfolio & grant/budget tracking. |
| **`assets` & `maintenance` (`OPS`/`MFG`)** | `OpsOperationsAsset`, `MfgMaintenanceWorkOrder` | Analytical instruments bind `instrumentAssetId -> OpsOperationsAsset.id`; overdue calibration or open `MfgMaintenanceWorkOrder` blocks regulated GLP runs. |
| **`inventory` (`OPS` Suite)** | `OpsInventoryItem` | Bulk commercial reagents/consumables link to `OpsInventoryItem.id` for stock drawdown and low-par reorder signals. |
| **`plm`, `bom` & `quality` (`MFG` Suite)** | `MfgProductRevision`, `MfgBom`, `MfgQualityInspection` | Graduating a validated lead `IndResearchEntity`/formulation creates initial `MfgProductRevision`, lab-to-pilot `MfgBom`, and analytical spec parameters in `quality`. |
| **Rapider Platform Services** | Identity/RBAC, Home `WorkItem`, `projectChannelMessage`, Files | Peer witnessing, QA 21 CFR Part 11 co-signatures, and PLM graduation approvals route via Home `WorkItem`s; raw `.csv`/`.fastq`/spectra files reside in Platform Files. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture

To comply strictly with the **Rapider Minimum 3 Items Sidebar Rule**, all visible pages are organized into **3 sidebar sections (`Overview`, `Registry & Sample Lineage`, `Assays, Compliance & Transfer`) containing 3 visible items each (9 visible menu items total)**, while detail and drawer routes set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | R&D Lab Hub | `Overview` | `true` (Order 1) | KPI cards (`countSWR`), open ELN entries awaiting witness, active assay queue, `-80°C`/LN2 freezer capacity & excursion alerts, instrument calibration status. |
| 2 | `eln-entries` | Lab Notebook Entries | `Overview` | `true` (Order 2) | Searchable `IndElnEntry` workspace (`findSWR`), `#activeFilterTagsBar` with `Clear all`, status chips (`IN_PROGRESS`, `AWAITING_WITNESS`, `WITNESSED_LOCKED`), `ApmProject` ref. |
| 3 | `protocols` | Protocols & SOP Library | `Overview` | `true` (Order 3) | Versioned `IndLabProtocol` catalog, biosafety/GHS hazard badges, molarity/step templates, one-click **Instantiate Experiment**. |
| 4 | `entity-registry` | Molecular & Entity Registry | `Registry & Sample Lineage` | `true` (Order 4) | Canonical `IndResearchEntity` table (`BIOLOGIC_SEQUENCE`, `CELL_LINE`, `SMALL_MOLECULE`, `FORMULATION`), unique `REG-*` IDs, sequence/SMILES hash & lineage count. |
| 5 | `sample-containers` | Samples, Vials & Plates | `Registry & Sample Lineage` | `true` (Order 5) | Barcoded `IndLabSampleContainer` ledger (`Decimal128` volume/conc), box/well coordinates, `freezeThawCycles` warning chips, Biosafety Officer `<rapider-phone-input>`. |
| 6 | `freezer-storage` | Freezers, Racks & Boxes | `Registry & Sample Lineage` | `true` (Order 6) | `IndStorageHierarchy` tree + interactive `9x9` / `10x10` / `96-well` visual occupancy grid, temperature class (`-80C`, `LN2`), emergency safety contact. |
| 7 | `assay-runs-board` | Assay Queue & Results | `Assays, Compliance & Transfer` | `true` (Order 7) | `<rapider-kanban>` core-facility assay workflow (`REQUESTED`, `SAMPLES_RECEIVED`, `IN_ASSAY_RUN`, `DATA_QC`, `PUBLISHED_TO_ELN`) + `IndAssayResultRun` SAR metrics. |
| 8 | `part11-signatures` | 21 CFR Part 11 Witnessing | `Assays, Compliance & Transfer` | `true` (Order 8) | Immutable `IndNotebookSignature` & SHA-256 lock register, pending witness queue, post-lock signed addenda log, IND/patent dossier export. |
| 9 | `sar-tech-transfer` | SAR Matrix & PLM Transfer | `Assays, Compliance & Transfer` | `true` (Order 9) | Candidate potency/purity/stability comparison matrix across light/dark themes plus guarded graduation handoff to `MfgProductRevision` & `MfgBom`. |
| 10 | `eln-entry-detail` | Experiment Workspace | *(Hidden)* | `false` | Full `IndElnEntry` view (`?id=...`), protocol steps, stoichiometry table, consumed `IndLabSampleContainer`s, `IndAssayResultRun`s, 21 CFR Part 11 sign/lock bar, AI review (`projectChannelMessage`), `Back to list`. |
| 11 | `entity-detail` | Registered Entity 360 | *(Hidden)* | `false` | `IndResearchEntity` dossier (`?id=...`), sequence/SMILES structure, parent/child lineage graph, active freezer aliquots, all citing ELN entries & assay runs, `Back to list`. |
| 12 | `entity-drawer` | Register Scientific Entity | *(Hidden)* | `false` | Sliding drawer validating canonical sequence/SMILES uniqueness, BSL/GHS safety flags, parent lineage, `finally` save reset & `closePageDrawer()`. |
| 13 | `witness-sign-drawer` | Sign / Witness Entry (Part 11) | *(Hidden)* | `false` | Sliding drawer capturing 21 CFR Part 11 signature meaning, `reasonForChange` (if addendum), witness `<rapider-phone-input>` MFA contact, enforcing `witness != author`. |

### Mandatory Rapider UI Standards Enforced Across All Pages
- **SWR-First Clean Reads:** Initial loads invoke `window.rapiderApi.findSWR` / `countSWR` with zero manual `isDeleted` filter clauses in API payloads and filter `item.isDeleted !== true` in memory.
- **Table Actions & Row Navigation:** Clicking primary identifiers (Entry Number/Title, Registry ID `REG-*`, Container Barcode, Assay Run Code, Protocol Code) navigates to detail views (`font-semibold text-primary hover:underline cursor-pointer`). **Zero standalone "View" buttons** appear in `Actions`; rows render icon+text **Edit** (disabled/hidden on `WITNESSED_LOCKED` immutable records in favor of **Add Addendum**) and icon-only **Delete** (`title="Delete" aria-label="Delete"`).
- **Custom Elements & Contrast:** Biosafety officer / freezer-alarm emergency contacts use `<rapider-phone-input>`, `#/assay-runs-board` uses `<rapider-kanban>`, all primary/danger buttons enforce `#ffffff !important` white text, and native browser `alert`/`confirm`/`prompt` are banned.

---

## 4. Canonical Data Models (`Ind*` — 7 Models)

All models belong to the `IND` domain (`Ind*` prefix), omit `projectId`, assign platform UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in deterministic seeds), store scientific/stoichiometric quantities as `Decimal128`, and track concurrency via `version`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`IndLabProtocol`** | `id: UUID`, `protocolCode: String`, `title: String`, `versionNumber: Int`, `domainType: Enum(MOLECULAR_BIO, SYNTHETIC_CHEM, ANALYTICAL_QC, FORMULATION, MATERIALS)`, `biosafetyLevel: Enum(BSL_1, BSL_2, BSL_3, BSL_4, CHEM_FUME_HOOD)`, `ghsHazardCodes: String[]`, `stepsSchemaJson: JSON`, `status: Enum(DRAFT, APPROVED_ACTIVE, SUPERSEDED, ARCHIVED)`, `version: Int` | `approvedByUserId -> User.id?` | Unique `(protocolCode, versionNumber)`; once `APPROVED_ACTIVE`, edits create `versionNumber + 1` so historical `IndElnEntry` runs retain their exact executed protocol snapshot. |
| **`IndResearchEntity`** | `id: UUID`, `registryId: String`, `name: String`, `entityClass: Enum(PLASMID_DNA, OLIGO_CRISPR, PROTEIN_ANTIBODY, CELL_LINE, SMALL_MOLECULE, POLYMER_MATERIAL, FORMULATION_RECIPE)`, `canonicalSequenceOrSmiles: String`, `structureHashSha256: String`, `molecularWeightDa: Decimal128?`, `extinctionCoefficient: Decimal128?`, `biosafetyLevel: String`, `confidentialityTier: Enum(STANDARD_RD, STEALTH_RESTRICTED)`, `lifecycleStage: Enum(DISCOVERY, LEAD_OPTIMIZATION, PRECLINICAL_PILOT, GRADUATED_TO_PLM, ARCHIVED)`, `version: Int` | `parentEntityIds: UUID[]`, `originElnEntryId -> IndElnEntry.id?`, `graduatedProductRevisionId -> MfgProductRevision.id?`, `graduatedBomId -> MfgBom.id?` | Unique `registryId` and unique `(entityClass, structureHashSha256)` preventing duplicate registration of identical canonical sequences/structures. |
| **`IndElnEntry`** | `id: UUID`, `entryNumber: String`, `title: String`, `confidentialityTier: Enum(STANDARD_RD, STEALTH_RESTRICTED)`, `regulatedMode: Enum(EXPLORATORY_NON_GXP, PATENT_WITNESSED, GLP_GXP_21CFR11)`, `hypothesisAndNotesMd: String`, `stoichiometryTableJson: JSON?`, `protocolDeviationsJson: JSON`, `referencedEntityIds: UUID[]`, `consumedSampleJson: JSON`, `contentSha256Digest: String?`, `addendaJson: JSON`, `status: Enum(IN_PROGRESS, AWAITING_WITNESS, REJECTED_NEEDS_REVISION, WITNESSED_LOCKED)`, `lockedAt: DateTime?`, `version: Int` | `studyProjectId -> ApmProject.id`, `protocolId -> IndLabProtocol.id?`, `authorUserId -> User.id`, `instrumentAssetIds: UUID[]`, `witnessWorkItemId -> WorkItem.id?` | Hard 21 CFR Part 11 invariant: once `status == WITNESSED_LOCKED`, `hypothesisAndNotesMd`, `stoichiometryTableJson`, and `consumedSampleJson` are permanently immutable; post-lock updates append to `addendaJson` with mandatory `reasonForChange` + new `IndNotebookSignature`. |
| **`IndStorageHierarchy`** | `id: UUID`, `locationCode: String`, `name: String`, `levelType: Enum(LAB_ROOM, ULT_FREEZER_MINUS80, LN2_DEWAR, FREEZER_MINUS20, FRIDGE_4C, AMBIENT_CABINET, RACK, CRYOBOX_GRID)`, `targetTempC: Decimal128`, `gridRows: Int?`, `gridCols: Int?`, `occupiedSlots: Int`, `emergencyContactPhone: String (E.164)?`, `status: Enum(NORMAL, TEMP_EXCURSION_HOLD, DECOMMISSIONED)`, `version: Int` | `parentStorageId -> IndStorageHierarchy.id?`, `freezerAssetId -> OpsOperationsAsset.id?` | Acyclic `parentStorageId`; `TEMP_EXCURSION_HOLD` flags all child `IndLabSampleContainer`s for QC check before assay use. |
| **`IndLabSampleContainer`** | `id: UUID`, `barcode: String`, `containerType: Enum(CRYOVIAL, MICROTUBE, WELL_PLATE_96, WELL_PLATE_384, REAGENT_BOTTLE)`, `lotNumber: String`, `gridPosition: String?`, `remainingQuantity: Decimal128`, `quantityUnit: Enum(UL, ML, MG, G)`, `concentrationValue: Decimal128?`, `concentrationUnit: String?`, `freezeThawCycles: Int`, `maxAllowedFreezeThaw: Int`, `expiresAt: Date?`, `status: Enum(AVAILABLE, CHECKED_OUT, DEPLETED, EXPIRED_QUARANTINE, DISPOSED)`, `version: Int` | `researchEntityId -> IndResearchEntity.id?`, `stockInventoryItemId -> OpsInventoryItem.id?`, `storageLocationId -> IndStorageHierarchy.id`, `parentContainerId -> IndLabSampleContainer.id?` | Unique `barcode` and unique `(storageLocationId, gridPosition)` for active containers; `remainingQuantity >= 0`; if `freezeThawCycles > maxAllowedFreezeThaw` or `expiresAt < today`, flips to `EXPIRED_QUARANTINE`. |
| **`IndAssayResultRun`** | `id: UUID`, `runNumber: String`, `assayType: String`, `workflowStage: Enum(REQUESTED, SAMPLES_RECEIVED, IN_ASSAY_RUN, DATA_QC, PUBLISHED_TO_ELN)`, `primaryMetricName: String`, `primaryMetricValue: Decimal128?`, `primaryMetricUnit: String?`, `purityOrPassPct: Decimal128?`, `structuredRowsJson: JSON`, `rawInstrumentFileId: UUID?`, `rawFileSha256: String?`, `qcPassed: Boolean`, `version: Int` | `elnEntryId -> IndElnEntry.id`, `studyProjectId -> ApmProject.id`, `testedEntityIds: UUID[]`, `testedContainerIds: UUID[]`, `instrumentAssetId -> OpsOperationsAsset.id?` | Publishing (`PUBLISHED_TO_ELN`) under `GLP_GXP_21CFR11` fails if `instrumentAssetId` has an active calibration-overdue lock in `assets`/`maintenance`. |
| **`IndNotebookSignature`** | `id: UUID`, `signatureNumber: String`, `signatureRole: Enum(AUTHOR_SUBMIT, PEER_IP_WITNESS, QA_GXP_APPROVER, ADDENDUM_AUTHOR)`, `meaningStatement: String`, `reasonForChange: String?`, `signedByUserNameSnapshot: String`, `signerContactPhone: String (E.164)?`, `signedAt: DateTime`, `entryDigestAtSignSha256: String`, `version: Int` | `elnEntryId -> IndElnEntry.id`, `signedByUserId -> User.id` | Append-only immutable per 21 CFR 11.50 / 11.70; `PEER_IP_WITNESS` and `QA_GXP_APPROVER` enforce `signedByUserId != IndElnEntry.authorUserId`. |

---

## 5. Core End-to-End User Journeys

### Journey 1: Molecular Entity Registration with Duplicate-Sequence Guardrail & Aliquot Creation
1. Protein Engineer opens `#/entity-registry`, clicks **Register Entity** (`entity-drawer`), and submits humanized antibody construct `mAb-HER2-v4` (`PROTEIN_ANTIBODY`) derived from parental plasmid `REG-PLAS-0088`.
2. `ind.eln.registerEntity` computes canonical `structureHashSha256`, verifies zero duplicate construct exists (blocking accidental re-registration if already registered), assigns `REG-PROT-00419`, and preserves parent lineage.
3. The scientist creates 5 barcoded `CRYOVIAL` aliquots (`SMP-2026-8801`..`8805`, `500.00 uL` at `2.50 mg/mL`, `maxAllowedFreezeThaw = 3`) in `-80°C Freezer-02 -> Rack-B -> Box-04` (`A01`–`A05`).

### Journey 2: Regulated ELN Execution, Sample Drawdown & Instrument Calibration Gate
1. Analytical Scientist instantiates `IndLabProtocol` `SOP-SEC-HPLC-v3` into `IndElnEntry` (`ELN-2026-1104`, `GLP_GXP_21CFR11`) linked to `ApmProject` `PRJ-ONCO-2026`.
2. Checking out `SMP-2026-8801` deducts `50.00 uL` (`remainingQuantity = 450.00 uL`) and increments `freezeThawCycles` (`0 -> 1`).
3. On `#/assay-runs-board` (`<rapider-kanban>`), if selected HPLC `OpsOperationsAsset` `AST-HPLC-01` has an open overdue calibration `MfgMaintenanceWorkOrder`, publishing the run is blocked; selecting calibrated `AST-HPLC-02` parses the chromatogram CSV (`purityOrPassPct = 99.15%`, `Kd = 1.85 nM`) and attaches raw file + SHA-256 hash.

### Journey 3: FDA 21 CFR Part 11 Author Sign + Independent Peer Witness Lock via Home `WorkItem`
1. Author clicks **Submit & Sign** (`witness-sign-drawer`) on `ELN-2026-1104`, recording `AUTHOR_SUBMIT` (`"I attest I conducted this experiment and recorded raw observations contemporaneously"`), transitioning the entry to `AWAITING_WITNESS` and creating a Rapider Home `WorkItem` for Principal Scientist `Dr. Aris Thorne`.
2. If the Author attempts to co-sign as `PEER_IP_WITNESS`, `ind.eln.countersignEntry` deterministically rejects self-witnessing (`signedByUserId == authorUserId`).
3. `Dr. Thorne` reviews the AI protocol-deviation check in `projectChannelMessage`, verifies raw data, and signs `PEER_IP_WITNESS` -> `ELN-2026-1104` stamps `contentSha256Digest` and locks (`WITNESSED_LOCKED`). Subsequent direct edits are rejected; adding a minor note invokes `appendSignedAddendum` with mandatory `reasonForChange`.

### Journey 4: Lead Candidate Graduation to Canonical `plm`, `bom` & `quality`
1. On `#/sar-tech-transfer`, `REG-PROT-00419` leads all candidates across potency (`1.85 nM`) and purity (`99.15%`).
2. R&D Director triggers **Graduate to PLM Tech Transfer**, publishing a Home `WorkItem` co-approved by QA; upon approval, `candidateTechTransferWorkflow` creates canonical `MfgProductRevision`, formulation `MfgBom`, and analytical release specification template in `quality` while stamping `lifecycleStage = GRADUATED_TO_PLM`.

### Journey 5: Record Click-Through Navigation (`Entity Registry -> Entity 360 -> Back Restoration`)
1. From `#/entity-registry` filtered to `Entity Class: "PROTEIN_ANTIBODY"` and `Search: "HER2"`, the Scientist clicks `REG-PROT-00419`.
2. Router navigates cleanly to `#/entity-detail?id=00000000-0192-0000-0000-000000000419` without `<base href>` 404 diversion, rendering amino-acid sequence, parent plasmid `REG-PLAS-0088`, 5 freezer vials, and witnessed `ELN-2026-1104`.
3. Clicking `Back to list` (`#btnGoBack`) returns to `#/entity-registry` with `Entity Class: "PROTEIN_ANTIBODY"` and `Search: "HER2"` preserved in `#activeFilterTagsBar`.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation Work Packages (Must-Have for Initial Release)
- **WP-P0-1 — Structured ELN & Versioned SOP Protocols (`ELN-001`, `ELN-002`):** Deliver `IndElnEntry` (`ApmProject` link, inline `@`-entity/sample refs, markdown + tables) and versioned `IndLabProtocol` templates.
- **WP-P0-2 — Scientific Entity Registry & Uniqueness Engine (`ELN-005`, `ELN-006`):** Build `IndResearchEntity` collision-free `REG-*` IDs and SHA-256 canonical sequence/SMILES duplicate prevention.
- **WP-P0-3 — Freezer Storage Hierarchy, Sample Aliquots & Assay Runs (`ELN-009`, `ELN-010`, `ELN-011`, `ELN-012`):** Deliver `IndStorageHierarchy` visual box grids (with `<rapider-phone-input>` emergency contacts), `IndLabSampleContainer` `Decimal128` drawdowns + `freezeThawCycles`, and `IndAssayResultRun` CSV/instrument result ingestion.
- **WP-P0-4 — 21 CFR Part 11 Dual Signatures, SHA-256 Lock & Addenda (`ELN-014`, `ELN-015`):** Build `IndNotebookSignature` (`witness != author` via Home `WorkItem`), cryptographic entry lock, and `reasonForChange` signed addenda.

### `P1` Enterprise Scale Work Packages
- **WP-P1-1 — Stoichiometry, Instrument Calibration Gates, Lineage & Safety (`ELN-003`, `ELN-004`, `ELN-007`, `ELN-008`, `ELN-018`):** Add `Decimal128` molar/dilution calculators, `OpsOperationsAsset`/`MfgMaintenanceWorkOrder` GLP calibration blocks, parent-child entity graphs, BSL/GHS safety banners, and max freeze-thaw quarantines.
- **WP-P1-2 — Assay Queue Kanban, SAR Matrix, Dossier Export & PLM Tech Transfer (`ELN-013`, `ELN-016`, `ELN-017`, `ELN-019`):** Build `<rapider-kanban>` core-lab assay queue, SAR candidate comparison matrices, IND/patent dossier exports, and guarded graduation into `MfgProductRevision`/`MfgBom`/`MfgQualityInspection`.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1 — Stealth ACLs, AI Deviation Review, Schema Mapper & Registry Copilot (`ELN-020`, `ELN-021`, `ELN-022`, `ELN-023`, `ELN-024`):** Deliver `STEALTH_RESTRICTED` pre-patent program isolation, grounded AI witness pre-review briefs in `projectChannelMessage`, AI CSV-to-assay parser mapping, `OpsInventoryItem` reorder signals, and natural-language sequence/potency copilot queries.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Bench Scientist / Researcher** | Author `IndElnEntry`s in assigned `ApmProject`s, register `IndResearchEntity` constructs, aliquot/draw down `IndLabSampleContainer`s, sign `AUTHOR_SUBMIT`, peer-witness *colleagues'* entries. | Cannot peer-witness own `IndElnEntry` (`witness != author`), edit `WITNESSED_LOCKED` entries in place, or view `STEALTH_RESTRICTED` programs outside roster. |
| **Core Facility / Analytical Analyst** | Advance `<rapider-kanban>` `IndAssayResultRun`s, upload/parse raw instrument outputs, verify `OpsOperationsAsset` calibration readiness. | Cannot unlock witnessed ELN entries or approve PLM tech-transfer graduations. |
| **Principal Investigator / Lab Lead** | Approve `IndLabProtocol` versions, complete `PEER_IP_WITNESS` Home `WorkItem`s, nominate lead candidates for PLM tech transfer. | Cannot delete audit trails or alter SHA-256 digests on locked entries. |
| **QA / GxP Compliance Officer** | Co-sign `QA_GXP_APPROVER` on regulated `GLP_GXP_21CFR11` entries, audit full 21 CFR 11.10(e) change histories, co-approve PLM graduation `WorkItem`s, export IND/patent dossiers. | Read-only on experimental prose (cannot fabricate or edit raw scientific results). |
| **Lab Operations / Biosafety Officer** | Manage `IndStorageHierarchy` freezers, place excursion/expired `IndLabSampleContainer`s on quarantine hold, oversee BSL/GHS safety flags. | Cannot sign scientific authorship or witness IP claims without study access. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every mutating command enforces `idempotencyKey`, `correlationId`, and `expectedVersion`:
- `ind.eln.registerEntity` — Canonicalizes sequence/SMILES, checks `(entityClass, structureHashSha256)` uniqueness, and assigns gapless `REG-*` identifier.
- `ind.eln.consumeOrAliquotSample` — Deducts `Decimal128` `remainingQuantity`, increments `freezeThawCycles`, quarantines vials exceeding `maxAllowedFreezeThaw`, and spawns child aliquot barcodes.
- `ind.eln.countersignAndLockEntry` — Validates re-authenticated signature meaning, enforces `signedByUserId != authorUserId` for `PEER_IP_WITNESS`/`QA_GXP_APPROVER`, computes `contentSha256Digest`, and locks `IndElnEntry` (`WITNESSED_LOCKED`).
- `ind.eln.graduateCandidateToPlm` — Verifies QA/PI Home `WorkItem` approval and locked supporting assay runs before emitting tech-transfer commands to `plm`, `bom`, and `quality`.

### 8.2 Domain Events Published & Consumed (Kafka)
- **Published:** `ind.eln.entityRegistered.v1`, `ind.eln.entryWitnessedLocked.v1`, `ind.eln.sampleQuarantined.v1`, `ind.eln.candidateGraduatedToPlm.v1`.
- **Consumed:** `mfg.maintenance.workOrderOpened.v1` / `Completed.v1` (toggles `OpsOperationsAsset` lab instrument calibration availability), `apm.project.archived.v1`.

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `part11WitnessingAndLockWorkflow` — Routes `AWAITING_WITNESS` entries via Home `WorkItem`s, enforces `author != witness`, stamps SHA-256 digests, and governs signed post-lock addenda.
2. `sampleLineageAndFreezeThawGuardWorkflow` — Tracks aliquot genealogy, freezer excursion holds, shelf-life expirations, and `OpsInventoryItem` stockroom par alerts.
3. `instrumentAssayParsingAndQcWorkflow` — Normalizes uploaded CSV/ASM instrument files into `IndAssayResultRun` rows while verifying `OpsOperationsAsset` calibration status.
4. `candidatePlmTechTransferWorkflow` — Translates graduated `IndResearchEntity` formulations and release specs into canonical `MfgProductRevision`, `MfgBom`, and `MfgQualityInspection` records.

### 8.4 Grounded Rapider AI Rules
- AI Protocol Deviation Reviews (`ELN-021`), CSV Schema Mappers (`ELN-022`), and Registry Copilot answers (`ELN-024`) MUST cite exact `IndElnEntry`, `IndResearchEntity`, `IndAssayResultRun`, and `IndLabSampleContainer` IDs.
- AI MUST strictly respect `STEALTH_RESTRICTED` program ACLs, MUST NEVER fabricate experimental assay values or stoichiometry yields, and MUST NEVER execute a 21 CFR Part 11 signature on behalf of a human scientist.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **FDA 21 CFR Part 11, EU GMP Annex 11, OECD GLP & Patent Priority Integrity:** Time-stamped computer-generated audit trails (`11.10(e)`) capture previous/new values, actor, UTC timestamp, and `reasonForChange`; electronic signature manifestations (`11.50`) print signer full name, UTC date/time, and signature meaning (`Authored`, `Witnessed`, `QA Approved`) bound cryptographically (`11.70`) via SHA-256 digest; records retain immutably for 15–30+ years (patent life + regulatory retention).
- **Pre-Patent Trade-Secret Protection & Zero PHI Boundary:** `STEALTH_RESTRICTED` encryption and query isolation protect pre-filing chemical structures and biological sequences; zero clinical patient PII/PHI is stored (strictly delegated to `#157`).
- **Exact `Decimal128` Scientific Precision:** Microliter sample volumes (`0.2500 uL`), nanomolar affinities (`1.8500 nM`), molecular weights (`148,210.45 Da`), and reaction yields (`99.15%`) never use floating-point numbers.
- **Accessibility & Lab Bench UX:** Full WCAG 2.2 AA compliance (`#ffffff !important` contrast on primary/danger buttons across light and dark modes, glove-friendly tap targets, ARIA labels on icon-only Delete buttons) across `390px` freezer-room barcode smartphones, `768px` fume-hood iPads, and `1440px` bioinformatics/chemistry workstations.

---

## 10. Deterministic Acceptance Criteria

1. **Sidebar 3-Item Section Rule:** `app.manifest.json` defines 3 visible sidebar sections (`Overview`, `Registry & Sample Lineage`, `Assays, Compliance & Transfer`) with 3 visible items each (`displayOnMenu: true`) and 4 hidden detail/drawer routes (`displayOnMenu: false`).
2. **SWR & Soft-Delete Cleanliness:** Every page load uses `findSWR` / `countSWR` without manual `isDeleted` API query filters and defensively filters `item.isDeleted !== true` in memory.
3. **Active Filter Tags & Clear All:** Filtering `#/eln-entries`, `#/entity-registry`, or `#/assay-runs-board` renders `#activeFilterTagsBar` with HTML-escaped dismissible chips and `[Clear all]`, synchronously updating both table and `<rapider-kanban>` views.
4. **Table Action Standard:** Zero standalone "View" buttons exist in `Actions`; Entry Numbers, `REG-*` IDs, Container Barcodes, Run Numbers, and Protocol Codes navigate to detail routes, Edit buttons render icon + text (replaced by **Add Addendum** on `WITNESSED_LOCKED` entries), and Delete buttons render icon-only with `title="Delete"` and `aria-label="Delete"`.
5. **Custom Elements Adoption:** Biosafety/freezer-alarm and witness MFA phone inputs use `<rapider-phone-input>`, and `#/assay-runs-board` uses `<rapider-kanban>`.
6. **Optimistic Lifecycle & Native Dialog Ban:** Saving `entity-drawer` or `witness-sign-drawer` resets button state in `finally`, calls `closePageDrawer()`, clears SWR cache, and updates parent views optimistically; deletions use `#rapiderConfirmOkBtn` with zero `window.alert`/`confirm`/`prompt`.
7. **21 CFR Part 11 Witness Separation & Immutability Lock:** Attempting `ind.eln.countersignAndLockEntry` (`PEER_IP_WITNESS`) where `signedByUserId == authorUserId` fails deterministically; once `WITNESSED_LOCKED`, in-place edits to `IndElnEntry` body/tables are rejected and post-lock addenda require non-empty `reasonForChange`.
8. **Duplicate Sequence / Structure Prevention:** Registering a new `IndResearchEntity` whose canonicalized sequence or SMILES `structureHashSha256` already exists in the same `entityClass` fails deterministically and surfaces the existing `REG-*` entity.
9. **Sample Freeze-Thaw & Grid Collision Guard (`Decimal128`):** Placing two active `IndLabSampleContainer`s into the same `(storageLocationId, gridPosition)` is rejected, deducting sample volume uses exact `Decimal128` math, and exceeding `maxAllowedFreezeThaw` flips status to `EXPIRED_QUARANTINE`.
10. **GLP Uncalibrated Instrument Block:** Publishing a `GLP_GXP_21CFR11` `IndAssayResultRun` linked to an `OpsOperationsAsset` with an overdue calibration `MfgMaintenanceWorkOrder` is deterministically blocked.
11. **Click-Through Navigation & State Restoration:** Clicking an entity on `#/entity-registry` transitions to `#/entity-detail?id=...` without `<base href>` 404 diversion, renders lineage, aliquots, and ELN citations, and `Back to list` restores prior filter tags.
12. **Canonical Suite Reuse & Zero `projectId`:** Zero `Ind*` models define `projectId`, and R&D projects, lab instruments, stockroom items, and graduated manufacturing specs reuse `ApmProject`, `OpsOperationsAsset`/`MfgMaintenanceWorkOrder`, `OpsInventoryItem`, and `MfgProductRevision`/`MfgBom`/`MfgQualityInspection`.
