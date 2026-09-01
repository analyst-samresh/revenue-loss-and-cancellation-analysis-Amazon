# Revenue Loss & Cancellation Analysis - Amazon(2022)

The analysis is focused on identifying the scale of financial impact - cancellation and revenue loss across Amazon India's full year 2022 sales data.

---

## Business Problem

**The Revenue Assurance Manager at Amazon India is concerned about revenue leakage from cancelled orders despite overall business growth. He wants to understand the scale of financial loss with actual numbers, "how many orders are being cancelled", "what is the total financial impact", and an assessment of whether the Cancellation & Revenue Loss rates are at an alarming stage or within a manageable range. He also needs to identify which geographies, product categories, sizes, and shipping types require priority attention.**

The goal is not to build a model — it is to understand the hidden pattern, scale of financial impact and area of improvement for business to action on it.

---

## Dataset

- **Source:** Amazon India Sales Data — Full Year 2022 (Kaggle)
- **Size:** 1,28,975 orders (Jan 1 – Dec 31, 2022)
- **Key Fields:** Order ID, Date, Status, Category, Size, Fulfilment Type, Courier Status, Amount, Ship State, Ship City, Promotions.

---

## Tools Used

- Python (Pandas, NumPy, Matplotlib, Seaborn, FuzzyWuzzy, BhartAddress)
- Jupyter Notebook
- Qlik Sense
- Storytelling for reporting (PDF)
- Excel (Initial data inspection)

---

## Data Cleaning Highlights

- Found 69 unique state values (expected ~28-36 Indian states), cleaned variations (e.g., "rajeshthan" → "Rajasthan", “ap” → “Arunachal Pradesh”, “pb” → “Punjab”) 
- Missing states are flagged as “Unknown”, final states 37 including “Unknown” 
- Missing amount is considered as cancelled if “status” contains (Cancelled, Returned and Rejected) 
- **Cancellation defined as:** Cancelled and Rejected orders

---

## Key Findings

### Overall Impact
| Metric | Value |
|---|---|
| Total Orders | 1,28,975 |
| Cancelled Orders | 18,332 (14.21%) |
| Revenue Expected | ₹7,85,92,678 |
| Revenue Lost | ₹69,19,284.3 (8.8%) |
| Avg. Order Value | ₹449.13 |

### Where is the problem? (Geographic)
- Top 5 states — **Maharashtra, Andra Predesh, Karnataka, UP, Tamil Nadu** drive **57.5% of total revenue loss**.
- These states have *lower* cancellation rates (13–15%) than remote areas, but their volume makes them the priority.
- Remote/hill states (Lakshadweep, Ladakh, Mizoram) show higher rates (18–30%) but minimal business impact

### Which categories? (Categorical)
- **Top 3 categories** — Set, Kurta, Western Dress account for 91.81% of total revenue loss.
- *Set* alone contributes 50% of total revenue loss (₹34.7L), fixing Set category would solve half of the problem.

### Is it getting worse/stable/improving? (Trend)
- Cancellation rate is **stable at 13–16% throughout the year**, this is a process/structural issue, not a seasonal one

---

## Recommendations

1. **GEOGRAPHIC FOCUS** - Concentrate revenue recovery efforts on Maharashtra, Karnataka, and Andhra Pradesh first. These three states account for approximately 45% of total revenue loss, improving these 3 states would recover singnificant revenue impact.

2. **EXPAND PROMOTIONAL OFFERS**- Non-Promotional orders has 100x higher cancellation rate than promotional orders, the most impactful single intervention available. Currently 38% of orders have no promotion with cancellation rate at 36.7%. Extending promotional coverage to these orders could recover an estimated ₹50+ Lakh in annual revenue.

3. **MIGRATE HIGH-VALUE CATEGORIES FROM MERCHANT TO AMAZON** - Merchant fulfilment cancels at 17.5% vs Amazon at 12.8%, fulfilling high-volumne product categories Set, Kurta and Western Dress by Amazon would save 4.7% of revenue impact.

4. **INVESTIGATE JNE3797-KR (WESTERN DRESS)** - This single SKU accounts for ₹2.95 Lakh in revenue loss across all sizes. Conduct immediate product quality review, verify sizing accuracy, and review product photography and description for accuracy.

5. **ADDRESS SIZE MISMATCH** - XS and S sizes cancel at the highest rates (16.7% and 15.2%), whereas XS, S, M and L drives the cancellation rate between 14% - 17% approximately, investigate size guide and customer's reviews to this sizes across all categories to lower down the cancellation rate.

---

## Project Structure
```
revenue-loss-and-cancellation-analysis/
├── Dashboards/
│   ├── Executive Summary.pdf
│   ├── Geographic Analysis.pdf
│   └── Product Analysis.pdf
├── Dataset/
│   ├── Amazon raw data.csv
│   └── Amazon_clean_data.csv
├── Notebook (Data Cleansing)/
│   └── Data_Assessment_&_Cleanining_Amazon.ipynb
├── Qlik App/
│   └── Amazon Project.qvf
├── Report on Revenue Loss & Cancellation - Amazon.pdf
└── README.md
```

---

## Limitations

- 11 Orders with missing courier_status shows shipped but amount is missing and quantity = 0. This indicates potential inconsistency in status, courier_status, quantity and amount.
- 230 Orders with missing amount shows 91% shippied while contradicting with courier_status and shows approximately ~57% either Unshipped or ~43% Cancelled.
- No cancellation reason codes available in raw data hence cannot determine whether cancellations were customer-initiated or system-initiated.

---

## Author

**Samresh Mandal** — Data Analyst  
LinkedIn : [https://www.linkedin.com/in/samresh-mandal/](#) |
GitHub : [https://github.com/analyst-samresh?tab=repositories](#)  
*Analysis completed: March 2026*
