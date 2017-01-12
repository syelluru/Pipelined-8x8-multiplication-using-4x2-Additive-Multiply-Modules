library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity twolatch is
 Port ( clk : in std_logic;
 p23 : in std_logic_vector(1 downto 0) := "00";
 o23 : out std_logic_vector(1 downto 0) := "00"
 );
end twolatch;
architecture Behavioral of twolatch is
 type t_mem is array(natural range <>) of std_logic_vector(1 downto 0);
 signal mem : t_mem(0 to 1) := (others => "00");
begin
 process(clk)
 begin
 if rising_edge(Clk) then
 o23 <= mem(1);
 --mem(1) <= mem(0);
 mem(1) <= p23;
 end if;
 end process;
end Behavioral;
