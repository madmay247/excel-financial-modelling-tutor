# Excel Financial Modelling Tutor

**A Claude skill that teaches you to build a complete 3-statement financial model and DCF valuation in Excel, one formula at a time.**

Most modelling courses show you a finished model. This one makes you build it. Claude sets up the workbook, highlights the exact cells to work in, asks you one step at a time, checks your formula, and only moves on when it's right. By the end you will have typed every formula in a fully linked model yourself.

---

## What you'll build

A full model for **Kaveri Foods Ltd**, a made-up Indian packaged-foods company (figures in INR crore):

- **Income statement:** three years of history (FY23 to FY25) and five years of projections (FY26 to FY30)
- **Balance sheet:** projected so that it balances in every year
- **Cash flow statement:** linked to the other two statements
- **Supporting schedules:** working capital, fixed assets (capex and depreciation) and debt
- **DCF valuation:** FCFF, CAPM cost of equity, WACC, terminal value, and equity value per share
- **Sensitivity table:** value per share across WACC and terminal growth, coloured as a heatmap

## Course outline

The course has 89 steps in 13 modules. Each step takes about a minute.

| # | Module | What you do |
|---|--------|-------------|
| 0 | Setup | Get to know the workbook and the colour code |
| 1 | Historicals | Link three years of IS and BS data and build the balance check |
| 2 | Ratios | Growth, margins, and receivable, inventory and payable days |
| 3 | Assumptions | Set the revenue growth and COGS drivers |
| 4 | Revenue to EBITDA | Project the top half of the income statement |
| 5 | Working capital | Project receivables, inventory and payables, and the change in NWC |
| 6 | Fixed assets | Capex, depreciation and the net block roll-forward |
| 7 | Debt | Repayments, closing debt and interest on the average balance |
| 8 | Profit | Tax and net profit, and extend the ratios |
| 9 | Cash flow | CFO, CFI, CFF and closing cash |
| 10 | Balance sheet | Link everything until the balance check is zero in every year |
| 11 | DCF valuation | FCFF, WACC, terminal value and value per share |
| 12 | Sensitivity | A two-way table with mixed references, as a heatmap |

## How a lesson works

1. Claude highlights the cells to work in yellow and asks one question.
2. You type the formula in Excel, then answer **Done**, **Give me a hint** or **Why does this matter?**
3. Claude checks the result:
   - **Correct:** the highlight clears and the next step starts.
   - **Wrong:** the cell turns red, with a one-line explanation of how to fix it.
   - **Stuck:** two hints of increasing detail, then the exact formula.

A **Tutor Map** sheet tracks your progress, so you can stop at any time and say *"continue the modelling course"* to pick up where you left off. You can also jump straight to any module, and Claude fills in the earlier steps for you.

## Installation

### Claude Code

```bash
git clone https://github.com/madmay247/excel-financial-modelling-tutor.git
```

```bash
cp -r excel-financial-modelling-tutor/excel-financial-modelling-tutor ~/.claude/skills/
```

### Claude.ai / Claude desktop

1. Zip the inner `excel-financial-modelling-tutor/` folder (the one containing `SKILL.md`).
2. Go to **Settings → Capabilities → Skills** and upload the zip.

## Usage

Works best with the **Claude for Excel** add-in, where Claude builds and checks the workbook live. Once the skill is installed, say:

> Start the financial modelling course.

In plain Claude chat, without a live workbook, Claude checks your work from uploaded `.xlsx` files or from screenshots with formulas shown (`Ctrl + backtick`).

## Who it's for

- Students preparing for finance, equity research or investment banking roles
- Analysts who want to understand how the three statements link together
- Anyone who has read about DCFs but never built one end to end

No prior modelling experience is needed. Basic Excel (typing a formula, dragging the fill handle) is enough.

## Repository structure

```
excel-financial-modelling-tutor/
├── README.md
└── excel-financial-modelling-tutor/
    └── SKILL.md      # Full course script, layout spec and tutor rules
```

## Notes

- Kaveri Foods is fictional. All figures are for practice only and are not investment advice.
- The valuation inputs (risk-free rate, ERP, beta) are illustrative. Use current market data for real work.
- The skill refers to `assets/kaveri-starter.xlsx` and `assets/kaveri-solution.xlsx` for chat-only use. These workbooks aren't in this repo yet.

## Contributing

Issues and pull requests are welcome. Every expected value in the script has been checked against a solved model, so if you change a formula or an input, recheck the expected values in every later step.
