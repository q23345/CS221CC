CXX=g++-8
CXXFLAGS=-Wall -Wextra -pedantic -Werror -std=c++17 -O3 -g
LDFLAGS=$(CXXFLAGS)
OBJ=$(SRC:.cc=.o)

all:  test_bitio test_hforest test_huffman test_tree encoder decoder

test_bitio: bitio.o test_bitio.o
	$(CXX) $(LDFLAGS) -o $@ $^

test_tree: test_tree.o tree.o
	$(CXX) $(LDFLAGS) -o $@ $^

test_huffman: test_huffman.o huffman.o hforest.o
	$(CXX) $(LDFLAGS) -o $@ $^

test_hforest: test_hforest.o hforest.o
	$(CXX) $(LDFLAGS) -o $@ $^

encoder: encoder.o bitio.o huffman.o hforest.o htree.o
	$(CXX) $(LDFLAGS) -o $@ $^

decoder: decoder.o  bitio.o huffman.o hforest.o htree.o
	$(CXX) $(LDFLAGS) -o $@ $^

%.o: %.cpp %.h
	$(CXX) $(CXXFLAGS) $(OPTFLAGS) -c -o $@ $<

clean:
	rm -rf *.o test_bitio encoder decoder

test: all
	./test_tree
	./test_hforest
	./test_huffman
	./test_bitio
