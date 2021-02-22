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

_equals(SoP)_ = m<sub>1</sub> + m<sub>6</sub> + m<sub>11</sub> + m<sub>16</sub> = !B1 !B0 !A1 !A0 + !B1 B0 !A1 A0 + B1 !B0 A1 !A0 + B1 B0 A1 A0

_equals(PoS)_ = m<sub>2</sub> ⋅ m<sub>3</sub> ⋅ m<sub>4</sub> ⋅ m<sub>5</sub> ⋅ m<sub>7</sub> ⋅ m<sub>8</sub> ⋅ m<sub>9</sub> ⋅ m<sub>10</sub> ⋅ m<sub>12</sub> ⋅ m<sub>13</sub> ⋅ m<sub>14</sub> ⋅ m<sub>15</sub> = (B1+B0+A1+!A0) ⋅ (B1+B0+!A1+A0) ⋅ (B1+B0+!A1+!A0) ⋅ (B1+!B0+A1+A0) ⋅ (B1+!B0+!A1+A0) ⋅ (B1+!B0+!A1+!A0) ⋅ (!B1+B0+A1+A0) ⋅ (B1+B0+!A1+!A0) ⋅ (!B1+B0+!A1+!A0) ⋅ (!B1+!B0+A1+A0) ⋅ (!B1+!B0+A1+!A0) ⋅ (!B1+!B0+!A1+!A0)

_lessThan(SoP)_ = m<sub>2</sub> + m<sub>3</sub> + m<sub>4</sub> + m<sub>7</sub> + m<sub>8</sub> + m<sub>12</sub> = !B1 !B0 !A1 A0 + !B1 !B0 A1 !A0 + !B1 !B0 A1 A0 + B1 !B0 !A1 A0 + !B1 B0 A1 A0 + B1 !B0 A1 A0

_lessThan(PoS)_ = m<sub>1</sub> ⋅ m<sub>5</sub> ⋅ m<sub>6</sub> ⋅ m<sub>9</sub> ⋅ m<sub>10</sub> ⋅ m<sub>11</sub> ⋅ m<sub>13</sub> ⋅ m<sub>14</sub> ⋅ m<sub>15</sub> ⋅ m<sub>16</sub> = (B1+B0+A1+A0) ⋅ (B1+!B0+A1+A0) ⋅ (B1+!B0+A1+!A0) ⋅ (!B1+B0+A1+A0) ⋅ (!B1+B0+A1+!A0) ⋅ (!B1+B0+!A1+A0) ⋅ (!B1+!B0+A1+A0) ⋅ (!B1+!B0+A1+!A0) ⋅ (!B1+!B0+!A1+A0) ⋅ (!B1+!B0+!A1+!A0)




My code: https://www.edaplayground.com/x/wQCr

![Waveform screenshot.](https://raw.githubusercontent.com/Docekal-Ondrej/Digital-electronics-1/main/labs/01-gates/Screenshot-EDU1.jpg "Waveforms")

Distributive law verification: https://www.edaplayground.com/x/KgU8

![Waveform screenshot.](https://raw.githubusercontent.com/Docekal-Ondrej/Digital-electronics-1/main/labs/01-gates/Screenshot-EDU2.jpg "Waveforms")