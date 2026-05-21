# Record-IMPLEMENTATION-OF-HUFFMAN-CODING
## NAME : HARINI S
## REG NO : 212224240049
## EXP NO : 11

## Aim

To implement Huffman Coding using Python for generating variable-length binary codes based on the frequency of characters in a given string.

## Algorithm

- Start the program.
- Read the input string.
- Calculate the frequency of each character in the string.
- Create nodes for every character with its frequency.
- Sort the nodes based on frequency in ascending order.
- Select the two nodes with the smallest frequencies.
- Combine them into a new node with the sum of frequencies.
- Insert the new node back into the list.
- Repeat the process until only one node remains.
- The remaining node becomes the Huffman Tree.
- Traverse the Huffman Tree:
- Assign 0 for the left branch.
- Assign 1 for the right branch.
- Generate Huffman codes for all characters.
- Display the character and its corresponding Huffman code.
- Stop the program.
  
## Program
```PYTHON
# Get the input String
input_string = "harini"

# Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Main function to implement Huffman Coding
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]

    nodes.append(new_node)

# Final Huffman Tree
huffman_tree = nodes[0]

# Dictionary to store Huffman codes
huffman_codes = {}

# Function to generate codes
def generate_codes(tree, code=""):

    # Leaf node
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code

    # Internal node
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

# Generate Huffman Codes
generate_codes(huffman_tree)

# Display Huffman Codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
  ```

## Output 
<img width="228" height="129" alt="image" src="https://github.com/user-attachments/assets/810dd344-5fac-4102-9056-b82c42e0d637" />

## Result

The Huffman Coding algorithm was successfully implemented using Python.
The program generated Huffman codes for each character in the input string based on their frequencies. The output displayed the characters along with their corresponding binary Huffman codes.
