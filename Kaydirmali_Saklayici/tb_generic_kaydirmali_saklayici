library IEEE;
use IEEE.STD_LOGIC_1164.ALL;


entity tb_generic_kaydirmali_saklayici is
end tb_generic_kaydirmali_saklayici;

	architecture behavioral of tb_generic_kaydirmali_saklayici is
	
		component generic_kaydirmali_saklayici is
		Port(
			in_clk 			: in std_logic;
			
			in_rst 			: in std_logic;
			in_director 	: in std_logic;
			in_bit			: in std_logic;
			out_bit			: out std_logic_vector(3 downto 0));
		end component;
		
		constant CLK_PERIOD : time := 150 ns;
		signal in_clk : std_logic := '0';
		signal in_rst : std_logic := '0';
		signal in_director : std_logic := '0';
		signal in_bit : std_logic := '0';
		signal out_bit : std_logic_vector(3 downto 0) := (others =>'0');
		
	begin
	
	process
	begin
		in_clk <= '1'; wait for CLK_PERIOD / 2;
		in_clk <= '0'; wait for CLK_PERIOD / 2;
		
	end process;
	
	process
	begin
		in_rst <= '0'; wait for  2000 ns;
		in_rst <= '1'; wait for  150 ns;
		in_rst <= '0'; wait for  300 ns;
	end process;
	
	process
	begin
		in_director <= '0'; wait for  350 ns;
		in_director <= '1'; wait for  350 ns;
		in_director <= '1'; wait for  300 ns;
	end process;
	
	process
	begin
		in_bit <= '1'; wait for CLK_PERIOD;
		in_bit <= '0'; wait for CLK_PERIOD;
		in_bit <= '1'; wait for CLK_PERIOD;
		in_bit <= '0'; wait for CLK_PERIOD;
		in_bit <= '1'; wait for 2 * CLK_PERIOD;
		in_bit <= '0'; wait for CLK_PERIOD;
	end process;
	
	generic_kaydirmali_saklayici_map : generic_kaydirmali_saklayici
	port map(
	in_clk 				=> in_clk,
	in_rst 				=> in_rst,
	in_director 		=> in_director,
	in_bit 				=> in_bit,
	out_bit				=> out_bit
	);
end behavioral;
	
	
