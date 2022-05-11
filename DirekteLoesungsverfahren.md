# Direkte Lösungsverfahren

## LR-Zerlegung
Seien $A \in \mathbb{R}^{N \times N}$ und $\bold{b} \in \mathbb{R}^{N}$.

### Erklären Sie, wann genau und warum eine Zerlegung $A=LR$ für $A$ existiert und mit welchem Aufwand sich diese berechnen lässt.
- Es existiert genau dann eine Zerlegung $PA=LR$ mit $P \in \mathbb{R}^{N \times N}$ wenn $A$ regulär.
  - Grund $A\bold{x} = \bold{b} \rightarrow A^{-1}\bold{b} = \bold{x} \rightarrow$ es existiert eine eindeutige Lösung.
- Aufwand: $\frac{1}{3}N^3$

### Geben Sie an, für welche spezielle Klasse von Matrizen $A$ auf jeden Fall eine Zerlegung $A=LR$ existiert.
- Für Matrizen $A$, wo für alle $n = 1,...,N$ gilt $A_{[1:n,1:n]}$ ist regulär.

### Erklären Sie, wann genau und warum eine Zerlegung $PA=LR$ für $A$ existiert.
- $A$ muss regulär sein. (Ich verstehe nicht warum das 3mal gefragt wird, was ist der unterschied zwischen 1. und 3. Frage?)

### Beschreiben Sie, wie sich das lineare Gleichungssystem $A\bold{x}=\bold{b}$ bei Kenntnis einer Zerlegung $PA=LR$ lösen lässt, und geben Sie den Aufwand der einzelnen Schritte an.
- $L\bold{y} = P\bold{b}$ Vorwärtssubstitution in $\frac{1}{2}N^2$
- $R\bold{x} = \bold{y}$ Rückwärtssubstitution in $\frac{1}{2}N^2$

### Erklären Sie, warum die Kenntnis der Inversen $A^{−1}$ gegenüber einer bekannten Zerlegung $PA=LR$ beim Lösen von $Ax=b$ keinen Vorteil darstellt.
- Matrixmultiplikation $A^{-1}b = x$ kostet $N^2$, Vortwärts + Rückwärtssubstitution ebenfalls, also kein Gewinn.

## Cholesky- und QR-Zerlegung
### Erklären Sie, für welche Matrizen genau eine Cholesky-Zerlegung existiert und wie bei Kenntnis einer solchen Zerlegung das Gleichungssystem $Ax=b$ gelöst werden kann.
- spd-Matrix $A \in \mathbb{R}^{N \times N}$
- Zerlegung $A = LL^T$
- $A\bold{x} = LL^T = L\bold{y} = \bold{b}$
  - Löse $L\bold{y} = \bold{b}$
  - Löse $L^T \bold{x} = \bold{y}$
### Geben Sie an, wie eine $QR$-Zerlegung einer Matrix $A\in R^{M×N}$ definiert ist, indem Sie die Faktoren beschreiben, und erklären Sie, wie sich ein lösbares LGS $Ax=b$ durch eine solche Zerlegung lösen lässt.
- $A \in \mathbb{R}^{M \times N},\ M \geq N, A\ \textrm{hat maximalen Rang}$
- $A = QR$ mit $Q \in \mathbb{R}^{M \times M}, R = \begin{bmatrix} \bar{R} \\ 0 \end{bmatrix} \in \mathbb{R}^{M \times N}, \bar{R} \in \mathbb{R}^{N \times N}$
- $Q\bold{c} = \bold{b} \rightarrow \bold{c} = Q^T\bold{b}, R\bold{x} = \bold{c}$ durch Rückwärtssubstitution.

### Nennen Sie einen Vorteil und einen Nachteil der $QR$-Zerlegung gegenüber der $LR$- und Cholesky-Zerlegung.
- $QR$ ist sehr stabil, aber für $M \approx N$ doppelt so teuer wie $LR$-Zerlegung

