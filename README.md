# DepositorClassification

# Will a potential client make a deposit or not? 

For marketing and sales purposes, who, how, and when should we target with offers regarding making a deposit with our bank.

### Data
Data on banking deposits from UCI machine learning repository. [Here](data/bank-additional-full.csv)

### Methodology
1. Data - limited the number of columns in use, depending on situation. At first we used only 7 key features, but expanded to almost all of the rest of the features later on. 
2. Models - ran a total of 8 models
 - First we tried LogisticRegression, KNN, SVM, and Decision Tree with only the most basic features available
 - Second we tried LogisticRegression, KNN, and Decision Tree with all available features
3. Evaluation - evaluated using recall because we mostly cared about the amount of true positives the model was able to detect. We need to know who to target more so than who not to target.


### Goal
Successfully identify key clients that have a significantly higher chance of making a deposit.

# Insights

### Best model

![DtreeConfMatrix](https://github.com/alexanderpspahr/DepositorClassification/assets/129889030/c92e94d9-980f-46f5-bb89-563f52adae19)

The vast majority of these models did not yield actionable results, and in fact, did not even differ in any way from the trivial dummy classifier. We tried 'tricking' the model by training it on something other than recall if it was getting 100% recall via trivial guesses, but even then it did not budge. The decision tree model, once hyperparameter tuned, was by far the best result. It was able to differentiate a certain subsection of clients that had a significantly elevated chance of making a deposit. Since it was a large decision tree, it is rather hard to extract what criteria the model uses to to make it's decisions. It seems, as well, that this complexity is the differentiating factor that allows the model to have significantly better results than the other models.

### Conclusion

The model is actionable and meaningful. The business can now target clients identified by the model, and know that there is an increased likelyhood of success in those cases. A client is almost 4x as likely to make a deposit if they are among the group identified by the model. The main problem is the volume of clients identified by the model is still only ~1/3 of the overall list of clients that would make a deposit. Still, the results are not too bad. It would be good if the data could be improved, or if there is any way to improve upon the model. Perhaps using something such as XGBoost would yield even better results.

We know that whatever the case, it seems unlikely any models readable by a human could easily make this decision. It seems the complexity of the model should remain as high as possible in order to gain any glimpse of information that might otherwise not be present. Attempts at reducing the overfitting of the model so far yielded poor results, but it may also be possible to increase complexity, and then still cut down on overfitting. Regardless, the overfitted model was wholly superior to the numerous underfifted models as of right now. It seems it is no coincidence that a complex decision tree was the only model to perform well.
 

Next Steps:
1. See if more relevant data can be improved, or if model was lacking in some way
2. Despite a lacking in the raw number of true positives identified, the results are still actionable, just that they represent only a smaller subset of potential clients. But among these clients, they have approixmately a 35% chance of making a deposit, which is much higher than the ~9.5% chance that any given client **not** identified by the model would have.
