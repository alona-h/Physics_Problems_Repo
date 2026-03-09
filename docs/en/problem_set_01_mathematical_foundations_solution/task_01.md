# Problem Set 1 – Problem 1: Vectors and Linear Transformations

---

## Part 1 – Vector Operations

**Given:**
$$\vec{a} = (2, -1, 3), \qquad \vec{b} = (1, 4, -2)$$

---

### 1.1 – Lengths of the vectors $|\vec{a}|$ and $|\vec{b}|$

The **length (magnitude)** of a vector $\vec{v} = (v_1, v_2, v_3)$ is defined as:
$$|\vec{v}| = \sqrt{v_1^2 + v_2^2 + v_3^2}$$

**For $\vec{a} = (2, -1, 3)$:**
$$|\vec{a}| = \sqrt{2^2 + (-1)^2 + 3^2} = \sqrt{4 + 1 + 9} = \sqrt{14}$$

**For $\vec{b} = (1, 4, -2)$:**
$$|\vec{b}| = \sqrt{1^2 + 4^2 + (-2)^2} = \sqrt{1 + 16 + 4} = \sqrt{21}$$

> **Explanation:** The magnitude of a vector is essentially its "length" in space — the straight-line distance from the origin to the tip of the vector. It's computed by squaring each component, summing them, and taking the square root. This comes directly from the Pythagorean theorem generalized to 3D.

---

### 1.2 – Normalized vector $\hat{a} = \frac{\vec{a}}{|\vec{a}|}$

A **unit vector** (normalized vector) has the same direction as the original vector but has a magnitude of exactly 1. It is computed by dividing each component by the magnitude:

$$\hat{a} = \frac{\vec{a}}{|\vec{a}|} = \frac{(2, -1, 3)}{\sqrt{14}}$$

$$\hat{a} = \left(\frac{2}{\sqrt{14}},\ \frac{-1}{\sqrt{14}},\ \frac{3}{\sqrt{14}}\right)$$

**Verification:**
$$|\hat{a}| = \sqrt{\left(\frac{2}{\sqrt{14}}\right)^2 + \left(\frac{-1}{\sqrt{14}}\right)^2 + \left(\frac{3}{\sqrt{14}}\right)^2} = \sqrt{\frac{4 + 1 + 9}{14}} = \sqrt{\frac{14}{14}} = 1 \checkmark$$

> **Explanation:** Normalization is useful whenever you care about *direction* but not magnitude. For example, in physics, a unit vector is used to specify the direction of a force or velocity without encoding any particular speed or strength. Dividing by the magnitude "scales down" the vector to length 1.

---

### 1.3 – Dot product $\vec{a} \cdot \vec{b}$ and angle between the vectors

The **dot product** of two vectors is:
$$\vec{a} \cdot \vec{b} = a_1 b_1 + a_2 b_2 + a_3 b_3$$

**Calculation:**
$$\vec{a} \cdot \vec{b} = (2)(1) + (-1)(4) + (3)(-2) = 2 - 4 - 6 = -8$$

**Finding the angle $\theta$:**

Using the formula:
$$\vec{a} \cdot \vec{b} = |\vec{a}|\ |\vec{b}| \cos\theta$$

Solving for $\theta$:
$$\cos\theta = \frac{\vec{a} \cdot \vec{b}}{|\vec{a}|\ |\vec{b}|} = \frac{-8}{\sqrt{14} \cdot \sqrt{21}} = \frac{-8}{\sqrt{294}}$$

Simplifying $\sqrt{294}$:
$$\sqrt{294} = \sqrt{2 \cdot 3 \cdot 7^2} = 7\sqrt{6}$$

$$\cos\theta = \frac{-8}{7\sqrt{6}} \approx \frac{-8}{17.146} \approx -0.4667$$

$$\theta = \arccos(-0.4667) \approx 117.8°$$

> **Explanation:** The dot product measures how much two vectors "point in the same direction." A positive dot product means the angle between the vectors is less than 90° (they lean toward each other), zero means they are perpendicular, and a negative value (as here, $-8$) means the angle is greater than 90° — the vectors point in somewhat opposite directions. The formula connecting the dot product to the angle is one of the most fundamental relationships in linear algebra.

