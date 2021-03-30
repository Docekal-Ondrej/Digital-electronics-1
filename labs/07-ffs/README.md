# LABS - 07

My github: https://github.com/Docekal-Ondrej

Tables:

D flip-flop:
q(n+1) = d

| clk | d | q(n) | q(n+1) |
| --- | - | ---- | ------ |
|  ↑  | 0 |  0   |  q(n)  |
|  ↑  | 0 |  1   |  q(n)  |
|  ↑  | 1 |  0   |   1    |
|  ↑  | 1 |  1   |   0    |

JK flip-flop
q(n+1) = J · /q(n) + /K · q(n)

| clk | j | k | q(n) | q(n+1) |
| --- | - | - | ---- | ------ |
|  ↑  | 0 | 0 |  0   |   0    |
|  ↑  | 0 | 0 |  1   |   1    |
|  ↑  | 0 | 1 |  0   |   0    |
|  ↑  | 0 | 1 |  1   |   0    |
|  ↑  | 1 | 0 |  0   |   1    |
|  ↑  | 1 | 0 |  1   |   1    |
|  ↑  | 1 | 1 |  0   |   1    |
|  ↑  | 1 | 1 |  1   |   0    |

T flip-flop
q(n+1) = T · /q(n) + /T · q(n)

| clk | t | q(n) | q(n+1) |
| --- | - | ---- | ------ |
|  ↑  | 0 |  0   |   0    |
|  ↑  | 0 |  1   |   1    |
|  ↑  | 1 |  0   |   1    |
|  ↑  | 1 |  1   |   0    |

## Architecture

```vhdl
p_d_latch : process (d, arst, en)
    begin
        if (arst = '1') then
             q     <= '0';
             q_bar <= '1';
         
        elsif (en = '1') then
            q     <= d;
            q_bar <= not d;
        
        end if;     
        
    end process p_d_latch;
```

```vhdl
architecture testbench of tb_d_latch is
           signal s_en    : std_logic;
           signal s_arst  : std_logic;
           signal s_d     : std_logic;
           signal s_q     : std_logic; 
           signal s_q_bar : std_logic;
begin
    uut_d_latch: entity work.d_latch
    port map(
    en   => s_en,   
    arst => s_arst, 
    d    => s_d,    
    q    => s_q,    
    q_bar => s_q_bar
    );
    -------------------------------------------------------------------- 
    -- Reset generation processend Behavioral;
    --------------------------------------------------------------------
    p_reset_gen : process
    begin
        s_arst <= '0';
        wait for 40 ns;
        
        -- Reset activated
        s_arst <= '1';
        wait for 53 ns;

        -- Reset deactivated
        s_arst <= '0';
        wait for 300 ns;

        -- Reset deactivated
        s_arst <= '1';

        wait;
    end process p_reset_gen;

    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_d  <= '0';
        s_en <= '0';
        
        --sekvence
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        assert (s_q = '0' and s_q_bar = '1')
        report "reset error" severity error;
        wait for 10 ns;
        s_d <= '0';
        
        s_en <= '1';
        
        assert (s_q = '0' and s_q_bar = '1')
        report "s_q = s_q_bar" severity error;
        --sekvence
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        
        wait for 10 ns;
        
        
        wait for 200 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        
        --sekvence
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        assert (s_q = s_d)
        report "enable error" severity error;
        
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        s_en <= '0';
        --sekvence
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        

        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
    
end architecture testbench;
```

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot1.png)

## D flip-flop arst
```vhdl
p_d_ff_arst : process (arst, clk)
    begin
        if (arst = '1') then
             q     <= '0';
             q_bar <= '1';
         
        elsif rising_edge(clk) then
            q     <= d;
            q_bar <= not d;
        
        end if;     
        
    end process p_d_ff_arst;
```

```vhdl
    p_clk_gen : process
    begin
        while now < 750 ns loop         -- 75 periods of 100MHz clock
            s_clk_100MHz <= '0';
            wait for c_CLK_100MHZ_PERIOD / 2;
            s_clk_100MHz <= '1';
            wait for c_CLK_100MHZ_PERIOD / 2;
        end loop;
        wait;
    end process p_clk_gen;
    
    p_reset_gen : process
    begin
        s_arst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_arst <= '1';
        wait for 13 ns;

        -- Reset deactivated
        s_arst <= '0';
        
        wait for 17 ns;
        s_arst <= '1';
        
        wait for 33 ns;
        s_arst <= '0';
        wait;
    end process p_reset_gen;

    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_d <= '0';
        
         wait for 14 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        assert (s_q = '0' and s_q_bar = '1')
        report "s_q = s_q_bar" severity error;
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        assert (s_q = '0' and s_q_bar = '1')
        report "reset error" severity error;
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';       
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot2.png)

## d flip-flop rst
```vhdl
p_d_ff_arst : process (clk)
    begin
        if rising_edge(clk) then
            if (rst = '1') then
                q     <= '0';
                q_bar <= '1';
            else
                q     <= d;
                q_bar <= not d;
        
            end if;     
        end if;
    end process p_d_ff_arst;
