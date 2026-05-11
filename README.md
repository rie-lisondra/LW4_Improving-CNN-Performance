# LW4_Improving-CNN-Performance

###### [Google Collab Link](https://colab.research.google.com/drive/1dlY8q166N7yaK7NIT4kQAYVZQy1SaLCc?usp=sharing)

---

## Guide Questions (Student Reflection & Explanation) 

## A. Model Evaluation Analysis

###  1. What were the weakest-performing classes based on the confusion matrix?
  <div align="justify">
    Based on the classification_report output, several classes showed extremely poor performance, with precision, recall, and F1-score values of 0.00. These classes included arrow_arum, blue_flag_iris, bulrush_scirpus, cabomba, cattail, common_reed, frogbit, golden_club, hornwort, large-leaf_pondweed, marsh_marigold, red_mangrove, rockweed, water_clover, and water_stargrass. This indicated that the initial model completely failed to correctly classify any instances of these classes. The confusion matrix also showed that these classes were frequently misclassified into other categories, demonstrating weak class discrimination and poor feature learning in the initial model.
  </div>

###   2. How did Precision, Recall, and F1-score vary across classes?
  <div align="justify">
    For the initial model, the precision, recall, and F1-scores were extremely low across almost all classes, with many values equal to 0.00. Only a few classes showed small non-zero values, indicating poor classification capability. However, after implementing the transfer learning model (model_transfer), the precision, recall, and F1-scores improved significantly across all classes. Most classes achieved values ranging from approximately 0.83 to 0.99 for precision, 0.87 to 0.99 for recall, and 0.88 to 0.98 for F1-score. This demonstrates that the improved model was able to classify images much more accurately and consistently compared to the initial model.
  </div>

###    3. What does a low recall indicate in your model?
   <div align="justify">
    A low recall indicates that the model failed to correctly identify many actual positive instances of a class. In other words, the model produced a high number of false negatives. For example, a recall value of 0.00 means that none of the images belonging to a specific class were correctly identified by the model. This suggests that the model had difficulty recognizing important visual patterns associated with those classes.
   </div>

###    4.  How does AUC score reflect model performance compared to accuracy? 
   <div align="justify">
     <p>
       The AUC (Area Under the Receiver Operating Characteristic Curve) score measures the model’s ability to distinguish between classes across different classification thresholds. An AUC score of 0.5 indicates performance equivalent to random guessing, while higher values indicate better classification capability.
     </p>
    <p>
      The initial model achieved an overall AUC score of approximately 0.52, which is only slightly better than random prediction and indicates very poor discriminatory power. In contrast, the transfer learning model achieved an overall AUC score of 0.9917, which demonstrates excellent classification performance and strong ability to separate classes correctly.
    </p>
     <p>
     Accuracy, on the other hand, only measures the proportion of correct predictions at a single threshold. Although accuracy is easy to interpret, it can sometimes be misleading, especially when datasets are imbalanced. Therefore, AUC provides a more robust evaluation of overall model performance.
    </p>
   </div>
  
## B. Model Improvement
###  5. How did data augmentation affect validation accuracy?
  <div align="justify">
    Data augmentation significantly improved validation accuracy by increasing the diversity of the training dataset. The improved data_augmentation_v2 included additional augmentation techniques such as RandomTranslation, which generated more variations of existing images. This helped the model generalize better to unseen data and reduced overfitting. As a result, the validation accuracy improved from approximately 7% in the initial model to around 29% in model_v2.
  </div>
  
###  6. Why is Batch Normalization important in CNNs? 
  <div align="justify"> 
    Batch Normalization is important in CNNs because it stabilizes and accelerates the training process. It works by normalizing the activations of each mini-batch, typically to have zero mean and unit variance. This reduces internal covariate shift, improves gradient stability, and allows the model to train using higher learning rates. Additionally, Batch Normalization helps reduce overfitting and speeds up convergence during training.
  </div>

###  7. What role did Dropout play in improving your model? 
  <div align="justify"> 
    Dropout acted as a regularization technique that helped prevent overfitting. During training, Dropout randomly disables a portion of neurons, forcing the network to learn more generalized and robust features instead of relying heavily on specific neurons. In the improved models, Dropout layers were added after convolutional and dense layers, which helped improve the model’s generalization performance on unseen images.
  </div>

###  8. How did Early Stopping prevent overfitting? 
  <div align="justify"> 
    Early Stopping prevented overfitting by monitoring the model’s validation performance during training. If the validation loss stopped improving after a certain number of epochs, the training process was automatically stopped. The model then restored the weights from the best-performing epoch. This prevented the model from continuing to memorize the training data and learning unnecessary noise, ensuring better generalization on unseen data.
  </div>

## C. Performance Comparison

###  9. What improvements were observed after modifying the model?
   <div align="justify">
    After modifying the model to model_v2, the validation accuracy increased from approximately 7% to around 29%, while the validation loss decreased significantly. The greatest improvement was achieved after implementing transfer learning using model_transfer, which reached approximately 94% validation accuracy and a validation loss of around 0.39. These results indicate that the improved model learned more meaningful image features and generalized much better compared to the previous models.
  </div>
  
###  10. Which enhancement contributed the most to performance improvement? Why?
   <div align="justify">
     Transfer learning contributed the most to the performance improvement. Although architectural enhancements and data augmentation improved model_v2 to approximately 29% accuracy, the transfer learning model dramatically increased the validation accuracy to about 94%. By using a pre-trained model such as MobileNetV2, the network was able to utilize feature representations already learned from large datasets like ImageNet. This provided a strong foundation for image classification and significantly improved the model’s ability to recognize complex image patterns.
  </div>

###  11. Did the gap between training and validation accuracy decrease? Explain.
   <div align="justify">
     For model_v2, there was still a noticeable gap between training and validation accuracy, although both metrics showed improvement over time. However, in the transfer learning model (model_transfer), the gap between training and validation accuracy became much smaller, and both achieved high values. This indicates that the model generalized well to unseen data and was not severely overfitting or underfitting. The close alignment between training and validation accuracy is a strong indicator of effective model generalization.
  </div>
  
## D. Explainability (Grad-CAM Integration)
###   12.  How did Grad-CAM help in understanding model predictions?
   <div align="justify">
    Grad-CAM (Gradient-weighted Class Activation Mapping) helped visualize the regions of the image that were most important for the model’s predictions. By overlaying heatmaps on the original images, Grad-CAM showed where the CNN focused its attention during classification. This improved the interpretability of the model by revealing whether the model concentrated on meaningful image regions or irrelevant background areas. Grad-CAM also helped increase trust and transparency in the model’s decision-making process.
  </div>

###   13.  Did the improved model focus on more relevant regions? Provide evidence.
   <div align="justify"> 
    The Grad-CAM visualization used was generated using the initial model (my_image_classifier.keras) rather than model_v2 or model_transfer. Therefore, a direct comparison between the initial and improved models could not be fully performed. However, based on the significant improvement in validation accuracy, lower validation loss, and higher AUC score achieved by the transfer learning model, it is likely that the improved model learned to focus on more relevant image features. Additional Grad-CAM visualizations generated using model_transfer would provide stronger visual evidence of this improvement.
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
  
