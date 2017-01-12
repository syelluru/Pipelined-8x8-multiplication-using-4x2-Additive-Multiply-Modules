library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity ece689_proj is
 Port ( clk : in STD_LOGIC;
 a : in STD_LOGIC_VECTOR (7 downto 0);
 b : in STD_LOGIC_VECTOR (7 downto 0);
 p : out STD_LOGIC_VECTOR (15 downto 0));
end ece689_proj;
architecture Behavioral of ece689_proj is
 signal a1 : STD_LOGIC_VECTOR (3 downto 0);
 signal a2 : STD_LOGIC_VECTOR (3 downto 0);

 signal b1 : STD_LOGIC_VECTOR (1 downto 0);
 signal b2 : STD_LOGIC_VECTOR (1 downto 0);
 signal b3 : STD_LOGIC_VECTOR (1 downto 0);
 signal b4 : STD_LOGIC_VECTOR (1 downto 0);

 signal c : STD_LOGIC_VECTOR (3 downto 0) := "0000";
 signal d : STD_LOGIC_VECTOR (1 downto 0) := "00";

 --two latch outputs
 signal q1 : STD_LOGIC_VECTOR (1 downto 0);
 signal q2 : STD_LOGIC_VECTOR (1 downto 0);
 signal q3 : STD_LOGIC_VECTOR (1 downto 0);

 --four latch outputs
 signal r1 : STD_LOGIC_VECTOR (3 downto 0);
 signal r2 : STD_LOGIC_VECTOR (3 downto 0);
 signal r3 : STD_LOGIC_VECTOR (3 downto 0);

 type s is array(7 downto 0) of std_logic_vector(5 downto 0);
 signal x : s := (others => "000000");

 component amm_module is
 Port( clk : in STD_LOGIC;
 a : in STD_LOGIC_VECTOR (3 downto 0);
 b : in STD_LOGIC_VECTOR (1 downto 0);
 c : in STD_LOGIC_VECTOR (3 downto 0);
 d : in STD_LOGIC_VECTOR (1 downto 0);
 p : out STD_LOGIC_VECTOR (5 downto 0));
 end component;

 component twolatch is
 Port ( Clk : in std_logic;
 p23 : in std_logic_vector(1 downto 0) := "00";
 o23 : out std_logic_vector(1 downto 0) := "00"
 );
6
 end component;

 component fourlatch is
 Port ( Clk : in STD_LOGIC;
 p23 : in STD_LOGIC_VECTOR(3 downto 0):= "0000";
 o23 : out STD_LOGIC_VECTOR(3 downto 0):= "0000");
 end component;
begin

 a1 <= a(3 downto 0);
 a2 <= a(7 downto 4);

 b1 <= b(1 downto 0);
 b2 <= b(3 downto 2);
 b3 <= b(5 downto 4);
 b4 <= b(7 downto 6);

--XL*Y10 (4x2 AMM)
MODULE1: amm_module port map (clk,a1,b1,c,d,x(0));
--XH*Y10 (4x2 AMM)
MODULE2: amm_module port map (clk,a2,b1,c,x(0)(5 downto 4),x(1));
mod1: twolatch port map(clk, x(0)(3 downto 2), q1);
--XL*Y32 (4x2 AMM)
MODULE3: amm_module port map (clk,a1,b2,(x(1)(1 downto 0) & q1),d,x(2));
mod2: fourlatch port map(clk, x(1)(5 downto 2), r1);
--XH*Y32 (4x2 AMM)
MODULE4: amm_module port map(clk,a2,b2,r1,x(2)(5 downto 4), x(3));
mod3: twolatch port map(clk, x(2)(3 downto 2), q2);
--XL*Y54 (4x2 AMM)
MODULE5: amm_module port map(clk,a1,b3,(x(3)(1 downto 0) & q2),d,x(4));
mod4: fourlatch port map(clk,x(3)(5 downto 2), r2);
--XH*Y54 (4x2 AMM)
MODULE6: amm_module port map(clk,a2,b3,r2,x(4)(5 downto 4), x(5));
mod5: twolatch port map(clk, x(4)(3 downto 2), q3);
--XL*Y76 (4x2 AMM)
MODULE7: amm_module port map(clk,a1,b4,(x(5)(1 downto 0) & q3),d,x(6));
mod6: fourlatch port map(clk, x(5)(5 downto 2), r3);
--XH*Y76 (4x2 AMM)
MODULE8: amm_module port map(clk,a2,b4,r3,x(6)(5 downto 4), x(7));
p <= (x(7) & x(6)(3 downto 0) & x(4)(1 downto 0) & x(2)(1 downto 0) & x(0)(1 downto
0));
end Behavioral;
