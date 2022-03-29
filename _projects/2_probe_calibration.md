---
layout: page
title: Probe Calibration
description: Calibrating a Surgical Drill Bit using Physical-to-Image (3D-2D) Transformation
img: assets/img/project-2_probe/calibration_inverted.png
importance: 1
category: work
---

## <span style="color:#ff4703">Acknowledgements</span>

This project was done in association with the Medical Image Guidance (MIG) team at the [Indian Institute of Technology - Madras](https://www.iitm.ac.in/) under the supervision of my principal investigator [Dr. Ramya Balachandran](http://www.ee.iitm.ac.in/~bramya/), her PhD student Ms. Ruchitha Manne, and her Junior Research Fellow Mr. Swaminathan. This work was funded by the [Department of Biotechnology](http://dbtindia.gov.in/) (Government of India under the Ramalingaswami Fellowship Grant) and the [Science and Engineering Research Board](http://www.serb.gov.in/home.php) (Government of India under the Early Career Research Award).

## <span style="color:#ff4703">Objective</span>

To calibrate a surgical drill bit (probe tip) using 3D-2D transformation.

## <span style="color:#ff4703">Method</span>

In order to calibrate a probe tip, there are two ways to do it. 

1. When the tip remains stationary in a time interval $$t_1$$ to $$t_n$$.
2. When the tip moves around from time interval $$t_1$$ to $$t_n$$. 

### <span style="color:#ff7f50">Calibration of stationary probe tip</span>

[Source](http://rwthmeditec.github.io/TRTK/html/class_t_r_t_k_1_1_pivot_calibration_combinatorial_approach.html)

<div class="row justify-content-sm-center">
    {% include figure.html path="assets/img/project-2_probe/calibration_inverted.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>

To find the pose components, i.e., rotation *$$R$$* and translation **$$t$$**, of a stationary probe tip, we can use the standard equation for displacing a point using *$$R$$* and **$$t$$**:
\begin{equation}
\mathbf{x}' = R . \mathbf{x} + \mathbf{t}\nonumber
\end{equation}
where $$\mathbf{x}'$$ is the new location of the probe tip $$\mathbf{x}$$ after it is rotated and translated by *$$R$$* and **$$t$$** respectively. We note that $$\mathbf{x}' = \mathbf{x}$$, if the probe tip remains stationary. For time interval $$[1,n]$$, we can construct a system of equations as follows. 

<p align=center>
$$\mathbf{x} = R_1 . \mathbf{x} + \mathbf{t}_1$$
$$\mathbf{x} = R_2 . \mathbf{x} + \mathbf{t}_2$$
$$\vdots$$
$$\mathbf{x} = R_n . \mathbf{x} + \mathbf{t}_n$$
</p>

We can write the first equation like,
<p align=center>
$$R_1 . \mathbf{x} + \mathbf{t}_1 = R_2 . \mathbf{x} + \mathbf{t}_2$$
$$R_1 . \mathbf{x} - R_2 . \mathbf{x} = \mathbf{t}_2 - \mathbf{t}_1$$
</p>

Repeating this LHS and RHS obtained from entire time interval $$[1,n]$$, we can construct a matrix formulation as follows,

\begin{equation}
\begin{pmatrix}
R_1 & -R_{2}\newline
R_1 & -R_{2}\newline
\vdots & \vdots\newline
R_n & -R_{n-1}
\end{pmatrix} t = \begin{pmatrix}
t_2 & -t_1\newline
t_3 & -t_1\newline
\vdots & \vdots\newline
t_{n-1} & -t_n\newline
\end{pmatrix}\nonumber
\end{equation}

which takes the form, 
<p align=center> 
$$A t = b$$ 
</p>

However, the matrix $$A$$ is non-square, i.e., it is of size $$n \times 2$$. Therefore, we use the Moore-Penrose pseudoinverse to find **$$t$$** as follows,
<p align=center> 
$$t = {(A^T A)}^{-1} A^T b$$ 
</p>



### <span style="color:#ff7f50">Calibration of moving probe tip</span>

To find the pose components, i.e., rotation *R* and translation **t**, of a moving probe tip, we perform point-based rigid registration as follows. 

1. Compute weighted centroid **$$\bar{x}$$** and **$$\bar{y}$$** using points $$\langle$$**$$\bar{x}$$**$$_i$$ , **$$\bar{y}$$**$$_i \rangle$$.
2. Compute the displacement of each point using,
   <p align=center>
   $$\mathbf{\tilde{x}}_i = \mathbf{x}_i - \bar{\mathbf{x}}$$
   $$\mathbf{\tilde{y}}_i = \mathbf{y}_i - \bar{\mathbf{y}}$$
   </p>
3. Compute the covariance matrix using,
   <p align=center>
   $$H = \ \sum_{i}^{N} \mathbf{\tilde{x}}_i \mathbf{\tilde{y}}_i^t \ $$
   </p>
4. Perform Singular Value Decomposition of H.\\
   <p align=center> 
   $$H = U \Lambda V $$
   </p>
5. Obtain the rotation matrix.
   <p align=center> 
   $$ R = V . diag(1, 1, det(VU)) . U^t$$
   </p>
6. Obtain the translation vector. 
   <p align=center>
   $$ \mathbf{t} = \mathbf{\bar{y}} - R\mathbf{\bar{x}} $$
   </p>

