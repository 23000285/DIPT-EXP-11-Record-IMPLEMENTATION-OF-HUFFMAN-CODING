# DIPT-EXP-11-Record-IMPLEMENTATION-OF-HUFFMAN-CODING

**Name:** VENKATANATHAN P R  
**Register No:** 212223240173

---

## Aim

To implement Huffman coding to compress the data using Python.

---

## Software Required

1. Anaconda - Python 3.7
2. Jupyter Notebook / VS Code

---

## Algorithm & Explanation

### Step 1: Get the Input String

Get the input string that needs to be encoded using Huffman coding.

### Step 2: Calculate Frequency of Each Character

Calculate the frequency of occurrence of each character in the input string and store the character-frequency pairs.

### Step 3: Create Tree Nodes

Create individual tree nodes for each character using its corresponding frequency.

### Step 4: Implement Huffman Coding

Sort the nodes based on their frequency and select the two nodes with the smallest frequencies. Combine them into a new node with the sum of their frequencies. Repeat this process until a single node remains, which represents the complete Huffman tree.

### Step 5: Generate Huffman Codes

Traverse the Huffman tree recursively. Assign `0` to the left branch and `1` to the right branch to generate the Huffman code for each character.

### Step 6: Print the Characters and Huffman Codes

Display each character along with its corresponding Huffman code.

---

## Program

```python
# Step 1: Get the input string
input_string = "huffman coding"  # Example input string


# Step 2: Calculate frequency of each character in the input string
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1


# Step 3: Create tree nodes
nodes = [
    [char, freq]
    for char, freq in frequency.items()
]


# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(
        nodes,
        key=lambda x: x[1]
    )

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [
        [left, right],
        left[1] + right[1]
    ]

    nodes.append(new_node)


# The final node is the Huffman tree
huffman_tree = nodes[0]


# Step 5: Generate Huffman codes
huffman_codes = {}


def generate_codes(tree, code=""):

    if isinstance(tree[0], str):
        # If it's a leaf node
        huffman_codes[tree[0]] = code

    else:
        # If it's an internal node, recurse
        generate_codes(
            tree[0][0],
            code + "0"
        )

        generate_codes(
            tree[0][1],
            code + "1"
        )


generate_codes(huffman_tree)


# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

---

## Output

<img width="436" height="305" alt="image" src="https://github.com/user-attachments/assets/fd180691-4541-4762-a5ef-27d7ec7698fe" />


## Result

Thus, Huffman coding was successfully implemented using Python to generate variable-length binary codes based on the frequency of occurrence of characters in the input string.
