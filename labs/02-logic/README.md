# LABS - 02

My github: https://github.com/Docekal-Ondrej

Table:

| Dec | B1 | B0 | A1 | A0 | B > A | B = A | B < A |
| --- | -- | -- | -- | -- | ----- | ----- | ----- |
|  1  |  0 |  0 |  0 |  0 |   0   |   1   |   0   |
|  2  |  0 |  0 |  0 |  1 |   0   |   0   |   1   |
|  3  |  0 |  0 |  1 |  0 |   0   |   0   |   1   |
|  4  |  0 |  0 |  1 |  1 |   0   |   0   |   1   |
|  5  |  0 |  1 |  0 |  0 |   1   |   0   |   0   |
|  6  |  0 |  1 |  0 |  1 |   0   |   1   |   0   |
|  7  |  0 |  1 |  1 |  0 |   0   |   0   |   1   |
|  8  |  0 |  1 |  1 |  1 |   0   |   0   |   1   |
|  9  |  1 |  0 |  0 |  0 |   1   |   0   |   0   |
|  10 |  1 |  0 |  0 |  1 |   1   |   0   |   0   |
|  11 |  1 |  0 |  1 |  0 |   0   |   1   |   0   |
|  12 |  1 |  0 |  1 |  1 |   0   |   0   |   1   |
|  13 |  1 |  1 |  0 |  0 |   1   |   0   |   0   |
|  14 |  1 |  1 |  0 |  1 |   1   |   0   |   0   |
|  15 |  1 |  1 |  1 |  0 |   1   |   0   |   0   |
|  16 |  1 |  1 |  1 |  1 |   0   |   1   |   0   |

_equals(SoP)_ = m<sub>1</sub>+m<sub>6</sub>+m<sub>11</sub>+m<sub>16</sub> = !B1 !B0 !A1 !A0 + !B1 B0 !A1 A0 + B1 !B0 A1 !A0 + B1 B0 A1 A0

_equals(PoS)_ = M<sub>2</sub>⋅M<sub>3</sub>⋅M<sub>4</sub>⋅M<sub>5</sub>⋅M<sub>7</sub>⋅M<sub>8</sub>⋅M<sub>9</sub>⋅M<sub>10</sub>⋅M<sub>12</sub>⋅M<sub>13</sub>⋅M<sub>14</sub>⋅M<sub>15</sub> = (B1+B0+A1+!A0) ⋅ (B1+B0+!A1+A0) ⋅ (B1+B0+!A1+!A0) ⋅ (B1+!B0+A1+A0) ⋅ (B1+!B0+!A1+A0) ⋅ (B1+!B0+!A1+!A0) ⋅ (!B1+B0+A1+A0) ⋅ (B1+B0+!A1+!A0) ⋅ (!B1+B0+!A1+!A0) ⋅ (!B1+!B0+A1+A0) ⋅ (!B1+!B0+A1+!A0) ⋅ (!B1+!B0+!A1+!A0)

_lessThan(SoP)_ = m<sub>2</sub>+m<sub>3</sub>+m<sub>4</sub>+m<sub>7</sub>+m<sub>8</sub>+m<sub>12</sub> = !B1 !B0 !A1 A0 + !B1 !B0 A1 !A0 + !B1 !B0 A1 A0 + B1 !B0 !A1 A0 + !B1 B0 A1 A0 + B1 !B0 A1 A0

_lessThan(PoS)_ = M<sub>1</sub>⋅M<sub>5</sub>⋅M<sub>6</sub>⋅M<sub>9</sub>⋅M<sub>10</sub>⋅M<sub>11</sub>⋅M<sub>13</sub>⋅M<sub>14</sub>⋅M<sub>15</sub>⋅M<sub>16</sub> = (B1+B0+A1+A0) ⋅ (B1+!B0+A1+A0) ⋅ (B1+!B0+A1+!A0) ⋅ (!B1+B0+A1+A0) ⋅ (!B1+B0+A1+!A0) ⋅ (!B1+B0+!A1+A0) ⋅ (!B1+!B0+A1+A0) ⋅ (!B1+!B0+A1+!A0) ⋅ (!B1+!B0+!A1+A0) ⋅ (!B1+!B0+!A1+!A0)

B > A Table:
A(1;0), B(1;0)

|   | A 00| A 01| A 11| A 10|
|-----|---|-----|-----|-----|
| B 00| 0 |  0  |  0  |  0  |
| B 01| 1 |  0  |  0  |  0  |
| B 11| 1 |  1  |  0  |  1  |
| B 10| 1 |  1  |  0  |  0  |

B < A Table:
A(1;0), B(1;0)

|   | A 00| A 01| A 11| A 10|
|-----|---|-----|-----|-----|
| B 00| 0 |  1  |  1  |  1  |
| B 01| 0 |  0  |  1  |  1  |
| B 11| 0 |  0  |  0  |  0  |
| B 10| 0 |  0  |  1  |  0  |

My code: https://www.edaplayground.com/x/wQCr

![Waveform screenshot.](https://raw.githubusercontent.com/Docekal-Ondrej/Digital-electronics-1/main/labs/01-gates/Screenshot-EDU1.jpg "Waveforms")