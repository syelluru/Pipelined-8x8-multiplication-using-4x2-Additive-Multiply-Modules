library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity fourlatch is
 Port ( clk : in STD_LOGIC;
 p23 : in STD_LOGIC_VECTOR(3 downto 0):= "0000";
 o23 : out STD_LOGIC_VECTOR(3 downto 0):= "0000");
end fourlatch;
architecture Behavioral of fourlatch is
 type t_mem is array(natural range <>) of std_logic_vector(3 downto 0);
 signal mem : t_mem(0 to 1) := (others => "0000");
5
begin
process(clk)
 begin
 if rising_edge(clk) then
 o23 <= mem(1);
 --mem(1) <= mem(0);
 mem(1) <= p23;
 end if;
 end process;
end Behavioral;
