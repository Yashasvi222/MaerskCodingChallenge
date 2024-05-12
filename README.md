## Methodology followed
### First Approach

In the initial approach, a straightforward Brute-Force methodology was adopted to lay the foundation for subsequent refinements. Each feature was label encoded without extensive deliberation, and three models—Random Forest Regressor, LightGBM, and Decision Tree Regressor—were employed. The outcomes obtained were as follows:


|         | **Random Forest Regressor** | **LightGBM** | **Decision Tree Regressor** |  
|---------|-----------------------------|--------------|-----------------------------|
| **MSE** | 5442                        | 4982         | 5529                        |
| **MAE** | 138                         | 129          | 140                         |

.

### Next Approach (The Final Approach)

This approach took a series of iterations of refinements. 
- Features demonstrating an inherent order were subjected to appropriate encoding methods so label encoding was applied, while one-hot encoding was applied to the remaining features.
- Subsequently, attention was directed towards outlier management. Initially, a box plot was constructed for the sole numerical column, "Sourcing Cost," revealing the presence of outliers. However, these outliers posed a visual challenge by compressing the rest of the data. To mitigate this issue, the dataset was segmented into 10 deciles, resulting in an improved visualization. Upon closer examination, outliers in the form of negative instances and elevated values within the 10th decile were identified. These outliers were subsequently removed, leading to a significant improvement in model performance, reducing the mean squared error from thousands to hundreds.
- Subsequent to addressing outliers, I experimented with a neural network model; however, its performance fell short of expectations. The machine learning models, on the other hand, exhibited superior performance.
- After adding a neural network, attention shifted towards fine-tuning the hyperparameters of the employed models. The culmination of these efforts yielded the subsequent results:

|         | **Random Forest Regressor** | **LightGBM** | **Decision Tree Regressor** | **Neural Network** | 
|---------|-----------------------------|--------------|-----------------------------|--------------------|
| **MSE** | 560.3                       | 600.3        | 550.6                       | 1033.5             |
| **MAE** | 14.6                        | 14.7         | 14.5                        | 19.5               |


The Decision Tree model emerged as the most effective, yielding the best results among the models tested. Therefore, it has been selected as the optimal and final model for this task.


