# ai-go

This is the example from Gophercon 2021 "Production AI with Go" workshop.

Original repo can be found here: (Gophercon 2021 AI-Go workshop)[https://github.com/dwhitena/gc2021-ai-workshop]

## Summary - My learnings 

Majority of model trainings happen with Python frameworks - Tensorflow and Pytorch, in majority.

#### Benefits of using Go to present the models in Prod, given that most models are written in Python
Python being single threaded makes it hard to scale. 
Go multithreading has been tailored for scalability and robustness to help with obtaining inferences in prod realtime 
Validation and testing advantages

#### Training packages in Go - 
* (Gorgonia)[www.gorgonia.org] - Deep learning in Go - Neural network and Go models 
* Golearn - (https://github.com/sjwhitworth/golearn)[https://github.com/sjwhitworth/golearn]
* NLPOdyssey/SpaGo - (SpaGo)[https://github.com/nlpodyssey/spago]
* Sajari - (Regression)[https://github.com/sajari/regression] - For regression exercises specifically 
* Good Go package for data wrangling - Start with the Gonum  - Spectacular set of numerical packages - used by CERN and other very scientific leaders of the world.


#### Inference/model serving
* Option-1: Production Go API - Use the model files (pb files ) -> Integrate with prod quality Go code -> Load model into Go code, supply inputs into the model (call the model within Go code) and produce output
* Packages for loading models in Go - TF has Go bindings itself. Thirs party libraries - Onnx-go with open format for model files, Gocv - provides support for OpenCV library that supports TF and other models, Spago - NLP library
* All of these libraries do their binding well, but custom layers could cause some long term pain for support. 
* Model optimizers with Go bindings - Apache TVM and OpenVINO - Take the model file output and optimize it for a certain hardware architecture - these can be called from Go.
* Option 2 - Prod Python API being called by Go API serving as a proxy layer on top 
* Example: Flask or FastAPI for Python API. Framework that takes Python model code and create a layer on top that can be called for serving- TF Serving or Seldon
* Only works best when the Python API functionality is limited - does one thing well
* Option-3 : Hosted inference service - directly loads the model and calls the model, Top it by a Go API that calls the inference service and implement other business logic. Example- Hugging Face's Inference API


#### Model Decision Tree 
(Python model vs Go inference calls)[https://github.com/dwhitena/gc2021-ai-workshop/blob/main/model_deploy_decision_tree.pdf]

#### Testing perspectives
* Tests for model functionality for inferences with specific model versions

#### References

State of the art use cases [https://paperswithcode.com/sota]
Model hubs - TF model hub [https://www.tensorflow.org/hub]
Hugging face model hub - [https://huggingface.co/models] - public models that can be used off the shelf - credible models. Allows versioning and uploading models.
Used distilbert-base-cased-distilled-squad ofr question and answer model





