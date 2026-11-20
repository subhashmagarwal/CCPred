======================================================
                                    CCPred
    Machine Learning-Based Prediction of Compounds Against Cervical Cancer
                                 User Manual
================================================================

1. INTRODUCTION & OVERVIEW
--------------------------------------------------------------------------------
CCPred is a freely available, standalone computational screening suite designed
for drug discovery and academic research. It enables researchers to screen
chemical candidate molecules for potential inhibitory activity against three
major human cervical cancer cell lines:
  - HeLa  
  - KB   
  - SiHa 

================================================================================
2. SYSTEM CAPABILITIES & COMPATIBILITY
================================================================================

A. STANDALONE APPLICATION (CCPred.exe):
----------------------------------------
  - Operating System Friendly:
      * Windows 11 (64-bit)  -> Fully Supported & Tested (Recommended)
      * Windows 10 (64-bit)  -> Fully Supported & Tested
      * Note: The .exe is built specifically for 64-bit Windows architectures (x86_64).
        It does NOT require administrative privileges to run.

  - Dependencies:
      * ZERO installation required!
      * Python, RDKit, and machine learning libraries are completely self-contained
        inside the executable.

  - Hardware Requirements:
      * Processor: Intel Core i3 / AMD Ryzen 3 or higher (64-bit)
      * RAM: Minimum 4 GB RAM (8 GB or higher recommended for screening large libraries)
      * Storage: ~500 MB free hard drive space
      * Screen Resolution: 1280x720 minimum (1920x1080 Full HD recommended)

================================================================================
3. HOW TO USE CCPRED (STEP-BY-STEP GUIDE)
================================================================================

STEP 1: LAUNCH THE APPLICATION
------------------------------
Double-click "CCPred.exe".
On first launch, Windows may take a few seconds to unpack the embedded scientific
libraries into a temporary directory. The main application window will open on your screen.


STEP 2: CHOOSE A PREDICTION MODEL (SECTION 1)
---------------------------------------------
1. Click the "Cell Line" dropdown box under "1. Choose prediction model".
2. Select your target:
   - "All Cell Lines" : Screens every compound simultaneously against HeLa, KB, and SiHa.
   - "HeLa"           : Screens compounds specifically against HeLa cells.
   - "KB"             : Screens compounds specifically against KB cells.
   - "SiHa"           : Screens compounds specifically against SiHa cells.


STEP 3: ADD MOLECULES (SECTION 2)
---------------------------------
You can supply molecules using any of the following three methods:

  A. Type or Paste SMILES:
     Directly paste SMILES notations into the text box (one SMILES string per line).
     Example:
       C1=CC=C(C=C1)C(=O)O
       CC(=O)OC1=CC=CC=C1C(=O)O

  B. Import a Text File (.txt):
     Click the "📁 Import .txt" button at the bottom of Section 2.
     Select any plain text file containing SMILES lines.

  C. Load Sample Molecules:
     Click the "🧪 Load Sample" button to load benchmark cervical anticancer compounds
     (including Cisplatin, Paclitaxel, Topotecan, and 5-Fluorouracil).

 STEP 4: RUN PREDICTIONS
-----------------------
Click the teal "⚡ Predict Activity" button.
- The button will display "⏳ Screening..." during computation.
- Predictions run asynchronously on a background thread so the interface never freezes.
- For each molecule:
    1. RDKit parses and canonicalizes the SMILES structure.
    2. A 2048-bit Morgan Fingerprint (radius 2) is calculated.
    3. The Random Forest classifier predicts biological activity.


STEP 5: REVIEW & EXPORT RESULTS (SECTION 3)
-------------------------------------------
1. Live Results Table:
   The predictions appear in the table with three clean columns:
     - MODEL      : Target cell line (HeLa, KB, or SiHa)
     - SMILES     : Molecular SMILES string
     - PREDICTION : Classification result:
         * "Active"   (highlighted in green bold font)
         * "Inactive" (highlighted in red font)
         * "Invalid"  (highlighted in amber italic font if SMILES is unparseable)

2. Export as CSV:
   Click the "📥 Export CSV Report" button at the bottom right.
   Choose a file name and save location to export a formatted CSV spreadsheet
   ready for Microsoft Excel, LibreOffice Calc, or further statistical analysis.


================================================================================
4. INPUT & OUTPUT FORMAT DETAILS
================================================================================

INPUT SPECIFICATION:
  - Input Type: 1D SMILES (Simplified Molecular Input Line Entry System)
  - Layout: One SMILES per line
  - Blank lines and whitespace are automatically ignored.

OUTPUT CSV STRUCTURE:
  - Column 1: MODEL       (e.g., HeLa, KB, SiHa)
  - Column 2: SMILES      (e.g., CC(=O)OC1=CC=CC=C1C(=O)O)
  - Column 3: PREDICTION  (Active / Inactive / Invalid SMILES)


================================================================================
5. TROUBLESHOOTING & FREQUENTLY ASKED QUESTIONS
================================================================================

Q1: Windows Defender or SmartScreen says "Windows protected your PC"?
A1: Because CCPred.exe is an academic research executable built without an expensive
    commercial enterprise digital certificate, Windows SmartScreen may show an alert.
    Click "More info" and then select "Run anyway".

Q2: What causes an "Invalid SMILES" output?
A2: If a chemical string contains syntax errors, unsupported stereochemical symbols,
    or non-chemical text, RDKit will flag it as invalid rather than crashing.
    Check the chemical structure syntax in ChemDraw or PubChem.

Q3: Can I run this without an Internet connection?
A3: Yes! CCPred is 100% offline. All machine learning models and fingerprint algorithms
    run locally on your CPU. No data is sent over the network.


================================================================================
6. DISCLAIMER
================================================================================
CCPred is an in silico research support tool intended for computational drug
screening and prioritization. Predicted activities are computational estimates
and should be validated experimentally using in vitro biological assays before
clinical or therapeutic conclusions are drawn.

================================================================================
