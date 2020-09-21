# FaceMaskDetection-model

This repo have Dockerfile for [FaceMaskDetection](https://github.com/AIZOOTech/FaceMaskDetection) model serving and example code about how to use it.

[example code](./keras_example)

### Keras 
[![Run on Ainize](https://ainize.ai/images/run_on_ainize_button.svg)](https://ainize.web.app/redirect?git_repo=https://github.com/woomurf/FaceMaskDetection-model)

#### usage  
```
## input shape = [None, 260, 260, 3]
## output shape = [None, 5972, 4], [None, 5972, 2]

URL = " https://keras-face-mask-detection-model-woomurf.endpoint.ainize.ai/v1/models/keras:predict"
image = image.tolist()
data = {
    "instances" : image 
}

data = json.dumps(data)
response = requests.post(URL, data=data)

if response.status_code == 200:
    text = response.text 
    text = json.loads(text)

    prediction = text['predictions'][0]
    
    y_bboxes = np.array([prediction['output']])  # [None, 5972, 4]
    y_scores = np.array([prediction['output2']]) # [None, 5972, 2]
```