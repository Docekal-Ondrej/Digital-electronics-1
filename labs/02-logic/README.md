# LABS - 02 (2-bit comparator)

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

B = A Table:
A(1;0), B(1;0)

|   | A 00| A 01| A 11| A 10|
|-----|---|-----|-----|-----|
| B 00| 1 |  0  |  0  |  0  |
| B 01| 0 |  1  |  0  |  0  |
| B 11| 0 |  0  |  1  |  0  |
| B 10| 0 |  0  |  0  |  1  |

B > A Table:
A(1;0), B(1;0)

|   | A 00| A 01| A 11| A 10|
|-----|---|-----|-----|-----|
| B 00| 0 |  0  |  0  |  0  |
| B 01| 1 |  0  |  0  |  0  |
| B 11| 1 |  1  |  0  |  1  |
| B 10| 1 |  1  |  0  |  0  |

_greaterThan(SoP)_ = B1!A1+!A1!A0B0+B1B0!A0

B < A Table:
A(1;0), B(1;0)

|   | A 00| A 01| A 11| A 10|
|-----|---|-----|-----|-----|
| B 00| 0 |  1  |  1  |  1  |
| B 01| 0 |  0  |  1  |  1  |
| B 11| 0 |  0  |  0  |  0  |
| B 10| 0 |  0  |  1  |  0  |

_lessThan(PoS)_ = (A1+A0) ⋅ (!B1+!B0) ⋅ (!B1+A1) ⋅ (!B0+A1) ⋅ (!B1+A0)

My code (2-bit comparator): https://www.edaplayground.com/x/8UWE

## 4-bit comparator

My code (4-bit comparator): https://www.edaplayground.com/x/jdEM

### design.vhd:

library ieee;  
use ieee.std_logic_1164.all;

entity comparator_4bit is  
    port(  
        a_i           : in  std_logic_vector(4 - 1 downto 0); -- Data A  
        b_i           : in  std_logic_vector(4 - 1 downto 0); -- Data B  
        B_greater_A_o : out std_logic; -- B is greater than A  
        B_equals_A_o  : out std_logic; -- B equals A  
        B_less_A_o    : out std_logic  -- B is less than A  
    );  
end entity comparator_4bit;

architecture Behavioral of comparator_4bit is  
begin  
	B_greater_A_o <= '1' when (b_i > a_i) else '0';  
	B_equals_A_o  <= '1' when (b_i = a_i) else '0';  
	B_less_A_o    <= '1' when (b_i < a_i) else '0';  

end architecture Behavioral;

### testbench.vhd:

library ieee;  
use ieee.std_logic_1164.all;  

entity tb_comparator_4bit is

end entity tb_comparator_4bit;

architecture testbench of tb_comparator_4bit is
  
    signal s_a       : std_logic_vector(4 - 1 downto 0);  
    signal s_b       : std_logic_vector(4 - 1 downto 0);  
    signal s_B_greater_A : std_logic;  
    signal s_B_equals_A  : std_logic;  
    signal s_B_less_A    : std_logic;  

begin

    uut_comparator_4bit : entity work.comparator_4bit  
        port map(  
            a_i           => s_a,  
            b_i           => s_b,  
            B_greater_A_o => s_B_greater_A,  
            B_equals_A_o  => s_B_equals_A,  
            B_less_A_o    => s_B_less_A  
        );  

    p_stimulus : process  
    begin  
        report "Stimulus process started" severity note;  


        s_b <= "0000"; s_a <= "0000"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '1') and (s_B_less_A = '0'))
        report "Test failed for input combination: 0000, 0000" severity error;
        
        s_b <= "0001"; s_a <= "0101"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '0') and (s_B_less_A = '1'))
        report "Test failed for input combination: 0001, 0101" severity error;
        
        s_b <= "0011"; s_a <= "1011"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '0') and (s_B_less_A = '1'))
        report "Test failed for input combination: 0010, 1011" severity error;
        
        s_b <= "0000"; s_a <= "1111"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '0') and (s_B_less_A = '1'))
        report "Test failed for input combination: 0000, 1111" severity error;
        
        s_b <= "0100"; s_a <= "0011"; wait for 100 ns;
        assert ((s_B_greater_A = '1') and (s_B_equals_A = '0') and (s_B_less_A = '0'))
        report "Test failed for input combination: 0100, 0011" severity error;
        
        s_b <= "0100"; s_a <= "0100"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '1') and (s_B_less_A = '0'))
        report "Test failed for input combination: 0100, 0100" severity error;
        
        s_b <= "0111"; s_a <= "1011"; wait for 100 ns;
        assert ((s_B_greater_A = '0') and (s_B_equals_A = '0') and (s_B_less_A = '1'))
        report "Test failed for input combination: 0111, 1011" severity error;
        
        s_b <= "0101"; s_a <= "1111"; wait for 100 ns;
        assert ((s_B_greater_A = '1') and (s_B_equals_A = '0') and (s_B_less_A = '0'))
        report "Test failed for input combination: 0101, 1111" severity error;
        
        s_b <= "1000"; s_a <= "0000"; wait for 100 ns;
        assert ((s_B_greater_A = '1') and (s_B_equals_A = '0') and (s_B_less_A = '0'))
        report "Test failed for input combination: 1000, 0000" severity error;
        
        s_b <= "1011"; s_a <= "0101"; wait for 100 ns;
        assert ((s_B_greater_A = '1') and (s_B_equals_A = '0') and (s_B_less_A = '0'))
        report "Test failed for input combination: 1011, 0101" severity error;

        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;

end architecture testbench;

### console output

[2021-02-23 12:58:44 EST] ghdl -i design.vhd testbench.vhd  && ghdl -m  tb_comparator_4bit && ghdl -r  tb_comparator_4bit   --vcd=dump.vcd && sed -i 's/^U/X/g; s/^-/X/g; s/^H/1/g; s/^L/0/g' dump.vcd  
analyze design.vhd  
analyze testbench.vhd  
elaborate tb_comparator_4bit  
testbench.vhd:50:9:@0ms:(report note): Stimulus process started  
testbench.vhd:83:9:@800ns:(assertion error): Test failed for input combination: 0101, 1111  
testbench.vhd:95:9:@1us:(report note): Stimulus process finished  
Finding VCD file...
./dump.vcd  
[2021-02-23 12:58:45 EST] Opening EPWave...  
Done