## Project overview
This project uses market basket analysis (association rule mining) to identify products that are frequently purchased together and translate those relationships into practical promotion ideas.

The business focus is a retail chain looking to design promotions for items commonly bought together across **Health & Beauty Aids** and **Stationery**, using three months of point-of-sale transactions (400k+ baskets). 

## Business problem
Retail promotions work best when they reflect real customer shopping behaviour. The goal is to discover product affinities that can be used for:
- cross-selling and bundle design
- better placement of complementary items
- simple promotional mechanics that increase basket size without heavy discounting

## Data
**Dataset:** transactional basket data (one row = one item in one transaction). 

**Core fields and roles**
- `PurchaseId` (ID): transaction identifier   
- `Item` (Target): product purchased   
- `Outlet` (Rejected): store identifier (not used in modeling)   
- `Amount` (Rejected): quantity (not used in modeling)   

Products include a defined set across both departments (e.g., toothbrushes, toothpaste, perfume, greeting cards, pens, pencils, magazines, etc.). 
