library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity generic_kaydirmali_saklayici is
	generic(
		n_bit : integer := 4
	);
	Port (
		in_clk			:	in std_logic;
		in_rst			:	in std_logic;
		in_director		:	in std_logic;
		in_bit			:	in std_logic;

		out_bit			:	out std_logic_vector(n_bit - 1 downto 0)	
		);
	end generic_kaydirmali_saklayici;

	architecture Behavioral of generic_kaydirmali_saklayici is
		signal r_saklayici : std_logic_vector(n_bit - 1 downto 0) := (others => '0');
		

--------------------------------------------------------------------------------------------------------------------

	function f_sola_kaydir(in_bit : std_logic; in_saklayici : std_logic_vector(n_bit - 1 downto 0))
		return std_logic_vector is
			variable v_saklayici : std_logic_vector(n_bit - 1 downto 0);
		begin
		v_saklayici := in_saklayici;
		for n_i in n_bit -2 downto 0 loop
			v_saklayici(n_i + 1) := v_saklayici (n_i);
		end loop;
		v_saklayici(0) := in_bit;
		return v_saklayici;
	end f_sola_kaydir;

--------------------------------------------------------------------------------------------------------------------

	function f_saga_kaydir(in_bit : std_logic; in_saklayici : std_logic_vector(n_bit - 1 downto 0))
		return std_logic_vector is
			variable v_saklayici : std_logic_vector(n_bit - 1 downto 0);
		begin
		v_saklayici := in_saklayici ;
		for n_i in 1 to n_bit - 1 loop 
			v_saklayici(n_i - 1) := v_saklayici(n_i);
		end loop;
		v_saklayici(n_bit - 1) := in_bit;
		return v_saklayici;
  
	end f_saga_kaydir;
	
----------------------------------------------------------------------------------------------------------------------
	
begin
  
  out_bit <= r_saklayici;
  
process(in_clk, in_rst, in_bit)
 begin
		if in_rst = '1' then
	
		r_saklayici <= (others => '0');
	
	elsif rising_edge(in_clk) then
	
		if in_director = '0' then
			r_saklayici <= f_sola_kaydir(in_bit, r_saklayici);
		elsif in_director = '1' then
			r_saklayici <= f_saga_kaydir(in_bit, r_saklayici);
		end if;
	end if;
end process;

end behavioral;

