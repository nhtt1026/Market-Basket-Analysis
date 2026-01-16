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
The model generated **36 valid association rules** from the transaction dataset. 

### Strongest association (Maximum lift):

<img width="2534" height="1182" alt="image" src="https://github.com/user-attachments/assets/ecad6cb8-03f5-491b-9a9b-f3c748ae9d90" />

- **Maximum Lift:** **3.60**   
- This maximum Lift is achieved by 2 reciprocal rules:  
  - Perfume → Toothbrush (Lift 3.60; Support 2.18%; Transaction Count 4,364)   
  - Toothbrush → Perfume (Lift 3.60; Support 2.18%; Transaction Count 4,364)   

**Key Takeaway**:
- Because Support and Transaction Count are identical, these 2 rules are 2 directional views of the same co-occurrence pattern.
- The confidence differs by direction:
  - When a customer buys Perfume, ~24% of the time they also buy a Toothbrush in the same basket.
  - When a customer buys a Toothbrush, ~32% of the time they also buy Perfume in the same basket.
- This difference is normal because one product is purchased more often overall, so starting from one side can make the “add-on” rate look higher



