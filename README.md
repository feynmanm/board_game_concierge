# Board Game Concierge: Answering Questions for Complex Board Games
## Fine-tuning DistilBERT Question-Answering on an unsupervised, small-domain corpus.
In the realm of complex board games, rules questions abound. A tool that simply answers a player's rules questions would be helpful. An NLP solution applied to this problem may be able to take advantage of a special circumstance of this realm to avoid labeling game rules for the question-answering task --> Questions themselves will only be asked of the exact text corpus that the fine-tuned model would be trained on. And, thusly, overfitting on the training corpus is good.
## Overview
This notebook presents the preprocessing, training, and inference algorithm of the Board Game Concierge reference aid. We demonstrate it with the 25k+-word game rules of the complex board game High Frontier 4 All (base game). 
> High Frontier 4 All Core Rules   
Copyright &copy; 2020 Ion Game Design & Sierra Madre Games  
Lead Designer: Phil Eklund  

We utilize our own flavor of domain adaptation so that the rules need not be labelled. The key is fine tuning the contextualized representation of the English language of the well-known vanilla DistilBERT model on our game rules corpus, then freezing the early encoders, and then retraining the model for question answering on the off-the-shelf SQuAD v1 corpus. The resulting QA model contains particular knowledge of the game rules while being fully trained to process English-language questions.

During inference, the user asks a question. we utilize staCy to identify appropriate passages from the game rules that might contain an answer to the question, then ask the question of each such passage, and return the answer(s) with the highest confidence scores. spaCy also plays an interesting role in addressing some preprocessing challenges specific to the rules of High Frontier 4 All.
