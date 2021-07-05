
# Humanloop _Data Debugger_ Challenge 

This is an engineering exercise that will give you some insight into the
types of things we are building at Humanloop. We use the same test for ML engineers
and full-stack engineers but the guidelines and evaluation differ slightly.
 
At Humanloop we want to make programming computers as natural as teaching a colleague
 so that anyone can collaborate with AI to achieve their goals.
 
An initial step towards this goal is creating tools for
programming a system by simply providing carefully curated data. And an essential
feature of any reliable programming environment is the debugger...
   
One of the most common challenges in the lifecycle of a Machine Learning
project is trying to improve the performance of an existing trained model. An
 important route to tackling this is to try and understand
where in the data the model is under-performing. 
      
The ability to diagnose which data points the model is struggling with can provide a
 host of benefits. For example it can expose issues with the original training data (e.g
  labelling mistakes). It can also inform strategies for what additional types of
   data might be most useful to spend time collecting. This knowledge, coupled with
    techniques like [active learning](https://humanloop.com/blog/why-you-should-be-using-active-learning/),
can help to rapidly enhance the performance of a model through additional targeted
 training.
 
**For this exercise we would like you to build a small application that
 helps a user debug the data associated to a classifier model trained using the
  [Humanloop Platform](https://humanloop.com/signup).**
  
## Background

A company have used Humanloop to create a simple chat-bot
intent classifier. Their team of in-house client servicing experts trained the
 model by annotating a proportion of the available data on the Humanloop Platform.
 
Their data team now wish to debug the data to understand the
quality of the annotation process and interrogate the model's
strengths and weaknesses. This will be used to help inform what the next steps for improving
the data might be.

**You have access to:**

1. An API to get batch predictions and associated confidence scores
 from the classifier.
2. An export of the full dataset used – broken down into the training, validation and test sets.
 
## Requirements

The basics of your app should:

- Store the dataset in a suitable database of your choice.
- Provide a debugger service that operates on the data.
- Serve a simple user interface for users to get value from the
 debugger. 
 
Please create and share with us a github repository with your solution and provide clear
 instructions for how to run your application locally.

  
### Dataset 
The dataset is included as a json file (_chatbot_intent_classifier_data.json.zip_) in this directory.

The `complete` field indicates whether an annotation has been
provided and the `usage` field indicates whether the annotated data point was
used for training, testing or validation purposes. 
  
We also provide an active learning `score` field as a bonus. This is the [entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) of the softmax classification output of the model –– which can be used as an estimate for how confused the model is with that datapoint.

### Prediction API 

You can leverage the [prediction api](https://humanloop.com/docs#operation/create_prediction_projects__id__predict_post) 
from the intent classifier project: 

    X-API-KEY: sk_63f406a2690ccd01a3234492e2e99996

Snippet:
    
    curl -H "X-API-Key: sk_63f406a2690ccd01a3234492e2e99996" \
    -H "Content-Type: application/json" \
    -d '{"data":[{"text": "What is my new credit limit?"}], "n_best":1}' \
    -X POST https://api.humanloop.com/projects/716/predict

You should limit batch sizes to 20 data points at a time and can use this to enrich
 the data.
 
## Guidelines
- Ideally we'd like you to spend around 4 hours working on this, so keep things simple.
 Please let us know how much time you do end up spending so we can calibrate
  expectations. 
 
- You are free to use any languages and libraries you want. 
 
- Given the indicated time-frame, we don't expect you to spend much time in this
  exercise on 'non-functional' aspects such as authentication, testing, performance, deployment or documentation. We are most interested in what useful debugging functionality you are able to ship here and expect a prototypical solution - although we do care a lot about code quality and style!

### For Full-Stack Engineers 

- Whilst we are hoping to see creativity and ML knowledge for the debugging
 approach, it is far more important that you deliver some small piece of functionality that
 works. ML knowledge and creativity are a bonus. An example feature could be: providing a view of the data to the user where the model most
  confidently disagrees with the annotations provided - what might this uncover? 

- Although the UI is not the focus of this exercise, we do care a lot
 about UX across all aspects of product at Humanloop and are very interested in ways
  to communicate potentially complex data in intuitive user friendly ways.

### For ML Engineers
    
- Unlike the full-stack guidelines, we're far more interested in your creativity
and ML knowledge. It's less important that you are able to code a fully functional app, and more important
that you can leverage what you know of ML to help the end user improve their model or data. 
For example, could you make use of pre-trained models or embeddings? What visualisation or clustering techniques
might help? There's no right answer here, so feel free to be creative.
  
  
Any questions, please let us know! careers@humanloop.com
