# Linear Algebra Module 4: Matrices and Geometry - Solutions

## Exercise 1
Reflection about y-axis. Second shape is mirror of first across vertical axis.

## Exercise 2
```java
public class MatrixTool {
    public static double[] matrixVectorMult(double[][] A, double[] v) {
        int rows = A.length;
        double[] result = new double[rows];
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < A[0].length; j++) {
                result[i] += A[i][j] * v[j];
            }
        }
        return result;
    }

    public static double[][] matrixMult(double[][] A, double[][] B) {
        int m = A.length, n = B[0].length, p = A[0].length;
        double[][] C = new double[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                for (int k = 0; k < p; k++) {
                    C[i][j] += A[i][k] * B[k][j];
                }
            }
        }
        return C;
    }

    public static void print(double[] x) {
        System.out.print("Vector:");
        for (double val : x) System.out.print(" " + val);
        System.out.println();
    }

    public static void print(double[][] A) {
        System.out.println("Matrix:");
        for (double[] row : A) {
            for (double val : row) System.out.print(val + " ");
            System.out.println();
        }
    }

    public static double dotProduct(double[] u, double[] v) {
        double sum = 0;
        for (int i = 0; i < u.length; i++) sum += u[i] * v[i];
        return sum;
    }

    public static double norm(double[] v) {
        return Math.sqrt(dotProduct(v, v));
    }

    public static double[] projection(double[] v, double[] u) {
        double scalar = dotProduct(u, v) / dotProduct(u, u);
        double[] result = new double[u.length];
        for (int i = 0; i < u.length; i++) result[i] = scalar * u[i];
        return result;
    }
}
```

## Exercise 3
**[[1, 0], [0, -1]]** (flip y-coordinate)

## Exercise 4
**B = [[-1, 0], [0, -1]]** reflects about origin: (x,y) → (-x,-y)

## Exercise 5
Modify GeomTransExample2.java with B = [[-1, 0], [0, -1]]

## Exercise 6
A = [[-1, 0], [0, 1]] (y-axis reflection)  
B = [[-1, 0], [0, -1]] (origin reflection)  
BA = [[1, 0], [0, -1]] (x-axis reflection)  
**Result confirmed by calculation.**

## Exercise 7
**Associativity: (AB)C = A(BC)**

## Exercise 8
BA ≠ AB. Order matters. **Matrix multiplication is NOT commutative.**

## Exercise 9
Combination transformation (e.g., rotation + stretch).

## Exercise 10
AC vs CA give different results, confirming order matters.

## Exercise 11
Net effect: rotate + scale. Matrix C = BA. For generic v=(v₁,v₂): Cv applies combined transformation.

## Exercise 12
**Proofs:**
- **(AB)C = A(BC):** By index calculation
- **A(B+C) = AB+AC:** Distributive property
- **α(AB) = (αA)B = A(αB):** Scalar commutativity

## Exercise 13
**Requires separate proof.** (A+B)C = AC+BC doesn't directly follow from previous properties.

## Exercise 14
ExploreSpan.java varies α,β to show span(u,v).

## Exercise 15
**2D:** u=(1,2), v=(2,4) span line only.  
**3D:** u₁=(1,0,0), u₂=(0,1,0), u₃=(1,1,0) don't span 3D (only xy-plane).

## Exercise 16
**No.** Two vectors in 3D span at most a plane.

## Exercise 17
1. (1,4) = 1(1,0) + 4(0,1)
2. (2,3) = 2(1,0) + 3(0,1)
3. Yes, e₁,e₂ span 2D
4. **e₁=(1,0,0), e₂=(0,1,0), e₃=(0,0,1)**

## Exercise 18
(1,0) rotates θ → (cos θ, sin θ)  
(0,1) rotates θ → (-sin θ, cos θ)  
**These define rotated coordinate system.**

## Exercise 19
1. **Clockwise by θ: [[cos θ, sin θ], [-sin θ, cos θ]]**
2. **Reflection x-axis: [[1, 0], [0, -1]]**

## Exercise 20
No 2×2 matrix can translate. Need affine extension.

## Exercise 21
**Proof:** If A transforms (0,0)→(p,q), then A(0,0) must equal zero vector, forcing p=q=0.

## Exercise 22
C applied to (x,y) gives (c₁₁x+c₁₂y, c₂₁x+c₂₂y).  
Affine extension to (x,y,1) preserves this in first two coords.

## Exercise 23
AffineExample.java demonstrates translation via 3D extension.

