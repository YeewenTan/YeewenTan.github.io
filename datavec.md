---
title: DataVec - A Vectorization and ETL Library
layout: default
---

# DataVec: A Vectorization and ETL Library

DataVec solves one of the most important obstacles to effective machine or deep learning: getting data into a format that neural nets can understand. Nets understand vectors. Vectorization is the first problem many data scientists will have to solve to start training their algorithms on data. If your data is in CSV (Comma Seperated Values) format stored in flat files that must be converted to numeric and ingested, or your data is a directory structure of labelled images then DataVec is the tool to help you organize that data for use in DeepLearning4J. 


Please **read this entire page**, particularly the section [Reading Records](#record) below, before working with DataVec.



## Introductory Video

This video describes the conversion of image data to a vector. 

<iframe width="420" height="315" src="https://www.youtube.com/embed/EHHtyRKQIJ0" frameborder="0" allowfullscreen></iframe>

## Key Aspects
- [DataVec](https://github.com/deeplearning4j/DataVec) uses an input/output format system (similar in some ways to how Hadoop MapReduce uses InputFormat to determine InputSplits and RecordReaders, DataVec also provides RecordReaders to Serialize Data)
- Designed to support all major types of input data (text, CSV, audio, image and video) with these specific input formats
- Uses an output format system to specify an implementation-neutral type of vector format (ARFF, SVMLight, etc.)
- Can be extended for specialized input formats (such as exotic image formats); i.e. You can write your own custom input format and let the rest of the codebase handle the transformation pipeline
- Makes vectorization a first-class citizen
- Built in Transformation tools to convert and normalize data
- Please see the [DataVec Javadoc](http://deeplearning4j.org/datavecdoc/) here

There's a <a href="#tutorial">brief tutorial below</a>.

## A Few Examples

 * Convert the CSV-based UCI Iris dataset into svmLight open vector text format
 * Convert the MNIST dataset from raw binary files to the svmLight text format.
 * Convert raw text into the Metronome vector format
 * Convert raw text into TF-IDF based vectors in a text vector format {svmLight, metronome, arff}
 * Convert raw text into the word2vec in a text vector format {svmLight, metronome, arff}

## Targeted Vectorization Engines

 * Any CSV to vectors with a scriptable transform language
 * MNIST to vectors
 * Text to vectors
    * TF-IDF
    * Bag of Words
    * word2vec

## CSV Transformation Engine

If data is numeric and appropriately formatted then CSVRecordReader may be satisfactory.  If however your data has non-numeric fields such as strings representing boolean (T/F) or strings for labels then a Schema Transformation will be required. DataVec uses apache [Spark](http://spark.apache.org/) to perform transform operations. *note you do not need to know the internals of Spark to be succesful with DataVec Transform

## Schema Transformation Video

A video tutorial of a simple DataVec transform along with code is available [here](http://www.youtube.com/watch?v=L5DtC8_4F-c)

## Example Java Code

Our [examples](https://deeplearning4j.org/quickstart#examples) include a collection of DataVec examples.   

<!-- Note to Tom, write DataVec setup content

## <a name="tutorial">Setting Up DataVec</a>

Search for [DataVec](https://search.maven.org/#search%7Cga%7C1%7CDataVec) on Maven Central to get a list of JARs you can use.

Add the dependency information into your pom.xml.

-->


## <a name="record">Reading Records, Iterating Over Data</a>

The following code shows how to work with one example, raw images, transforming them into a format that will work well with DL4J and ND4J:

``` java
// Instantiating RecordReader. Specify height and width of images.
RecordReader recordReader = new ImageRecordReader(28, 28, true, labels);

// Point to data path. 
recordReader.initialize(new FileSplit(new File(labeledPath)));
```

The RecordReader is a class in DataVec that helps convert the byte-oriented input into data that's oriented toward a record; i.e. a collection of elements that are fixed in number and indexed with a unique ID. Converting data to records is the process of vectorization. The record itself is a vector, each element of which is a feature.

The [ImageRecordReader](https://github.com/deeplearning4j/Canova/blob/f03f32dd42f14af762bf443a04c4cfdcc172ac83/canova-nd4j/canova-nd4j-image/src/main/java/org/canova/image/recordreader/ImageRecordReader.java) is a subclass of the RecordReader and is built to automatically take in 28 x 28 pixel images. Thus, LFW images are scaled to 28 pixels x 28 pixels. You can change dimensions to match your custom images by changing the parameters fed to the ImageRecordReader, as long as you make sure to adjust the `nIn` hyperparameter, which will be equal to the product of image height x image width. 

Other parameters shown above include `true`, which instructs the reader to append a label to the record, and `labels`, which is the array of supervised values (e.g. targets) used to validate neural net model results. Here are all the RecordReader extensions that come pre-built with DataVec (you can find them by right-clicking on `RecordReader` in IntelliJ, clicking `Go To` in the drop-down menu, and selection `Implementations`):

![Alt text](./img/recordreader_extensions.png)

The DataSetIterator is a Deeplearning4J class that traverses the elements of a list. Iterators pass through the data list, accesses each item sequentially, keeps track of how far it has progressed by pointing to its current element, and modifies itself to point to the next element with each new step in the traversal.

``` java
// DataVec to DL4J
DataSetIterator iter = new RecordReaderDataSetIterator(recordReader, 784, labels.size());
```

The DataSetIterator iterates through input datasets, fetching one or more new examples with each iteration, and loading those examples into a DataSet object that neural nets can work with. The line above also tells the [RecordReaderDataSetIterator](https://github.com/deeplearning4j/deeplearning4j/blob/3e5c6a942864ced574c7715ae548d5e3cb22982c/deeplearning4j-core/src/main/java/org/deeplearning4j/datasets/canova/RecordReaderDataSetIterator.java) to convert the image to a straight line (e.g. vector) of elements, rather than a 28 x 28 grid (e.g. matrix); it also specifies the number of labels possible.

`RecordReaderDataSetIterator` can take as parameters the specific recordReader you want (for images, sound, etc.) and the batch size. For supervised learning, it will also take a label index and the number of possible labels that can be applied to the input (for LFW, the number of labels is 5,749). 

For a walkthrough of the other steps associated with moving data from DataVec to Deeplearning4j, you can read about [how to build a customized image data pipeline here](./simple-image-load-transform).

## Execution

Runs as both a local serial process and a MapReduce (MR engine on the roadmap) scale-out process with no code changes.

## Targetted Vector Formats
* svmLight
* libsvm
* Metronome
* ARFF

## Built-In General Functionality
* Understands how to take general text and convert it into vectors with stock techniques such as kernel hashing and TF-IDF

