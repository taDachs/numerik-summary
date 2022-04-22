# Gleitpunktrechnung
## Erklären Sie den genauen Aufbau einer normalisierten Gleitpunktzahl
- in der Form $x = m \cdot B^e$ mit
  - $e = e_{min} + \sum_{l=0}^{L_e - 1} c_l B^l$ mit $c_l \in \{0,...,B - 1\}$
  - $m = \pm \sum_{l=1}^{L_m} a_l B^{-l}$ mit $a_l \in \{0,...,B-1\}$
  - normalisisert $\rightarrow a_1 \neq 0$
  - $B$: Basis
  - $L_m$: Länge der Mantisse
  - $L_e$: Länge des Exponenten

## Geben Sie die Definition der Maschinengenauigkeit an und erklären Sie, in welcher Weise die Mantissenlänge $L_m$ die relative Genauigkeit der Darstellung reeller Zahlen durch eine normalisierte Gleitpunktzahl bestimmt
- Definition: $\textrm{fl}(x) = x(1 + \epsilon)$ mit $|\epsilon| \leq \textrm{eps}$
  - $\frac{|x - \textrm{fl}(x)|}{|x|} \leq \textrm{eps}$
    - der relative Fehler für eine gegebene Zahl und ihre Repräsentation als Gleitkommazahl ist kleiner als eps
  - $\textrm{eps} := \frac{B^{1-L_m}}{2}$
    - die Länge der Mantisse bestimmt die Genaugkeit (TODO: etwas sinnvolles schreiben, da gabs doch irgendwas mit runden)
- die Maschinengenauigkeit ist die kleinste Zahl, die auf 1 addiert eine Zahl größer 1 ergibt

## Beschreiben Sie den IEEE-Standard des Double Precision-Formats und erklären Sie, warum $1+\textrm{eps}$ die kleinste Zahl echt größer 1 in FL ist.
- IEEE-754-Floating Point Standard:
  - $B = 2$
  - $e_{min} = -1022$
  - 1 Bit Vorzeichen
  - 52 Bit Mantisse
  - 11 Bit Exponent
- da beim IEEE-754-Floating Point Standard die erste 1 weggelassen wird ist ein Bit mehr Platz für die Mantisse
- TODO: Mehr eigenschaften von Gleitkommazahlen (minFL etc.)

## Nennen Sie mögliche Fehlerquellen der Eingabedaten eines numerischen Verfahrens und innerhalb des Verfahrens selbst beim Lösen eines mathematischen Problems und formulieren Sie die Fragestellungen, welche der Stabilität eines Verfahrens und der Kondition des Problems zugrunde liegen.
- schlechte Messungen
- Ungenauigkeiten durch Repräsentation im Speicher
- Rundungsfehler
- Stabilität
  - Auswirkung von Fehlern im numerischen Verfahren auf die Lösung des mathematischen Problems
  - bezieht sich auf das Verfahren
- Kondition
  - Wie wirken sich Störungen der Eingabedaten auf das Resultat unabhängig vom gewählten Algorithmus ab
  - bezieht sich auf die Problemstellung

## Vollziehen Sie die Untersuchung und Deutung der Kondition der Summe zweier Zahlen der Vorlesung nach, indem Sie auch das Phänomen der Auslöschung erklären.
- $\sqrt{2 - \sqrt{4 - g_{n}^{2}}}$ ist schlecht konditioniert, da $g_n$ sehr klein werden kann, und da $2 = \sqrt{4}$. Danach bleibt nurnoch der Rundungsfehler $\textrm{eps}$ übrig und bestimmt das Ergebnis