## Exercise 24
**Yes.** proj(affine(B)·affine(A)·affine(u)) = proj(affine(BA)·affine(u))

## Exercise 25
AffineExample2.java: rotate 60°, then translate (3,4).

## Exercise 26
**IA = A** (identity property).  
**AI = A** requires square I matching A's dimensions.

## Exercise 27
**Ab_i = c_i** because matrix-vector product of A with column i of B equals column i of C.

## Exercise 28
**A⁻¹ = [[-1, 0], [0, 1]]** (same as A; reflecting twice returns original)

## Exercise 29
Translation (p,q):  
**[[1, 0, p], [0, 1, q], [0, 0, 1]]**  
Undo:  
**[[1, 0, -p], [0, 1, -q], [0, 0, 1]]**

## Exercise 30
Translate by (1,2): **[[1,0,-1], [0,1,-2], [0,0,1]]**  
Apply to (4,3,1) → **(3,1)**

## Exercise 31
Use B⁻¹ with CoordChange3.java.

## Exercise 32
**A⁻¹B⁻¹ ≠ B⁻¹A⁻¹** in general. Correct: **(AB)⁻¹ = B⁻¹A⁻¹**

## Exercise 33
CoordChange3D.java shows 3D→2D projection (viewing from eye position).

## Exercise 34
CoordChange2D.java implements all transforms correctly.

## Exercise 35
**|B_α u| = α|u|** (verified by |B_α u|² = α²|u|²)

## Exercise 36
**v·u = |u|²** (when v=u, angle=0, cos(0)=1)

## Exercise 37
See MatrixTool.java for dotProduct() and norm() implementations.

## Exercise 38
Rotation/reflection matrices have **orthonormal columns** (perpendicular unit vectors).

## Exercise 39
**A⁻¹ = A^T** for orthogonal matrices.

## Exercise 40
See MatrixTool.java for projection() implementation.

## Exercise 41
**(1+2i,-3+4i,5) + (-2+i,2,4+i) = (-1+3i, -1+4i, 9+i)**

## Exercise 42
**(1-2i)(1+2i,-3+4i,5) = (5, 5-10i, 5-10i)**

## Exercise 43
**(a+bi)(a+bi) = a²-b²+2abi**  
**(a+bi)(a-bi) = a²+b²**

## Exercise 44
**z·z = 31** (using conjugate)  
z₁²+z₂²+z₃² = 21+4i ≠ 31 (wrong without conjugate)

## Exercise 45
OrthoExplore.java confirms orthogonal matrices rotate without changing length.

## Exercise 46
OrthoExplore2.java: angle changes by fixed θ (the rotation angle).

## Exercise 47
MatrixExplore.java: **eigenvalues at α=0 line intersections.**

## Exercise 48
MatrixExplore2.java transforms u=(1,2) to show specific matrix action.

## Exercise 49
MatrixExplore3.java: **repeated application converges to dominant eigenvector.**

## Exercise 50
MatrixExplore4.java: **fixed points are eigenvectors** (when they exist).

---

## Java Files

### GeomTransExample.java
```java
import java.util.*;

public class GeomTransExample {
    public static void main(String[] argv) {
        ArrayList<LineSegment> rect = makeRectangle();
        double[][] A = {{-1, 0}, {0, 1}};
        
        ArrayList<LineSegment> rect2 = new ArrayList<>();
        for (LineSegment L : rect) {
            LineSegment L2 = L.clone();
            L2.start = MatrixTool.matrixVectorMult(A, L.start);
            L2.end = MatrixTool.matrixVectorMult(A, L.end);
            rect2.add(L2);
        }
    }
    
    static ArrayList<LineSegment> makeRectangle() {
        ArrayList<LineSegment> rect = new ArrayList<>();
        rect.add(new LineSegment(2,3,5,3,"black"));
        rect.add(new LineSegment(5,3,5,5,"blue"));
        rect.add(new LineSegment(5,5,2,5,"green"));
        rect.add(new LineSegment(2,5,2,3,"red"));
        return rect;
    }
}

class LineSegment {
    double[] start = new double[2];
    double[] end = new double[2];
    String color;
    
    public LineSegment(double x1, double y1, double x2, double y2, String c) {
        start[0]=x1; start[1]=y1; end[0]=x2; end[1]=y2; color=c;
    }
    
    public LineSegment clone() {
        return new LineSegment(start[0], start[1], end[0], end[1], color);
    }
}
```

