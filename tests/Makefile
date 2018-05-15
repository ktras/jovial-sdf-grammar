SGLRI = sglri
SYNTAX = ../src/syntax

PASSING_TESTS = \
  1_2_2_non-nested-subroutine_a.jov  \
  1_2_2_non-nested-subroutine_b.jov  \
  1_2_2_procedure-module_a.jov       \
  1_2_2_procedure-module_b.jov       \
  1_2_2_procedure-module_c.jov       \
  1_2_2_procedure-module_d.jov       \
  1_2_2_procedure-module_e.jov       \
  1_2_2_procedure-module_f.jov       \
  1_2_2_procedure-module_g.jov       \
  1_2_3_main-program-module_a.jov    \
  1_2_3_main-program-module_b.jov    \
  1_2_3_main-program-module_c.jov    \
  1_2_3_main-program-module_d.jov    \
  1_2_3_program-body_a.jov           \
  1_2_3_program-body_b.jov           \
  1_2_3_program-body_c.jov           \
  1_2_3_program-body_d.jov           \
  1_2_3_program-body_e.jov           \
  1_2_3_program-body_f.jov           \
  1_2_3_program-body_g.jov           \
  1_2_3_program-body_h.jov           \
  2_1_1_6_status_type_desc.jov       \
  2_1_2_1_table_dimension_list_a.jov \
  2_1_2_1_table_dimension_list_b.jov \
  2_3_stmt_name_decl.jov             \
  4_6_return_stmt.jov                \
  4_7_goto_stmt_a.jov                \
  4_8_exit_stmt.jov                  \
  4_9_stop_stmt_a.jov                \
  4_9_stop_stmt_b.jov                \
  4_9_stop_stmt_c.jov                \
  4_10_abort_stmt_a.jov              \
  4_10_abort_stmt_b.jov              \
  4_10_abort_stmt_c.jov              \
  5_0_formula.jov                    \
  5_1_1_integer-factor.jov           \
  5_1_1_integer-formula.jov          \
  5_1_1_integer-precedence.jov       \
  5_1_1_integer-primary.jov          \
  5_1_1_integer-term.jov             \
  8_4_comments.jov

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
