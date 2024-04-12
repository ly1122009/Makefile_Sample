DEBUG = 1
INCLUDE_DIR = inc
SOURCE_DIR = src
BUILD_DIR = obj

CXX_STANDARD = 
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = gcc
CXXFLAGS = $(CXX_WARNINGS) $(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug.exe
else
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease.exe
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.c)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.c, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

##############
## TARGETS  ##
##############
create:
	@mkdir -p obj

build: create $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_NAME)
	rm -rf $(BUILD_DIR)

##############
## PATTERNS ##
##############
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.c
	$(CXX_COMPILER_CALL) -c $< -o $@