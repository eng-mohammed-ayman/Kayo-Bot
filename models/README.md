# Required local artifacts

This source snapshot does not include the trained `chatBotAI_model.h5` (about 141 MB) or `df_processed.csv` (about 1.5 MB). Request an authorized copy from the project team and place both in this directory. A public artifact download has not been supplied. Do not publish the original archive or any credentials.

Both artifacts must come from the same training run: this app rebuilds its tokenizer vocabulary from the processed CSV. Changing the CSV can change token IDs and break compatibility with the model. Training code and a separately serialized tokenizer are not included in the supplied app snapshot.
