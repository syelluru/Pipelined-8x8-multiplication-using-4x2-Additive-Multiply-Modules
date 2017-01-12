library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity amm_module is
 Port ( clk : in STD_LOGIC;
 a : in STD_LOGIC_VECTOR (3 downto 0);
 b : in STD_LOGIC_VECTOR (1 downto 0);
 c : in STD_LOGIC_VECTOR (3 downto 0);
 d : in STD_LOGIC_VECTOR (1 downto 0);
 p : out STD_LOGIC_VECTOR (5 downto 0));
end amm_module;
architecture Behavioral of amm_module is
--signal clk : STD_LOGIC;
signal and00 : STD_LOGIC;
signal and10 : STD_LOGIC;
signal and20 : STD_LOGIC;
signal and30 : STD_LOGIC;
signal and01 : STD_LOGIC;
signal and11 : STD_LOGIC;
signal and21 : STD_LOGIC;
signal and31 : STD_LOGIC;
signal fa1c : STD_LOGIC;
signal fa2s : STD_LOGIC;
signal fa2c : STD_LOGIC;
signal fa3s : STD_LOGIC;
signal fa3c : STD_LOGIC;
signal fa4s : STD_LOGIC;
signal fa4c : STD_LOGIC;
signal fa5c : STD_LOGIC;
signal fa6c : STD_LOGIC;
signal fa7c : STD_LOGIC;
begin
 process(clk)
 begin
 if rising_edge(clk) then

 --AND Products
 and00 <= a(0) AND b(0);
 and10 <= a(1) AND b(0);
 and20 <= a(2) AND b(0);
 and30 <= a(3) AND b(0);
 and01 <= a(0) AND b(1);
 and11 <= a(1) AND b(1);
 and21 <= a(2) AND b(1);
 and31 <= a(3) AND b(1);

 --FULLADDER-1
 fa1c <= (c(0) AND and00)OR(d(0) AND and00)OR(c(1) AND d(0));
 p(0) <= c(0) XOR and00 XOR d(0);
 --FULLADDER-2
 fa2s <= and10 XOR and01 XOR c(1);
 fa2c <= (and10 AND and01) OR (and10 AND c(1)) OR (c(1) AND and01);
 --FULLADDER-3
 fa3s <= and20 XOR and11 XOR c(2);
 fa3c <= (and20 AND and11) OR (and20 AND c(2)) OR (c(2) AND and11);
3
 --FULLADDER-4
 fa4s <= and30 XOR and21 XOR c(3);
 fa4c <= (and30 AND and21) OR (and30 AND c(3)) OR (c(3) AND and21);
 --FULLADDER-5
 p(1) <= fa1c XOR d(1) XOR fa2s;
 fa5c <= (fa1c AND d(1)) OR (fa1c AND fa2s) OR (d(1) AND fa2s);
 --FULLADDER-6
 p(2) <= fa5c XOR fa2c XOR fa3s;
 fa6c <= (fa5c AND fa2c) OR (fa5c AND fa3s) OR (fa3s AND fa2c);

 --FULLADDER-7
 p(3) <= fa3c XOR fa4s XOR fa6c;
 fa7c <= (fa3c AND fa4s) OR (fa3c AND fa6c) OR (fa4s AND fa6c);
 --FULLADDER-8
 p(4) <= and31 XOR fa4c XOR fa7c;
 p(5) <= (fa4c AND fa7c) OR (fa4c AND and31) OR (fa7c AND and31);

 end if;
 end process;
end Behavioral;
