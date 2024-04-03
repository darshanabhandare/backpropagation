# Backpropagation Assignment
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

Repeat for the next layer and get 
**a_o1=σ(o1)
a_o2=σ(o2)**

we consider 
**E1 = 1/2 * (t1-a_o1)^2
E2 = 1/2 * (t2-a_o2)^2**
and total error 
**E_Total = E1 + E2**

**Backpropagation is to identify the rate of change in the error**
Below is how we derive the effect of each weight on the total error

*  ∂E1/∂a_h1 = ∂E1/∂a_o1 * ∂a_o1/∂o1*∂o1/∂w5*∂w5/∂a_h1
*  a_o1-t1 * a_o1*(1-a_o1)* w5

* ∂E2/∂a_h1 = a_o2-t2 * a_o2*(1-a_o2)  * w7
**so we get formula for total error**
* ∂E_total/∂a_h1 =∂E1/∂a_h1 +∂E2/∂a_h1
* ∂E_total/∂a_h1 = a_o1-t1 * a_o1*(1-a_o1)* w5 + a_o2-t2 * a_o2*(1-a_o2)  * w7
* ∂E_total/∂a_h2 = a_o1-t1 * a_o1*(1-a_o1)* w6 + a_o2-t2 * a_o2*(1-a_o2)  * w8

* ∂E_Total/∂w5 = ∂(E1+E2)/∂w5
* **w5 has no effect on E2 since it is out of the path**
* ∂E_Total/∂w5 = ∂(E1)/∂w5
* 
**Split the derivatives**
* ∂E_Total/∂w5 = ∂(E1)/∂w5 =  ∂E1/a_o1 * ∂a_o1/∂o1 * ∂o1/∂w5
* ∂E1/a_o1 =  ∂(1/2 * (t1-a_o1)^2)/∂a_o1 = a_o1-t1
* ∂a_o1/∂o1 = ∂( σ(o1))/∂o1 = σ(o1) * (1 - σ(o1)) = a_o1 * ( 1 - a_o1)
* ∂o1/∂w5 = ∂(a_h1*w5 + a_h2*w6)/∂w5 = a_h1
* 
**which will give us the rate of change of Error w.r.t weights as below**
* ∂E_total/∂w1 =∂E_total/∂a_h1 * ∂a_h1/∂h1 * ∂h1/∂w1 
* ∂E_total/∂w2 =∂E_total/∂a_h1 * ∂a_h1/∂h1 * ∂h1/∂w2
* ∂E_total/∂w3 =∂E_total/∂a_h2 * ∂a_h2/∂h2 * ∂h2/∂w3
* ∂E_total/∂w4 =∂E_total/∂a_h2 * ∂a_h2/∂h2 * ∂h2/∂w4

**Finally the rate of change of Error_total w.r.t all Weights comes to**

* ∂E_total/∂w1 =(a_o1-t1 * a_o1*(1-a_o1)* w5 + a_o2-t2 * a_o2*(1-a_o2)  * w7)* ∂a_h1/∂h1 * ∂h1/∂w1 
* ∂E_total/∂w1 =(a_o1-t1 * a_o1*(1-a_o1)* w5 + a_o2-t2 * a_o2*(1-a_o2)  * w7)* a_h1(1-a_h1) * i1
* ∂E_total/∂w2 =(a_o1-t1 * a_o1*(1-a_o1)* w5 + a_o2-t2 * a_o2*(1-a_o2)  * w7)* a_h1(1-a_h1) * i2
* ∂E_total/∂w3 =(a_o1-t1 * a_o1*(1-a_o1)* w6 + a_o2-t2 * a_o2*(1-a_o2)  * w8)* a_h2(1-a_h2) * i1
* ∂E_total/∂w4 =(a_o1-t1 * a_o1*(1-a_o1)* w6 + a_o2-t2 * a_o2*(1-a_o2)  * w8)* a_h2(1-a_h2) * i2

* ∂E_Total/∂w5 = a_o1-t1 * a_o1*(1-a_o1) * a_h1
* ∂E_Total/∂w6 = a_o1-t1 * a_o1*(1-a_o1) * a_h2
* ∂E_Total/∂w7 = a_o2-t2 * a_o2*(1-a_o2) * a_h1
* ∂E_Total/∂w8 = a_o2-t2 * a_o2*(1-a_o2) * a_h2



Calculate all these in the excel columns.
Keep t1, t2, i1, i2 constant

weights in the next epoc will be decided by learning rate 
set lr = 1 and see the line chart
change lr to different values to see the variations in the learning curve.

LR = 0.1
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/66b8776d-db55-4a5b-a73e-2807b7123764)

LR = 0.2
0.5![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/f00124c8-6ffc-4c58-8e61-bbb455846535)

LR = 0.5
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/a2af76f4-3bb1-4b43-9a7c-b15ed2bb8704)

LR = 0.8
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/61be5b2f-c6b6-4258-b770-7ca079e69fe9)

LR = 1.0
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/e1259baf-47ce-4284-ba91-25c502343ddb)

LR = 2.0
![image](https://github.com/darshanabhandare/backpropagation/assets/73514918/7024ce3c-5e51-4624-841b-ab402c8d6c0b)


