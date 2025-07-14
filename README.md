# CIND-820---Capstone-Customer-Segmentation-Profitability-Forecasting-Retail-Marketing

---

## Practical Applications
- Targeted Marketing Campaigns for Cluster 0:
  - Cluster 0’s high revenue ($8,739.37, non-churned: $17,064.81) and multi-channel engagement make it the priority for marketing. The Friedman test’s block-specific insights (Online/Social Media: $14,258.55–$14,250.46, Groceries: $14,395.04, Buy One Get One Free: $14,561.83, Winter: $14,626.67) guide precise campaigns:
    - Digital Campaigns:
      - Leverage Cluster 0’s high online engagement (online_purchases: 0.223115 from PC2, PCA loadings [0.211415 for PC1, 0.227419 for PC2]) and social media activity (promotion_channel_social_media: 0.003437 from PC1, PCA loadings [0.003437 for PC1, 0.0 for PC2]) to deploy social media ads for Groceries and Clothing during Winter and Fall. Use Buy One Get One Free offers to drive transactions, capitalizing on Cluster 0’s responsiveness (transactions: 58.34 for Buy One Get One Free).
    - Personalized Messaging:
      - Target Cluster 0’s distant shoppers (distance_to_store: 0.300149 from PC2, PCA loadings [0.024249 for PC1, 0.305939 for PC2]) with personalized email or app-based promotions, emphasizing convenience and digital accessibility, aligned with their high engagement (product_review_count: 0.167017 from PC1, PCA loadings [0.351882 for PC1, 0.032676 for PC2]; customer_support_calls: 0.110766 from PC1, PCA loadings [0.233369 for PC1, 0.265792 for PC2]).
    - Engagement-Driven Promotions (Priority):
      - Prioritize loyalty rewards and exclusive previews for Cluster 0 due to its high transaction frequency (total_transactions: 0.255302 from PC2, PCA loadings [0.018509 for PC1, 0.260227 for PC2]) but low membership duration (membership_years: -0.097108 from PC1, PCA loadings [0.204593 for PC1, 0.054198 for PC2]). This indicates that Cluster 0 customers are highly active but not necessarily long-term members, making retention through engagement-driven incentives critical to prevent churn and sustain their high-value contributions ($8,739.37 total mean sales revenue). Offer exclusive product previews or tiered loyalty rewards (e.g., bonus points for frequent online purchases) via social media and online platforms to encourage repeat purchases and foster long-term loyalty.
    - Deploy generative AI models to craft hyper-personalized social media ads for Cluster 0’s multi-channel shoppers targeting Groceries ($14,395.04) and Buy One Get One Free offers ($14,561.83) in Winter ($14,626.67) for peak revenue.
- Retention Strategies:
  - Loyalty Programs
    - Address Cluster 0’s churn sensitivity (89% revenue drop at 90% churn) with loyalty programs tailored to its multi-channel, high frequency, engaged shoppers with distance store access profile.
      - Implement proactive support via chatbots or dedicated agents to maintain high-value relationships.
      - Implement loyalty programs to encourage repeat purchases.
      - Implement loyalty progrms to foster long-term loyalty
          
- Real-Time Customer Identification:
  - Deploy the further hyperparameter tuned Random Forest - Balanced - All Attributes model (recall: 0.84) in CRM systems for real-time classification of Cluster 0 customers.

- ***Together, these strategies maximize value from Cluster 0 by safeguarding its high revenue contribution through timely support, personalized engagement, and sustained customer loyalty.***

---
- Operational Optimization: To ensure equitable resource allocation, focus should also be allocated to Clusters 1 and 2 alongside Cluster 0.
    - Optimize in-store strategies for Cluster 1 (total_items_purchased 0.214929) by enhancing store layouts and inventory near physical locations.
    - For Cluster 2 (discount_applied 0.203976), design loyalty-based discount campaigns to re-engage infrequent shoppers, maximizing ROI.





