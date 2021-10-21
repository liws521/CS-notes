# The PAQ1 Data Compression Program
- Matthew V. Mahoney
- Florida Tech., CS Dept.
- mmahoney@cs.fit.edu
- Draft, Jan. 20, 2002, revised Mar. 19.

## Abstract
- This paper describes the PAQ1 lossless data compression program. 
- PAQ1 is an arithmetic encoder using a weighted average of five bit-level predictors. 
- The five models are: 
    - (1) a bland model with 0 or 1 equally likely, 
    - (2) a set of order-1 through 8 nonstationary n-gram models, 
    - (3) a string matching model for n-grams longer than 8, 
    - (4) a 
nonstationary word unigram and bigram model for English text, and (5) a positional context model for data with 
fixed length records. Probabilities are weighted roughly by n
2
/tp(0)p(1) where n is the context length, t is the age of 
the training data (number of subsequent events), and p(0) and p(1) are the probabilities of a 0 or 1 (favoring long 
runs of zeros or ones). The aging of training statistics makes the model nonstationary, which gives excellent 
compression for mixed data types. PAQ1 compresses the concatenated Calgary corpus to 1.824 bits per character, 
which is 4.5% better than RK (Taylor, 1999) and 2.9% better than PPMONSTR (Shkarin, 2001), the top programs 
rated by Gilchrist (2001) and Ratushnyak (2001) respectively, although those programs do slightly better on 
homogeneous data.
1. Introduction
The best general purpose lossless compression algorithms are prediction by partial match, or PPM (Bell, Witten, and 
Cleary, 1989) and the Burrows-Wheeler transform, or BWT (Burrows and Wheeler, 1994). These are both 
stationary models, in the sense that the statistics used to estimate the probability (and therefore the code length) of a 
symbol are independent of the age of the training data. However, many types of data are nonstationary, in that newer 
statistics are more reliable. This can be shown by plotting the probability of matching two randomly chosen n-grams 
(sequences of n characters) as a function of t, the distance between them. Table 1 shows the result for Thomas 
Hardy’s Far from the Madding Crowd, which is also book1 from the Calgary corpus (Bell, Witten, and Cleary, 
1989). Probabilities for the 768,771 byte file were estimated for each t by sampling one million random pairs 
separated by t plus or minus 10%.
n t = 1 10 100 1000 104 105
1 2.133 6.450 6.500 6.427 6.411 6.403
2 0.027 0.650 0.734 0.701 0.691 0.689
3 0.016 0.129 0.193 0.166 0.161 0.157
4 0.013 0.045 0.078 0.063 0.056 0.056
5 0.012 0.017 0.037 0.025 0.021 0.021
6 0.011 0.010 0.017 0.011 0.007 0.006
Table 1. Percent probability of matching n consecutive characters separated by t in Far from the Madding Crowd.
The peak at around t = 100 is peculiar to natural language text, and is due to the tendency of words not to repeat in 
close proximity, as in the the. The long range drop off from 100 and 105
is due to the cache effect (Clarkson and 
Robinson, 1997), the tendency of words to be used in topic-specific contexts confined to a portion of the text. This 
effect can be used to improve compression by assigning higher probabilities (and shorter codes) to words that have 
already appeared recently.
The cache effect can be observed in all kinds of data, not just text. For example, the effect can be seen in the DNA 
sequence E.coli from the Canterbury corpus (Arnold and Bell, 1997) large file collection in Table 2. The file 
consists of 4,638,690 bytes from the alphabet a, t, c, and g.
n t = 1 10 100 1000 104 105 106
1 26.263 25.840 25.481 25.183 25.025 25.035 24.989
2 6.760 6.978 6.739 6.541 6.429 6.429 6.355
3 1.903 1.971 1.832 1.719 1.692 1.663 1.677
4 0.566 0.564 0.513 0.461 0.453 0.438 0.441
5 0.146 0.164 0.151 0.124 0.124 0.118 0.116
6 0.030 0.047 0.045 0.034 0.032 0.032 0.033
Table 2. Percent probability of matching n consecutive DNA nucleotides separated by t in E.coli.
The cache effect can be found in 13 of 14 files in the Calgary corpus (all except bib) and in 13 of 14 files in the 
Canterbury corpus regular and large file sets (all except kennedy.xls). Yet neither of the best algorithms, PPM or 
BWT exploit this effect. For example, if the input to be compressed is
 ...can...can...can...cat...cat (1)
