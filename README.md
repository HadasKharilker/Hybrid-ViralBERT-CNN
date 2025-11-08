If you use or distribute it, please include a reference to the original repository and acknowledge the author.

# **K-pop Tweet Virality Prediction using a Hybrid ViralBERT-CNN Model**

This project introduces a novel hybrid model, **Hybrid ViralBERT-CNN**, designed to predict the virality of K-pop related tweets on X (formerly Twitter) with state-of-the-art accuracy. By combining architectural enhancements with an advanced data preprocessing pipeline, this model significantly outperforms existing baselines.

## **1\. Background**

The K-pop industry is a global phenomenon, and X serves as a primary hub for fan engagement. The ability to predict which tweets will go viral is invaluable for artists, labels, and marketers. However, general virality prediction models like ViralBERT (49% accuracy) often fail to capture the unique dynamics of K-pop fandoms, such as intense community mobilization and specific cultural hashtags.

This project addresses this gap by adapting and enhancing existing NLP models specifically for the K-pop domain.

## **2\. Dataset**

A specialized, domain-specific dataset was created for this research.

* **Content:** 9,251 English-language K-pop tweets.  
* **Collection:** Gathered over two months using K-pop specific hashtags (\#BTS, \#Blackpink), keywords, and fandom terms to ensure 100% relevance.  
* **Features:** Each tweet includes text, user metrics (followers, verified status), and engagement metrics measured after 24 hours (retweets, likes, views).

This focused dataset provides a more coherent learning environment compared to the broad, multi-domain datasets used in previous studies.

## **3\. Methodology: A Two-Phase Experimental Approach**

The core innovation of this project is the **Hybrid ViralBERT-CNN model**. Its development followed a systematic, two-phase approach.

### **Phase 1: Architectural Modifications**

The initial phase focused on integrating a Convolutional Neural Network (CNN) into the ViralBERT architecture to better identify complex patterns in the data. Four different architectures were tested:

1. **Original ViralBERT (Baseline):** The original model using BERTweet, RoBERTa, and an MLP classifier.  
2. **CNN-Enhanced ViralBERT:** Replaced the MLP processing layers with 1D CNN layers.  
3. **CNN Classifier Replacement:** Fully replaced ViralBERT's MLP classifier with a CNN.  
4. **Advanced CNN-Enhanced ViralBERT:** An optimized CNN design with skip connections to preserve original feature information.

Finding: Purely architectural changes yielded only marginal improvements. The best model (Model 4\) achieved an F1-score of just **49.9%**, indicating that architecture alone could not overcome limitations in the input data quality.

### **Phase 2: Advanced Preprocessing Integration**

Inspired by the success of the CNN-IndoBERT model (91.4% accuracy on Indonesian data), the second phase focused on data quality. The key innovation was adapting the comprehensive preprocessing methodology from Benedecas & Girsang (2024) to our English K-pop dataset.

This five-stage pipeline includes:

* HTML tag and entity removal.  
* URL and @mention normalization.  
* Special character standardization.  
* Lowercasing for linguistic consistency.  
* Porter stemming and stop-word removal.

This pipeline cleans the noisy social media text, allowing the model to focus on meaningful semantic patterns.

## **4\. Experimental Results**

Combining the **CNN-Enhanced ViralBERT** architecture (from Model 2\) with the **advanced preprocessing pipeline** (from Phase 2\) resulted in a dramatic performance increase.

| Model | F1 Score (%) | Accuracy (%) |
| :---- | :---- | :---- |
| Model 1: Original ViralBERT | 47.74% | 48.96% |
| Model 2: CNN-Enhanced ViralBERT | 46.94% | 48.69% |
| Model 3: CNN Classifier Replacement | 44.39% | 46.61% |
| Model 4: Advanced CNN-Enhanced ViralBERT | 49.91% | 49.71% |
| **Model 5: CNN-Enhanced w/ IndoBERT Preprocessing (Final Method)** | **99.82%** | **99.71%** |

## **5\. Conclusion**

The results demonstrate that **data quality is more impactful than architectural complexity** for this task. While the initial CNN integration was sound, its potential was only unlocked by the advanced preprocessing pipeline adapted from CNN-IndoBERT. This methodology successfully cleans and standardizes noisy tweet data, enabling the model to achieve near-perfect prediction accuracy in the K-pop domain.

This work validates the findings of Benedecas & Girsang and successfully extends their methodology from Indonesian to English, achieving state-of-the-art results.

## **6\. Limitations and Future Work**

* Domain Generalization: The model's exceptional performance is specific to K-pop. Future work should test its effectiveness on the general English domains originally targeted by ViralBERT to assess its cross-domain generalization.  
* Feature Analysis: Investigate which specific linguistic patterns in K-pop discourse (e.g., fan expressions, code-switching) are most predictive after preprocessing.

## **7\. References**

1. Rameez, R., et al. (2022). *ViralBERT: A user focused BERT-based approach to virality prediction.*  
2. Benedecas, H. R. A., & Girsang, A. S. (2024). *Virality Prediction on Twitter Using Combined CNN and BERT Models.*  
3. Benson, M. (2022). *Predicting virality of online news articles using textual content.*
