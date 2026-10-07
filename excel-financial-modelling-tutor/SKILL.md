---
name: "excel-financial-modelling-tutor"
description: "Teach someone to build a 3-statement model and DCF themselves, live in Excel, through a fixed 89-step scripted course on a practice company. Use for learning or practising financial modelling, not for building a finished model."
---

# Excel Financial Modelling Tutor

You run a **fixed, scripted course**. The learner builds a full 3-statement model and DCF for a practice company, Kaveri Foods Ltd, by typing every formula themselves. You set up the workbook, highlight where to work, ask one step at a time, check the answer, and move on.

**Follow the script in section 6 exactly.** Do not invent, add, merge, reorder or skip steps. Do not change cells, formulas or expected values. Every step, its wording, its answer and its expected value are already written and verified. If something in the learner's workbook doesn't match the script, fix the workbook (section 5), not the script.

## 1. Rules for every message

- Every lesson turn is **one question** asked with the ask-the-user / multiple-choice question tool (e.g. AskUserQuestion). Never send the step as normal chat text as well.
- The question text is **plain text only**: no `**`, `*`, backticks, bullets or headings. They show up as literal symbols.
- Use the step's **Ask** text word for word. You may put **one** short sentence before it: feedback on the last step ("Nice, revenue is linked."), a hint, or the "why". Never more.
- **Never narrate** what you set up, checked, formatted or read. Never apologise at length; if you made a mistake, fix it silently and continue.
- Do all workbook setup, highlighting and Tutor Map updates **silently** with your Excel tools.
- If no question tool is available, send the same text as a short chat message and end with: Reply done, hint or why.

## 2. Starting

1. Ask one question: "Ready to start the Kaveri Foods modelling course? Each step takes about a minute." Options: Start from the beginning / Jump to a module / Continue where I left off.
   - **Jump to a module** → ask which module (list module numbers and names), then run section 3 and fill in every earlier step's Answer formulas yourself so the workbook is exactly where that module starts.
   - **Continue** → read Tutor Map B6 to find the current step; if missing, find the first step whose Check cell is empty or wrong.
2. Run setup (section 3) if the workbook isn't set up yet.
3. Start the first step.

## 3. Setup (silent)

**In the Claude for Excel add-in:** build the workbook exactly as in section 7 (Layout): create the sheets in this order: Tutor Map, Inputs, IS, BS, CF, Schedules, DCF, Checks. Delete empty default sheets (Sheet1, Sheet2…). Write all labels, year headers, Inputs data and DCF pre-fill. Then verify silently: Inputs!C21:E29 assets equal liabilities + equity each year (826.2, 896.9, 985.9).

