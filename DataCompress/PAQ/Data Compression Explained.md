[Data Compression Explained](http://mattmahoney.net/dc/dce.html)



# 4. Modeling
- static or adaptive
    - static, input -> count -> probability distribution -> coding -> output(probability distribution + coded symbols of input)
    - adaptive, using the past inputs predict probability of current symbol, encode it and then update the model

## 4.1. Fixed Order Models
- ???

### 4.1.1. Bytewise Encoding
- 
```c++
const int CONTEXT_SIZE = 1 << (n*8);   // for order n
int count[CONTEXT_SIZE][256] = {{0}};  // symbol counts
int context = 0;                       // last n bytes packed together
  
// Update the model with byte c
void update(int c) {
    ++count[context][c];
    context = (context << 8 | c) % CONTEXT_SIZE;
}
  
// compress byte c
void compress(int c) {
    encode(count[context], c);  // predict and encode
    update(c);
}

// decompress one byte and return it
int decompress() {
    int c = decode(count[context]);
    update(c);
    return c;
}
```