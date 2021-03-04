# LABS - 03

My github: https://github.com/Docekal-Ondrej

## Table

![Waveform screenshot.](https://raw.githubusercontent.com/Docekal-Ondrej/Digital-electronics-1/main/labs/03-VIVADO/Screenshot-1.jpg)

## Two-bit wide 4-to-1 multiplexer.

```
architecture Behavioral of mux_2bit_4to1 is
begin
f_o <= a_i when (sel_i = "00") else
       b_i when (sel_i = "01") else
       c_i when (sel_i = "10") else
       d_i;

end architecture Behavioral;

 p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        
        s_a <= "10"; s_b <= "11"; s_c <= "01"; s_d <= "00";
        s_sel <="00"; wait for 100 ns;
        
        s_a <= "00"; s_b <= "11"; s_c <= "01"; s_d <= "00";
        s_sel <="00"; wait for 100 ns;
        
        s_a <= "00"; s_b <= "11"; s_c <= "01"; s_d <= "00";
        s_sel <="01"; wait for 100 ns;
        
        s_a <= "00"; s_b <= "11"; s_c <= "01"; s_d <= "00";
        s_sel <="10"; wait for 100 ns;
        
        s_a <= "00"; s_b <= "00"; s_c <= "10"; s_d <= "11";
        s_sel <="11"; wait for 100 ns;
        
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```
![Waveform screenshot.](https://raw.githubusercontent.com/Docekal-Ondrej/Digital-electronics-1/main/labs/03-VIVADO/Screenshot-2.jpg)

## Tutorial - Create new project

1. Launch Vivado
2. Create project
3. Next
4. Write project name and select desired location
5. Next
6. Next, note - make sure to have selected "RTL Project"
7. Target language - select "VHDL"
8. Create file
9. Write source file name
10. OK
11. Next
12. Create file
13. Write constraints file name
14. OK
15. Next
16. Next
17. Finish
18. File->Add sources...->Select "Add or create simulation sources"
19. Next
20. Create file
21. Write your source file name
22. OK
23. Finish
24. OK
To run simulation select Flow->Run Simulation->Run Behavioral Simulation