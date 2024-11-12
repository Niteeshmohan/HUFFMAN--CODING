# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1: Count the frequency of each character in the input string.

### Step2: Create nodes for each character and store them in a priority queue based on frequency.

### Step3: Combine the two nodes with the lowest frequency into a new node, repeating until one root node remains.

### Step4: Traverse the tree from root to each leaf node, assigning binary codes by adding '0' for left and '1' for right.

### Step5: Replace each character in the original string with its binary code, producing the compressed output.
 
## Program:
``` Python
Developed by : NITEESH M
Register number: 212222230098
# Get the input String
string =input()
# Create tree nodes
class NodeTree(object):
    def __init__(self, left=None, right=None): 
        self.left = left
        self.right=right
    def children(self):
        return (self.left,self.right)
    def nodes (self):
        return (self.left,self.right)
    def __str__(self):
        return '%s %s' %(self.left,self.right)


# Main function to implement huffman coding
def huffman_code_tree (node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree (l, True, binString + '0'))
    d.update(huffman_code_tree (r, False, binString + '1'))
    return d

# Calculate frequency of occurrence
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes=freq
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)

# Print the characters and its huffmancode
huffmanCode=huffman_code_tree(nodes[0][0])
print(' Char | Huffman code ') 
print('----------------------')
for (char, frequency) in freq:
    print('%-4r|%12s'%(char,huffmanCode[char]))

```
## Output:

### Print the characters and its huffmancode
<br>

![image](https://github.com/user-attachments/assets/9e909710-9823-4b38-942b-e011de7427e8)

<br>

## Result
Thus the huffman coding was implemented to compress the data using python programming.