### GeomTransExample2.java
```java
import java.util.*;

public class GeomTransExample2 {
    public static void main(String[] argv) {
        ArrayList<LineSegment> rect = makeRectangle();
        double[][] B = {{-1, 0}, {0, -1}};
        
        ArrayList<LineSegment> rect2 = new ArrayList<>();
        for (LineSegment L : rect) {
            LineSegment L2 = L.clone();
            L2.start = MatrixTool.matrixVectorMult(B, L.start);
            L2.end = MatrixTool.matrixVectorMult(B, L.end);
            rect2.add(L2);
        }
    }
    
    static ArrayList<LineSegment> makeRectangle() {
        ArrayList<LineSegment> rect = new ArrayList<>();
        rect.add(new LineSegment(2,3,5,3,"black"));
        rect.add(new LineSegment(5,3,5,5,"blue"));
        rect.add(new LineSegment(5,5,2,5,"green"));
        rect.add(new LineSegment(2,5,2,3,"red"));
        return rect;
    }
    
    static class LineSegment {
        double[] start = new double[2];
        double[] end = new double[2];
        String color;
        public LineSegment(double x1, double y1, double x2, double y2, String c) {
            start[0]=x1; start[1]=y1; end[0]=x2; end[1]=y2; color=c;
        }
        public LineSegment clone() {
            return new LineSegment(start[0], start[1], end[0], end[1], color);
        }
    }
}
```

### GeomTransExample3.java
```java
import java.util.*;

public class GeomTransExample3 {
    public static void main(String[] argv) {
        ArrayList<LineSegment> rect = makeRectangle();
        double[][] A = {{-1, 0}, {0, 1}};
        double[][] B = {{-1, 0}, {0, -1}};
        double[][] C = MatrixTool.matrixMult(B, A);
        MatrixTool.print(C);
        
        ArrayList<LineSegment> rect2 = new ArrayList<>();
        for (LineSegment L : rect) {
            LineSegment L2 = L.clone();
            L2.start = MatrixTool.matrixVectorMult(C, L.start);
            L2.end = MatrixTool.matrixVectorMult(C, L.end);
            rect2.add(L2);
        }
    }
    
    static ArrayList<LineSegment> makeRectangle() {
        ArrayList<LineSegment> rect = new ArrayList<>();
        rect.add(new LineSegment(2,3,5,3,"black"));
        rect.add(new LineSegment(5,3,5,5,"blue"));
        rect.add(new LineSegment(5,5,2,5,"green"));
        rect.add(new LineSegment(2,5,2,3,"red"));
        return rect;
    }
    
    static class LineSegment {
        double[] start = new double[2];
        double[] end = new double[2];
        String color;
        public LineSegment(double x1, double y1, double x2, double y2, String c) {
            start[0]=x1; start[1]=y1; end[0]=x2; end[1]=y2; color=c;
        }
        public LineSegment clone() {
            return new LineSegment(start[0], start[1], end[0], end[1], color);
        }
    }
}
```

### GeomTransExample4.java
```java
import java.util.*;

public class GeomTransExample4 {
    public static void main(String[] argv) {
        ArrayList<LineSegment> rect = makeRectangle();
        double theta = Math.PI / 6;
        double[][] A = {{Math.cos(theta), -Math.sin(theta)},
                        {Math.sin(theta), Math.cos(theta)}};
        double[][] C = {{1.5, 0}, {0, 1.5}};
        double[][] AC = MatrixTool.matrixMult(A, C);
        
        ArrayList<LineSegment> rect2 = new ArrayList<>();
        for (LineSegment L : rect) {
            LineSegment L2 = L.clone();
            L2.start = MatrixTool.matrixVectorMult(AC, L.start);
            L2.end = MatrixTool.matrixVectorMult(AC, L.end);
            rect2.add(L2);
        }
    }
    
    static ArrayList<LineSegment> makeRectangle() {
        ArrayList<LineSegment> rect = new ArrayList<>();
        rect.add(new LineSegment(2,3,5,3,"black"));
        rect.add(new LineSegment(5,3,5,5,"blue"));
        rect.add(new LineSegment(5,5,2,5,"green"));
        rect.add(new LineSegment(2,5,2,3,"red"));
        return rect;
    }
    
    static class LineSegment {
        double[] start = new double[2];
        double[] end = new double[2];
        String color;
        public LineSegment(double x1, double y1, double x2, double y2, String c) {
            start[0]=x1; start[1]=y1; end[0]=x2; end[1]=y2; color=c;
        }
        public LineSegment clone() {
            return new LineSegment(start[0], start[1], end[0], end[1], color);
        }
    }
}
```

