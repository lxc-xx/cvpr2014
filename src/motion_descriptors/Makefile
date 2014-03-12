FLAGS = -D__STDC_CONSTANT_MACROS -O3 -rdynamic
SOURCE_FILES = main.cpp
LIBS = -lc -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_video -lopencv_calib3d -lavcodec -lavformat -lavutil -lswscale  

exe: $(SOURCE_FILES)
	mkdir -p build
	$(CC) $(SOURCE_FILES) -o build/motion_descriptors $(FLAGS) $(LIBS)

clean:
	rm -rf build
