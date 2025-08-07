# Title: Moving Past the Data: Challenges in Adopting AI in Industry  
**Author:** Khalid Taha  
**Date:** 7 August 2025  

## Abstract

High-quality data is crucial for the successful adoption of AI, yet many initiatives falter due to various other factors. This paper highlights four key structural challenges that obstruct AI implementation: complexity of integration, organizational inertia, ambiguity regarding return on investment, and an excessive focus on data perfection. Insights from industry benchmarks and recent studies suggest that achieving AI readiness requires a holistic approach that goes beyond merely having clean data; it demands systemic alignment throughout the organization.

## 1. Introduction

Some industry experts link the failures of AI projects to issues with data quality. Yet, few studies systematically assess this belief, and many documented failures stem from broader challenges that aren't solely related to data inputs. In their 2023 study, Zha et al. introduce a framework for data-centric AI that evaluates readiness in three key areas: the development of training data, the preparation of inference data, and ongoing maintenance. They suggest that placing too much emphasis on model architecture has shifted focus away from critical data and systems engineering challenges. Their findings advocate for a more comprehensive view that emphasizes the need for alignment between technical and organizational systems, rather than just improved datasets.

## 2. Integration Complexity

AI systems often need to work alongside legacy software, batch processes, and disconnected workflows. Many operational systems struggle to handle real-time outputs or incorporate predictive decisions effectively. This challenge is illustrated by Mazumder et al. (2024) in their study of the Gen-QOT inventory control framework. They model realistic constraints such as specific lead times from suppliers, rules for batch shipments, and patterns of disruption. Even when using clean, simulated data, the outputs of these models can fall flat unless they are seamlessly integrated into existing business workflows. The main hurdle isn't the quality of the data; instead, it's the difficulty of applying predictions to decision-making in legacy systems. Numerous projects come to a standstill because downstream systems cannot utilize model outputs.

## 3. Organizational Inertia

The success of AI hinges on the people involved and the processes in place, not merely on the algorithms themselves. Often, internal resistance, insufficient training, and ambiguous accountability can hinder deployment efforts. 

The DataPerf suite (Mazumder et al., 2023) evaluates data-focused interventions in areas like vision, speech, and retail. Their research indicates that human-driven initiatives, such as targeted data cleaning and effective sample selection, led to performance improvements that surpassed those achieved through model tuning. Organizations that engage in ongoing collaboration with their data teams generally outpace those that strive for a flawless dataset from the start.

Ultimately, organizational readiness—characterized by teamwork, iterative development, and clear ownership—proves to be more influential than infrastructure alone.

## 4. Economic Friction and ROI Ambiguity

Many businesses are often reluctant to adopt AI due to uncertainties around its short-term value. Complex solutions frequently struggle to provide quick or apparent returns. In a study by Chandra et al. (2024), various forecasting models were assessed using retail data. Surprisingly, simpler machine learning methods, such as LightGBM and XGBoost, which are based on decision trees, outperformed deep neural networks. These models not only trained faster and offered more precise explanations for their outcomes but also required considerably fewer resources. Their success stemmed not from sophisticated data or computing power, but from their practical fit with real-world deployment challenges. By selecting models that align closely with business needs rather than focusing solely on technical innovation, companies can effectively lower costs and mitigate risks.

## 5. Tolerance of AI to Imperfect Data

AI has shown remarkable resilience, performing effectively even in situations where data is noisy, incomplete, or subjected to censorship. A notable development in this area is the FreshRetailNet-50K benchmark introduced by Singh et al. (2024) for demand forecasting during stockouts. Their research explored various time-series models like TimesNet and ImputeFormer, which leverage attention mechanisms to fill in the gaps left by missing demand signals. Despite a significant 30% data loss, these models managed to maintain low bias and high accuracy, challenging the traditional belief that missing data renders forecasting unreliable. Thanks to these advancements, modern models are now equipped to handle the messiness often found in real-world scenarios. As a result, businesses can begin their data-driven initiatives with imperfect information rather than holding out for complete data quality.

## 6. Conclusion

The successful deployment of AI involves more than just having clean data. It requires the seamless integration of existing systems, alignment with business priorities, and strong collaboration among teams. Benchmarks like DataPerf and FreshRetailNet-50K highlight that readiness stems from organizational adaptability, not merely the quality of input data. Enhancing AI maturity entails investing in system design, refining organizational processes, and embracing iterative practices—not solely focusing on datasets.

## References

Zha, D., Bhat, Z. P., Lai, K. H., Yang, F., Jiang, Z., Zhong, S., & Hu, X. (2023). Data-centric Artificial Intelligence: A Survey. *arXiv preprint arXiv:2303.10158*.

Mazumder, M., et al. (2023). DataPerf: Benchmarks for Data-Centric AI Development. *arXiv preprint arXiv:2207.10062*.

Mazumder, M., et al. (2024). Learning an Inventory Control Policy with General Inventory Arrival Dynamics. *arXiv preprint arXiv:2405.17533*.

Chandra, R., Ruj, S., & Pal, A. (2024). Comparative Analysis of Modern Machine Learning Models for Retail Sales Forecasting. *arXiv preprint arXiv:2506.05941*.

Singh, K. K., et al. (2024). FreshRetailNet-50K: A Stockout-Annotated Censored Demand Dataset for Latent Demand Recovery and Forecasting in Fresh Retail. *arXiv preprint arXiv:2405.10468*.
