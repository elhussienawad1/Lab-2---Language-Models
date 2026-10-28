Forward

$$z = x,W_x + h_{prev},W_h + b$$
$$h = \tanh(z)$$

Given

$$dh = \frac{\partial L}{\partial h}$$

Step 1: through the tanh

$$\frac{\partial h}{\partial z} = 1 - \tanh^2(z) = 1 - h^2$$

$$\boxed{;dz = dh \odot (1 - h^2);}$$

($\odot$ = multiply element by element)

Step 2: through the sum

Written out one element at a time:

$$z_k = \sum_d x_d,W_x[d,k] ;+; \sum_j h_{prev,j},W_h[j,k] ;+; b_k$$

Previous state

$$\frac{\partial z_k}{\partial h_{prev,j}} = W_h[j,k] \quad\Rightarrow\quad dh_{prev,j} = \sum_k dz_k,W_h[j,k]$$

$$\boxed{;dh_{prev} = dz,W_h^{T};}$$

Input weights

$$\frac{\partial z_k}{\partial W_x[d,k]} = x_d \quad\Rightarrow\quad dW_x[d,k] = x_d,dz_k$$

$$\boxed{;dW_x = x^{T}dz;}$$

Hidden weights

$$\frac{\partial z_k}{\partial W_h[j,k]} = h_{prev,j} \quad\Rightarrow\quad dW_h[j,k] = h_{prev,j},dz_k$$

$$\boxed{;dW_h = h_{prev}^{T}dz;}$$

Bias

$$\frac{\partial z_k}{\partial b_k} = 1 \quad\Rightarrow\quad db_k = \sum_{n} dz[n,k]$$

$$\boxed{;db = \text{sum of }dz\text{ down the rows};}$$

Shapes

$$x:(N,D)\qquad h_{prev},h,z:(N,H)\qquad W_x:(D,H)\qquad W_h:(H,H)\qquad b:(H)$$

$$dz:(N,H)\qquad dh_{prev}:(N,H)\qquad dW_x:(D,H)\qquad dW_h:(H,H)\qquad db:(H)$$

Each result has the same shape as the thing it is the derivative of.