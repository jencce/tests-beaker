# The name of the package under test
PACKAGE_NAME=kernel

# The toplevel namespace within which the test lives.
TOPLEVEL_NAMESPACE=/$(PACKAGE_NAME)

# The version of the test rpm that gets
#  created / submitted
export TESTVERSION=1.0

# The path of the test below the package
RELATIVE_PATH=tracepoints/operational

# The relative path name to the test 
export TEST=$(TOPLEVEL_NAMESPACE)/$(RELATIVE_PATH)

# All files you want bundled into your rpm
FILES=	$(METADATA) \
	runtest.sh  \
	Makefile

clean:
	$(RM) *~ $(METADATA)
	$(RM) rh-tests-kernel*.rpm

run:	$(METADATA)
	@echo "No Build required"
	chmod +x ./runtest.sh
	./runtest.sh

# Include a global make rules file
# Common Variables
TEST_DIR=/mnt/tests$(TEST)
INSTALL_DIR=$(DEST)$(TEST_DIR)
METADATA=testinfo.desc

showmeta: $(METADATA)
	@cat $(METADATA)

$(METADATA):
	touch $(METADATA)
	@echo "Name:		$(TEST)"	> $(METADATA)
	@echo "Description:	Ensure tracepoints are working" >> $(METADATA)
	@echo "Path:		$(TEST_DIR)"	>> $(METADATA)
	@echo "TestVersion:	$(TESTVERSION)"	>> $(METADATA)
	@echo "Releases:        RHELServer5 RHEL6 Fedora16 RHEL7 RedHatEnterpriseLinux7 RedHatEnterpriseLinuxPegas7 RedHatEnterpriseLinuxAlternateArchitectures7 RedHatEnterpriseLinux8" >> $(METADATA)
	@echo "#Architectures:	All"		>> $(METADATA)
	@echo "Destructive:	no"		>> $(METADATA)
	@echo "Confidential:	no"		>> $(METADATA)
	@echo "Priority:	Normal"		>> $(METADATA)
	@echo "Type:		KernelTier1"	>> $(METADATA)
	@echo "Requires:	systemtap"	>> $(METADATA)
	@echo "Requires:        python3-lxml"   >> $(METADATA)
	@echo "repoRequires:    cki_lib"        >> $(METADATA)
	@echo "RunFor:		kernel"		>> $(METADATA)
	@echo "RunFor:		kernel-devel"	>> $(METADATA)
	@echo "RunFor:		systemtap"	>> $(METADATA)
	@echo "License:		GPLv2"		>> $(METADATA)
	@echo "Owner:		Jeff Bastian <jbastian@redhat.com>"	>> $(METADATA)
