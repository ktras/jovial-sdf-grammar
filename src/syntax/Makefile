all : Jovial.tbl

Main.def : Main.sdf JovialLex.sdf
	pack-sdf -i $< -o $@

Jovial.tbl : Main.def
	sdf2table -i $< -o $@ -m Main

check : Jovial.tbl
	sglri -p Jovial.tbl -i testfile.jov | pp-aterm

cpl : Jovial.tbl
	sglri -p Jovial.tbl -i cpl_testfile.cpl | pp-aterm

clean :
	rm -f *.def *.tbl
