# Analysis Tools

This contains codes of the following functionality: 
- Compute average f2 score for ships.
- Draw analysis histogram for the model prediction.


## ##
## Usage
- Run the following script to Compute average f2 score.
    ```sh
    python3 compute_f_score.py
    ```
  This script loads ship masks from prediction CSV and ground truth CSV (both CSVs are in run-length format).
        
  **Run-length Format: Pairs of values that contain a start position and a run length.* 
            
        E.g. '1 3' implies starting at pixel 1 and running a total of 3 pixels (1,2,3).
  
  **`compute_f_score.py` provides an option `if_store_img_info` for:** 
      
    - If `False`, computing average f2 score:
        
        - The f2 score metric sweeps over a range of IoU thresholds, at each point calculating an F2 Score. 
            
            **The threshold values range from 0.5 to 0.95 with a step size of 0.05: 
            (0.5, 0.55, 0.6, 0.65, 0.7, 0.75, 0.8, 0.85, 0.9, 0.95).*
        
                E.g. At a threshold of 0.5, a predicted object is considered a "hit", 
                     if its intersection over union with a ground truth object is greater than 0.5.
        
        - At each threshold value t, the F2 Score value is calculated based on the number of true positives (TP), false 
        negatives (FN), and false positives (FP) resulting from comparing the predicted object to all ground truth objects.
        
        $ \sum_{\forall i}{x_i^{2}} $
        
    - If `True`, save the tp, fp, fn, fp information into a dict
    

 
 - Run the following script to generate run-length submission CSV.
    ```sh
    python3 pickle_to_csv.py
    ```
    ***Param:*** `threshold` - After selecting the confidence threshold on validation set, generate prediction of test 
    set, then apply the selected threshold here.