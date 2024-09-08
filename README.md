# Fall Prediction API

A Flask-based API for predicting fall events using a trained TensorFlow model. This API accepts input features, such as sensor data, and returns a predicted class indicating whether a fall is detected, predicted, or not detected. It is designed for integration with IoT devices, wearables, or health monitoring systems to provide real-time fall detection and prediction.

## Features

- REST API built with Flask
- TensorFlow model for fall prediction
- Supports multi-class classification:
  - Class 0: No fall detected
  - Class 1: Fall predicted
  - Class 2: Fall detected
- Model deployment via ngrok for local testing
- Easy to integrate with mobile apps, IoT devices, or external monitoring systems

## Setup & Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/fall-prediction-api.git
    cd fall-prediction-api
    ```

2. Install the required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Train your model (or load an existing one) and place it in the appropriate directory:

    ```python
    model = tf.keras.models.load_model('/path_to_model/my_model.keras')
    ```

4. Start the Flask server:

    ```bash
    python app.py
    ```

5. For local testing and public access, use ngrok:

    ```bash
    ngrok http 5000
    ```

## Usage

### Predict a Fall Event

To get predictions, send a POST request to `/predict` with a JSON payload containing the input features. Example:

```bash
curl -X POST https://<your-ngrok-url>/predict \
     -H "Content-Type: application/json" \
     -d '{"features": [ <hrv>,<sugar-level>,<spo2>,<accelerometer>]}'
```

### Example Response

```json
{
  "predicted_class": 1
}
```
Where the predicted class corresponds to one of the following:
```bash

- `0`: No fall detected
- `1`: Fall predicted
- `2`: Fall detected
```
