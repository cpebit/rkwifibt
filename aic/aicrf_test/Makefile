TARGETS := wifi_test bt_test

all: $(TARGETS)

wifi_test: wifi_test.o
	$(CC) $^ -o $@ $(LDFLAGS) $(LDLIBS)

bt_test: bt_test.o
	$(CC) $^ -o $@ $(LDFLAGS) $(LDLIBS) -lpthread

%.o: %.c
	$(CC) -c $< -o $@ $(CPPFLAGS) $(CFLAGS)

clean:
	$(RM) -f $(TARGETS) *.o