### Wiederholen Sie Eigenschaften und die Struktur von Householder-Transformationen.
- $Q = I_m - 2\bold{ww}^T$
- Durch Householder-Vektor $w$ eindeutig bestimmt
- Symmetrie: $Q^T = Q$
- Orthogonalität: $Q^{-1} = Q^T$
- Spiegelung:
  - $Q(\lambda\bold{w}) = \lambda Q \bold{w} = \lambda \bold{w},\ \forall \lambda \in \mathbb{R}$
  - $Q\bold{y} = \bold{y},\ \forall \bold{y} \in \mathbb{R}^N,\ \bold{w}^T\bold{y} = 0$

### Erklären Sie, wie eine Householder-Transformation $Q$ effizient gespeichert werden kann und wie ein Produkt $Q\bold{y}$ berechnet wird.
- Man muss nur die Householder-Vektoren $\bold{w}$ speichern
- TODO: is this correct? Missing $Q\bold{y}$
<!-- TODO: is this correct? -->

## Kondition linearer Gleichungssysteme

### Geben Sie zu einer Norm $\|\cdot\|$ auf $\mathbb{R}^N$ die zugehörige Matrixnorm an und nennen Sie drei wichtige Beispiele solcher Normen.
- $\|A\| \coloneqq \sup_{x \neq 0}\frac{\|A\bold{x}\|}{\|\bold{x}\|}, \forall A \in \mathbb{R}^{N \times N}$
- Beispiele:
  - Spaltensummennorm: $\|A\|_1 = \max_{m=1,...,N}\sum_{n=1}^{N}{|a_{nm}|}$
  - Spektralnorm: $\|A\|_2 = \sqrt{\textrm{größter EW von } A^T A}$
  - Zeilennorm: $\|A\|_{\infty} = \max_{n=1,...,N}\sum_{m=1}^N{|a_{nm}|}$

### Formulieren Sie die Frage, der sich die Kondition eines Problems widmet.
- Wie viel Einfluss haben Störungen auf den Eingabedaten auf die Ausgabe

### Erklären Sie, was genau eine kleine Kondition bzw. eine große Kondition $\textrm{cond}(A)$ über das Problem $A\bold{x}=\bold{b}$ aussagt.
- Kondition ist eine obere Schranke für den relativen Fehler abhängig von den Eingabedaten
- Hohe Kondition $\rightarrow$ Fehler in den Eingabedaten **können** (nicht zwingend) stark Auswirkungen auf das Ergebnis haben

### Nennen Sie mindestens drei Eigenschaften der Funktion $\textrm{cond}(\cdot)$.
- $\textrm{cond}(A)=\|A\|\|A^{-1}\|$
- $1 = \|I_N\|=\|AA^{-1}\|\leq\|A\|\|A^{-1}\|=\textrm{A}$
- $1 = \textrm{cond}{\alpha}, \forall \alpha \in \textrm{R} \setminus \{0\}$
- $\textrm{cond}(\alpha A) = \textrm{cond}(A), \forall \alpha \in \mathbb{R} \setminus \{0\}$
- $\textrm{cond}(A) = \frac{\max_{\|\bold{y}\|=1}\|A\bold{y}\|}{\max_{\|\bold{z}\|=1}\|A\bold{z}\|}$
- $\textrm{cond}_2(A)=\frac{\max\{|\lambda|: \lambda \textrm{EW von A}\}}{\min\{|\lambda|: \lambda \textrm{EW von A}\}}$

### Erklären Sie, warum die Kondition orthogonaler Matrizen bezüglich $\|\cdot\|_2$ gleich $1$ ist und wie sich die Kondition von symmetrischen und spd-Matrizen bezüglich dieser Norm berechnen lässt.
- Größter Eigenwert von orthogonalen Matrizen ist immer 1
- TODO spd + symmetrische
<!-- TODO spd + symmetrische -->

