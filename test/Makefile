SOURCES := \
	$(wildcard ../include/*) \
	catch.hpp \
	main.cpp \
	delegate_test.cpp \

out/test.exe : $(patsubst %.cpp,out/%.obj,$(filter %.cpp,$(SOURCES)))
	link.exe /nologo /OUT:$@ $+

define cpp_rule
$(patsubst %.cpp,%.obj,out/$(notdir $1)) : $1 $2
	@mkdir out 2>nul & cl.exe /nologo /c /Fo:$$@ $$< /EHsc /I../include
endef

$(foreach cpp,$(filter %.cpp,$(SOURCES)),$(eval $(call cpp_rule,$(cpp),$(filter-out %.cpp,$(SOURCES)))))
