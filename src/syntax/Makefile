all : Jovial.tbl

Main.def : Main.sdf JovialLex.sdf
	pack-sdf -i $< -o $@

Jovial.tbl : Main.def
	sdf2table -i $< -o $@ -m Main

check :
	sglri -p Jovial.tbl -i testfile.jov | pp-aterm

clean :
	rm -f *.def *.tbl
