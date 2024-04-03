# backpropagation
ERA assignment 6 backpropagation
Creates neural network by referring to the classroom Excel. 
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/981d2c27-54f5-44bc-9c25-3a3c34faead5)

1. The objective is to build a neural network, given inputs (i1, i2) and outputs (t1, t2)
2. Initial weights are known
3. h1, h2 are sums of weights multiplied by i/ps, on which sigmoid activation is applied to arrive at a_h1 and a_h2
   The formula is
   **h1=i1*w1+i2*w2**
   and
   **h2=i1*w3+i2*w4**
4. Apply sigmoid to calculate a_h1 **_a_h1=σ(h1)=1/1+exp(-h1)_** and **_a_h2 =σ(h2) = exp(h2)/1+exp(h2)_**
5. Apply weights w5 and w6 to get output from first layer o1 and o2
6. **o1=a_h1*w5 +a_h2*w6**
7. **o2=a_h1*w7+a_h2*w8**