---

### 1.4 – Cross product $\vec{a} \times \vec{b}$ and area of the parallelogram

The **cross product** of $\vec{a} = (a_1, a_2, a_3)$ and $\vec{b} = (b_1, b_2, b_3)$ is computed using the determinant formula:

$$\vec{a} \times \vec{b} = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{vmatrix}$$

Expanding:
$$\vec{a} \times \vec{b} = \vec{i}(a_2 b_3 - a_3 b_2) - \vec{j}(a_1 b_3 - a_3 b_1) + \vec{k}(a_1 b_2 - a_2 b_1)$$

**Substituting values** ($\vec{a} = (2,-1,3)$, $\vec{b} = (1,4,-2)$):

- $i$-component: $(-1)(-2) - (3)(4) = 2 - 12 = -10$
- $j$-component: $-[(2)(-2) - (3)(1)] = -[-4 - 3] = -(-7) = 7$
- $k$-component: $(2)(4) - (-1)(1) = 8 + 1 = 9$

$$\vec{a} \times \vec{b} = (-10,\ 7,\ 9)$$

**Area of the parallelogram:**

The area equals the magnitude of the cross product:
$$\text{Area} = |\vec{a} \times \vec{b}| = \sqrt{(-10)^2 + 7^2 + 9^2} = \sqrt{100 + 49 + 81} = \sqrt{230}$$

$$\text{Area} = \sqrt{230} \approx 15.17$$

> **Explanation:** The cross product produces a new vector that is *perpendicular* to both $\vec{a}$ and $\vec{b}$. Its magnitude equals the area of the parallelogram formed by the two vectors. This is extremely useful in physics and engineering: for example, torque is computed as a cross product of a position vector and a force vector, and the result is perpendicular to both, pointing along the axis of rotation.

---

## Part 2 – Matrix Operations

**Given matrix:**
$$A = \begin{pmatrix} 2 & 1 & 0 \\ 0 & 1 & -1 \\ 1 & 0 & 1 \end{pmatrix}$$

---

### 2.1 – Matrix-vector product $A\vec{a}$

To multiply a $3\times3$ matrix by a vector $\vec{a} = (2, -1, 3)^T$, each row of the matrix is dotted with the vector:

$$A\vec{a} = \begin{pmatrix} 2 & 1 & 0 \\ 0 & 1 & -1 \\ 1 & 0 & 1 \end{pmatrix} \begin{pmatrix} 2 \\ -1 \\ 3 \end{pmatrix}$$

**Row 1:** $2(2) + 1(-1) + 0(3) = 4 - 1 + 0 = 3$

**Row 2:** $0(2) + 1(-1) + (-1)(3) = 0 - 1 - 3 = -4$

**Row 3:** $1(2) + 0(-1) + 1(3) = 2 + 0 + 3 = 5$

$$A\vec{a} = \begin{pmatrix} 3 \\ -4 \\ 5 \end{pmatrix}$$

> **Explanation:** Multiplying a matrix by a vector applies a **linear transformation** to that vector. The matrix $A$ can be thought of as a machine: you feed it $\vec{a}$, and it outputs a new vector $A\vec{a}$ that has been rotated, scaled, or sheared. Each component of the output is a weighted sum of the input components, where the weights come from one row of the matrix.

---

### 2.2 – Determinant $\det A$

For a $3\times3$ matrix, the determinant is computed by **cofactor expansion** along the first row:

$$\det A = a_{11} \begin{vmatrix} a_{22} & a_{23} \\ a_{32} & a_{33} \end{vmatrix} - a_{12} \begin{vmatrix} a_{21} & a_{23} \\ a_{31} & a_{33} \end{vmatrix} + a_{13} \begin{vmatrix} a_{21} & a_{22} \\ a_{31} & a_{32} \end{vmatrix}$$

Substituting:
$$\det A = 2 \begin{vmatrix} 1 & -1 \\ 0 & 1 \end{vmatrix} - 1 \begin{vmatrix} 0 & -1 \\ 1 & 1 \end{vmatrix} + 0 \begin{vmatrix} 0 & 1 \\ 1 & 0 \end{vmatrix}$$

