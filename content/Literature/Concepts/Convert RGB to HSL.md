---
tags:
  - programming
  - rgb2hsl
  - conversion
  - cplusplus
  - algorithm
  - code
  - mathematics
  - colortheory
DateCreated: 5/3/2024 11:00 am
---

### Hue Calculation
To calculate the hue, \( h \):
$$
h = \begin{cases}
    \frac{g - b}{\Delta} + (g < b ? 6 : 0), & \text{if } \max = r \\
    \frac{b - r}{\Delta} + 2, & \text{if } \max = g \\
    \frac{r - g}{\Delta} + 4, & \text{if } \max = b
\end{cases}
$$

$$
\Delta = \max - \min
$$
and \(\max\) and \(\min\) are the maximum and minimum RGB values, respectively. The result is normalized:
$$
h = \frac{h}{6}
$$



### Saturation Calculation
To calculate the saturation, \( s \):
$$
s = \begin{cases}
    0, & \text{if } \max = \min \\
    \frac{\Delta}{2 - \max - \min}, & \text{if } l > 0.5 \\
    \frac{\Delta}{\max + \min}, & \text{otherwise}
\end{cases}
$$
where
$$
l = \frac{\max + \min}{2}
$$
is the lightness.



### Lightness Calculation
To calculate the lightness, \( l \):
$$
l = \frac{\max + \min}{2}
$$

## Pseudocode Algorithm
```pseudo
\begin{algorithm}
\caption{RGBtoHSL}
\begin{algorithmic}
  \Procedure{RGBtoHSL}{$r, g, b$}
    \State Normalize $r, g, b$ by dividing each by $255$
    \State $maxVal \gets \max(r, g, b)$
    \State $minVal \gets \min(r, g, b)$
    \State $l \gets (maxVal + minVal) / 2$
    \If{$maxVal = minVal$}
      \State $s \gets 0$
      \State $h \gets 0$
    \Else
      \State $delta \gets maxVal - minVal$
      \If{$l > 0.5$}
        \State $s \gets delta / (2 - maxVal - minVal)$
      \Else
        \State $s \gets delta / (maxVal + minVal)$
      \EndIf
      \If{$maxVal = r$}
        \State $h \gets (g - b) / delta + (g < b \ ? 6 \ : 0)$
      \ElsIf{$maxVal = g$}
        \State $h \gets (b - r) / delta + 2$
      \ElsIf{$maxVal = b$}
        \State $h \gets (r - g) / delta + 4$
      \EndIf
      \State $h \gets h / 6$
    \EndIf
    \State \Return $h, s, l$
  \EndProcedure
\end{algorithmic}
\end{algorithm}
```


