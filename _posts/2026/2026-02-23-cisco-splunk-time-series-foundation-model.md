---
layout: post
title: "Cisco Splunk Time Series Foundation Model"
subtitle: ""
date: 2026-02-23
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "AI"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: 6zl6V1yU0NI
video-duration: "2:58"
thumbnail-img: https://i.ytimg.com/vi/6zl6V1yU0NI/hqdefault.jpg
share-img: https://i.ytimg.com/vi/6zl6V1yU0NI/hqdefault.jpg
excerpt: "LLMs are great at predicting the next word in a sentence such as 'I like my coffee with cream and (?)' because they are trained on language. But, what if you need something trained on time series machine data? That is where the Cisco Time Series Model comes in. Jeff Wiedemann breaks it down for…"
featured: false
---
LLMs are great at predicting the next word in a sentence such as 'I like my coffee with cream and (?)' because they are trained on language. But, what if you need something trained on time series machine data? That is where the Cisco Time Series Model comes in. Jeff Wiedemann breaks it down for us at Cisco Live EMEA and gives some practical ways the model can be used in Splunk.  The link Jeff mentions in the video is below:

{% include youtube.html id="6zl6V1yU0NI" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Live in Amsterdam and I ran into Jeff here and we were talking about the time series foundational model. You know what is that and why is it important? &gt;&gt; Yeah. Uh before I answer that, Jason, I want you to answer a question for me. Maybe you can fill in the blank here. I like my coffee with cream and sugar. &gt;&gt; Yes, you got it right. So what I did there was I held back the last word of the sentence and I asked you to predict what it was. That's actually how large language models are trained. It's called self-supervised machine learning. Okay? And so what we do is uh like I said, we hold back that last word and we do that and we ask the LM to predict what the result is. Now, the first time it's going to get it horribly wrong. It's going to say dog or something like that, right? But we're going to kind of tune those dials until it responds correctly with the word sugar. And then we do that over and over again, millions of times across tons of different sentences until this model is really, really good at predicting the next word. in almost any sentence. That's how large language models are trained today. Now, &gt;&gt; let me try another one on you if you don't mind. Uh, let's go. &gt;&gt; User timeout session terminated. &gt;&gt; Oh, you were close. It was actually disconnected. Okay, but really the problem here and this really illustrates the need for these machine data models, models that are trained on machine data because while machine data contains English words, the bottom line is that they don't really appear in context in sentences like we see in the real world. And so these models, these large language models that were built and trained for text aren't very good at, you know, predicting what's next for machine learning. So if we want to get value and insights and analyze machine data, we need models that are specifically trained on and for machine data. And that's exactly what we're doing at Cisco with several different models. So we've actually released uh two different models. We have the security model and then we have the uh deep time series foundation model that you talked about. So that's where we're at right now. &gt;&gt; So you say we released these models. Are these like publicly available releases? &gt;&gt; Yes, absolutely. So if you're familiar with hugging face and you know how to go download those models, you can download those on hugging face, deploy them where you want and you can start training them today. However, we are uh looking to make these models much more approachable for our traditional Splunk customers. So we actually have an active uh preview right now that you can click the link and uh join that preview and that's going to allow us to you know work with you to make sure that we're training our models in order to provide the most accurate results possible. And then in the next release of the AI toolkit, we're actually going to be hosting these models directly in the app. So you don't even have to go download them on HuggingFace or try to run them your yourself. &gt;&gt; That's incredible. So stay tuned everybody. Looking forward to it. Awesome.
