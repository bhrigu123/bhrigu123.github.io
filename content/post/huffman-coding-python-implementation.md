+++
title = "Huffman Coding Python Implementation"
date = "2017-01-17"
lastmode = "2020-07-02 00:51:55 +0530"
description = "Python implementation of Huffman Coding, with working compression and decompression functions"
aliases = ["/blog/2017/01/17/huffman-coding-python-implementation"]
tags = ["Programming"]
images = ["/images/huffman/huffman.png"]
authors = ["Bhrigu"]
+++

Huffman Coding is one of the lossless data compression techniques. It assigns variable-length codes to the input characters, based on the frequencies of their occurence. The most frequent character is given the smallest length code. 
<!--more-->


---
**Update**: I now have this article as YouTube video lessons now. It's in two parts: 1) Explanation of Huffman Coding 2) Implementing Huffman Coding in Python with explanation and doing hands-on coding with a demo. Check out the videos on **Youtube** below:

1. [Huffman Coding - Explanation and Example](https://youtu.be/_Kl3TtBXxq8)
2. [Huffman Coding - Python Implementation and Demo](https://youtu.be/JCOph23TQTY)
---

[contd.]

I thought of implementing the data compression program. The key things in the implementation were:  

* Building frequency dictionary

* Select 2 minimum frequency symbols and merge them repeatedly: Used Min Heap 

* Build a tree of the above process: Created a HeapNode class and used objects to maintain tree structure

* Assign code to characters: Recursively traversed the tree and assigned the corresponding codes

* Encode the input text. Added padding to the encoded text, if it's not of a length of multiple of 8. Stored this padding information, in 8 bits, in the beginning of the resultant code.

* Write the result to an output binary file, which will be our compressed file.


### End result
After running on a several sample text files, Compression Ratio on an average was achieved to be 2.1 : 1.

So it's like you have your very own text file compression program.


I implemented both the *compression* and *decompression* functions. Decompressing the compressed file brought back the original state of the file, without any data loss.


Before you look at the code from beginning, first check out the outline of the 2 functions **compress** (line 101) and **decompress** (line 157) , and then look at details of the other functions called from them.


| Compression (line 101)               | Decompression (line 157)        |
|--------------------------------------|---------------------------------|
| Make frequency dictionary            | Read binary file                |
| Make heap                            | Remove padding                  |
| Merge Nodes and build tree           | Decode text                     |
| Make codes                           | Output decoded text to txt file |
| Encode Text                          |                                 |
| Pad encodded text                    |                                 |
| Make byte array                      |                                 |
| Output the byte array to binary file |                                 |


The class `HuffmanCoding` takes complete path of the text file to be compressed as parameter. (as its data members store data specific to the input file). 

The *compress()* function returns the path of the output compressed file. 

The function *decompress()* requires path of the file to be decompressed. (and *decompress()* is to be called from the same object created for *compression*, so as to get code mapping from its data members)

{{< gist bhrigu123 a0e50b1b468cff905346b451ab3a2c39 >}}

### Running the program:


Save the above code, in a file `huffman.py`.


Create a sample text file. Or download a sample file from [sample.txt](https://raw.githubusercontent.com/bhrigu123/huffman-coding/master/sample.txt) (right click, save as)


Save the code below, in the same directory as the above code, and Run this python code (edit the `path` variable below before running. initialize it to text file path)

```python UseHuffman.py
from huffman import HuffmanCoding

#input file path
path = "/home/ubuntu/Downloads/sample.txt"

h = HuffmanCoding(path)

output_path = h.compress()
h.decompress(output_path)
```

The compressed `.bin` file and the decompressed file are both saved in the same directory as of the input file.


### Result:

On running on the above linked sample text file:


| Initial Size: | Compressed file size: |
|---------------|-----------------------|
| 715.3 KB      | 394.0 KB              |


Plus, the decompressed file comes out to be exactly the same as the original file, without any data loss.


And that is all for Huffman Coding implementation, with compression and decompression. This was fun to code.

> The above program requires the decompression function to be run using the same object that created the compression file (because the code mapping is stored in its data members). We can also make the compression and decompression function run independently, if somehow, during compression we store the mapping info also in the compressed file (in the beginning). Then, during decompression, we will first read the mapping info from the file, then use that mapping info to decompress the rest file.

[View On Github](https://github.com/bhrigu123/huffman-coding)