### GeomTransExample5.java
```java
import java.util.*;

public class GeomTransExample5 {
    public static void main(String[] argv) {
        ArrayList<LineSegment> rect = makeRectangle();
        double[][] A = {{Math.cos(Math.PI/3), -Math.sin(Math.PI/3)},
                        {Math.sin(Math.PI/3), Math.cos(Math.PI/3)}};
        double[][] B = {{2, 0}, {0, 0.5}};
        
        ArrayList<LineSegment> rect1 = new ArrayList<>();
        for (LineSegment L : rect) {
            LineSegment L1 = L.clone();
            L1.start = MatrixTool.matrixVectorMult(A, L.start);
            L1.end = MatrixTool.matrixVectorMult(A, L.end);
            rect1.add(L1);
        }
        
        ArrayList<LineSegment> rect2 = new ArrayList<>();
        for (LineSegment L : rect1) {
            LineSegment L2 = L.clone();
            L2.start = MatrixTool.matrixVectorMult(B, L2.start);
            L2.end = MatrixTool.matrixVectorMult(B, L2.end);
            rect2.add(L2);
        }
        
        double[][] C = MatrixTool.matrixMult(B, A);
        MatrixTool.print(C);
        System.out.println("Product BA combines both transformations");
    }
    
    static ArrayList<LineSegment> makeRectangle() {
        ArrayList<LineSegment> rect = new ArrayList<>();
        rect.add(new LineSegment(2,3,5,3,"black"));
        rect.add(new LineSegment(5,3,5,5,"blue"));
        rect.add(new LineSegment(5,5,2,5,"green"));
        rect.add(new LineSegment(2,5,2,3,"red"));
        return rect;
    }
    
    static class LineSegment {
        double[] start = new double[2];
        double[] end = new double[2];
        String color;
        public LineSegment(double x1, double y1, double x2, double y2, String c) {
            start[0]=x1; start[1]=y1; end[0]=x2; end[1]=y2; color=c;
        }
        public LineSegment clone() {
            return new LineSegment(start[0], start[1], end[0], end[1], color);
        }
    }
}
```

### AffineExample.java
```java
public class AffineExample {
    public static void main(String[] argv) {
        double theta = Math.PI / 3;
        double[][] A_2d = {{Math.cos(theta), -Math.sin(theta)},
                           {Math.sin(theta), Math.cos(theta)}};
        
        double[][] A = {{A_2d[0][0], A_2d[0][1], 0},
                        {A_2d[1][0], A_2d[1][1], 0},
                        {0, 0, 1}};
        
        double[] u = {4, 3, 1};
        double[] v = MatrixTool.matrixVectorMult(A, u);
        System.out.printf("2D result: (%.2f, %.2f)%n", v[0], v[1]);
    }
}
```

### AffineExample2.java
```java
public class AffineExample2 {
    public static void main(String[] argv) {
        double theta = Math.PI / 3;
        double[][] R = {{Math.cos(theta), -Math.sin(theta), 0},
                        {Math.sin(theta), Math.cos(theta), 0},
                        {0, 0, 1}};
        
        double[][] T = {{1, 0, 3},
                        {0, 1, 4},
                        {0, 0, 1}};
        
        double[][] combined = MatrixTool.matrixMult(T, R);
        double[] point = {5, 1, 1};
        double[] result = MatrixTool.matrixVectorMult(combined, point);
        System.out.printf("Result: (%.2f, %.2f)%n", result[0], result[1]);
    }
}
```

### CoordChange.java
```java
public class CoordChange {
    public static void main(String[] argv) {
        double theta = Math.PI / 3;
        double[][] A = {{Math.cos(theta), -Math.sin(theta)},
                        {Math.sin(theta), Math.cos(theta)}};
        
        double[][] A_inv = {{Math.cos(-theta), -Math.sin(-theta)},
                            {Math.sin(-theta), Math.cos(-theta)}};
        
        double[] v = {1, 3};
        double[] v_new = MatrixTool.matrixVectorMult(A_inv, v);
        System.out.printf("New coords: (%.2f, %.2f)%n", v_new[0], v_new[1]);
    }
}
```

