LIBCURL_CFLAGS := $(shell pkg-config --cflags libcurl)
LIBCURL_LDFLAGS := $(shell pkg-config --libs libcurl)

LIBOPENSSL_CFLAGS := $(shell pkg-config --cflags openssl)
LIBOPENSSL_LDFLAGS := $(shell pkg-config --libs openssl)

CFLAGS ?= -Wall -Wextra -O1

LIBS_CFLAGS := $(LIBCURL_CFLAGS) $(LIBOPENSSL_CFLAGS)
LIBS_LDFLAGS := $(LIBCURL_LDFLAGS) $(LIBOPENSSL_LDFLAGS)

.PHONY: all clean

all: curl-websocket autobahn-testee

curl-websocket: main.c curl-websocket.c curl-websocket-utils.c Makefile
	$(CC) $(CFLAGS) $(LIBS_CFLAGS) main.c curl-websocket.c -o $@ $(LIBS_LDFLAGS)

autobahn-testee: autobahn-testee.c curl-websocket.c curl-websocket-utils.c Makefile
	$(CC) $(CFLAGS) $(LIBS_CFLAGS) autobahn-testee.c curl-websocket.c -o $@ $(LIBS_LDFLAGS)

clean:
	rm -f curl-websocket autobahn-testee
