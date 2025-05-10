# De Bruijn Graph Generator for DNA Sequences

This repository provides a simple Python implementation to generate a **De Bruijn graph** from a given DNA sequence and k-mer length.

## Overview

De Bruijn graphs are widely used in computational biology, especially in genome assembly, where they help reconstruct the original DNA sequence from short sequencing reads. This script takes a DNA string and a `k` value as input and constructs a graph where:

- Each node represents a (k-1)-mer.
- An edge from node A to node B exists if there is a k-mer in the DNA string where A is the prefix and B is the suffix.

## Usage

### Function

```python
def de_bruijn_graph(k, text):
    graph = {}

    for i in range(len(text) - k + 1):
        kmer = text[i:i + k - 1]
        next_kmer = text[i + 1:i + k]

        if kmer in graph:
            graph[kmer].append(next_kmer)
        else:
            graph[kmer] = [next_kmer]

    return graph

Example
k_value = 12
input_text = "TCCCGGTGAACAAGTTTACTGGCCAACCCACGCGCATACGCAGTGCCTTTCAT..."

result_graph = de_bruijn_graph(k_value, input_text)

for node, neighbors in result_graph.items():
    print(f"{node}: {' '.join(neighbors)}")

```

### Output Format

Each line in the output shows a node followed by the list of its connected nodes (edges):
TCCCGGTGAAC: CCCGGTGAACA
CCCGGTGAACA: CCGGTGAACAA
...

### Requirements
Python 3.6 or higher
No external dependencies are required.

### License
This project is licensed under the MIT License.