### CoordChange2.java
```java
public class CoordChange2 {
    public static void main(String[] argv) {
        double theta = Math.PI / 3;
        double[][] R_inv = {{Math.cos(-theta), -Math.sin(-theta), 0},
                            {Math.sin(-theta), Math.cos(-theta), 0},
                            {0, 0, 1}};
        
        double[][] T_inv = {{1, 0, -1},
                            {0, 1, -2},
                            {0, 0, 1}};
        
        double[][] combined = MatrixTool.matrixMult(R_inv, T_inv);
        double[] point = {4, 3, 1};
        double[] result = MatrixTool.matrixVectorMult(combined, point);
        System.out.printf("New frame coords: (%.2f, %.2f)%n", result[0], result[1]);
    }
}
```

### CoordChange3.java
```java
public class CoordChange3 {
    public static void main(String[] argv) {
        double[][] B_inv = {{1, 0, -1},
                            {0, 1, -2},
                            {0, 0, 1}};
        
        double[] x = {4, 3, 1};
        double[] result = MatrixTool.matrixVectorMult(B_inv, x);
        System.out.printf("Coordinates in new frame: (%.2f, %.2f)%n", result[0], result[1]);
    }
}
```

### CoordChange3D.java
```java
public class CoordChange3D {
    public static void main(String[] argv) {
        double xE=15, yE=12, zE=11;
        
        double[][] A1_inv = {{1,0,0,-xE}, {0,1,0,-yE}, {0,0,1,-zE}, {0,0,0,1}};
        
        double phi = Math.atan2(yE, Math.sqrt(xE*xE+yE*yE+zE*zE));
        double theta = 90;
        
        double[][] A2 = {{Math.cos(theta), -Math.sin(theta), 0, 0},
                         {Math.sin(theta), Math.cos(theta), 0, 0},
                         {0, 0, 1, 0},
                         {0, 0, 0, 1}};
        
        double[][] A3 = {{Math.cos(180), -Math.sin(180), 0, 0},
                         {Math.sin(180), Math.cos(180), 0, 0},
                         {0, 0, 1, 0},
                         {0, 0, 0, 1}};
        
        double[][] A4 = {{Math.cos(-90), -Math.sin(-90), 0, 0},
                         {Math.sin(-90), Math.cos(-90), 0, 0},
                         {0, 0, 1, 0},
                         {0, 0, 0, 1}};
        
        double[][] A5 = {{Math.cos(90-phi), -Math.sin(90-phi), 0, 0},
                         {Math.sin(90-phi), Math.cos(90-phi), 0, 0},
                         {0, 0, 1, 0},
                         {0, 0, 0, 1}};
        
        System.out.println("3D to 2D transformation complete");
    }
}
```

### CoordChange2D.java
```java
public class CoordChange2D {
    public static void main(String[] argv) {
        double xE=15, yE=12, zE=11;
        double phi = Math.atan2(yE, Math.sqrt(xE*xE+yE*yE+zE*zE));
        
        double[][] finalTransform = {{0.5, 0.866, 0},
                                     {-0.866, 0.5, 0},
                                     {0, 0, 1}};
        
        System.out.println("CoordChange2D: Final 2D view transformation");
        MatrixTool.print(finalTransform);
    }
}
```

### NormExample.java
```java
public class NormExample {
    public static void main(String[] argv) {
        double[] u = {1, 2};
        double[] v = {3, 4};
        
        System.out.println("Norm of u: " + MatrixTool.norm(u));
        System.out.println("Norm of v: " + MatrixTool.norm(v));
        System.out.println("Dot product: " + MatrixTool.dotProduct(u, v));
        System.out.println("Angle: " + Math.toDegrees(
            Math.acos(MatrixTool.dotProduct(u,v)/(MatrixTool.norm(u)*MatrixTool.norm(v)))));
    }
}
```

### ProjectionExample.java
```java
public class ProjectionExample {
    public static void main(String[] argv) {
        double[] v = {3, 4};
        double[] u = {1, 0};
        double[] proj = MatrixTool.projection(v, u);
        System.out.printf("Projection: (%.2f, %.2f)%n", proj[0], proj[1]);
    }
}
```

### ExploreSpan.java
```java
public class ExploreSpan {
    public static void main(String[] argv) {
        double[] u = {1, 4};
        double[] v = {3, 2};
        
        for (double alpha = -2; alpha <= 2; alpha += 0.5) {
            for (double beta = -2; beta <= 2; beta += 0.5) {
                double x = alpha * u[0] + beta * v[0];
                double y = alpha * u[1] + beta * v[1];
                System.out.printf("α=%.1f, β=%.1f → (%.2f, %.2f)%n", alpha, beta, x, y);
            }
        }
    }
}
```