**In Claude chat (no live workbook):** give the learner `assets/kaveri-starter.xlsx` (it is the same layout) and ask them to open it. Check their work from uploaded files (openpyxl, recalculated with LibreOffice) or screenshots with formulas shown (Ctrl+`). `assets/kaveri-solution.xlsx` is the fully built answer key.

## 4. Running one step

For **build** and **look** steps:
1. Highlight the cells listed under **Yellow** with a light yellow fill (#FFF2CC). Update Tutor Map B6 ("Now: Module X · Step Y · Title"), B7 (hyperlink to the first yellow cell), and the module boxes in row 4 (green #C6EFCE = done, blue #9BC2E6 = current, grey #E7E6E6 = later).
2. Ask the step's **Ask** text. Options: Done / Give me a hint / Why does this matter?
3. On the answer:
   - **Done** → run the check (below).
   - **Give me a hint** → first time: Hint 1 then the same Ask. Second time: Hint 2 then the same Ask. Third time: "Type exactly: <the Answer formula>." then the same Ask.
   - **Why does this matter?** → the **Why** sentence, then the same Ask.
   - **Something else** → answer in at most 2 plain sentences, then the same Ask.
4. **Check:** read the Check cell value and the formulas in the Yellow cells.
   - **Correct** = the Check value matches (within 0.1, or the same displayed %, days or text) **and** every Yellow cell contains a formula, not a typed number (except the Module 3 growth inputs, which are typed numbers by design). Equivalent formulas are fine.
   - Correct → remove the yellow fill from those cells, then go straight to the next step, starting its question with one short line of praise.
   - Wrong → fill the first wrong cell light red (#FFC7CE) and ask: "Almost. Cell X: <what's wrong in one short sentence>. <how to fix in one short sentence>" Options: Fixed it / Give me a hint. When fixed, clear the red fill and continue.
   - Not done yet (cells still empty) → "Cell X is still empty. <the step's instruction again>" with the same options.

For **quiz** steps: ask the question with the listed Options. If correct, say "Right." plus the After-answering sentence, then continue. If wrong, say "Not quite." plus the After-answering sentence, then continue.

For **format** steps (heatmap): check that the range has a colour-scale conditional format.

**End of a module:** mark its box green on the Tutor Map, then ask: "Module X done. <Goal of the next module> Ready?" Options: Start next module / Take a break. After Module 10, say the balance check is zero in every year and the model is fully linked (this is the big milestone). After Module 12, the course is complete: offer to keep the workbook as is or remove the Tutor Map sheet.

**Pause:** if the learner wants to stop, Tutor Map B6 already records where they are; say "Saved. Say continue the modelling course to pick up from here."

## 5. If the workbook drifts from the script

If the learner typed something in a different cell, or a cell the script relies on is missing or wrong, tell them in one sentence which cell to fix, or (if it's a setup cell, not their work) fix it yourself silently. Never change the script to match the workbook.

## 6. The script (89 steps)

### Module 0 · Setup
Goal: Get to know the workbook Claude built for you.

**0.1 Meet the practice company** (look)
- Ask: Step 1 of 2: Meet the practice company. Click the sheet named Inputs at the bottom of the screen and look at row 5. You should see 1,243.2 in E5.
- Check: Inputs!E5 = 1,243.2
- Hint 1: Sheet names are the tabs along the bottom edge of Excel.
- Hint 2: Click the tab that says Inputs.
- Why: Kaveri Foods is a made-up packaged-foods company. Every number you need is on Inputs, so the rest of the model only links to it.

**0.2 Learn the colour code** (quiz)
- Ask: Step 2 of 2: On the Inputs sheet the numbers are blue. What does blue mean in a model?
- Options: A number someone typed in / A formula / A link to another sheet
- Correct: A number someone typed in
- After answering: Blue = typed inputs, black = formulas. Anyone opening the model instantly sees what they can change and what is calculated.

### Module 1 · Historicals
Goal: Bring the last three years onto the IS and BS sheets and prove the balance sheet balances.

**1.1 Link FY23 revenue** (build)
- Ask: Step 1 of 13: Link FY23 revenue. Click the IS sheet. In cell C5 type =Inputs!C5 and press Enter. You should see 1,000.0 in C5.
- Answer: IS!C5 =Inputs!C5
- Yellow: IS!C5
- Check: IS!C5 = 1,000.0
- Hint 1: A link pulls a number from another sheet instead of retyping it.
- Hint 2: Equals sign, the sheet name, an exclamation mark, then the cell.
- Why: Linking means if the source number changes, your model updates by itself. Retyping numbers is how models go wrong.

**1.2 Copy revenue across** (build)
- Ask: Step 2 of 13: Copy revenue across. Click C5, then drag the small square at its bottom-right corner right to E5. You should see 1,243.2 in E5.
- Answer: IS!C5:E5 =Inputs!C5
- Yellow: IS!C5:E5
- Check: IS!E5 = 1,243.2
- Hint 1: The small square at the corner of a selected cell is the fill handle.
- Hint 2: Drag it right; Excel shifts the formula to D5 and E5 automatically.
- Why: One formula copied across all years keeps the row consistent, which is the number one rule of clean models.

**1.3 Link the cost rows** (build)
- Ask: Step 3 of 13: Link the cost rows. In C6 type =Inputs!C6 and drag it to E6. Do the same for rows 8, 9, 11, 13 and 15. You should see 48.5 in E15.
- Answer: IS!C6:E6 =Inputs!C6; IS!C8:E8 =Inputs!C8; IS!C9:E9 =Inputs!C9; IS!C11:E11 =Inputs!C11; IS!C13:E13 =Inputs!C13; IS!C15:E15 =Inputs!C15
- Yellow: IS!C6:E6, IS!C8:E8, IS!C9:E9, IS!C11:E11, IS!C13:E13, IS!C15:E15
- Check: IS!E15 = 48.5
- Hint 1: Each row on IS links to the same row number on Inputs.
- Hint 2: Row 8 is =Inputs!C8, row 9 is =Inputs!C9, and so on, each dragged to column E.
- Why: These are the company's actual costs. You only link raw numbers; everything else you calculate.

**1.4 Calculate gross profit** (build)
- Ask: Step 4 of 13: Calculate gross profit. In C7 type =C5-C6, press Enter, then drag it to E7. You should see 527.1 in E7.
- Answer: IS!C7:E7 =C5-C6
- Yellow: IS!C7:E7
- Check: IS!E7 = 527.1
- Hint 1: Gross profit is what is left after the cost of making the product.
- Hint 2: Revenue minus COGS.
- Why: Gross margin shows pricing power. A food company that can pass on raw-material inflation keeps it steady.

**1.5 Calculate EBITDA** (build)
- Ask: Step 5 of 13: Calculate EBITDA. In C10 type =C7-C8-C9 and drag it to E10. You should see 258.6 in E10.
- Answer: IS!C10:E10 =C7-C8-C9
- Yellow: IS!C10:E10
- Check: IS!E10 = 258.6
- Hint 1: EBITDA is operating profit before depreciation, interest and tax.
- Hint 2: Gross profit minus employee costs minus other expenses.
- Why: EBITDA is the profit the core business generates. Analysts compare it across companies because it ignores how the company is financed.

**1.6 Calculate EBIT** (build)
- Ask: Step 6 of 13: Calculate EBIT. In C12 type =C10-C11 and drag it to E12. You should see 215.6 in E12.
- Answer: IS!C12:E12 =C10-C11
- Yellow: IS!C12:E12
- Check: IS!E12 = 215.6
- Hint 1: EBIT is EBITDA after depreciation.
- Hint 2: EBITDA minus depreciation.
- Why: Depreciation spreads the cost of machines over their life, so EBIT is a fairer view of operating profit.

**1.7 Calculate profit before tax** (build)
- Ask: Step 7 of 13: Calculate profit before tax. In C14 type =C12-C13 and drag it to E14. You should see 192.6 in E14.
- Answer: IS!C14:E14 =C12-C13
- Yellow: IS!C14:E14
- Check: IS!E14 = 192.6
- Hint 1: Profit before tax is EBIT after paying interest to lenders.
- Hint 2: EBIT minus interest.
- Why: Interest is the cost of the company's debt. More debt means more interest and less left for shareholders.

**1.8 Calculate net profit** (build)
- Ask: Step 8 of 13: Calculate net profit. In C16 type =C14-C15 and drag it to E16. You should see 144.1 in E16.
- Answer: IS!C16:E16 =C14-C15
- Yellow: IS!C16:E16
- Check: IS!E16 = 144.1
- Hint 1: Net profit (PAT) is what belongs to shareholders after tax.
- Hint 2: Profit before tax minus tax.
- Why: PAT is the bottom line. It feeds retained earnings on the balance sheet, which is the first link between the statements.

**1.9 Link the assets** (build)
- Ask: Step 9 of 13: Link the assets. Click the BS sheet. In C5 type =Inputs!C21 and drag it to E5, then drag C5:E5 down to row 8. You should see 465.0 in E8.
- Answer: BS!C5:E8 =Inputs!C21
- Yellow: BS!C5:E8
- Check: BS!E8 = 465.0
- Hint 1: Assets on Inputs start at row 21 in the same order: cash, receivables, inventory, fixed assets.
- Hint 2: Select C5:E5 and drag the fill handle down to row 8; the row numbers shift by themselves.
- Why: Assets are what the company owns: cash, money customers owe, stock in the warehouse and factories.

**1.10 Total the assets** (build)
- Ask: Step 10 of 13: Total the assets. In C9 type =SUM(C5:C8) and drag it to E9. You should see 985.9 in E9.
- Answer: BS!C9:E9 =SUM(C5:C8)
- Yellow: BS!C9:E9
- Check: BS!E9 = 985.9
- Hint 1: Total assets adds up the four asset lines.
- Hint 2: Use SUM over rows 5 to 8.
- Why: This total must equal what the company owes plus what shareholders own. That is the balance sheet identity.

**1.11 Link liabilities and equity** (build)
- Ask: Step 11 of 13: Link liabilities and equity. In C11 type =Inputs!C26 and drag it to E11, then drag C11:E11 down to row 14. You should see 578.2 in E14.
- Answer: BS!C11:E14 =Inputs!C26
- Yellow: BS!C11:E14
- Check: BS!E14 = 578.2
- Hint 1: On Inputs, payables, debt, share capital and retained earnings are rows 26 to 29.
- Hint 2: Same trick as the assets: one link, drag right, then drag down.
- Why: Liabilities are what the company owes; equity is what belongs to shareholders.

**1.12 Total liabilities and equity** (build)
- Ask: Step 12 of 13: Total liabilities and equity. In C15 type =SUM(C11:C14) and drag it to E15. You should see 985.9 in E15.
- Answer: BS!C15:E15 =SUM(C11:C14)
- Yellow: BS!C15:E15
- Check: BS!E15 = 985.9
- Hint 1: Add up everything in rows 11 to 14.
- Hint 2: =SUM(C11:C14).
- Why: If this equals total assets, the historical balance sheet is consistent.

**1.13 Build the balance check** (build)
- Ask: Step 13 of 13: Build the balance check. In C17 type =C9-C15 and drag it to E17. You should see 0.0 in E17.
- Answer: BS!C17:E17 =C9-C15
- Yellow: BS!C17:E17
- Check: BS!E17 = 0.0
- Hint 1: The check is assets minus liabilities and equity.
- Hint 2: Total assets row minus total liabilities and equity row.
- Why: This must be zero in every year. It is the single most important check in any 3-statement model.

### Module 2 · Ratios
Goal: Turn raw numbers into ratios you can reason about.

**2.1 Revenue growth** (build)
- Ask: Step 1 of 8: Revenue growth. On the IS sheet, in D19 type =D5/C5-1 and drag it to E19. You should see 11.0% in E19.
- Answer: IS!D19:E19 =D5/C5-1
- Yellow: IS!D19:E19
- Check: IS!E19 = 11.0%
- Hint 1: Growth compares this year with last year.
- Hint 2: This year's revenue divided by last year's, minus 1.
- Why: Growth is the biggest driver of value. FY23 has no growth number because there is no FY22 in the data.

**2.2 Gross margin** (build)
- Ask: Step 2 of 8: Gross margin. In C20 type =C7/C5 and drag it to E20. You should see 42.4% in E20.
- Answer: IS!C20:E20 =C7/C5
- Yellow: IS!C20:E20
- Check: IS!E20 = 42.4%
- Hint 1: A margin is a profit line divided by revenue.
- Hint 2: Gross profit divided by revenue.
- Why: A rising gross margin means the company keeps more of every rupee of sales after raw-material costs.

**2.3 EBITDA margin** (build)
- Ask: Step 3 of 8: EBITDA margin. In C21 type =C10/C5 and drag it to E21. You should see 20.8% in E21.
- Answer: IS!C21:E21 =C10/C5
- Yellow: IS!C21:E21
- Check: IS!E21 = 20.8%
- Hint 1: Same idea as gross margin, one level lower.
- Hint 2: EBITDA divided by revenue.
- Why: EBITDA margin shows how efficiently the company runs day to day.

**2.4 Net profit margin** (build)
- Ask: Step 4 of 8: Net profit margin. In C22 type =C16/C5 and drag it to E22. You should see 11.6% in E22.
- Answer: IS!C22:E22 =C16/C5
- Yellow: IS!C22:E22
- Check: IS!E22 = 11.6%
- Hint 1: The bottom line as a share of sales.
- Hint 2: Net profit divided by revenue.
- Why: This is how many paise of profit shareholders earn for every rupee of sales.

**2.5 Receivable days** (build)
- Ask: Step 5 of 8: Receivable days. Click the Schedules sheet. In C5 type =Inputs!C22/IS!C5*365 and drag it to E5. You should see 45 in E5.
- Answer: Schedules!C5:E5 =Inputs!C22/IS!C5*365
- Yellow: Schedules!C5:E5
- Check: Schedules!E5 = 45
- Hint 1: Receivable days = how many days of sales customers still owe.
- Hint 2: Receivables divided by revenue, times 365.
- Why: If customers take longer to pay, cash gets stuck. That is why fast-growing companies can run out of money.

**2.6 Inventory days** (build)
- Ask: Step 6 of 8: Inventory days. In C6 type =Inputs!C23/IS!C6*365 and drag it to E6. You should see 50 in E6.
- Answer: Schedules!C6:E6 =Inputs!C23/IS!C6*365
- Yellow: Schedules!C6:E6
- Check: Schedules!E6 = 50
- Hint 1: Inventory is measured against the cost of goods, not revenue.
- Hint 2: Inventory divided by COGS, times 365.
- Why: Inventory days show how long products sit in the warehouse before being sold.

**2.7 Payable days** (build)
- Ask: Step 7 of 8: Payable days. In C7 type =Inputs!C26/IS!C6*365 and drag it to E7. You should see 60 in E7.
- Answer: Schedules!C7:E7 =Inputs!C26/IS!C6*365
- Yellow: Schedules!C7:E7
- Check: Schedules!E7 = 60
- Hint 1: Payables are what the company owes its suppliers.
- Hint 2: Payables divided by COGS, times 365.
- Why: Paying suppliers later frees up cash. Kaveri pays suppliers in about 60 days but collects from customers in 45.

**2.8 Read the ratios** (quiz)
- Ask: Step 8 of 8: Gross margin went from 41.5% to 42.4%. What does that most likely mean?
- Options: Raw materials got relatively cheaper or prices rose / The company took on more debt / Customers paid faster
- Correct: Raw materials got relatively cheaper or prices rose
- After answering: Gross margin only involves revenue and the cost of goods, so it reflects pricing and input costs.

### Module 3 · Assumptions
Goal: Choose the drivers that will push the model into the future.

**3.1 Set revenue growth** (build)
- Ask: Step 1 of 3: Set revenue growth. Click the Inputs sheet. In F32 to J32 type 12%, 11%, 10%, 9% and 8%, one per cell. You should see 8.0% in J32.
- Answer: Inputs!F32 12%; Inputs!G32 11%; Inputs!H32 10%; Inputs!I32 9%; Inputs!J32 8%
- Yellow: Inputs!F32, Inputs!G32, Inputs!H32, Inputs!I32, Inputs!J32
- Check: Inputs!J32 = 8.0%
- Hint 1: Growth was 12% and 11% in the last two years. Assume it slows down gently.
- Hint 2: Type 12% in F32, 11% in G32 and so on. These are typed inputs, so they stay blue.
- Why: Growth usually slows as a company gets bigger. Tapering it is more believable than a flat 12% forever.

**3.2 Base COGS on history** (build)
- Ask: Step 2 of 3: Base COGS on history. In F33 type =1-AVERAGE(IS!C20:E20) and press Enter. You should see 58.0% in F33.
- Answer: Inputs!F33 =1-AVERAGE(IS!C20:E20)
- Yellow: Inputs!F33
- Check: Inputs!F33 = 58.0%
- Hint 1: COGS % is the opposite of gross margin.
- Hint 2: 1 minus the average gross margin of the last three years.
- Why: Anchoring an assumption to history makes it defensible. You can always argue for changing it later.

**3.3 Keep COGS flat** (build)
- Ask: Step 3 of 3: Keep COGS flat. In G33 type =F33 and drag it to J33. You should see 58.0% in J33.
- Answer: Inputs!G33:J33 =F33
- Yellow: Inputs!G33:J33
- Check: Inputs!J33 = 58.0%
- Hint 1: Each year uses the year before.
- Hint 2: G33 points at F33; dragging makes H33 point at G33, and so on.
- Why: Now you can change the COGS assumption in one cell, F33, and every year follows.

### Module 4 · Revenue to EBITDA
Goal: Project the top half of the income statement.

**4.1 Project FY26 revenue** (build)
- Ask: Step 1 of 7: Project FY26 revenue. Click the IS sheet. In F5 type =E5*(1+Inputs!F32) and press Enter. You should see 1,392.4 in F5.
- Answer: IS!F5 =E5*(1+Inputs!F32)
- Yellow: IS!F5
- Check: IS!F5 = 1,392.4
- Hint 1: Next year's revenue is this year's revenue grown by the growth rate.
- Hint 2: Last year's revenue times one plus the growth rate on Inputs.
- Why: Revenue drives almost every other line, so it is always projected first.

**4.2 Project all revenue** (build)
- Ask: Step 2 of 7: Project all revenue. Drag F5 to J5. You should see 2,001.4 in J5.
- Answer: IS!F5:J5 =E5*(1+Inputs!F32)
- Yellow: IS!F5:J5
- Check: IS!J5 = 2,001.4
- Hint 1: Use the fill handle again.
- Hint 2: Each year now grows from the year before by its own rate.
- Why: By FY30 Kaveri's revenue is about 1.6 times today's.

**4.3 Project COGS** (build)
- Ask: Step 3 of 7: Project COGS. In F6 type =F5*Inputs!F33 and drag it to J6. You should see 1,161.5 in J6.
- Answer: IS!F6:J6 =F5*Inputs!F33
- Yellow: IS!F6:J6
- Check: IS!J6 = 1,161.5
- Hint 1: COGS is a percentage of revenue.
- Hint 2: Revenue times the COGS % on Inputs.
- Why: Costs that move with sales are modelled as a percentage of sales.

**4.4 Extend gross profit** (build)
- Ask: Step 4 of 7: Extend gross profit. Click E7 and drag it right to J7. You should see 839.9 in J7.
- Answer: IS!C7:J7 =C5-C6
- Yellow: IS!F7:J7
- Check: IS!J7 = 839.9
- Hint 1: The gross profit formula you wrote in Module 1 works for future years too.
- Hint 2: Drag the existing formula; do not retype it.
- Why: Reusing the same formula across history and projections keeps the row consistent.

**4.5 Project employee costs** (build)
- Ask: Step 5 of 7: Project employee costs. In F8 type =F5*Inputs!F34 and drag it to J8. You should see 194.1 in J8.
- Answer: IS!F8:J8 =F5*Inputs!F34
- Yellow: IS!F8:J8
- Check: IS!J8 = 194.1
- Hint 1: Same pattern as COGS.
- Hint 2: Revenue times employee costs % on Inputs row 34.
- Why: Salaries grow roughly in line with the business.

**4.6 Project other expenses** (build)
- Ask: Step 6 of 7: Project other expenses. In F9 type =F5*Inputs!F35 and drag it to J9. You should see 238.2 in J9.
- Answer: IS!F9:J9 =F5*Inputs!F35
- Yellow: IS!F9:J9
- Check: IS!J9 = 238.2
- Hint 1: Same pattern again.
- Hint 2: Revenue times other expenses % on Inputs row 35.
- Why: Rent, power, freight and marketing also scale with sales.

**4.7 Extend EBITDA** (build)
- Ask: Step 7 of 7: Extend EBITDA. Click E10 and drag it right to J10. You should see 407.6 in J10.
- Answer: IS!C10:J10 =C7-C8-C9
- Yellow: IS!F10:J10
- Check: IS!J10 = 407.6
- Hint 1: Reuse the EBITDA formula from Module 1.
- Hint 2: Drag E10 to J10.
- Why: You now have five years of projected operating profit.

### Module 5 · Working capital
Goal: Project receivables, inventory and payables, and see how they tie up cash.

**5.1 Bring in day assumptions** (build)
- Ask: Step 1 of 8: Bring in day assumptions. Click the Schedules sheet. In F5 type =Inputs!F36 and drag it to J5, then drag F5:J5 down to row 7. You should see 60 in J7.
- Answer: Schedules!F5:J7 =Inputs!F36
- Yellow: Schedules!F5:J7
- Check: Schedules!J7 = 60
- Hint 1: The day assumptions live on Inputs rows 36 to 38.
- Hint 2: Link F5 to Inputs!F36, then fill right and down.
- Why: Days are the driver; balances are calculated from them.

**5.2 Link historical balances** (build)
- Ask: Step 2 of 8: Link historical balances. In C9 type =Inputs!C22 and drag it to E9, then drag C9:E9 down to row 10. In C11 type =Inputs!C26 and drag it to E11. You should see 117.7 in E11.
- Answer: Schedules!C9:E10 =Inputs!C22; Schedules!C11:E11 =Inputs!C26
- Yellow: Schedules!C9:E10, Schedules!C11:E11
- Check: Schedules!E11 = 117.7
- Hint 1: Receivables and inventory are Inputs rows 22 and 23; payables is row 26.
- Hint 2: Two separate links because payables sits on a different row.
- Why: History gives the starting point for the projection.

**5.3 Project receivables** (build)
- Ask: Step 3 of 8: Project receivables. In F9 type =F5/365*IS!F5 and drag it to J9. You should see 246.7 in J9.
- Answer: Schedules!F9:J9 =F5/365*IS!F5
- Yellow: Schedules!F9:J9
- Check: Schedules!J9 = 246.7
- Hint 1: Reverse the days formula you built in Module 2.
- Hint 2: Days divided by 365, times revenue.
- Why: As revenue grows, receivables grow with it, which absorbs cash.

**5.4 Project inventory** (build)
- Ask: Step 4 of 8: Project inventory. In F10 type =F6/365*IS!F6 and drag it to J10. You should see 159.1 in J10.
- Answer: Schedules!F10:J10 =F6/365*IS!F6
- Yellow: Schedules!F10:J10
- Check: Schedules!J10 = 159.1
- Hint 1: Inventory days are measured on COGS.
- Hint 2: Inventory days divided by 365, times COGS.
- Why: More sales need more stock on the shelves.

**5.5 Project payables** (build)
- Ask: Step 5 of 8: Project payables. In F11 type =F7/365*IS!F6 and drag it to J11. You should see 190.9 in J11.
- Answer: Schedules!F11:J11 =F7/365*IS!F6
- Yellow: Schedules!F11:J11
- Check: Schedules!J11 = 190.9
- Hint 1: Payables are also measured on COGS.
- Hint 2: Payable days divided by 365, times COGS.
- Why: Suppliers effectively lend the company money, which offsets some of the cash tied up.

**5.6 Net working capital** (build)
- Ask: Step 6 of 8: Net working capital. In C12 type =C9+C10-C11 and drag it to J12. You should see 214.9 in J12.
- Answer: Schedules!C12:J12 =C9+C10-C11
- Yellow: Schedules!C12:J12
- Check: Schedules!J12 = 214.9
- Hint 1: Working capital is what customers and stock tie up, minus what suppliers fund.
- Hint 2: Receivables plus inventory minus payables.
- Why: This is the cash permanently locked in day-to-day operations.

**5.7 Change in working capital** (build)
- Ask: Step 7 of 8: Change in working capital. In D13 type =D12-C12 and drag it to J13. You should see 15.9 in J13.
- Answer: Schedules!D13:J13 =D12-C12
- Yellow: Schedules!D13:J13
- Check: Schedules!J13 = 15.9
- Hint 1: Compare this year's working capital with last year's.
- Hint 2: This year's NWC minus last year's.
- Why: An increase is cash that went into the business instead of the bank. It reduces cash flow.

**5.8 Working capital and cash** (quiz)
- Ask: Step 8 of 8: If customers start paying in 60 days instead of 45, what happens to cash?
- Options: Cash goes down / Cash goes up / No change
- Correct: Cash goes down
- After answering: Higher receivable days means more money stuck with customers, so less cash in the bank.

### Module 6 · Fixed assets
Goal: Project capex, depreciation and the net block.

**6.1 Historical net block** (build)
- Ask: Step 1 of 6: Historical net block. On the Schedules sheet, in C19 type =Inputs!C24 and drag it to E19. You should see 465.0 in E19.
- Answer: Schedules!C19:E19 =Inputs!C24
- Yellow: Schedules!C19:E19
- Check: Schedules!E19 = 465.0
- Hint 1: Net fixed assets are on Inputs row 24.
- Hint 2: =Inputs!C24, dragged to E19.
- Why: FY25 closing net block is where the projection starts.

**6.2 Opening net block** (build)
- Ask: Step 2 of 6: Opening net block. In F16 type =E19 and drag it to J16. You should see 465.0 in F16.
- Answer: Schedules!F16:J16 =E19
- Yellow: Schedules!F16:J16
- Check: Schedules!F16 = 465.0
- Hint 1: This year starts where last year ended.
- Hint 2: Point at last year's closing net block in row 19.
- Why: Every roll-forward schedule follows opening + additions − reductions = closing.

**6.3 Capex** (build)
- Ask: Step 3 of 6: Capex. In F17 type =IS!F5*Inputs!F39 and drag it to J17. You should see 100.1 in J17.
- Answer: Schedules!F17:J17 =IS!F5*Inputs!F39
- Yellow: Schedules!F17:J17
- Check: Schedules!J17 = 100.1
- Hint 1: Capex is spending on new factories and machines.
- Hint 2: Revenue times capex % on Inputs row 39.
- Why: A growing food company needs more production capacity.

**6.4 Depreciation** (build)
- Ask: Step 4 of 6: Depreciation. In F18 type =F16*Inputs!F40 and drag it to J18. You should see 46.5 in F18.
- Answer: Schedules!F18:J18 =F16*Inputs!F40
- Yellow: Schedules!F18:J18
- Check: Schedules!F18 = 46.5
- Hint 1: Depreciation is a percentage of the assets at the start of the year.
- Hint 2: Opening net block times depreciation % on Inputs row 40.
- Why: Depreciation is a cost with no cash going out, which is why cash flow adds it back.

**6.5 Closing net block** (build)
- Ask: Step 5 of 6: Closing net block. In F19 type =F16+F17-F18 and drag it to J19. You should see 628.9 in J19.
- Answer: Schedules!F19:J19 =F16+F17-F18
- Yellow: Schedules!F19:J19
- Check: Schedules!J19 = 628.9
- Hint 1: Closing = what you started with, plus what you bought, minus what wore out.
- Hint 2: Opening plus capex minus depreciation.
- Why: This closing figure will become fixed assets on the projected balance sheet.

**6.6 Depreciation into IS** (build)
- Ask: Step 6 of 6: Depreciation into IS. Click the IS sheet. In F11 type =Schedules!F18 and drag it to J11. You should see 58.8 in J11.
- Answer: IS!F11:J11 =Schedules!F18
- Yellow: IS!F11:J11
- Check: IS!J11 = 58.8
- Hint 1: The income statement takes depreciation from the schedule.
- Hint 2: Link to Schedules row 18.
- Why: This is a green link: the schedule does the work, the statement just shows the answer.

### Module 7 · Debt
Goal: Project debt repayments and the interest cost.

**7.1 Historical debt** (build)
- Ask: Step 1 of 6: Historical debt. Click the Schedules sheet. In C24 type =Inputs!C27 and drag it to E24. You should see 240.0 in E24.
- Answer: Schedules!C24:E24 =Inputs!C27
- Yellow: Schedules!C24:E24
- Check: Schedules!E24 = 240.0
- Hint 1: Debt is on Inputs row 27.
- Hint 2: =Inputs!C27, dragged to E24.
- Why: FY25 closing debt is where the projection starts.

**7.2 Opening debt** (build)
- Ask: Step 2 of 6: Opening debt. In F22 type =E24 and drag it to J22. You should see 240.0 in F22.
- Answer: Schedules!F22:J22 =E24
- Yellow: Schedules!F22:J22
- Check: Schedules!F22 = 240.0
- Hint 1: Same roll-forward idea as fixed assets.
- Hint 2: Opening debt = last year's closing debt.
- Why: Every roll-forward links each year to the one before.

**7.3 Repayment** (build)
- Ask: Step 3 of 6: Repayment. In F23 type =Inputs!F42 and drag it to J23. You should see 30.0 in J23.
- Answer: Schedules!F23:J23 =Inputs!F42
- Yellow: Schedules!F23:J23
- Check: Schedules!J23 = 30.0
- Hint 1: Kaveri repays a fixed amount each year.
- Hint 2: Link to Inputs row 42.
- Why: Repaying debt uses cash but lowers future interest.

**7.4 Closing debt** (build)
- Ask: Step 4 of 6: Closing debt. In F24 type =F22-F23 and drag it to J24. You should see 90.0 in J24.
- Answer: Schedules!F24:J24 =F22-F23
- Yellow: Schedules!F24:J24
- Check: Schedules!J24 = 90.0
- Hint 1: Opening minus repayment.
- Hint 2: =F22-F23.
- Why: Debt falls from 240 to 90 crore over five years.

**7.5 Interest** (build)
- Ask: Step 5 of 6: Interest. In F25 type =AVERAGE(F22,F24)*Inputs!F41 and drag it to J25. You should see 9.4 in J25.
- Answer: Schedules!F25:J25 =AVERAGE(F22,F24)*Inputs!F41
- Yellow: Schedules!F25:J25
- Check: Schedules!J25 = 9.4
- Hint 1: Debt changes during the year, so use the average balance.
- Hint 2: Average of opening and closing debt, times the interest rate.
- Why: Using the average is more accurate than using only the opening or closing balance.

**7.6 Interest into IS** (build)
- Ask: Step 6 of 6: Interest into IS. Click the IS sheet. In F13 type =Schedules!F25 and drag it to J13. You should see 9.4 in J13.
- Answer: IS!F13:J13 =Schedules!F25
- Yellow: IS!F13:J13
- Check: IS!J13 = 9.4
- Hint 1: Same idea as depreciation.
- Hint 2: Link to Schedules row 25.
- Why: Now the income statement knows the cost of the company's debt.

### Module 8 · Profit
Goal: Finish the projected income statement down to net profit.

**8.1 Extend EBIT** (build)
- Ask: Step 1 of 5: Extend EBIT. Click E12 and drag it right to J12. You should see 348.8 in J12.
- Answer: IS!C12:J12 =C10-C11
- Yellow: IS!F12:J12
- Check: IS!J12 = 348.8
- Hint 1: Reuse your Module 1 formula.
- Hint 2: Drag E12 to J12.
- Why: Depreciation is now flowing in from the schedule, so EBIT is complete.

**8.2 Extend profit before tax** (build)
- Ask: Step 2 of 5: Extend profit before tax. Click E14 and drag it right to J14. You should see 339.4 in J14.
- Answer: IS!C14:J14 =C12-C13
- Yellow: IS!F14:J14
- Check: IS!J14 = 339.4
- Hint 1: Reuse your Module 1 formula.
- Hint 2: Drag E14 to J14.
- Why: Interest is flowing in from the debt schedule.

**8.3 Project tax** (build)
- Ask: Step 3 of 5: Project tax. In F15 type =F14*Inputs!F43 and drag it to J15. You should see 85.4 in J15.
- Answer: IS!F15:J15 =F14*Inputs!F43
- Yellow: IS!F15:J15
- Check: IS!J15 = 85.4
- Hint 1: Tax is a percentage of profit before tax.
- Hint 2: Profit before tax times the tax rate on Inputs row 43.
- Why: 25.17% is the rate for Indian companies under the new tax regime.

**8.4 Extend net profit** (build)
- Ask: Step 4 of 5: Extend net profit. Click E16 and drag it right to J16. You should see 254.0 in J16.
- Answer: IS!C16:J16 =C14-C15
- Yellow: IS!F16:J16
- Check: IS!J16 = 254.0
- Hint 1: Reuse your Module 1 formula.
- Hint 2: Drag E16 to J16.
- Why: This is projected profit for shareholders.

**8.5 Extend the ratios** (build)
- Ask: Step 5 of 5: Extend the ratios. Select E19:E22 and drag it right to J22. You should see 12.7% in J22.
- Answer: IS!D19:J19 =D5/C5-1; IS!C20:J20 =C7/C5; IS!C21:J21 =C10/C5; IS!C22:J22 =C16/C5
- Yellow: IS!F19:J19, IS!F20:J20, IS!F21:J21, IS!F22:J22
- Check: IS!J22 = 12.7%
- Hint 1: Your ratio formulas work for projected years too.
- Hint 2: Select the four ratio cells in column E and drag right.
- Why: Comparing projected margins to history is the quickest way to sanity-check a forecast.

### Module 9 · Cash flow
Goal: Build the cash flow statement from the IS and schedules.

**9.1 Start with net profit** (build)
- Ask: Step 1 of 9: Start with net profit. Click the CF sheet. In F5 type =IS!F16 and drag it to J5. You should see 254.0 in J5.
- Answer: CF!F5:J5 =IS!F16
- Yellow: CF!F5:J5
- Check: CF!J5 = 254.0
- Hint 1: Cash flow starts from profit.
- Hint 2: Link to IS row 16.
- Why: Profit is not cash. The next lines adjust profit into actual cash.

**9.2 Add back depreciation** (build)
- Ask: Step 2 of 9: Add back depreciation. In F6 type =IS!F11 and drag it to J6. You should see 58.8 in J6.
- Answer: CF!F6:J6 =IS!F11
- Yellow: CF!F6:J6
- Check: CF!J6 = 58.8
- Hint 1: Depreciation reduced profit but no cash left the company.
- Hint 2: Link to IS row 11.
- Why: Adding it back undoes a non-cash cost.

**9.3 Subtract working capital** (build)
- Ask: Step 3 of 9: Subtract working capital. In F7 type =-Schedules!F13 and drag it to J7. You should see -15.9 in J7.
- Answer: CF!F7:J7 =-Schedules!F13
- Yellow: CF!F7:J7
- Check: CF!J7 = -15.9
- Hint 1: An increase in working capital uses cash.
- Hint 2: Minus the change in NWC from Schedules row 13.
- Why: The minus sign matters: more working capital means less cash.

**9.4 Cash from operations** (build)
- Ask: Step 4 of 9: Cash from operations. In F8 type =SUM(F5:F7) and drag it to J8. You should see 296.8 in J8.
- Answer: CF!F8:J8 =SUM(F5:F7)
- Yellow: CF!F8:J8
- Check: CF!J8 = 296.8
- Hint 1: Add the three lines above.
- Hint 2: =SUM(F5:F7).
- Why: CFO is the cash the business actually generates from running.

**9.5 Capex and investing** (build)
- Ask: Step 5 of 9: Capex and investing. In F10 type =-Schedules!F17 and drag it to J10. In F11 type =F10 and drag it to J11. You should see -100.1 in J11.
- Answer: CF!F10:J10 =-Schedules!F17; CF!F11:J11 =F10
- Yellow: CF!F10:J10, CF!F11:J11
- Check: CF!J11 = -100.1
- Hint 1: Capex is cash going out, so it is negative.
- Hint 2: Minus capex from Schedules row 17; investing total equals capex here.
- Why: Kaveri's only investment is in its own factories.

**9.6 Repayment and dividends** (build)
- Ask: Step 6 of 9: Repayment and dividends. In F13 type =-Schedules!F23 and drag it to J13. In F14 type =-IS!F16*Inputs!F44 and drag it to J14. You should see -63.5 in J14.
- Answer: CF!F13:J13 =-Schedules!F23; CF!F14:J14 =-IS!F16*Inputs!F44
- Yellow: CF!F13:J13, CF!F14:J14
- Check: CF!J14 = -63.5
- Hint 1: Both are cash paid out, so both are negative.
- Hint 2: Minus the repayment; minus net profit times the payout ratio.
- Why: These are the company's payments to lenders and shareholders.

**9.7 Cash from financing** (build)
- Ask: Step 7 of 9: Cash from financing. In F15 type =F13+F14 and drag it to J15. You should see -93.5 in J15.
- Answer: CF!F15:J15 =F13+F14
- Yellow: CF!F15:J15
- Check: CF!J15 = -93.5
- Hint 1: Add repayment and dividends.
- Hint 2: =F13+F14.
- Why: CFF is the net cash flowing to lenders and shareholders.

**9.8 Net change in cash** (build)
- Ask: Step 8 of 9: Net change in cash. In F17 type =F8+F11+F15 and drag it to J17. You should see 103.2 in J17.
- Answer: CF!F17:J17 =F8+F11+F15
- Yellow: CF!F17:J17
- Check: CF!J17 = 103.2
- Hint 1: Add the three sections.
- Hint 2: Operations plus investing plus financing.
- Why: This is how much the cash balance grows each year.

**9.9 Opening and closing cash** (build)
- Ask: Step 9 of 9: Opening and closing cash. In F18 type =BS!E5 and drag it to J18. In F19 type =F18+F17 and drag it to J19. You should see 322.2 in F19.
- Answer: CF!F18:J18 =BS!E5; CF!F19:J19 =F18+F17
- Yellow: CF!F18:J18, CF!F19:J19
- Check: CF!F19 = 322.2
- Hint 1: Opening cash is last year's cash on the balance sheet.
- Hint 2: Opening cash plus net change gives closing cash.
- Why: Closing cash goes back onto the balance sheet. That loop is what ties the three statements together.

### Module 10 · Balance sheet
Goal: Project the balance sheet and make it balance.

**10.1 Cash from the CF** (build)
- Ask: Step 1 of 8: Cash from the CF. Click the BS sheet. In F5 type =CF!F19 and drag it to J5. You should see 657.1 in J5.
- Answer: BS!F5:J5 =CF!F19
- Yellow: BS!F5:J5
- Check: BS!J5 = 657.1
- Hint 1: Cash comes from the cash flow statement.
- Hint 2: Link to closing cash, CF row 19.
- Why: Cash is the one balance sheet line that is never forecast directly.

**10.2 Operating assets** (build)
- Ask: Step 2 of 8: Operating assets. In F6 type =Schedules!F9 and drag it to J6, then drag F6:J6 down to row 7. In F8 type =Schedules!F19 and drag it to J8. You should see 628.9 in J8.
- Answer: BS!F6:J7 =Schedules!F9; BS!F8:J8 =Schedules!F19
- Yellow: BS!F6:J7, BS!F8:J8
- Check: BS!J8 = 628.9
- Hint 1: Receivables and inventory are Schedules rows 9 and 10; net block is row 19.
- Hint 2: Link, fill right, fill down; then a separate link for fixed assets.
- Why: The schedules do the work; the balance sheet just collects the results.

**10.3 Total assets** (build)
- Ask: Step 3 of 8: Total assets. Click E9 and drag it right to J9. You should see 1,691.8 in J9.
- Answer: BS!C9:J9 =SUM(C5:C8)
- Yellow: BS!F9:J9
- Check: BS!J9 = 1,691.8
- Hint 1: Reuse the SUM from Module 1.
- Hint 2: Drag E9 to J9.
- Why: Total assets for every projected year.

**10.4 Payables and debt** (build)
- Ask: Step 4 of 8: Payables and debt. In F11 type =Schedules!F11 and drag it to J11. In F12 type =Schedules!F24 and drag it to J12. You should see 90.0 in J12.
- Answer: BS!F11:J11 =Schedules!F11; BS!F12:J12 =Schedules!F24
- Yellow: BS!F11:J11, BS!F12:J12
- Check: BS!J12 = 90.0
- Hint 1: Both come from the Schedules sheet.
- Hint 2: Payables row 11, closing debt row 24.
- Why: Again, the statement links; the schedule calculates.

**10.5 Share capital** (build)
- Ask: Step 5 of 8: Share capital. In F13 type =E13 and drag it to J13. You should see 50.0 in J13.
- Answer: BS!F13:J13 =E13
- Yellow: BS!F13:J13
- Check: BS!J13 = 50.0
- Hint 1: Kaveri issues no new shares.
- Hint 2: Each year equals the year before.
- Why: Share capital only changes if the company raises or buys back equity.

**10.6 Retained earnings** (build)
- Ask: Step 6 of 8: Retained earnings. In F14 type =E14+IS!F16+CF!F14 and drag it to J14. You should see 1,360.9 in J14.
- Answer: BS!F14:J14 =E14+IS!F16+CF!F14
- Yellow: BS!F14:J14
- Check: BS!J14 = 1,360.9
- Hint 1: Retained earnings grow by profit and shrink by dividends.
- Hint 2: Last year's retained earnings plus net profit plus dividends (already negative on CF).
- Why: This is the second link between the statements: profit flows into equity.

**10.7 Total and check** (build)
- Ask: Step 7 of 8: Total and check. Select E15:E17 and drag it right to J17. You should see 0.0 in J17.
- Answer: BS!C15:J15 =SUM(C11:C14); BS!C17:J17 =C9-C15
- Yellow: BS!F15:J15, BS!F17:J17
- Check: BS!J17 = 0.0
- Hint 1: Reuse your total and balance check formulas.
- Hint 2: Select E15 to E17 and drag right to column J.
- Why: If every year in row 17 shows 0, your 3-statement model is fully linked. That is the big milestone.

**10.8 Checks sheet** (build)
- Ask: Step 8 of 8: Checks sheet. Click the Checks sheet. In C5 type =IF(MAX(BS!C17:J17)-MIN(BS!C17:J17)<0.01,"OK","ERROR") and press Enter. You should see OK in C5.
- Answer: Checks!C5 =IF(MAX(BS!C17:J17)-MIN(BS!C17:J17)<0.01,"OK","ERROR")
- Yellow: Checks!C5
- Check: Checks!C5 = OK
- Hint 1: One cell that tells you if any year is out of balance.
- Hint 2: If the largest and smallest balance-check values are both zero, show OK.
- Why: In big models you cannot eyeball every year. One check cell catches mistakes instantly.

### Module 11 · DCF valuation
Goal: Value Kaveri Foods from its future cash flows.

**11.1 Start from EBIT** (build)
- Ask: Step 1 of 10: Start from EBIT. Click the DCF sheet. In F5 type =IS!F12 and drag it to J5. You should see 348.8 in J5.
- Answer: DCF!F5:J5 =IS!F12
- Yellow: DCF!F5:J5
- Check: DCF!J5 = 348.8
- Hint 1: Free cash flow to the firm starts from operating profit.
- Hint 2: Link to IS row 12.
- Why: We start before interest because the DCF values the whole business, for lenders and shareholders.

**11.2 Tax and NOPAT** (build)
- Ask: Step 2 of 10: Tax and NOPAT. In F6 type =F5*Inputs!F43 and drag it to J6. In F7 type =F5-F6 and drag it to J7. You should see 261.0 in J7.
- Answer: DCF!F6:J6 =F5*Inputs!F43; DCF!F7:J7 =F5-F6
- Yellow: DCF!F6:J6, DCF!F7:J7
- Check: DCF!J7 = 261.0
- Hint 1: Tax as if the company had no debt.
- Hint 2: EBIT times tax rate, then EBIT minus that tax.
- Why: NOPAT is operating profit after tax, ignoring financing.

**11.3 Free cash flow** (build)
- Ask: Step 3 of 10: Free cash flow. In F8 type =IS!F11 and drag it to J8. In F9 type =Schedules!F17 and drag it to J9. In F10 type =Schedules!F13 and drag it to J10. In F11 type =F7+F8-F9-F10 and drag it to J11. You should see 203.8 in J11.
- Answer: DCF!F8:J8 =IS!F11; DCF!F9:J9 =Schedules!F17; DCF!F10:J10 =Schedules!F13; DCF!F11:J11 =F7+F8-F9-F10
- Yellow: DCF!F8:J8, DCF!F9:J9, DCF!F10:J10, DCF!F11:J11
- Check: DCF!J11 = 203.8
- Hint 1: Same adjustments as the cash flow statement, but on NOPAT.
- Hint 2: NOPAT plus depreciation minus capex minus increase in working capital.
- Why: FCFF is the cash available to everyone who funded the company.

**11.4 Cost of equity** (build)
- Ask: Step 4 of 10: Cost of equity. In C14 type =Inputs!C47+Inputs!C48*Inputs!C49 and press Enter. You should see 12.8% in C14.
- Answer: DCF!C14 =Inputs!C47+Inputs!C48*Inputs!C49
- Yellow: DCF!C14
- Check: DCF!C14 = 12.8%
- Hint 1: CAPM: risk-free rate plus beta times the equity risk premium.
- Hint 2: Risk-free + beta × ERP.
- Why: Shareholders want a higher return than a government bond because shares are riskier.

**11.5 WACC** (build)
- Ask: Step 5 of 10: WACC. In C15 type =Inputs!C50*(1-Inputs!J43). In C16 type =C14*(1-Inputs!C51)+C15*Inputs!C51. You should see 11.6% in C16.
- Answer: DCF!C15 =Inputs!C50*(1-Inputs!J43); DCF!C16 =C14*(1-Inputs!C51)+C15*Inputs!C51
- Yellow: DCF!C15, DCF!C16
- Check: DCF!C16 = 11.6%
- Hint 1: WACC blends the cost of equity and the after-tax cost of debt.
- Hint 2: Cost of equity × equity weight + after-tax cost of debt × debt weight.
- Why: WACC is the discount rate: the return all investors together expect.

**11.6 Discount factors** (build)
- Ask: Step 6 of 10: Discount factors. In F25 type =1/(1+$C$16)^F24 and drag it to J25. You should see 0.578 in J25.
- Answer: DCF!F25:J25 =1/(1+$C$16)^F24
- Yellow: DCF!F25:J25
- Check: DCF!J25 = 0.578
- Hint 1: The $ signs lock C16 so it does not move when you drag.
- Hint 2: 1 divided by (1 + WACC) to the power of the year number in row 24.
- Why: A rupee five years away is worth less than a rupee today.

**11.7 Present value of FCFF** (build)
- Ask: Step 7 of 10: Present value of FCFF. In F26 type =F11*F25 and drag it to J26. You should see 117.8 in J26.
- Answer: DCF!F26:J26 =F11*F25
- Yellow: DCF!F26:J26
- Check: DCF!J26 = 117.8
- Hint 1: Cash flow times its discount factor.
- Hint 2: =F11*F25.
- Why: This converts each future year's cash into today's money.

**11.8 Terminal value** (build)
- Ask: Step 8 of 10: Terminal value. In C29 type =SUM(F26:J26). In C30 type =J11*(1+Inputs!C52)/(C16-Inputs!C52). In C31 type =C30*J25. You should see 1,877.9 in C31.
- Answer: DCF!C29 =SUM(F26:J26); DCF!C30 =J11*(1+Inputs!C52)/(C16-Inputs!C52); DCF!C31 =C30*J25
- Yellow: DCF!C29, DCF!C30, DCF!C31
- Check: DCF!C31 = 1,877.9
- Hint 1: The company keeps going after FY30; the terminal value captures that.
- Hint 2: FY30 FCFF grown once, divided by WACC minus growth; then discount it with the FY30 factor.
- Why: The terminal value is usually most of the valuation, which is why the growth assumption matters so much.

**11.9 Enterprise to equity value** (build)
- Ask: Step 9 of 10: Enterprise to equity value. In C32 type =C29+C31. In C33 type =BS!E12. In C34 type =BS!E5. In C35 type =C32-C33+C34. You should see 2,516.4 in C35.
- Answer: DCF!C32 =C29+C31; DCF!C33 =BS!E12; DCF!C34 =BS!E5; DCF!C35 =C32-C33+C34
- Yellow: DCF!C32, DCF!C33, DCF!C34, DCF!C35
- Check: DCF!C35 = 2,516.4
- Hint 1: Enterprise value belongs to lenders and shareholders together.
- Hint 2: EV minus today's debt plus today's cash equals equity value.
- Why: Debt holders get paid first; what's left belongs to shareholders.

**11.10 Value per share** (build)
- Ask: Step 10 of 10: Value per share. In C36 type =Inputs!C53. In C37 type =C35/C36. You should see Rs 252 in C37.
- Answer: DCF!C36 =Inputs!C53; DCF!C37 =C35/C36
- Yellow: DCF!C36, DCF!C37
- Check: DCF!C37 = Rs 252
- Hint 1: Divide equity value by the number of shares.
- Hint 2: Both are in crore, so the answer is in rupees per share.
- Why: This is the number you would compare with the share price to decide if a stock is cheap or expensive.

### Module 12 · Sensitivity
Goal: See how much the value depends on your assumptions.

**12.1 Build the sensitivity formula** (build)
- Ask: Step 1 of 4: Build the sensitivity formula. In D42 type =(SUMPRODUCT($F$11:$J$11,1/(1+$C42)^$F$24:$J$24)+$J$11*(1+D$41)/($C42-D$41)/(1+$C42)^5-$C$33+$C$34)/$C$36 and press Enter. You should see Rs 307 in D42.
- Answer: DCF!D42 =(SUMPRODUCT($F$11:$J$11,1/(1+$C42)^$F$24:$J$24)+$J$11*(1+D$41)/($C42-D$41)/(1+$C42)^5-$C$33+$C$34)/$C$36
- Yellow: DCF!D42
- Check: DCF!D42 = Rs 307
- Hint 1: This is the whole DCF in one cell, using the WACC in column C and the growth rate in row 41.
- Hint 2: $C42 locks the column, D$41 locks the row, so it works when copied in both directions.
- Why: Mixed references are the key Excel skill for any two-way table.

**12.2 Fill the table** (build)
- Ask: Step 2 of 4: Fill the table. Copy D42 to every cell from D42 to H46. You should see Rs 252 in F44.
- Answer: DCF!D42:H46 =(SUMPRODUCT($F$11:$J$11,1/(1+$C42)^$F$24:$J$24)+$J$11*(1+D$41)/($C42-D$41)/(1+$C42)^5-$C$33+$C$34)/$C$36
- Yellow: DCF!D42:H46
- Check: DCF!F44 = Rs 252
- Hint 1: Select D42, copy, then select D42:H46 and paste.
- Hint 2: The centre cell F44 should match your value per share.
- Why: The centre of the table is your base case; everything else shows what happens if you are wrong.

**12.3 Colour it as a heatmap** (format)
- Ask: Step 3 of 4: Colour it as a heatmap. Select D42:H46, then on the Home tab click Conditional Formatting, Color Scales, and pick the green-yellow-red one. You should see the table turn green, yellow and red.
- Check: DCF!D42:H46 has a colour-scale conditional format
- Hint 1: Conditional Formatting is on the Home tab, in the middle of the ribbon.
- Hint 2: Color Scales, then the first option (green to red).
- Why: Colour makes it obvious where the value is high or low without reading every number.

**12.4 Read the table** (quiz)
- Ask: Step 4 of 4: Which change moves the value per share more in this table?
- Options: WACC up by 1% / Terminal growth down by 0.5% / They move it by exactly the same amount
- Correct: WACC up by 1%
- After answering: Small changes in WACC swing the value a lot. That is why analysts always show a sensitivity table, never one number.

## 7. Layout

Years in row 3: C=FY23A, D=FY24A, E=FY25A, F=FY26E, G=FY27E, H=FY28E, I=FY29E, J=FY30E. Historical C:E, projections F:J. Column B holds labels. Row 1 = sheet title, B2 = "INR crore".

- **Inputs** labels (column B): 4 [Historical income statement]; 5 Revenue; 6 Cost of goods sold (COGS); 8 Employee costs; 9 Other expenses; 11 Depreciation; 13 Interest; 15 Tax; 17 Dividends paid; 19 [Historical balance sheet]; 21 Cash; 22 Receivables; 23 Inventory; 24 Net fixed assets (net block); 26 Payables; 27 Debt; 28 Share capital; 29 Retained earnings; 31 [Projection assumptions]; 32 Revenue growth; 33 COGS % revenue; 34 Employee costs % revenue; 35 Other expenses % revenue; 36 Receivable days; 37 Inventory days (on COGS); 38 Payable days (on COGS); 39 Capex % revenue; 40 Depreciation % opening net block; 41 Interest rate on debt; 42 Debt repayment; 43 Tax rate; 44 Dividend payout; 46 [Valuation inputs]; 47 Risk-free rate (practice value, use current 10Y G-sec for real work); 48 Beta; 49 Equity risk premium; 50 Pre-tax cost of debt; 51 Debt weight in capital (D/V); 52 Terminal growth rate; 53 Shares outstanding (crore)
- **IS** labels (column B): 4 [Income statement]; 5 Revenue; 6 COGS; 7 Gross profit; 8 Employee costs; 9 Other expenses; 10 EBITDA; 11 Depreciation; 12 EBIT; 13 Interest; 14 Profit before tax; 15 Tax; 16 Net profit (PAT); 18 [Ratios]; 19 Revenue growth; 20 Gross margin; 21 EBITDA margin; 22 Net profit margin
- **BS** labels (column B): 4 [Assets]; 5 Cash; 6 Receivables; 7 Inventory; 8 Net fixed assets; 9 Total assets; 10 [Liabilities and equity]; 11 Payables; 12 Debt; 13 Share capital; 14 Retained earnings; 15 Total liabilities and equity; 17 Balance check (must be 0)
- **CF** labels (column B): 4 [Operating]; 5 Net profit; 6 Add: depreciation; 7 Less: increase in working capital; 8 Cash from operations; 9 [Investing]; 10 Capex; 11 Cash from investing; 12 [Financing]; 13 Debt repayment; 14 Dividends; 15 Cash from financing; 17 Net change in cash; 18 Opening cash; 19 Closing cash
- **Schedules** labels (column B): 4 [Working capital]; 5 Receivable days; 6 Inventory days; 7 Payable days; 9 Receivables; 10 Inventory; 11 Payables; 12 Net working capital; 13 Change in working capital; 15 [Fixed assets]; 16 Opening net block; 17 Capex; 18 Depreciation; 19 Closing net block; 21 [Debt]; 22 Opening debt; 23 Repayment; 24 Closing debt; 25 Interest
- **DCF** labels (column B): 4 [Free cash flow]; 5 EBIT; 6 Tax on EBIT; 7 NOPAT; 8 Add: depreciation; 9 Less: capex; 10 Less: increase in working capital; 11 Free cash flow to firm (FCFF); 13 [Discount rate]; 14 Cost of equity; 15 After-tax cost of debt; 16 WACC; 23 [Discounting]; 24 Year number; 25 Discount factor; 26 PV of FCFF; 28 [Valuation]; 29 Sum of PV of FCFF; 30 Terminal value; 31 PV of terminal value; 32 Enterprise value; 33 Less: debt (FY25); 34 Add: cash (FY25); 35 Equity value; 36 Shares outstanding (crore); 37 Value per share (Rs); 39 [Sensitivity: value per share (Rs)]; 40 WACC down, terminal growth across
- **Checks** labels (column B): 4 [Model checks]; 5 Balance sheet balances every year

**Inputs data (blue font, typed by Claude during setup):**
- Row 5 C:E = 1000.0, 1120.0, 1243.2
- Row 6 C:E = 585.0, 649.6, 716.1
- Row 8 C:E = 100.0, 109.8, 120.6
- Row 9 C:E = 122.0, 134.4, 147.9
- Row 11 C:E = 38.0, 40.0, 43.0
- Row 13 C:E = 28.4, 25.7, 23.0
- Row 15 C:E = 31.9, 40.4, 48.5
- Row 17 C:E = 23.7, 30.0, 36.0
- Row 21 C:E = 222.8, 239.8, 269.5
- Row 22 C:E = 123.3, 138.1, 153.3
- Row 23 C:E = 80.1, 89.0, 98.1
- Row 24 C:E = 400.0, 430.0, 465.0
- Row 26 C:E = 96.2, 106.8, 117.7
- Row 27 C:E = 300.0, 270.0, 240.0
- Row 28 C:E = 50.0, 50.0, 50.0
- Row 29 C:E = 380.0, 470.1, 578.2
- Row 34 F:J = 9.7% in every year
- Row 35 F:J = 11.9% in every year
- Row 36 F:J = 45 in every year
- Row 37 F:J = 50 in every year
- Row 38 F:J = 60 in every year
- Row 39 F:J = 5% in every year
- Row 40 F:J = 10% in every year
- Row 41 F:J = 9% in every year
- Row 42 F:J = 30 in every year
- Row 43 F:J = 25.17% in every year
- Row 44 F:J = 25% in every year
- Rows 32 and 33 F:J: leave empty with blue font (the learner fills them in Module 3).
- C47 = 6.5%
- C48 = 0.9
- C49 = 7%
- C50 = 9%
- C51 = 20%
- C52 = 5%
- C53 = 10

**DCF pre-fill:** F24:J24 = 1, 2, 3, 4, 5 (blue). D41:H41 = 4%, 4.5%, 5%, 5.5%, 6% (blue). C42 = =$C$16-0.02, C43 = =$C$16-0.01, C44 = =$C$16, C45 = =$C$16+0.01, C46 = =$C$16+0.02. B41 = "Terminal growth →", B42 = "WACC ↓".

**Number formats:** amounts #,##0.0; ratios and rates 0.0%; days 0; discount factors 0.000; value per share #,##0. Bold labels for section titles and totals.

**Tutor Map:** B2 title "Tutor Map: Kaveri Foods financial model". Row 4, columns B to N: one box per module ("0 Setup" … "12 Sensitivity"), grey fill. B6: "Now: Module X · Step Y · <step title>" in bold. B7: a hyperlink "Go to <Sheet>!<cell>" to the first yellow cell of the current step.