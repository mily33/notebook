## 矩阵求导

矩阵求导是转置还是不转置，之前都是根据矩阵维度来判断的，现在想想真的很傻逼。。

口诀：前导不转后导转

$$\frac{\delta A^T x}{\delta x} = A$$
$$\frac{\delta x^T A}{\delta x} = (\frac{\delta A^T x}{\delta x})^T = ((A^T)^T)^T = A^T$$
$$$$


