# LW4_Improving-CNN-Performance

###### [Google Collab Link](https://colab.research.google.com/drive/1Nq3wbeYp3mYK36y5m3oEWxqNzVBtEghs?usp=sharing)

---

## Guide Questions (Student Reflection & Explanation) 

## A. Model Evaluation Analysis

###  1. What were the weakest-performing classes based on the confusion matrix?
  <div align="justify">
    Based on the classification_report output, several classes showed extremely poor performance, with precision, recall, and F1-score values of 0.00. These classes included arrow_arum, blue_flag_iris, bulrush_scirpus, cabomba, cattail, common_reed, frogbit, golden_club, hornwort, large-leaf_pondweed, marsh_marigold, red_mangrove, rockweed, water_clover, and water_stargrass. This indicates that the model failed to correctly classify any samples belonging to these categories. The confusion matrix further showed that these classes were frequently misclassified into other categories, demonstrating weak class discrimination.
  </div>

###   2. How did Precision, Recall, and F1-score vary across classes?
  <div align="justify">
    The Precision, Recall, and F1-score values varied significantly across classes, but most remained very low. Many classes obtained scores of 0.00, indicating poor classification performance. Some classes such as giant_bur-reed, pickerelweed, sea_grape, turtle_grass, and water_mimosa showed slightly better results. For example, turtle_grass achieved the highest recall value of 0.64, meaning the model identified many actual samples of that class. However, its precision was only 0.06, showing that many predictions labeled as turtle_grass were incorrect. Overall, the metrics indicate that the model struggled to effectively distinguish between classes.
  </div>

###    3. What does a low recall indicate in your model?
   <div align="justify">
     A low recall indicates that the model failed to correctly identify many actual positive instances of a class. In other words, the model produced a high number of false negatives. For example, a recall value of 0.00 means that none of the images belonging to a particular class were correctly identified. This suggests that the model had difficulty recognizing important patterns associated with that class.
   </div>

###    4.  How does AUC score reflect model performance compared to accuracy? 
   <div align="justify">
     <p>
       The AUC (Area Under the Curve) score measures the model’s ability to distinguish between classes across different classification thresholds. An AUC score of 0.5 represents random guessing, while higher values indicate better classification capability. In this model, the overall AUC score was approximately 0.52, which is only slightly better than random prediction and indicates weak discriminatory performance.
     </p>
    <p>
      Unlike accuracy, which only measures the percentage of correct predictions, AUC provides a more reliable evaluation because it considers the model’s performance across all thresholds. Accuracy can sometimes be misleading, especially when datasets are imbalanced. Therefore, AUC is considered a more robust metric for evaluating classification models.
    </p>
   </div>
  
## B. Model Improvement
###  5. How did data augmentation affect validation accuracy?
  <div align="justify">
    Data augmentation improved the model’s validation accuracy by increasing the diversity of the training dataset. Techniques such as flipping, rotation, zooming, and random translation generated new variations of existing images, allowing the model to learn more generalized features. As a result, the validation accuracy improved from approximately 7% in the initial model to around 29% in the improved model. This demonstrates that data augmentation helped reduce overfitting and enhanced the model’s ability to generalize to unseen data.
  </div>
  
###  6. Why is Batch Normalization important in CNNs? 
  <div align="justify"> 
    Batch Normalization is important in Convolutional Neural Networks (CNNs) because it stabilizes and accelerates the training process. It works by normalizing the outputs of each layer, reducing internal covariate shift during training. This provides several benefits, including faster convergence, more stable gradients, and the ability to use higher learning rates. Additionally, Batch Normalization helps improve generalization and slightly reduces overfitting.
  </div>

###  7. What role did Dropout play in improving your model? 
  <div align="justify"> 
    Dropout acted as a regularization technique that helped reduce overfitting. During training, Dropout randomly disables a portion of neurons, preventing the network from becoming too dependent on specific features. This forces the model to learn more generalized and robust patterns from the data. In the improved model, Dropout layers were added after convolutional and dense layers, which helped improve the model’s generalization performance on unseen images.
  </div>

###  8. How did Early Stopping prevent overfitting? 
  <div align="justify"> 
    Early Stopping prevented overfitting by monitoring the model’s validation performance during training. When the validation loss stopped improving for several epochs, the training process was automatically terminated. This prevented the model from continuing to memorize the training data and learning unnecessary noise. Early Stopping also restored the best-performing model weights, ensuring that the final model achieved the best validation performance possible.
  </div>

## C. Performance Comparison

###  9. What improvements were observed after modifying the model?
   <div align="justify">
     After modifying the model, several improvements were observed. The validation accuracy increased significantly from approximately 7% to around 29%. In addition, the validation loss decreased from over 10 to approximately 2.29. These improvements indicate that the enhanced model learned more meaningful image features and generalized better to unseen data compared to the initial model.
  </div>
  
###  10. Which enhancement contributed the most to performance improvement? Why?
   <div align="justify">
     Among the implemented enhancements, the combination of deeper convolutional layers and stronger data augmentation likely contributed the most to performance improvement. Increasing the number of convolutional filters enabled the model to extract more complex image features, while additional augmentation techniques improved dataset diversity and reduced overfitting. Together, these changes improved the model’s learning capability and generalization performance.
  </div>

###  11. Did the gap between training and validation accuracy decrease? Explain.
   <div align="justify">
     The gap between training and validation accuracy became more controlled after applying the improvements. Both training and validation accuracy showed an increasing trend, indicating that the model was learning more effectively. Although a noticeable gap still existed, the validation accuracy improved compared to the initial model. This suggests that the model achieved better generalization and reduced overfitting, although further optimization is still needed to improve overall performance.
  </div>
  
## D. Explainability (Grad-CAM Integration)
###   12.  How did Grad-CAM help in understanding model predictions?
   <div align="justify">
    Grad-CAM (Gradient-weighted Class Activation Mapping) helped visualize the regions of the image that were most important for the model’s predictions. By generating heatmaps over the input images, Grad-CAM showed where the CNN focused its attention during classification. This improved the interpretability of the model by revealing whether it was analyzing meaningful object regions or irrelevant background areas.
  </div>

###   13.  Did the improved model focus on more relevant regions? Provide evidence.
   <div align="justify"> 
    Based on the improved validation accuracy and reduced validation loss, it is likely that the improved model learned to focus on more relevant image features. Additional Grad-CAM analysis using the improved model would provide clearer evidence of this improvement.
  </div>

###   14.  Why is explainability important in real-world AI applications? 
   <div align="justify">
    Explainability is important in real-world AI applications because it increases transparency, trust, and accountability. Users and stakeholders are more likely to trust AI systems when they understand how decisions are made. Explainability also helps developers identify errors, biases, and weaknesses in the model, enabling further improvements. In critical domains such as healthcare, security, finance, and autonomous systems, explainable AI is essential for ensuring fairness, reliability, and ethical decision-making.
  </div>
  
