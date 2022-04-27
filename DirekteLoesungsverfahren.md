# LR-Zerlegung
Seien $A \in \mathbb{R}^{N \times N}$ und $\bold{b} \in \mathbb{R}^{N}$.

## Erklären Sie, wann genau und warum eine Zerlegung $A=LR$ für $A$ existiert und mit welchem Aufwand sich diese berechnen lässt.
- Es existiert genau dann eine Zerlegung $PA=LR$ mit $P \in \mathbb{R}^{N \times N}$ wenn $A$ regulär.
  - Grund $A\bold{x} = \bold{b} \rightarrow A^{-1}\bold{b} = \bold{x} \rightarrow$ es existiert eine eindeutige Lösung.
- Aufwand: $\frac{1}{3}N^3$

## Geben Sie an, für welche spezielle Klasse von Matrizen $A$ auf jeden Fall eine Zerlegung $A=LR$ existiert.
- Für Matrizen $A$, wo für alle $n = 1,...,N$ gilt $A_{[1:n,1:n]}$ ist regulär.

## Erklären Sie, wann genau und warum eine Zerlegung $PA=LR$ für $A$ existiert.
- $A$ muss regulär sein. (Ich verstehe nicht warum das 3mal gefragt wird, was ist der unterschied zwischen 1. und 3. Frage?)

## Beschreiben Sie, wie sich das lineare Gleichungssystem $A\bold{x}=\bold{b}$ bei Kenntnis einer Zerlegung $PA=LR$ lösen lässt, und geben Sie den Aufwand der einzelnen Schritte an.
- $L\bold{y} = P\bold{b}$ Vorwärtssubstitution in $\frac{1}{2}N^2$
- $R\bold{x} = \bold{y}$ Rückwärtssubstitution in $\frac{1}{2}N^2$

## Erklären Sie, warum die Kenntnis der Inversen $A^{−1}$ gegenüber einer bekannten Zerlegung $PA=LR$ beim Lösen von $Ax=b$ keinen Vorteil darstellt.
- Matrixmultiplikation $A^{-1}b = x$ kostet $N^2$, Vortwärts + Rückwärtssubstitution ebenfalls, also kein Gewinn.
