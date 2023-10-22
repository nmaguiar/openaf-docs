---
layout: default
title: ow.ai
parent: Reference
grand_parent: OpenAF docs
---


## ow.ai

### ow.ai.cluster

__ow.ai.cluster(args) : Object__

````
Wraps access to clustering of data. The result will be an object with a classify method that will  return the clustering result given the provided data. Args expects different arguments depending on type of  clustering:

   args.type                (String) "kmeans" (default)
   args.numberOfClusters    (Number) number of clusters to use (default to 5)
   classify(normalizedData) (Map)    returns a map of centroids and cluster assignments


````
### ow.ai.decisionTree

__ow.ai.decisionTree(aMap) : Object__

````
Provides a wrapper to access the existing decision tree algorithms included:

ID3:
  type              'id3'
  trainingSet       (array of maps)   The training data
  categoryAttr      (key name)        The map key to build the decision tree on
  ignoredAttributes (array of keys)   The list of keys to be ignored in each map

RandomForest:
  type              'randomforest'
  trainingSet       (array of maps)   The training data
  categoryAttr      (key name)        The map key to build the decision tree on
  ignoredAttributes (array of keys)   The list of keys to be ignored in each map
  treesNumber       (number)          The number of decision trees to use

C45:
  type              'c45'
  data              (array of arrays) The training data
  features          (arrays of keys)  The keys name by order of each array data value
  featureTypes      (arrays of types) Categorization of each attribute between 'category' and 'number'
  target            (key)             The target key name (the last of each array data value)
````
### ow.ai.network

__ow.ai.network(aMap) : ow.ai.network__

````
Creates a neural network given the parameters in aMap. aMap should contain a "type" parameter to indicate the type of network (perceptron, lstm, liquid or hopfield). Then aMap should contain a "args" parameter to provide each network inialization parameters. Please see "help ow.ai.network.[type of network]" for more details about each one.
````
### ow.ai.network.fromJson

__ow.ai.network.fromJson(aMap)__

````
Tries to rebuild the network from aMap returned previously by a toJson function.
````
### ow.ai.network.get

__ow.ai.network.get(inputArray) : Array__

````
Given an inputArray of decimal values, normalize between 0 and 1, will activate the current network and  return an output array of decimal values between 0 and 1.
````
### ow.ai.network.hopfield

__ow.ai.network.hopfield(args) : ow.ai.network__

````
Hopfield serves as a content-addressable memory remembering patterns and when feed with new patterns the network returns the most similar one from the patterns it was trained to remember. You need to provide then number of input patterns args = [ 10 ].
````
### ow.ai.network.liquid

__ow.ai.network.liquid(args) : ow.ai.network__

````
Liquid state machines are neural networks where neurons are randomly connected to each other. The recurrent nature of the connections turns the time varying input into a spatio-temporal pattern of activations in the network nodes. You need to provide args = [number of inputs, size of pool of neurons, number of outputs, number of random connections, number of random gates] (e.g. 2, 20, 1, 30, 10).
````
### ow.ai.network.lstm

__ow.ai.network.lstm(args) : ow.ai.network__

````
LSTM (Long short-term memory) are well-suited to learn from experience to classify, process and predict time series when there are very long time lags of unknown size between important events. There is a minimum of 3 layers (input, memory block (input, memory cell, forget gate, output gate), output). args = [2, 6, 1] means 2 input, 6 memory blocks, 1 output; args = [2, 4, 4, 4, 1] means 2 input neurons, 3 memory blocks and 1 output.
````
### ow.ai.network.perceptron

__ow.ai.network.perceptron(args) : ow.ai.network__

````
Perceptron or feed-forward neural networks. There is a minimum of 3 layers (input, hidden and output) and a any nmumber of hidden layers. args = [2, 3, 1] means 2 input neurons, 3 hidden neurons and 1 output neuron; args = [2, 10, 10, 10, 10, 1] means 2 input neurons, 4 layers of 10 neurons and 1 output neuron.
````
### ow.ai.network.put

