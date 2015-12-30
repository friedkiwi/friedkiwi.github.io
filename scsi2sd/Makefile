
TITLE=SCSI2SD
MARKDOWN=markdown
SOURCES=index.md
OBJECTS=$(SOURCES:.md=.html)


$(OBJECTS):
	$(MARKDOWN) $(OBJECTS:.html=.md) -t $(TITLE) $< > $@


clean:
	rm *.html

all: $(SOURCES) $(OBJECTS)
