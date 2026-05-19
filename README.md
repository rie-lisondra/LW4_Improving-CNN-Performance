# LW4_Improving-CNN-Performance

###### [https://colab.research.google.com/drive/1F-j-5BSqdlWu90jitiYSE0U9LtxYDO7f?usp=sharing)

---

## Guide Questions (Student Reflection & Explanation) 

## A. Model Evaluation Analysis

###  1. What were the weakest-performing classes based on the confusion matrix?
  <div align="justify">
    Based on the confusion matrix results, the weakest-performing class in the Baseline Model was bulrush_scirpus, which obtained a recall score of 0.60. This indicates that the model failed to correctly identify many actual instances of that class. In the Improved Model, the performance of some classes decreased further, particularly arrow_arum, which had a recall score of 0.36, and red_mangrove, which showed a low precision score of 0.48. These results suggest that the model experienced significant confusion between visually similar plant classes.
  </div>

###   2. How did Precision, Recall, and F1-score vary across classes?
  <div align="justify">
    The Precision, Recall, and F1-score varied depending on the complexity and visual similarity of the plant classes. In the Good Model using MobileNetV2, the scores were consistently high, ranging from 0.90 to 1.00 across most classes, indicating balanced and reliable classification performance. However, in the Baseline and Improved Models, classes with similar leaf structures and background patterns, such as arrow_arum and red_mangrove, showed noticeable variations. Some classes achieved high precision but low recall, which means the model was accurate when predicting the class but failed to detect all actual instances of it.
  </div>

###    3. What does a low recall indicate in your model?
   <div align="justify">
     A low recall indicates that the model produced a high number of False Negatives. This means that many actual instances of a specific class were incorrectly classified as another class. In other words, the model failed to recognize several samples that truly belonged to that category.
   </div>

###    4.  How does AUC score reflect model performance compared to accuracy? 
   <div align="justify">
     The AUC score reflects the model’s ability to distinguish between classes across different classification thresholds, whereas accuracy only measures the percentage of correct predictions at a single threshold. In the Good Model, the AUC score reached 0.9994, which indicates excellent class separability and highly reliable prediction capability. Even if the accuracy value is slightly lower, a high AUC score demonstrates that the model can consistently differentiate between classes effectively.
   </div>
  
## B. Model Improvement
###  5. How did data augmentation affect validation accuracy?
  <div align="justify">
    Data augmentation had different effects depending on the model architecture used. In the Improved manual CNN model, strong augmentation techniques such as rotation, zooming, and contrast adjustment initially made the classification task more difficult, resulting in a temporary decrease in validation accuracy to around 70% compared to the Baseline Model. However, in the Good Model using MobileNetV2, data augmentation improved feature generalization and helped the model achieve approximately 97% validation accuracy while reducing overfitting.
  </div>
  
###  6. Why is Batch Normalization important in CNNs? 
  <div align="justify"> 
    Batch Normalization is important in CNNs because it stabilizes the learning process by normalizing the inputs of each layer during training. This allows the model to train faster, use higher learning rates, and improve convergence. In addition, Batch Normalization acts as a form of regularization, helping reduce overfitting and improving the overall performance of the model.
  </div>

###  7. What role did Dropout play in improving your model? 
  <div align="justify"> 
    Dropout improved the model by randomly deactivating neurons during training, particularly at rates of 0.4 and 0.5 in the implemented architecture. This prevented the network from becoming overly dependent on specific neurons or image features. As a result, the model learned more robust and generalized feature representations, which contributed to better performance on unseen data.
  </div>

###  8. How did Early Stopping prevent overfitting? 
  <div align="justify"> 
    Early Stopping prevented overfitting by monitoring the validation loss during training. When the validation loss stopped improving for eight consecutive epochs, the training process was automatically halted, and the best-performing model weights were restored. This prevented the model from memorizing noise and unnecessary patterns in the training dataset, ensuring better generalization performance.
  </div>

## C. Performance Comparison

###  9. What improvements were observed after modifying the model?
   <div align="justify">
    After modifying the model, significant improvements were observed in classification accuracy and overall performance. The Good Model using MobileNetV2 achieved approximately 97.13% accuracy, which was a substantial improvement compared to the Baseline Model’s 90% accuracy. Additionally, the confusion between visually similar plant species was greatly reduced, resulting in more accurate and consistent predictions.
  </div>
  
###  10. Which enhancement contributed the most to performance improvement? Why?
   <div align="justify">
     The enhancement that contributed the most to performance improvement was Transfer Learning using MobileNetV2. Since MobileNetV2 was pre-trained on the ImageNet dataset, it already possessed strong feature extraction capabilities for detecting edges, textures, and shapes. These pre-trained features provided a significant advantage over training a CNN model from scratch using a relatively limited dataset, resulting in higher accuracy and better generalization.
  </div>

###  11. Did the gap between training and validation accuracy decrease? Explain.
   <div align="justify">
     Yes, the gap between training and validation accuracy decreased significantly in the Good Model. The training accuracy was approximately 98%, while the validation accuracy reached around 97%, indicating strong generalization capability. This small gap suggests that the model learned meaningful patterns from the dataset without excessively memorizing the training data. The combination of Transfer Learning, Dropout, and data augmentation effectively minimized overfitting.
  </div>
  
## D. Explainability (Grad-CAM Integration)
###   12.  How did Grad-CAM help in understanding model predictions?
   <div align="justify">
    Grad-CAM helped in understanding the model predictions by generating heatmaps that highlighted the image regions most influential to the classification decision. This allowed visualization of whether the model focused on relevant plant features, such as leaf shapes and textures, rather than irrelevant background elements.
  </div>

###   13.  Did the improved model focus on more relevant regions? Provide evidence.
   <div align="justify"> 
     Yes, the improved model focused on more relevant regions of the images. Based on the Grad-CAM outputs from samples 001 to 020, the heatmaps became more concentrated on the unique botanical features of the plants as prediction confidence increased, particularly for predictions with confidence scores between 99% and 100%. The visualizations showed reduced attention on irrelevant image areas, such as water backgrounds or image borders, indicating that the model learned more meaningful features.
  </div>

###   14.  Why is explainability important in real-world AI applications? 
   <div align="justify">
    <p>
      Explainability is important in real-world AI applications because it increases transparency, trust, and accountability. Users and stakeholders are more likely to trust AI systems when they understand how predictions are made. Explainability also helps developers identify biases, errors, and unexpected model behaviors, allowing further improvements to be made.
    </p>
     <p>
       In critical fields such as healthcare, finance, security, and autonomous systems, explainable AI is essential for ensuring fairness, reliability, and ethical decision-making. Additionally, many industries and regulations require AI systems to provide interpretable and understandable results.
     </p>
  </div>
  