**Computing each $2\times2$ determinant:**

$$\begin{vmatrix} 1 & -1 \\ 0 & 1 \end{vmatrix} = (1)(1) - (-1)(0) = 1$$

$$\begin{vmatrix} 0 & -1 \\ 1 & 1 \end{vmatrix} = (0)(1) - (-1)(1) = 0 + 1 = 1$$

$$\begin{vmatrix} 0 & 1 \\ 1 & 0 \end{vmatrix} = (0)(0) - (1)(1) = -1 \quad \text{(multiplied by 0, so irrelevant)}$$

**Assembling:**
$$\det A = 2(1) - 1(1) + 0(-1) = 2 - 1 + 0 = 1$$

$$\boxed{\det A = 1}$$

> **Explanation:** The determinant is a single number that summarizes key properties of the matrix as a linear transformation. Geometrically, $|\det A|$ tells you the *factor by which volumes are scaled* when the transformation is applied. A determinant of 1 means volumes are preserved — no stretching or compression occurs.

---

### 2.3 – Does the transformation preserve orientation?

**Orientation** is preserved if $\det A > 0$, and reversed (mirrored) if $\det A < 0$.

Since $\det A = 1 > 0$:

> **The transformation preserves the orientation of space.** ✓

Since $|\det A| = 1$, it also preserves volume (no scaling).

> **Explanation:** Think of orientation as the "handedness" of a coordinate system. A right-handed coordinate system (where $\vec{x} \times \vec{y} = \vec{z}$) has positive orientation. If $\det A < 0$, the transformation includes a reflection, which would flip a right-handed system into a left-handed one. Since $\det A = 1$ here, both orientation and volume are perfectly preserved — the transformation is a **rotation** (or a combination of rotations).

---

## 5 Possible Questions & Answers

---

**Q1: What is the geometric meaning of the dot product $\vec{a} \cdot \vec{b} = -8$?**

**A:** The dot product $\vec{a} \cdot \vec{b} = |\vec{a}||\vec{b}|\cos\theta$. A negative value means $\cos\theta < 0$, so the angle between the vectors is obtuse (greater than 90°). In this case, $\theta \approx 117.8°$. Geometrically, the two vectors "lean away" from each other — if you project one onto the other, the projection points in the opposite direction.

---

**Q2: What does it mean for a vector to be normalized, and why is normalization useful?**

**A:** A normalized (unit) vector has magnitude exactly 1, preserving only the direction of the original vector. We compute $\hat{a} = \vec{a}/|\vec{a}|$. Normalization is useful whenever direction matters but magnitude does not — for example, when defining the direction of a force, a surface normal in graphics, or a basis direction in a coordinate system. It also simplifies formulas: the dot product of two unit vectors equals exactly $\cos\theta$.

---

**Q3: What is the geometric interpretation of the cross product $\vec{a} \times \vec{b}$?**

**A:** The cross product produces a vector perpendicular to both $\vec{a}$ and $\vec{b}$, with magnitude equal to the area of the parallelogram they span. The direction is given by the right-hand rule: if you curl your right-hand fingers from $\vec{a}$ toward $\vec{b}$, your thumb points in the direction of $\vec{a} \times \vec{b}$. Note that $\vec{b} \times \vec{a} = -(\vec{a} \times \vec{b})$, so the cross product is anti-commutative.

---

**Q4: What happens to a linear transformation when $\det A = 0$?**

**A:** A zero determinant means the transformation is **singular** — it collapses space by at least one dimension (e.g., mapping 3D space onto a plane or line). Such a matrix has no inverse, and vectors mapped by it lose information: multiple input vectors can produce the same output. In our case, $\det A = 1 \neq 0$, so $A$ is invertible and no such collapse occurs.

---

**Q5: If $\det A = -3$, what can you say about the transformation?**

**A:** Two things: first, volumes are scaled by a factor of $|\det A| = 3$, meaning a unit cube is mapped to a parallelepiped of volume 3. Second, since $\det A < 0$, the transformation **reverses orientation** — it includes a reflection, effectively converting a right-handed coordinate system into a left-handed one. A physical example would be a mirror reflection combined with a volume-tripling stretch.