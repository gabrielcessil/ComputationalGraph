# **Computational Graph-Based Automatic Differentiation**

## **Project Overview**
In modern numerical computing and machine learning, **automatic differentiation (AutoDiff)** plays a crucial role in efficiently computing gradients for optimization problems like **Neural Networks Backpropagation**. For those unfamiliar with Neural Networks theory, the backpropagation is the main driven force of training the model (learning about data) and it involves taking the partial derivatives of each one of the huge amount of adjustable parameters (compute how much each parameter influenciate the output and it's error in order to better tune it).

There are a handfull of methods of automatic differentiation, here you will find a Forward. This method enables to numerically evaluate **all** partial derivatives, given certain input values, taking no much longer than the processing time to evaluate the function output itself.

To do so, this project implements a **computational graph-based automatic differentiation system**, where mathematical expressions are represented as **directed graphs** based on python dictionaries and modularize it into classes. Each node in the graph corresponds to an operation (e.g., addition, multiplication, sine, power), while edges capture dependencies between variables.

### Complementary material about automatic differentiation:
- Amazing video with a very visual explanation: https://www.youtube.com/watch?v=wG_nF1awSSY
- Another great video but considering the Reverse method: https://www.youtube.com/watch?v=he_86Y4lQLw
- Full material in blog post format: https://www.ams.org/publicoutreach/feature-column/fc-2017-12
  
---

## **Project Features**
- A class-based implementation of a computational graph, allowing users to construct expressions dynamically.
- Support for common mathematical operations (addition, multiplication, exponentiation, trigonometric functions).
- Graph-based differentiation, enabling efficient computation of gradients via backpropagation.
- A structured visualization of the computational graph, helping users understand function composition.

---

# **Example**

## **Let's define the following function \\( f(x,y,z) \\)**

$$
f(x,y,z) = (xy + y^{\sin(z)})xy
$$

## **Where the partial derivatives are analytically defined as:**

$$
\frac{df}{dx} = y(2xy+y^{\sin(z)})
$$

$$
\frac{df}{dy} = x(2xy+\sin(z)y^{\sin(z)}+y^{\sin(z)})
$$

$$
\frac{df}{dz} = x\ln(y)\cos(z)y^{\sin(z)+1}
$$

### **With these analytical forms, we can verify the numerical results of the computational graph.**


## **Given:**
x = 1;

y = 3;

z = 0.5;

  
### Analytical values
----------------------------------------
Function: f = 14.080019381708262

Partial Derivatives:

  df/dx = 23.08001938170826

  df/dy = 8.505170136634511

  df/dz = 4.897763459363576



### Computed values
----------------------------------------
Function: f = 14.080019381708262

Partial Derivatives:

  df/dx = 23.08001938170826

  df/dy = 8.505170136634511

  df/dz = 4.897763459363575

----------------------------------------

## Structure output example: 

x is assigned to  var0 

y is assigned to  var1 

z is assigned to  var2 

Op1 is assinged to  var3 

Op2 is assinged to  var4 

Op3 is assinged to  var5 

Op4 is assinged to  var6 

Result is assinged to  var7 

🔗 var7: MULT

   ├──🔗 var6: ADD
   
   ├──   ├──🔗 var3: MULT
   
   ├──   ├──   ├──🔗 var0: SCAL
   
   ├──   ├──   └──🔗 var1: SCAL

   ├──   └──🔗 var5: POW
   
   ├──   └──   ├──🔗 var1: SCAL
   
   ├──   └──   └──🔗 var4: SIN
   
   ├──   └──   └──   └──🔗 var2: SCAL
   
   └──🔗 var3: MULT
   
   └──   ├──🔗 var0: SCAL
   
   └──   └──🔗 var1: SCAL

---
# Current State and Next Steps:

- Unfortunately, the current state of the code does not yet support matrix operations. Consequently, backpropagation for Neural Networks is also not currently supported. This feature will be added in future versions.
- Operation overloading is pretty much straight-forward, it was not implemented in this example to keep the examples more readable and less pythonic.
- Distributed computing and graph optimization would be essential for real applications.
 
 **Feel free to add examples and use it as a didactic source**



