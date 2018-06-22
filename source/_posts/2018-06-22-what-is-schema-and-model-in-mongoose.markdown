---
layout: post
title: "what is schema and model in mongoose?"
date: 2018-06-22 11:07:52 +0530
comments: true
categories: mongoose,node.js,Mode,Schema
---
Hi Friends,
  
  Today we will discuss what is schema and model in mongoose and what is the real purpose behind these concept.
  
  So let's start. Before going to topic we will discuss about some concept first.
  
  CONCEPT
  -------------
  1) What is mongoose and why it needed ?
  
  
  Ans:  In real world , our server side code(may be java, python, node etc) need to interact with database.For this blog, we will stick with 
        Node and mongoDB. MongoDB stores data in document manner.
        
  We have object in our node.js code which we need to store in MongoDB.
  So we need something which can map our object to document so that we can store it in database.That mapper is known as **"object document mapper" or ODM**. 
    
>So for Node.js and mongodb we have ODM known as "mongoose". 
 
 Now we are clear about what is mongoose and why it is needed now we will dive into our topic .So we need to understand how 'Mongoose' doing this mapping.
 
 Let's consider our MongoDB  structure.
 
    people               -- > collection name
    -------------
    {
      id:'1',                ----> document-1
      name :'Bob'
    }
    {
      id:'2',                ----> document-2
      name :'John'
    }   

so now we need one blueprint/constructor which can represent common structure of each document present in collection. This blueprint/constructor is known as **"Model"**. So every object created from this blueprint will be treated as document in mongoDB.Now our server side code will interact with mongoDB document via this "Model". 

Here if we observe we can say collection consist of a number of Model. 
>so Mongoose automatically looks for the plural version of your model name for  collection name.

    Example: 
    modelName                   Collection Name
    ---------                   ---------------
    Person                       People
    task                         tasks
    
Now our Model need to represent common structure.  We define that structure in a object known as **'Schema'**. So we need to derive our model from 'Schema'. So in mongoose documentation we can see the below line

>Models are fancy constructors compiled from Schema definitions. An instance of a model is called a document. Models are responsible for creating and reading documents from the underlying MongoDB database.

I hope you understood the concepts of schema and model in mongoose. 

You can share your thoughts or doubts in comment section .
    
    