PROJNAME_MAIN := "Quick-Practice-Presentation"
PROJ_DIR := $(shell pwd)
MAIN_SRC := main.tex
SLIDES_SRC := slides.tex
PREAMBLES := $(shell find $(PROJ_DIR) -name '*preamble.tex') 
DOC_TARGET_MAIN := $(PROJNAME_MAIN).pdf
GRAPHICS_DIR := "$(PROJ_DIR)/graphics"

.PHONY: all clean cleanall git 

all: $(DOC_TARGET_MAIN) 

$(DOC_TARGET_MAIN): $(MAIN_SRC) $(PREAMBLES) $(SLIDES_SRC) titleauthordate.tex
	latexmk -pdf -halt-on-error -use-make -jobname=$(PROJNAME_MAIN) $(MAIN_SRC)

cleanall:
	latexmk -C -jobname=$(PROJNAME_MAIN) $(MAIN_SRC)
	rm -rvf *~ $(GRAPHICS_DIR)/{*.pgf,*~}
clean:
	latexmk -c -jobname=$(PROJNAME_MAIN) $(MAIN_SRC)
	rm -vrf *~ $(GRAPHICS_DIR)/*~

git: all
	git add $(PROJ_DIR)
	git commit -a
	git push -u
