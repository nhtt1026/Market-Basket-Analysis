## Project Overview:
This project uses market basket analysis (association rule mining) to identify products that are frequently purchased together and translate those relationships into practical promotion ideas.

The business focus is a retail chain looking to design promotions for items commonly bought together across Health & Beauty Aids and Stationery, using 3 months of point-of-sale transactions (400k+ transactions). 

## Business problem:
Retail promotions work best when they reflect real customer shopping behaviour. The goal is to discover product affinities that can be used for:
- cross-selling and bundle design
- better placement of complementary items
- simple promotional mechanics that increase basket size without heavy discounting

## Data:
**Dataset:** Transactional basket data (1 row = 1 item in 1 transaction). 

**Core fields and roles**
- `PurchaseId` (ID): transaction identifier   
- `Item` (Target): product purchased   
- `Outlet` (Rejected): store identifier (not used in modeling)   
- `Amount` (Rejected): quantity (not used in modeling)   

Products include a defined set across both departments (e.g., toothbrushes, toothpaste, perfume, greeting cards, pens, pencils, magazines, etc.). 

## Method (Association rule mining):
I used association rule mining in SAS Enterprise Miner to generate rules and evaluate them using 3 standard metrics:   
- **Support:** How often items appear together  
- **Confidence:** How often the consequent appears when the antecedent appears, used to measure the reliability (If X, then Y)
- **Lift:** How much stronger the relationship is compared to random co-occurrence (Lift > 1: positive correlation, Lift < 1: negative, Lift = 1: independent)

## Key results:

The model generated **36 association rules**. For the actual execution, we should prioritize the rules that combine:
**(1) strong affinity (Lift)**
**(2) commercial scale (Support/basket count)**
**(3) simple activation** (easy for stores to run and customers to understand).

<img width="2534" height="1182" alt="image" src="https://github.com/user-attachments/assets/ecad6cb8-03f5-491b-9a9b-f3c748ae9d90" />

### 1) Toothbrush ⇄ Perfume (Strongest Pair):
- **Max Lift:** **3.60** (highest)  
- **Support:** 2.18% (4,364 baskets)  
- **Confidence:** 32.40% (Toothbrush → Perfume), 24.26% (Perfume → Toothbrush)  
- These two items appear together far more often than expected, making them the clearest “buy-together” opportunity.

### 2) Greeting Cards → (Magazine & Candy Bar): for Gift + Treat
- **Lift:** **2.68–2.80** (varies by direction)  
- **Support:** **~1.67%**  
- **Confidence:** **45.86%** (Greeting Cards → Magazine & Candy Bar)
- Greeting card purchases frequently come with a "small treat & read” add-on pattern.

### 3) Candy Bar ⇄ Toothpaste (High-Frequency Add-on Pair):
- **Lift:** **~1.45**  
- **Support:** **~3.98%**  
- This is a repeatable, high-frequency pairing that fits impulse add-on behaviour and is simple to activate at checkout or endcaps.

---

## Promotion Recommendations (Bundles):

### Bundle 1: “Fresh & Fragrant” (Toothbrush + Perfume):
- **Mechanic:** Buy both, get a small discount or bonus points.
- **Why it works:** Highest Lift in the results (3.60) + clear cross-sell story as the personal care deals with a grooming & a hygiene item.
- **Placement:** Cross-display in oral care / personal care or “Complete the routine” signage.

### Bundle 2: “Card + Treat + Read” (Greeting Cards + Magazine/Candy Bar):
- **Mechanic:** Buy a greeting card and get an offer on a magazine or candy bar  
  *(or “Buy 2, save on the 3rd” across these items during peak occasions)*.
- **Why it works:** High confidence (45.86%) indicates greeting cards act as a strong trigger for small add-ons.
- **Placement:** Seasonal display near greeting cards (birthdays, holidays, back-to-school), a practical “one-stop” shopping mission.

### Bundle 3: “Brush & Bite” Add-on (Toothpaste + Candy Bar):
- **Mechanic:** “Add 1 more item for a small discount” or “Buy 2, save on the 3rd.”  
- **Why it works:** Higher support (~3.98%) gives commercial scale, and the offer is easy to execute for easy-to-add items. This is suitable for a low-friction upsell mechanic.   
- **Placement:** Checkout lanes or high-traffic impulse zones where the add-ons perform well.

---

## Notes / Limitations:
- This dataset is scoped to a defined list of items, which is useful for learning and controlled insight generation, but it limits category breadth.
- Results should be validated with a simple A/B test in stores (or in loyalty data) to confirm incremental uplift from bundles.
