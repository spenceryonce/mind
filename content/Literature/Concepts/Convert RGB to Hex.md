---
tags:
  - programming
  - rgb2hex
  - algorithm
  - conversion
  - cplusplus
  - code
  - mathematics
  - colortheory
DateCreated: 5/3/2024 12:07 am
---
### RGB to Hexadecimal Conversion

1. **Normalize RGB values:**
   Each of the RGB components (\(r\), \(g\), and \(b\)) can range from 0 to 255.

2. **Convert to Hexadecimal:**
   Each RGB component needs to be converted to a two-digit hexadecimal value:
$$
   \text{hex}(r) = \text{int to hex}(r)
$$
$$
   \text{hex}(g) = \text{int to hex}(g)
$$
$$
   \text{hex}(b) = \text{int to hex}(b)
$$

3. **Combine Hex Values:**
   Combine the hexadecimal values into a single hex string:
$$
   \text{hex color} = "\#\{\text{hex}(r)\}\{\text{hex}(g)\}\{\text{hex}(b)\}"
$$

**Pseudocode:**

Below is pseudocode to convert RGB to a hexadecimal color string.

```pseudo
\begin{algorithm}
\caption{RGBtoHex}
\begin{algorithmic}
  \Procedure{RGBtoHex}{$r, g, b$}
    \Function{intToHex}{$num$}
      \State Convert $num$ to a hexadecimal string
      \State \Return the two-digit hexadecimal string, with leading zeros if needed
    \EndFunction
    \State $hexR \gets \text{intToHex}(r)$
    \State $hexG \gets \text{intToHex}(g)$
    \State $hexB \gets \text{intToHex}(b)$
    \State $hexColor \gets \text{\#} + $hexR + $hexG + $hexB
    \State \Return $hexColor$
   
  \EndProcedure
\end{algorithmic}
\end{algorithm}
```

### Explanation:
- The `intToHex` function converts an integer \( num \) to a two-digit hexadecimal string with leading zeros.
- The main procedure, `RGBtoHex`, uses this function to convert each of the RGB components to hexadecimal.
- The final hex color string is assembled and returned.

