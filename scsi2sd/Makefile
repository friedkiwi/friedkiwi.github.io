
TITLE=SCSI2SD
MARKDOWN=markdown
SOURCES=index.md
OBJECTS=$(SOURCES:.md=.html)

$(OBJECTS):
	$(MARKDOWN) $(OBJECTS:.html=.md) -t $(TITLE) $< > $@
	git add $(OBJECTS:.html=.md) $@

clean:
	rm *.html

push:
	git commit
	git push


all:  $(OBJECTS)
