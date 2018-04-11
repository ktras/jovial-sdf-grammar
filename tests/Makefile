SGLRI = sglri
SYNTAX = ../src/syntax

PASSING_TESTS = \
  1_2_3_main-program-module_a.jov    \
  1_2_3_main-program-module_b.jov    \
  1_2_3_program-body_b.jov           \
  1_2_3_program-body_c.jov           \
  2_1_2_1_table_dimension_list_a.jov \
  2_1_2_1_table_dimension_list_b.jov \
  4_9_stop_stmt_a.jov                \
  4_9_stop_stmt_b.jov                \
  4_9_stop_stmt_c.jov                \
  4_10_abort_stmt_a.jov              \
  4_10_abort_stmt_b.jov              \
  4_10_abort_stmt_c.jov              \
  5_1_1_integer-primary.jov

FAILING_TESTS =

all : check

$(SYNTAX)/Fortran.tbl :
	cd $(SYNTAX) ; make ; cd -

check : $(SYNTAX)/Jovial.tbl
	@for file in $(PASSING_TESTS) ; do \
           echo "Running test $$file"; \
           $(SGLRI) -p $(SYNTAX)/Jovial.tbl -i $$file | pp-aterm -o $$file.aterm; \
           if test $$? != 0 ; then \
             echo $$file "		Parsing FAILED!"; \
           fi; \
           diff $$file.aterm saved-aterms/$$file.aterm; \
           if test $$? != 0 ; then \
             echo $$file "		FAILED!"; \
             exit 1; \
           fi; \
        done;

clean :
	rm -f *.aterm
	rm -f *~