then to code the t at the end of the string, PPM would estimate its probability by counting characters in matching 
contexts (ca) with equal weight, regardless of their age. In this example, t occurred previously 1 out of 4 times in 
context ca, so that the next t would be assigned a code approximately -log2 1/4 = 2 bits long (neglecting for the 
moment the possibility of novel characters, such as car).
A BWT compressor sorts the input characters by their contexts prior to compression. For instance, context-sorting 
(1) might produce the sequence tnntn because they are all preceded by ca, and sorting brings them together. The 
exact order depends on the preceding characters (before the ca), and not on their original order, so the model is 
stationary regardless of the compression algorithm used on the transformed input.
Gilchrist’s (2001) Archive Comparison Test (ACT) ranks 165 PC and Macintosh based compression programs 
(including different versions) on various test sets including the 18 file version of the Calgary corpus (adding four 
small text files, paper3 through paper6). The top ranked programs as of July, 2001, from best to worst, are RK 
1.02b5 (Taylor, 1999), RK 1.04 (Taylor, 2000), SBC 0.910 (Mäkinen, 2001), BOA 0.58b (Sutton, 1998), and ACB 
2.00c (Buyanovsky, 1997). Ratushnyak (2001) ranked a smaller number of programs on the Canterbury corpus, and 
found the top three programs as of mid 2001 to be PPMONSTR var. H, PPMD var. H (Shkarin, 2001, 2002), and 
RK 1.02b5. All of these programs give 30-40% better compression than popular programs such as COMPRESS 
(1990), PKZIP (1993), or GZIP (Gailly, 1993), although they are slower and use more memory.
SBC is a BWT compressor. All of the others use PPM (except ACB, which uses associative coding). The PPM 
programs differ in how they compute the probability of novel characters. RK and BOA are based on PPMZ (Bloom, 
1998). PPMZ uses an adaptive second level model to estimate the optimum value as a function of the order, the total 
character count, number of unique characters, and the last one or two bytes of context. RK also models certain 
contexts to improve compression on certain types of data including ASCII text, executables, and 8, 16, and 32 bit 
numeric data. RK and BOA both produces solid archives, using the statistics from one file to improve compression 
on another. They perform an analysis to determine the optimal ordering prior to compression.
PPMD and PPMONSTR are based on PPMII, or PPM with information inheritance (Shkarin 2002). PPMII, like 
PPMZ, uses a secondary escape model. Unlike PPMZ and most other PPM models, which uses statistics from the 
longest matching context, PPMII inherits the statistics of shorter contexts to set the initial estimate when a longer 
context is encountered for the first time. This has the effect of including statistics from contexts shorter than the 
longest match. PPMONSTR is a variation of PPMD that gives better compression at the cost of execution speed. 
The maximum order (longest possible context) is 16 for PPMD and 64 for PPMONSTR.
ACB uses associative coding. The input is sorted by context, as in BWT, but instead of compressing the transform, 
the context-sorted data is used to build a permuted index (but sorted reading backwards) which grows as data is read 
in. Suppose that the input string is cx, where c is the part already encoded (the context), and x is the remaining input. 
To encode x, we look up both c and x in the permuted index, matching as many characters as possible of c reading 
left and x reading right. Often, the best two matches are at the same place in the index, or separated by some small 
distance, L. Suppose the best match reading to the right is n characters, x0x1...xn-1. Then we encode the next n + 1 
characters x0x1...xn as the triple (L, n, xn). Associative coding is stationary because the context sorting loses the 
relative position of the context, as with BWT.
Popular, fast compression programs such as COMPRESS, PKZIP, and GZIP use Ziv-Lempel (LZ) compression 
(Bell, Witten, and Cleary, 1989). In the LZ77 variant (used by GZIP), strings that occur more than once are replaced 
with pointers (offset and length) to previous occurrences. This exploits the cache effect because closer strings can be 
encoded using fewer bits for the offset, corresponding to a higher probability. However, LZ77 wastes code space 
whenever a string could be coded in more than one way. For example, the third occurrence of can in (1) could be 
coded as a pointer to either the first or the second occurrence, and we need some space to encode this arbitrary 
choice. LZ78 (used by COMPRESS) eliminates this redundancy by building a dictionary and coding repeat strings 
as pointers to dictionary entries. (Thus, it is stationary). This does not entirely eliminate redundancy because we 
could still find more than one encoding by choosing different token boundaries. For instance, we could encode can
using three pointers to three one-character entries. Although COMPRESS, PKZIP, and GZIP compression is 
relatively poor, part of the reason is that they sacrifice compression for speed and memory economy. (ACB also 
codes redundantly, but still achieves good compression). The top compressors use large amounts of memory (16-64 
MB or more) and are many times slower.
The rest of this paper is organized as follows. In section 2, we describe the architecture of the PAQ1 archiver, a bitlevel predictor using a weighted combination of models and an arithmetic encoder. In sections 3 through 6, we 
describe four model components: a nonstationary order-8 n-gram model, a long string matcher for n > 8, a word 
bigram model for English ASCII text, and a fixed length record model. In section 7, we compare PAQ1 with top 
ranked compression programs. In section 8, we isolate the effects of the PAQ1 components. In section 9, we 
summarize and suggest future directions.
2. The PAQ1 Architecture
PAQ1 is a predictive arithmetic encoder, like PPM, except that it uses a binary alphabet to simplify encoding and
model merging. The idea is to encode an input string s as a binary number x such that for any randomly chosen 
string r,
 p(r < s) ≤ x < p(r ≤ s) (2)
