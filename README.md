# 🚚 Delivery Optimization (NLP & Operations Research)

This project solves an operational optimization problem based on delivery shipment data from **Nasr City, Cairo** (11-10-2025 to 16-10-2025).  
It focuses on extracting structured address fields, estimating missing delivery locations, and optimizing courier assignment to minimize operational area.

---

## 📌 Project Objectives

### ✅ Task 1: Extract Meaningful Address Fields
Extract useful structured fields from noisy Arabic addresses, including:
- Building Number
- Street Name
- District
- Area Details
- Floor
- Apartment
- Landmark

A rule-based NLP preprocessing pipeline was applied using Arabic normalization + regex extraction.

---

### ✅ Task 2: Estimate Delivery Locations (16-10-2025)
For deliveries on **16-10-2025**, latitude and longitude were fully retracted.

To estimate locations, the system uses:
1. **Exact street matching** using historical centroid coordinates.
2. **TF-IDF + Cosine Similarity matching** against historical addresses.
3. **Fallback strategy** for low-confidence predictions.

Each prediction includes a **confidence score (0–100)**.

---

### ✅ Task 3: Optimize Shipment Distribution to Couriers
For **15-10-2025**, 308 deliveries are distributed to **20 couriers** under constraints:

- Each courier must handle **10 to 20 deliveries**
- Objective: **Minimize total operational area**
- Courier operational area is calculated using **Convex Hull polygons**

The optimization uses:
- KMeans clustering (initial assignment)
- Iterative rebalancing to satisfy courier constraints
- Convex Hull area approximation in km²


