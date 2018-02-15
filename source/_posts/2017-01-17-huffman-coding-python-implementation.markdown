---
layout: post
title: "Huffman Coding - Python Implementation"
date: 2017-01-17 23:47:55 +0530
updated: 2017-01-17 23:47:55 +0530
description: Python implementation of Huffman Coding, with working compression and decompression functions
comments: true
categories: [Python, Code]
---

[Huffman Coding](https://en.wikipedia.org/wiki/Huffman_coding) is one of the lossless data compression techniques. It assigns variable-length codes to the input characters, based on the frequencies of their occurence. The most frequent character is given the smallest length code. <br> <!-- more -->

<center>
	{% img [erimg] /images/huffman/huffman.png HuffmanCoding %}
</center><br>


I thought of implementing the data compression program. The key things in the implementation were: <br> 

* Building frequency dictionary

* Select 2 minimum frequency symbols and merge them repeatedly: Used Min Heap 

* Build a tree of the above process: Created a HeapNode class and used objects to maintain tree structure

* Assign code to characters: Recursively traversed the tree and assigned the corresponding codes

* Encode the input text. Added padding to the encoded text, if it's not of a length of multiple of 8. Stored this padding information, in 8 bits, in the beginning of the resultant code.

* Write the result to an output binary file, which will be our compressed file.


<h3 style="margin: 0;
    font-weight: 600;
    color: #888;">
    End result</h3>
After running on a several sample text files, Compression Ratio on an average was achieved to be 2.1 : 1.

So it's like you have your very own text file compression program.


I implemented both the *compression* and *decompression* functions. Decompressing the compressed file brought back the original state of the file, without any data loss.


Before you look at the code from beginning, first check out the outline of the 2 functions **compress** (line 101) and **decompress** (line 157) , and then look at details of the other functions called from them.


<table class="table">
	<tr class="center">
		<th>Compression <small style="font-weight: normal;"> (line 101)</small></th>
		<th>Decompression <small style="font-weight: normal;"> (line 157)</small></th>
	</tr>
	<tr>
		<td>
			<ol>
				<li>Make frequency dictionary</li>
				<li>Make heap</li>
				<li>Merge Nodes and build tree</li>
				<li>Make codes</li>
				<li>Encode Text</li>
				<li>Pad encodded text</li>
				<li>Make byte array</li>
				<li>Output the byte array to binary file</li>
			</ol>
		</td>
		<td>
			<ol>
				<li>Read binary file</li>
				<li>Remove padding</li>
				<li>Decode text</li>
				<li>Output decoded text to txt file</li>
			</ol>
		</td>
	</tr>
</table>

The class `HuffmanCoding` takes complete path of the text file to be compressed as parameter. (as its data members store data specific to the input file). 

The *compress()* function returns the path of the output compressed file. 

The function *decompress()* requires path of the file to be decompressed. (and *decompress()* is to be called from the same object created for *compression*, so as to get code mapping from its data members)

{% gist a0e50b1b468cff905346b451ab3a2c39 HuffmanCoding.py %}


<h3 style="margin: 0;
    font-weight: 600;
    color: #888;">
    Running the program:</h3>


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


<h3 style="margin: 0;
    font-weight: 600;
    color: #888;">
    Result</h3>

On running on the above linked sample text file:


<table class="table">
	<tr>
		<td><b>Initial Size:</b></td>
		<td>715.3 kB</td>
	</tr>
	<tr>
		<td><b>Compressed file Size:</b></td>
		<td>394.0 kB</td>
	</tr>
</table>

Plus, the decompressed file comes out to be exactly the same as the original file, without any data loss.


And that is all for Huffman Coding implementation, with compression and decompression. This was fun to code.

> The above program requires the decompression function to be run using the same object that created the compression file (because the code mapping is stored in its data members). We can also make the compression and decompression function run independently, if somehow, during compression we store the mapping info also in the compressed file (in the beginning). Then, during decompression, we will first read the mapping info from the file, then use that mapping info to decompress the rest file.


<button type="button" class="btn btn-default">
	<a href="https://github.com/bhrigu123/huffman-coding" target="_blank">
	View on GitHub</a>
</button>