# Design and implementation of EEG seizure detection and alarm system based on Arduino control
## Introduction
In order to be able to detect seizures and alert caregivers, a seizure detection and alert system based on Arduino and MATLAB is used. The system takes the patient's EEG signals in arduino, processes them in MATLAB, detects potential seizures, and sends an email alert to a designated mailbox when a seizure is detected. The system overcomes the limitations of traditional diagnostic means, improves the efficiency of medical treatment, and helps nursing staff to take timely actions.

### EMG data acquisition
![image](https://user-images.githubusercontent.com/95090256/228617766-b3a585d9-5430-420d-9800-7b5d00a92d32.png)
Implement an Arduino sketch to read EEG data from the sensor and send it to MATLAB via a serial connection

### Interactive interface design

![image](https://user-images.githubusercontent.com/95090256/228618306-f27333c3-c6ee-47b4-ab8d-2437d3ee6f71.png)
To create an interactive interface in MATLAB, I use the uifigure and uiaxes functions to create the interface and display real-time waveforms. Use uitable for peak detection results and uibutton for alert buttons.


### E-mail Alerts
![image](https://user-images.githubusercontent.com/95090256/228618705-64756afa-6682-42c8-a540-59e6bdce91d8.png)

The E-mail alert system is implemented using MATLAB's built-in sendmail function, which sends an E-mail to a specified mailbox when a seizure is detected.