```

```vhdl
 p_clk_gen : process
    begin
        while now < 750 ns loop         -- 75 periods of 100MHz clock
            s_clk_100MHz <= '0';
            wait for c_CLK_100MHZ_PERIOD / 2;
            s_clk_100MHz <= '1';
            wait for c_CLK_100MHZ_PERIOD / 2;
        end loop;
        wait;
    end process p_clk_gen;
    
    p_reset_gen : process
    begin
        s_rst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_rst <= '1';
        wait for 13 ns;

        -- Reset deactivated
        s_rst <= '0';
        
        wait for 17 ns;
        s_rst <= '1';
        
        wait for 33 ns;
        s_rst <= '0';
        wait;
    end process p_reset_gen;

    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_d <= '0';
        
         wait for 14 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        assert (s_q = '0' and s_q_bar = '1')
        report "s_q = s_q_bar" severity error;
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        assert (s_q = '0' and s_q_bar = '1')
        report "reset error" severity error;
        wait for 10 ns;
        s_d <= '0';
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';       
        wait for 10 ns;
        s_d <= '1';
        wait for 10 ns;
        s_d <= '0';
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot3.png)

## jk flip-flop rst
```vhdl
 p_jk_ff_rst : process (clk)
    begin
        if rising_edge(clk) then
            if(rst = '1') then
                s_q <= '0';
                else
                    if(j = '0' and k = '0')then
                        s_q <= s_q;
                    elsif(j = '0' and k = '1')then
                        s_q <= '0';
                    elsif(j = '1' and k = '0')then
                        s_q <= '1';
                    elsif(j = '1' and k = '1')then
                        s_q <= not s_q;
                    end if;
            end if;
        end if;    
    end process p_jk_ff_rst;
```

```vhdl
    p_reset_gen : process
    begin
        s_rst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_rst <= '1';
        wait for 13 ns;

        -- Reset deactivated
        s_rst <= '0';
        
        wait for 17 ns;
        s_rst <= '1';
        
        wait for 33 ns;
        s_rst <= '0';
        wait;
    end process p_reset_gen;

    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_j <= '0';
        s_k <= '0';
        
        wait for 40 ns;
        s_j <= '0';
        s_k <= '0';
        wait for 7 ns;
        s_j <= '0';
        s_k <= '1';
        wait for 7 ns;
        s_j <= '1';
        s_k <= '0';
        wait for 7 ns;
        s_j <= '1';
        s_k <= '1';
        wait for 7 ns;
        s_j <= '0';
        s_k <= '0';
        wait for 7 ns;
        s_j <= '0';
        s_k <= '1';
        wait for 7 ns;
        s_j <= '1';
        s_k <= '0';
        wait for 7 ns;
        s_j <= '1';
        s_k <= '1';
        wait for 7 ns;
        s_j <= '0';
        s_k <= '1';
        wait;
    end process p_stimulus;
```

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot4.png)

## t flip-flop rst
```vhdl
p_t_ff_rst : process (clk)
    begin
        if rising_edge(clk) then
            if (rst = '1') then
                s_q     <= '0';
            else
                if(t = '0')then
                s_q <= s_q;
                else
                s_q <= not s_q;
                end if;
            end if;     
        end if;
    end process p_t_ff_rst;
    q     <= s_q;
    q_bar <= not s_q;
```

```vhdl
     --------------------------------------------------------------------
    -- Clock generation process
    --------------------------------------------------------------------
    p_clk_gen : process
    begin
        while now < 750 ns loop         -- 75 periods of 100MHz clock
            s_clk_100MHz <= '0';
            wait for c_CLK_100MHZ_PERIOD / 2;
            s_clk_100MHz <= '1';
            wait for c_CLK_100MHZ_PERIOD / 2;
        end loop;
        wait;
    end process p_clk_gen;
    
    p_reset_gen : process
    begin
        s_rst <= '0';
        wait for 28 ns;
        
        -- Reset activated
        s_rst <= '1';
        wait for 13 ns;

        -- Reset deactivated
        s_rst <= '0';
        
        wait for 17 ns;
        s_rst <= '1';
        
        wait for 33 ns;
        s_rst <= '0';
        wait;
    end process p_reset_gen;

    --------------------------------------------------------------------
    -- Data generation process
    --------------------------------------------------------------------
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_t <= '0';
        
        wait for 10 ns;
        s_t <= '1';
        wait for 13 ns;
        s_t <= '0';
        wait for 13 ns;
        s_t <= '1';
        wait for 13 ns;
        s_t <= '0';
        wait for 13 ns;
        s_t <= '1';
        wait for 13 ns;
        s_t <= '0';
        wait for 13 ns;
        s_t <= '1';
        wait for 13 ns;
        s_t <= '0';
        wait for 13 ns;
        s_t <= '1';
        wait for 20 ns;
        s_t <= '0';
        wait for 20 ns;
        s_t <= '1';
        wait for 20 ns;
        s_t <= '0';
        wait for 20 ns;
        s_t <= '1';
        wait for 20 ns;
        s_t <= '0';         
        wait for 20 ns;
        s_t <= '1';
        wait for 20 ns;
        s_t <= '0';
        
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot5.png)

![Table.](https://github.com/Docekal-Ondrej/Digital-electronics-1/blob/main/labs/07-ffs/Screenshot6.png)