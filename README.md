# Board Game Concierge: Answering Questions for Complex Board Games
## Fine-tuning DistilBERT Question-Answering on an unsupervised, small-domain corpus.
In the realm of complex board games, rules questions abound. A tool that simply answers a player's rules questions would be helpful. An NLP solution applied to this problem may be able to take advantage of a special circumstance of this realm: Questions themselves will only be asked of the exact text corpus that the fine-tuned model would be trained on. Thus, overfitting on the training corpus is good.
