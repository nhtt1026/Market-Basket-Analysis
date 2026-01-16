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
### Overall output
The association analysis produced **36 rules**. Three patterns stand out as the most actionable:

<img width="2534" height="1182" alt="image" src="https://github.com/user-attachments/assets/ecad6cb8-03f5-491b-9a9b-f3c748ae9d90" />

### 1) Toothbrush ⇄ Perfume (Strongest Pair):
- **Max Lift:** **3.60** (highest)  
- **Support:** 2.18% (4,364 baskets)  
- **Confidence:** 32.40% (Toothbrush → Perfume), 24.26% (Perfume → Toothbrush)  
- These two items appear together far more often than expected, making them the clearest “buy-together” opportunity.

### 2) Greeting Cards → (Magazine & Candy Bar):
- **Lift:** 2.68  
- **Support:** 1.67%  
- **Confidence:** 45.86%  
- Greeting card purchases frequently come with a "small treat & read” add-on pattern.

### 3) Pencils → Greeting Cards:
- **Lift:** 1.48  
- **Support:** 2.92%  
- **Confidence:** 21.67%  
- A practical, repeatable stationery link that occurs often enough to promote.


