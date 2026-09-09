# Datasets

Two datasets are redistributed here so that the experiments in this repository can be
reproduced from a single checkout. Neither was created by us. Please cite the original
authors.

## CB1

Fine-grained cyberbullying classification: 47,692 tweets across six classes (age,
ethnicity, gender, religion, other cyberbullying, not cyberbullying).

File: `CB1/CB1.csv`, columns `tweet_text` and `cyberbullying_type`.

Original source: https://www.kaggle.com/datasets/andrewmvd/cyberbullying-classification

> J. Wang, K. Fu and C.-T. Lu. SOSNet: A graph convolutional network approach to
> fine-grained cyberbullying detection. Proc. 2020 IEEE International Conference on
> Big Data, pp. 1699-1708, 2020.

## CB2

Semi-synthetic cyberbullying dataset covering aggression, repetition, peerness and
intent to harm. The full release is included; the experiments use
`CB2/communication_data_among_users.csv`, which holds 90,356 individual messages
exchanged between users with a binary label, reduced to 89,525 after cleaning.

Original source: https://data.mendeley.com/datasets/wmx9jj2htd/2
(doi 10.17632/wmx9jj2htd.2)

> N. Ejaz, F. Razi and S. Choudhury. Towards comprehensive cyberbullying detection: A
> dataset incorporating aggressive texts, repetition, peerness, and intent to harm.
> Computers in Human Behavior, 153:108123, 2024. doi 10.1016/j.chb.2023.108123

Files:

| File | Contents |
|---|---|
| `users_data.csv` | 100 synthetic users with age, gender, school and grade |
| `peerness_values.csv` | Peerness for all 4,950 user pairs |
| `aggressive_all.csv` | 118,828 aggressive messages |
| `non_aggressive_all.csv` | 118,828 non-aggressive messages |
| `communication_data_among_users.csv` | 90,356 user-to-user messages, binary label |
| `cb_labels.csv` | Conversation-level cyberbullying labels, not used here |

## Preprocessing

Both datasets are cleaned inside the notebooks rather than beforehand, so the files
above are the originals as published. The notebooks remove corrupt rows, apply the
preprocessing function, drop annotation conflicts and exact duplicates, then split
75/25 with a further 10% of training held out for validation. Near-duplicates at
TF-IDF cosine similarity 0.90 are moved from test to training rather than discarded.

## Licence

The datasets remain the property of their original authors and are redistributed here
under CC BY-SA 4.0. The code in this repository is MIT licensed.