__ow.ai.network.put(inputArray, outputArray, learningRate)__

````
Given an inputArray of decimal values, normalize between 0 and 1, will activate the current network and then the outputArray of decimal values, normalize between 0 and 1, with an optionial learningRate (defaults to 0.3).
````
### ow.ai.network.readFile

__ow.ai.network.readFile(aFile)__

````
Rebuilds a network from a map stored in aFile previously with ow.ai.network.writeFile.
````
### ow.ai.network.toJson

__ow.ai.network.toJson() : Map__

````
Returns a map representation of the current network to be later rebuilt with the fromJson function.
````
### ow.ai.network.train

__ow.ai.network.train(trainingData, trainArgs)__

````
Trains the current network with the trainingData provided. trainingData should be an array of maps. Each  map entry should have a input and output keys. Each input and output entries should be an array for the  entry values and output values normalized to a decimal number between 0 and 1. Example:
[{input: [0,0], output: [0]}, {input: [0,1], output: [1]}, {input: [1,0], output: [1]}, {input: [1,1], output :[0]}]\. 

````
### ow.ai.network.writeFile

__ow.ai.network.writeFile(aFile)__

````
Writes a compressed file with the map representation of the current network.
````
### ow.ai.normalize.intArray

__ow.ai.normalize.intArray(anArray) : Array__

````
Returns anArray where all numbers have been rounded to an integer value.
````
### ow.ai.normalize.scaleArray

__ow.ai.normalize.scaleArray(anArray, aMax, aMin) : Array__

````
Given anArray of numbers tries to normalize returning an array of values between 0 and 1. If aMax or aMin are not provided they will be infered from the provided anArray.
````
### ow.ai.normalize.toFeaturesArray

__ow.ai.normalize.toFeaturesArray(anArrayOfObjects, ignoredAttrs) : Map__

````
Tries to convert anArrayOfObjects into an array of array of values where each value is positioned in the resulting array by the corresponding key sorted. The result will be a map with the resulting array in 'data' (with the features values ignoring any key on ignoredAttrs), the 'ignoredAttrs' and keys with all the 'keys' identified.
````
### ow.ai.normalize.withSchema

__ow.ai.normalize.withSchema(aSimpleMapOfData, aMapSchema, convertBools) : Array__

````
Tries to normalize and return aSimpleMapOfData normalized according with aMapSchema provided. Each element of aMapSchema should be a map describing how to normalize aSimpleMapOfData. Example:

var ar = [
   {name:'workout', duration:'120', enjoy: true, time:1455063275, tags:['gym', 'weights'], crucial: false },
   {name:'lunch', duration:'45', enjoy: false, time:1455063275, tags:['salad', 'wine'], crucial: true },
   {name:'sleep', duration:'420', enjoy: true, time:1455063275, tags:['bed', 'romance'], crucial: true}
];

var sar = {
   name    : { col: 0, oneOf: [ 'workout', 'lunch', 'sleep' ] },
   duration: { col: 1, min: 0, max: 1000 },
   enjoy   : { col: 2 },
   tags    : { col: 3, anyOf: [ 'gym', 'weights', 'salad', 'wine', 'bed', 'romance' ] },
   crucial : { col: 4, scaleOf: [
     { val: true,  weight: 0.85 },
     { val: false, weight: 0.15 }
   ]},
};

$from(ar).sort("time").select((r) => { return normalize(r, sar); });


````
### ow.ai.regression

__ow.ai.regression() : Regression__

````
Returns a Regression with the following functions:

   linear(data, options) : Map
   power(data, options) : Map
   exponential(data, options) : Map
   logarithmic(data, options) : Map
   polynomial(data, options) : Map

   data - an array of arrays of x, y values ([[0,1],[1,3],[2,5]])
   options - map to determine the order and precision ({ order: 2, precision: 5})


````