assuming some ordering over the strings. The range of x satisfying (2) has magnitude p(s), thus we can always 
encode a number that satisfies the inequality with at most log2 p(s) + 1 bits, which is within one bit of the Shannon 
limit (Shannon and Weaver, 1949). 
Howard and Viller (1992) describe efficient methods for encoding x in O(|s|) time, where |s| is the length of s in bits. 
The method used by PAQ1 is to estimate p(s) one bit at a time as the product of the conditional probabilities 
p(s1)p(s2|s1)p(s3|s1s2)...p(sn|s1s2s3...sn-1). We keep track of the range of x satisfying (2), initially [0,1), and as each bit 
is predicted, we divide the range into two parts in proportion to p(0) and p(1). Then when the bit is input, we the 
corresponding segment becomes the new range. When the range becomes sufficiently narrow that the leading base256 digits become known (because they are the same for the lower and upper bound), then they are output. The 
point where the range is split is rounded so that only 4 digits (32 bits) of the bounds need to be kept in memory. In 
practice, this rounding adds less than 0.0002 bits per character to the compressed output.
The advantage of using bit prediction is that it allows models that specialize in different types of data to be integrated 
by using a weighted combination of their predictions. In PAQ1 there are five models, each outputting a probability 
and a confidence. This is represented as a pair of non-negative counts, c0 and c1, which expresses the idea that the 
probability that the next bit will be a 1 is p(1) = c1/c with confidence (weight) c, where c = c0 + c1. Equivalently, it 
represents a set of c independent experiments in which 0 occurred c0 times and 1 occurred c1 times. The models are 
combined simply by adding their counts, i.e. p(1) = Σ c1 / Σ c with the summation over the models.
Because it is possible to have p(1) = 0 or p(1) = 1, which would imply an infinitely long code if the opposite bit 
actually occurs, we include a bland model to ensure that this does not happen. The bland model is c0 = 1 and c1 = 1, 
which expresses p(1) = 1/2 with confidence 2. The bland model by itself neither compresses nor expands the input.
3. The Nonstationary n-gram Model
PAQ1 guesses the next bit of input by finding a sequence of matching contexts in the input and recording the 
sequence of bits that followed. An n-gram model, with n = 1 through 8, consists of the previous n - 1 whole bytes of 
context, plus the 0 to 7 bits of the partially read byte. For example, suppose we wish to estimate p(1) for the fourth 
bit of the final t in cat in (1). The 3-gram context is ca,011, consisting of the last n - 1 = 2 whole characters, plus the 
bits read so far. This context occurs four times prior to the current occurrence (both n and t begin with the bits 011). 
In the first three occurrences (can), the next bit is 0. In the fourth (cat), the next bit is 1. Thus, the next-bit history in 
this context is 0001.
The next question is what to do with this history. As mentioned, PPM, BWT, and associative coding models would 
assume that the outcomes are stationary and independent, and weight all bits equally for p(1) = 1/4. However, from 
section 1 we saw that the most recent data ought to be given greater weight. Some possibilities are: 