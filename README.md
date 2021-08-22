# Classifying Credit Risk Using Machine Learning Techniques

## Purpose
The purpose of this project was to assess the performance of multiple algorithms when predicting outcomes with unbalanced data. The report analyzed oversampling, undersampling and combination technqiues, as well as classification methods that aim to reduce bias. The task was to predict high and low-risk credit applicants based on myriad factors, such as income, home-ownership and interest rates, among other things.

## Results

* The first technique evaluated was naive random oversampling, in which instances of the smaller class are oversampled to create balance. The balanced accuracy score, or, the average of recall on each class, is probably more middling than we'd probably like, at about 65. Meanwhile, the precision score -- which quantifies true positive class predictions -- is perfect when it comes to low-risk individuals, but almost exactly the opposite for the minority class (high-risk) individuals. The recall scores -- which quantify the number of positive class predictions made out of all positive examples in the data -- are more even for both (between 60 and 70), but still not great, with an average at 60.

![image](https://user-images.githubusercontent.com/1015285/130371226-0bdc113b-ad72-4655-a307-3b1059120522.png)


* The second technique is SMOTE oversampling, in which instances of the minority class are created synthetically instead of randomly chosen and added to the data. The balanced accuracy score in this technique is slightly higher (a little more than 66%), with the same precision scores for each class, and a boost in the average recall score, from 60 in the first example to 69. 

![image](https://user-images.githubusercontent.com/1015285/130371980-efb6f9f0-7395-4813-a291-6ec9df2de5cb.png)


* The third technique is undersampling -- shrinking the majority class instead of growing the minority class. The accuracy score for this technique decreases significantly, from 65-66 to just under 55. Again, we have the same precision scores, but a much lower average recall score of 40.

![image](https://user-images.githubusercontent.com/1015285/130372106-174f6855-392e-40dc-935f-d59ccef8e638.png)


* The fourth technique is a blend of over and undersampling, using the SMOTEEN algorithm, which combines the SMOTE and nearest-neighbors concepts to essentially create more room between the two classes and (hopefully) make classification easier. The model achieves the highest accuracy score so far, at around 68, with the same precision score as earlier models, but a lower recall score, at 57.

![image](https://user-images.githubusercontent.com/1015285/130372256-2d7896f2-416c-4cb0-8f59-ad3566d46d01.png)


* The final two techniques -- the ensemble algorithms -- appear to do significantly better at predicting credit risk than the sampling methods. The first, the Balanced Random Forest Classifier, achieves a roughly 79% accuracy score, with much better high and low-risk recall scores (0.70 for high-risk and 0.87 for low-risk), as well as a higher average recall at 0.87. To go a step further, the F1 score, which attempts to balance the concerns of precision and recall, is roughly 0.93.

![image](https://user-images.githubusercontent.com/1015285/130372317-6216ac17-ca16-4a47-b5a3-fb1d09456481.png)

* The Easy Ensemble AdaBoost Classifier does even better based purely on metrics, with a 93 balanced accuracy score, a .09 precision score for the high-risk class, and 0.92 and 0.94 recall scores for high and low-risk classes, respectively. On first blush, those metrics seem to be the most preferable in this analysis. However, even though we've tried to avoid the perils of overfitting by splitting data into training and testing sets, we should repeat our analysis to ensure the high scores aren't an artifact of the data or a quirk of using a particular algorithm.

![image](https://user-images.githubusercontent.com/1015285/130372572-b32e2930-18d3-4b2c-a52f-3063346bfc8d.png)

## Summary

If we wanted to rank the models based purely on accuracy scores, this would be the order:

1. Easy Ensenble AdaBoost Classifier (~93)
2. Balanced Random Forest Classifier (~79)
3. SMOTEEN (~68)
4. SMOTE (~66)
5. Naive Random Oversampling (~65)
6. Undersampling (~55)

Of course, that's not the only metric that matters. There are multiple considerations, such as interpretability, time and computing power, that could persuade us as analysts to choose one model over another. The Easy Ensemble method seems to have the best measurables of all of our algorithms, but an accuracy score around 93 is pretty high for any real-world analysis, and probably warrants a little more probing to ensure the metrics aren't a result of a quirk in the data. The Balanced Random Forest algorithm, meanwhile, seems a little more realistic. But again, I'd recommend further analysis to make sure we're not needlessly sacrificing accuracy.

It seems safe to say we can probably do better than the four sampling methods when predicting credit risk. So my recommendation would be further exploration of the ensemble methods if we're simply trying to get the most accurate predictions possible. If we want to, say, surmise a theory of credit risk -- one in which our chief concern is interpretation -- we'd probably want a simpler model that relies on only a few variables and is easier to explain.


