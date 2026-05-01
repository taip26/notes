Henry Arze

cv project

given the layout of the shelf, what are the missing products and send the id of the missing product to the backend

the problem is that it only sees whats there and not whats missing

outputs only bounding boxes on shelf, estimate stuff instead

metrics for evaluation
 - f1 and accuracy
 - model was already trained on grocery store things


Feedback
 - Fine-tine the model to better fit the use case
 - issues getting real data instead of planograms - fine-tune with the planograms and see how it goes
 - Try other data augmentation routes (rotation, color shift, etc.) to help supplement low data
