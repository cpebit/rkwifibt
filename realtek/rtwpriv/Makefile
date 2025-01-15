INCLUDE = .
RM = rm -f

# compiler flags:
#  -g    adds debugging information to the executable file
#  -Wall turns on most, but not all, compiler warnings
CFLAGS  = -g -Wall -static #-fno-exceptions

TARGET = rtwpriv

ifeq ($(CC),arm-linux-androideabi-g++)
TARGET = rtwpriv_arm
endif
ifeq ($(CC),aarch64-linux-android-g++)
TARGET = rtwpriv_arm64
endif
ifeq ($(CC),i686-linux-android-g++)
TARGET = rtwpriv_x86
endif
ifeq ($(CC),x86_64-linux-android-g++)
TARGET = rtwpriv_x86_64
endif
ifeq ($(CC),mipsel-linux-android-g++)
TARGET = rtwpriv_mips
endif
ifeq ($(CC),mips64el-linux-android-g++)
TARGET = rtwpriv_mips64
endif

ifeq ($(CC),g++)
# the build target executable:
TARGET = rtwpriv
endif

all: $(TARGET)
$(TARGET): rtwpriv.o rtw_api.o rtw_udpsrv.o
		$(CC) $(CFLAGS) -o $(TARGET) rtwpriv.o rtw_api.o rtw_udpsrv.o -lm
		
rtwpriv.o: rtw_api.h rtwpriv.h
	$(CC) -I$(INCLUDE) $(CFLAGS) -c rtwpriv.cpp 

rtw_api.o: rtw_api.h rtwpriv.h
		$(CC) -I$(INCLUDE) $(CFLAGS) -c rtw_api.cpp 

rtw_udpsrv.o:rtw_udpsrv.h
		$(CC) -I$(INCLUDE) $(CFLAGS) -c rtw_udpsrv.cpp

#hwtx.o: rtw_pmact.h
#	$(CC) -I$(INCLUDE) $(CFLAGS) -c hwtx.c

clean:
		$(RM) $(TARGET) *.o rtw_api.o rtw_udpsrv.o
