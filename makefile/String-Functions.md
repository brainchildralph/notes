

### Makefile字串函式的用法
```
字符串處理函數
$(subst <from>,<to>,<text>)
名稱：字符串替換函數——subst。
功能：把字串<text>中的<from>字符串替換成<to>。
返回：函數返回被替換過後的字符串。
示例：

$(subst ee,EE,feet on the street)，
把「feet on the street」中的「ee」替換成「EE」，返回結果是「fEEt on the strEEt」。
$(patsubst <pattern>,<replacement>,<text>)
名稱：模式字符串替換函數——patsubst。
功能：查找<text>中的單詞（單詞以「空格」、「Tab」或「回車」「換行」分隔）是否符合模式<pattern>，如果匹配的話，則以<replacement>替換。這裡，<pattern>可以包括通配符「%」，表示任意長度的字串。如果<replacement>中也包含「%」，那麼，<replacement>中的這個「%」將是<pattern>中的那個「%」所代表的字串。（可以用「」來轉義，以「%」來表示真實含義的「%」字符）
返回：函數返回被替換過後的字符串。
示例：
$(patsubst %.c,%.o,x.c.c bar.c)
把字串「x.c.c bar.c」符合模式[%.c]的單詞替換成[%.o]，返回結果是「x.c.o bar.o」
備註：
這和我們前面「變量章節」說過的相關知識有點相似。如：
「$(var:<pattern>=<replacement>)」
相當於
「$(patsubst <pattern>,<replacement>,$(var))」，
而「$(var: <suffix>=<replacement>)」
則相當於
「$(patsubst %<suffix>,%<replacement>,$(var))」。
例如有：objects = foo.o bar.o baz.o，
那麼，「$(objects:.o=.c)」和「$(patsubst %.o,%.c,$(objects))」是一樣的。
$(strip <string>)
名稱：去空格函數——strip。
功能：去掉<string>字串中開頭和結尾的空字符。
返回：返回被去掉空格的字符串值。
示例：
$(strip a b c )
把字串「a b c 」去到開頭和結尾的空格，結果是「a b c」。
$(findstring <find>,<in>)
名稱：查找字符串函數——findstring。
功能：在字串<in>中查找<find>字串。
返回：如果找到，那麼返回<find>，否則返回空字符串。
示例：
$(findstring a,a b c)
$(findstring a,b c)
第一個函數返回「a」字符串，第二個返回「」字符串（空字符串）
$(filter <pattern...>,<text>)
名稱：過濾函數——filter。
功能：以<pattern>模式過濾<text>字符串中的單詞，保留符合模式<pattern>的單詞。可以有多個模式。
返回：返回符合模式<pattern>的字串。
示例：
sources := foo.c bar.c baz.s ugh.h
foo: $(sources)
cc $(filter %.c %.s,$(sources)) -o foo
$(filter %.c %.s,$(sources))返回的值是「foo.c bar.c baz.s」。
$(filter-out <pattern...>,<text>)
名稱：反過濾函數——filter-out。
功能：以<pattern>模式過濾<text>字符串中的單詞，去除符合模式<pattern>的單詞。可以有多個模式。
返回：返回不符合模式<pattern>的字串。
示例：
objects=main1.o foo.o main2.o bar.o
mains=main1.o main2.o
$(filter-out $(mains),$(objects)) 返回值是「foo.o bar.o」。
$(sort <list>)
名稱：排序函數——sort。
功能：給字符串<list>中的單詞排序（升序）。
返回：返回排序後的字符串。
示例：$(sort foo bar lose)返回「bar foo lose」 。
備註：sort函數會去掉<list>中相同的單詞。
$(word <n>,<text>)
名稱：取單詞函數——word。
功能：取字符串<text>中第<n>個單詞。（從一開始）
返回：返回字符串<text>中第<n>個單詞。如果<n>比<text>中的單詞數要大，那麼返回空字符串。
示例：$(word 2, foo bar baz)返回值是「bar」。
$(wordlist <s>,<e>,<text>)
名稱：取單詞串函數——wordlist。
功能：從字符串<text>中取從<s>開始到<e>的單詞串。<s>和<e>是一個數字。
返回：返回字符串<text>中從<s>到<e>的單詞字串。如果<s>比<text>中的單詞數要大，那麼返回空字符串。如果<e>大於<text>的單詞數，那麼返回從<s>開始，到<text>結束的單詞串。
示例： $(wordlist 2, 3, foo bar baz)返回值是「bar baz」。
$(words <text>)
名稱：單詞個數統計函數——words。
功能：統計<text>中字符串中的單詞個數。
返回：返回<text>中的單詞數。
示例：$(words, foo bar baz)返回值是「3」。
備註：如果我們要取<text>中最後的一個單詞，我們可以這樣：$(word $(words <text>),<text>)。
$(firstword <text>)
名稱：首單詞函數——firstword。
功能：取字符串<text>中的第一個單詞。
返回：返回字符串<text>的第一個單詞。
示例：$(firstword foo bar)返回值是「foo」。
備註：這個函數可以用word函數來實現：$(word 1,<text>)。
以上，是所有的字符串操作函數，如果搭配混合使用，可以完成比較複雜的功能。這裡，舉一個現實中應用的例子。我們知道，make使用「VPATH」變量來指定「依賴文件」的搜索路徑。於是，我們可以利用這個搜索路徑來指定編譯器對頭文件的搜索路徑參數CFLAGS，如：
override CFLAGS += $(patsubst %,-I%,$(subst :, ,$(VPATH)))
如果我們的「$(VPATH)」值是「src:../headers」，那麼「$(patsubst %,-I%,$(subst :, ,$(VPATH)))」將返回「-Isrc -I../headers」，這正是cc或gcc搜索頭文件路徑的參數。
三、文件名操作函數
下面我們要介紹的函數主要是處理文件名的。每個函數的參數字符串都會被當做一個或是一系列的文件名來對待。
$(dir <names...>)
名稱：取目錄函數——dir。
功能：從文件名序列<names>中取出目錄部分。目錄部分是指最後一個反斜槓（「/」）之前的部分。如果沒有反斜槓，那麼返回「./」。
返回：返回文件名序列<names>的目錄部分。
示例： $(dir src/foo.c hacks)返回值是「src/ ./」。
$(notdir <names...>)
名稱：取文件函數——notdir。
功能：從文件名序列<names>中取出非目錄部分。非目錄部分是指最後一個反斜槓（「/」）之後的部分。
返回：返回文件名序列<names>的非目錄部分。
示例： $(notdir src/foo.c hacks)返回值是「foo.c hacks」。 
$(suffix <names...>)
名稱：取後綴函數——suffix。
功能：從文件名序列<names>中取出各個文件名的後綴。
返回：返回文件名序列<names>的後綴序列，如果文件沒有後綴，則返回空字串。
示例：$(suffix src/foo.c src-1.0/bar.c hacks)返回值是「.c .c」。
$(basename <names...>)
名稱：取前綴函數——basename。
功能：從文件名序列<names>中取出各個文件名的前綴部分。
返回：返回文件名序列<names>的前綴序列，如果文件沒有前綴，則返回空字串。
示例：$(basename src/foo.c src-1.0/bar.c hacks)返回值是「src/foo src-1.0/bar hacks」。
$(addsuffix <suffix>,<names...>)
名稱：加後綴函數——addsuffix。
功能：把後綴<suffix>加到<names>中的每個單詞後面。
返回：返回加過後綴的文件名序列。
示例：$(addsuffix .c,foo bar)返回值是「foo.c bar.c」。
$(addprefix <prefix>,<names...>)
名稱：加前綴函數——addprefix。
功能：把前綴<prefix>加到<names>中的每個單詞後面。
返回：返回加過前綴的文件名序列。
示例：$(addprefix src/,foo bar)返回值是「src/foo src/bar」。
$(join <list1>,<list2>)
名稱：連接函數——join。
功能：把<list2>中的單詞對應地加到<list1>的單詞後面。如果<list1>的單詞個數要比<list2>的多，那麼，<list1>中的多出來的單詞將保持原樣。如果<list2>的單詞個數要比<list1>多，那麼，<list2>多出來的單詞將被複製到<list2>中。
返回：返回連接過後的字符串。
示例：$(join aaa bbb , 111 222 333)返回值是「aaa111 bbb222 333
```
