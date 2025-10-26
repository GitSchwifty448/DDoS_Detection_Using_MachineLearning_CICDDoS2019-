This project implements both BINARY and MULTICLASS classification of network traffic to detect DDoS attacks using the CICDDoS2019 dataset.  
I experimented with **K-Nearest Neighbors (KNN)** and **Random Forest (RF)** models, and evaluated their performance.

Dataset used:CICDDoS2019 (https://www.unb.ca/cic/datasets/ddos-2019.html)  

preprocessing done:
  - Selected ~50k samples per attack type.
  - Dropped unnecessary columns (IPs, Flow ID, Timestamp, etc.).
  - Handled missing values and infinite values.
  - Scaled features using StandardScaler.
  - Binary label encoding: Benign = 0, Attack = 1.
  - Multiclass label encoding: BENIGN, LDAP, MSSQL, NetBIOS, Portmap, Syn, UDP, UDPLag.
Features used:
    - features = "Packet Length Mean", "Flow Bytes/s", "Bwd Packet Length Max", "Average Packet Size", "Total Backward Packets", "Bwd Packets/s",
                "Packet Length Std", "Fwd IAT Mean", "Fwd Packet Length Min", "Packet Length Variance", "Flow IAT Min", "Flow IAT Std",
                "Fwd IAT Std", "Flow IAT Mean", "Protocol", "Flow IAT Max", "Flow Duration", "Source Port", "Fwd IAT Total", "Flow Packets/s",
                "PSH Flag Count", "Fwd Packets/s", "Bwd Packet Length Min", "Min Packet Length", "Total Fwd Packets", "ACK Flag Count",
                "Fwd Packet Length Max", "Destination Port", "Init_Win_bytes_forward", "Init_Win_bytes_backward", "Label"

Results:
=== Multiclass Report ===
              precision    recall  f1-score   support

      BENIGN       1.00      1.00      1.00     11423
        LDAP       1.00      1.00      1.00       924
       MSSQL       0.86      0.99      0.92       591
     NetBIOS       0.24      0.13      0.17       354
     Portmap       0.72      0.84      0.78       961
         Syn       1.00      1.00      1.00      7792
         UDP       0.99      0.88      0.93       740
      UDPLag       0.00      0.00      0.00         1

    accuracy                           0.98     22786
   macro avg       0.73      0.73      0.72     22786
weighted avg       0.97      0.98      0.97     22786

=== Binary Report ===
              precision    recall  f1-score   support

      Benign       1.00      1.00      1.00     11423
      Attack       1.00      1.00      1.00     11363

    accuracy                           1.00     22786
   macro avg       1.00      1.00      1.00     22786
weighted avg       1.00      1.00      1.00     22786