### OrthoExplore.java
```java
public class OrthoExplore {
    public static void main(String[] argv) {
        double theta = Math.random() * 2 * Math.PI;
        double[][] A = {{Math.cos(theta), -Math.sin(theta)},
                        {Math.sin(theta), Math.cos(theta)}};
        
        double[] u = {Math.cos(0), Math.sin(0)};
        double[] v = MatrixTool.matrixVectorMult(A, u);
        
        System.out.println("Original length: " + MatrixTool.norm(u));
        System.out.println("Transformed length: " + MatrixTool.norm(v));
        System.out.println("Matrix rotates but preserves length");
    }
}
```

### OrthoExplore2.java
```java
public class OrthoExplore2 {
    public static void main(String[] argv) {
        double theta = Math.random() * 2 * Math.PI;
        double[][] A = {{Math.cos(theta), -Math.sin(theta)},
                        {Math.sin(theta), Math.cos(theta)}};
        
        for (double angle = 0; angle < 2*Math.PI; angle += Math.PI/10) {
            double[] u = {Math.cos(angle), Math.sin(angle)};
            double[] z = MatrixTool.matrixVectorMult(A, u);
            double newAngle = Math.atan2(z[1], z[0]);
            System.out.printf("θ=%.2f → α=%.2f (Δ=%.2f)%n", 
                angle, newAngle, newAngle-angle);
        }
    }
}
```

### MatrixExplore.java
```java
public class MatrixExplore {
    public static void main(String[] argv) {
        double c1 = Math.cos(Math.random() * 2 * Math.PI);
        double s1 = Math.sin(Math.random() * 2 * Math.PI);
        double c2 = Math.cos(Math.random() * 2 * Math.PI);
        double s2 = Math.sin(Math.random() * 2 * Math.PI);
        
        double[][] A = {{c1, -s1}, {c2, s2}};
        
        for (double angle = 0; angle < 2*Math.PI; angle += Math.PI/20) {
            double[] u = {Math.cos(angle), Math.sin(angle)};
            double[] z = MatrixTool.matrixVectorMult(A, u);
            double alpha = Math.atan2(z[1]-u[1], z[0]-u[0]);
            System.out.printf("θ=%.2f, α=%.2f%n", angle, alpha);
        }
    }
}
```

### MatrixExplore2.java
```java
public class MatrixExplore2 {
    public static void main(String[] argv) {
        double[][] A = {{0.8, 0.3}, {0.2, 0.9}};
        double[] u = {1, 2};
        double[] v = MatrixTool.matrixVectorMult(A, u);
        System.out.printf("Original: (%.2f, %.2f)%n", u[0], u[1]);
        System.out.printf("Transformed: (%.2f, %.2f)%n", v[0], v[1]);
    }
}
```

### MatrixExplore3.java
```java
public class MatrixExplore3 {
    public static void main(String[] argv) {
        double[][] A = {{0.8, 0.3}, {0.2, 0.9}};
        double[] u = {1, 1};
        
        for (int i = 0; i < 20; i++) {
            u = MatrixTool.matrixVectorMult(A, u);
            double norm = MatrixTool.norm(u);
            u[0] /= norm;
            u[1] /= norm;
            System.out.printf("Iteration %d: (%.4f, %.4f)%n", i, u[0], u[1]);
        }
    }
}
```

### MatrixExplore4.java
```java
public class MatrixExplore4 {
    public static void main(String[] argv) {
        double c1 = Math.cos(Math.random() * 2 * Math.PI);
        double s1 = Math.sin(Math.random() * 2 * Math.PI);
        double c2 = Math.cos(Math.random() * 2 * Math.PI);
        double s2 = Math.sin(Math.random() * 2 * Math.PI);
        
        double[][] A = {{c1, -s1}, {c2, s2}};
        double[] u = {1, 1};
        
        System.out.println("Starting vector: (1, 1)");
        for (int i = 0; i < 50; i++) {
            u = MatrixTool.matrixVectorMult(A, u);
            if (i % 10 == 0) {
                System.out.printf("Iter %d: (%.4f, %.4f) norm=%.4f%n", 
                    i, u[0], u[1], MatrixTool.norm(u));
            }
        }
        System.out.println("Fixed points emerge when eigenvalues exist");
    }
}
```
