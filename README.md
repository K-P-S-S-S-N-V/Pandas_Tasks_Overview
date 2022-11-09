<div align="center">
  <h1><code>Pandas an Python Library Beginner Tasks</code></h1>

  <p>
    <strong>Pandas Module
    <a href="https://www.guvi.in/">By GUVI _ Greek Networks</a></strong>
  </p>

  <strong>A <a href="https://pandas.pydata.org/"> Pandas </a> project Q/A</strong>

  <h3>
    <a href="https://pandas.pydata.org/docs/user_guide/index.html"> A Pandas User Guide by pandas.pydata.org</a>
    <span>  </span>
   
  </h3>
</div>

# Importing pandas

### Getting started and checking your pandas setup

1. Import pandas under the name pd.
```python
import pandas as pd
```
2. Print the version of pandas that has been imported.
```python
pd.__version__
```
Output:
```
1.3.5
```
3. Print out all the version information of the libraries that are required by the pandas library.
```python
pd.show_versions()
```
Output:
```
INSTALLED VERSIONS
------------------
commit           : 66e3805b8cabe977f40c05259cc3fcf7ead5687d
python           : 3.7.15.final.0
python-bits      : 64
OS               : Linux
OS-release       : 5.10.133+
Version          : #1 SMP Fri Aug 26 08:44:51 UTC 2022
machine          : x86_64
processor        : x86_64
byteorder        : little
LC_ALL           : None
LANG             : en_US.UTF-8
LOCALE           : en_US.UTF-8

pandas           : 1.3.5
numpy            : 1.21.6
pytz             : 2022.6
dateutil         : 2.8.2
pip              : 21.1.3
setuptools       : 57.4.0
Cython           : 0.29.32
pytest           : 3.6.4
hypothesis       : None
sphinx           : 1.8.6
blosc            : None
feather          : 0.4.1
xlsxwriter       : None
lxml.etree       : 4.9.1
html5lib         : 1.0.1
pymysql          : None
psycopg2         : 2.9.5 (dt dec pq3 ext lo64)
jinja2           : 2.11.3
IPython          : 7.9.0
pandas_datareader: 0.9.0
bs4              : 4.6.3
bottleneck       : None
fsspec           : 2022.10.0
fastparquet      : None
gcsfs            : None
matplotlib       : 3.2.2
numexpr          : 2.8.4
odfpy            : None
openpyxl         : 3.0.10
pandas_gbq       : 0.13.3
pyarrow          : 6.0.1
pyxlsb           : None
s3fs             : None
scipy            : 1.7.3
sqlalchemy       : 1.4.42
tables           : 3.7.0
tabulate         : 0.8.10
xarray           : 0.20.2
xlrd             : 1.1.0
xlwt             : 1.3.0
numba            : 0.56.4
```
# DataFrame basics
## A few of the fundamental routines for selecting, sorting, adding and aggregating data in DataFrames
### Consider the following Python dictionary data and Python list labels:
4. Create a DataFrame df from this dictionary data which has the index labels.
```python
import pandas as pd

data = {'animal': ['cat', 'cat', 'snake', 'dog', 'dog', 'cat', 'snake', 'cat', 'dog', 'dog'],
        'age': [2.5, 3, 0.5, "np.nan", 5, 2, 4.5, "np.nan", 7, 3],
        'visits': [1, 3, 2, 3, 2, 3, 1, 1, 2, 1],
        'priority': ['yes', 'yes', 'no', 'yes', 'no', 'no', 'no', 'yes', 'no', 'no']}

labels = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
df=pd.DataFrame(data,index=labels)
```
```python
print(df)
```
Output:
```
  animal     age  visits priority
a    cat     2.5       1      yes
b    cat       3       3      yes
c  snake     0.5       2       no
d    dog  np.nan       3      yes
e    dog       5       2       no
f    cat       2       3       no
g  snake     4.5       1       no
h    cat  np.nan       1      yes
i    dog       7       2       no
j    dog       3       1       no
```
5. Display a summary of the basic information about this DataFrame and its data.
```python
print(df.info())
```
Output:
```
<class 'pandas.core.frame.DataFrame'>
Index: 10 entries, a to j
Data columns (total 4 columns):
 #   Column    Non-Null Count  Dtype 
---  ------    --------------  ----- 
 0   animal    10 non-null     object
 1   age       10 non-null     object
 2   visits    10 non-null     int64 
 3   priority  10 non-null     object
dtypes: int64(1), object(3)
memory usage: 400.0+ bytes
None
```
6. Return the first 3 rows of the DataFrame df.
```python
df.head(3)
```
Output:
```
	animal	age	visits	priority
a	cat	2.5	1	yes
b	cat	3	3	yes
c	snake	0.5	2	no
```
7. Select just the 'animal' and 'age' columns from the DataFrame df.
```python
my_columns=["animal","age"]
df[my_columns]
```
Output:
```
animal	age
a	cat	2.5
b	cat	3
c	snake	0.5
d	dog	np.nan
e	dog	5
f	cat	2
g	snake	4.5
h	cat	np.nan
i	dog	7
j	dog	3
```
8. Select the data in rows [3, 4, 8] and in columns ['animal', 'age'].
```python
my_columns=["animal","age"]
df[my_columns]
df.loc[["d","e","i"]]
```
Output:
```
	animal	age	visits	priority
d	dog	np.nan	3	yes
e	dog	5	2	no
i	dog	7	2	no
```
9. Select only the rows where the number of visits is greater than 3.
```python
df[df['visits']>3]
```
Output:
```
	animal	age	visits	priority
```
10. Select the rows where the age is missing, i.e. is NaN.
```python
df[df['age'].isnull()]
```
Output:
```
animal	age	visits	priority
d	dog	NaN	3	yes
h	cat	NaN	1	yes
```
11. Select the rows where the animal is a cat and the age is less than 3.
```python
df[(df['animal']=='cat') & (df['age']<3)]
```
Output:
```
	animal	age	visits	priority
a	cat	2.5	1	yes
f	cat	2.0	3	no
```
12. Select the rows the age is between 2 and 4 (inclusive).
```python
df[(df['age']<=4)&(df['age']>=2)]
```
Output:
```
animal	age	visits	priority
```
13. Change the age in row 'f' to 1.5.
```python
df.loc['f', 'age'] = 1.5
print(df)
```
Output:
```
  animal     age  visits priority
a    cat     2.5       1      yes
b    cat       3       3      yes
c  snake     0.5       2       no
d    dog  np.nan       3      yes
e    dog       5       2       no
f    cat     1.5       3       no
g  snake     4.5       1       no
h    cat  np.nan       1      yes
i    dog       7       2       no
j    dog       3       1       no
```
14. Calculate the sum of all visits (the total number of visits).
```python
df['visits'].sum()
```
Output:
```
19
```
15. Calculate the mean age for each different animal in df.
```python
df['visits'].mean()
```
Output:
```
1.9
```
16. Append a new row 'k' to df with your choice of values for each column. Then delete that row to return the original DataFrame.
```python
df.loc['k'] = ['cat', '3', '2', 'no']
print("Print all records after insert a new row:")
print(df)
```
Output:
```
Print all records after insert a new row:
  animal     age visits priority
a    cat     2.5      1      yes
b    cat       3      3      yes
c  snake     0.5      2       no
d    dog  np.nan      3      yes
e    dog       5      2       no
f    cat     1.5      3       no
g  snake     4.5      1       no
h    cat  np.nan      1      yes
i    dog       7      2       no
j    dog       3      1       no
k    cat       3      2       no
```
```python
print("\nDelete the new row and display the original  rows:")
df = df.drop('k')
print(df)
```
Output:
```
Delete the new row and display the original  rows:
  animal     age visits priority
a    cat     2.5      1      yes
b    cat       3      3      yes
c  snake     0.5      2       no
d    dog  np.nan      3      yes
e    dog       5      2       no
f    cat     1.5      3       no
g  snake     4.5      1       no
h    cat  np.nan      1      yes
i    dog       7      2       no
j    dog       3      1       no
```
17. Count the number of each type of animal in df.
```python
df.groupby('animal').count()
```
Output:
```
	   age	   visits   	priority
animal			
cat 	4	        4	        4
dog	  4      	  4        	4
snake	2	        2       	2
```
18. Sort df first by the values in the 'age' in decending order, then by the value in the 'visit' column in ascending order.
```python
df.sort_values('age', ascending=False)
```
Output:
```
	animal	age	visits	priority
i	dog   	7.0	  2     	no
e	dog	    5.0  	2     	no
g	snake	  4.5	  1	      no
b	cat   	3.0	  3	      yes
j	dog	    3.0	  1	      no
a	cat   	2.5 	1     	yes
f	cat    	1.5	  3     	no
c	snake  	0.5  	2	      no
d	dog   	NaN 	3	     yes
h	cat	    NaN	  1      yes
```
```python
df.sort_values('visits', ascending=True)
```
Output:
```
animal	age	visits	priority
a	cat	  2.5	  1	     yes
g	snake	4.5	  1     	no
h	cat	 np.nan	1	     yes
j	dog	  3	    1	      no
c	snake	0.5	  2	      no
e	dog	  5	    2     	no
i	dog	  7	    2     	no
b	cat	  3	    3	     yes
d	dog	 np.nan	3	     yes
f	cat	  1.5	  3	      no
```
19. The 'priority' column contains the values 'yes' and 'no'. Replace this column with a column of boolean values: 'yes' should be True and 'no' should be False.
```python
df['priority'] = df['priority'].map(
                   {'yes':True ,'no':False})
Print(df)
```
Output:
```
	animal	age	visits	priority
a	cat	    2.5	  1	     True
b	cat	     3	  3      True
c	snake	  0.5  	2	     False
d	dog	   np.nan	3	     True
e	dog	    5	    2	     False
f	cat	    1.5	  3	     False
g	snake	  4.5	  1	     False
h	cat	   np.nan	1	     True
i	dog   	7	    2	     False
j	dog	    3	    1	     False
```
```python
df = df.replace({'priority': {'yes': True, 
                                'no': False}})
print(df)
```
Output:
```
	animal	age	visits	priority
a	cat   	2.5	  1	     True
b	cat	    3.0	  3	     True
c	snake	  0.5	  2	     False
d	dog	    NaN	  3	     True
e	dog	    5.0	  2	     False
f	cat	    1.5	  3	     False
g	snake	  4.5	  1	     False
h	cat   	NaN	  1	     True
i	dog	    7.0	  2	     False
j	dog	    3.0	  1	     False
```
20. In the 'animal' column, change the 'snake' entries to 'python'.
```python
df = df.replace({'animal': {'snake': 'python'}})
print(df)
```
Output:
```
	animal	age	visits	priority
a	cat    	2.5	   1	   True
b	cat	     3	   3	   True
c	python	0.5	   2	   False
d	dog	   np.nan	 3	   True
e	dog	     5	   2     False
f	cat	    1.5	   3	   False
g	python	4.5	   1	   False
h	cat	   np.nan	 1	   True
i	dog	     7	   2     False
j	dog	     3	   1     False
```
21. For each animal type and each number of visits, find the mean age. In other words, each row is an animal, each column is a number of visits and the values are the mean ages (hint: use a pivot table).
```python
mean=df.pivot_table(index="animal", columns="visits", aggfunc="mean")["age"]
```
Output:
```
 Input In [6]
    mean=df.pivot_table(index="animal", columns="visits", aggfunc="mean")["age"]
    ^
IndentationError: unexpected indent
```
















```sh
curl https://wasmtime.dev/install.sh -sSf | bash
```

Windows or otherwise interested users can download installers and
binaries directly from the [GitHub
Releases](https://github.com/bytecodealliance/wasmtime/releases) page.

## Example

If you've got the [Rust compiler
installed](https://www.rust-lang.org/tools/install) then you can take some Rust
source code:

```rust
fn main() {
    println!("Hello, world!");
}
```

and compile/run it with:

```sh
$ rustup target add wasm32-wasi
$ rustc hello.rs --target wasm32-wasi
$ wasmtime hello.wasm
Hello, world!
```

## Features

* **Fast**. Wasmtime is built on the optimizing [Cranelift] code generator to
  quickly generate high-quality machine code either at runtime or
  ahead-of-time. Wasmtime is optimized for efficient instantiation, low-overhead
  calls between the embedder and wasm, and scalability of concurrent instances.

* **[Secure]**. Wasmtime's development is strongly focused on correctness and
  security. Building on top of Rust's runtime safety guarantees, each Wasmtime
  feature goes through careful review and consideration via an [RFC
  process]. Once features are designed and implemented, they undergo 24/7
  fuzzing donated by [Google's OSS Fuzz]. As features stabilize they become part
  of a [release][release policy], and when things go wrong we have a
  well-defined [security policy] in place to quickly mitigate and patch any
  issues. We follow best practices for defense-in-depth and integrate
  protections and mitigations for issues like Spectre. Finally, we're working to
  push the state-of-the-art by collaborating with academic researchers to
  formally verify critical parts of Wasmtime and Cranelift.

* **[Configurable]**. Wasmtime uses sensible defaults, but can also be
  configured to provide more fine-grained control over things like CPU and
  memory consumption. Whether you want to run Wasmtime in a tiny environment or
  on massive servers with many concurrent instances, we've got you covered.

* **[WASI]**. Wasmtime supports a rich set of APIs for interacting with the host
  environment through the [WASI standard](https://wasi.dev).

* **[Standards Compliant]**. Wasmtime passes the [official WebAssembly test
  suite](https://github.com/WebAssembly/testsuite), implements the [official C
  API of wasm](https://github.com/WebAssembly/wasm-c-api), and implements
  [future proposals to WebAssembly](https://github.com/WebAssembly/proposals) as
  well. Wasmtime developers are intimately engaged with the WebAssembly
  standards process all along the way too.

[Wasmtime]: https://github.com/bytecodealliance/wasmtime
[Cranelift]: https://github.com/bytecodealliance/wasmtime/blob/main/cranelift/README.md
[Google's OSS Fuzz]: https://google.github.io/oss-fuzz/
[security policy]: https://bytecodealliance.org/security
[RFC process]: https://github.com/bytecodealliance/rfcs
[release policy]: https://docs.wasmtime.dev/stability-release.html
[Secure]: https://docs.wasmtime.dev/security.html
[Configurable]: https://docs.rs/wasmtime/latest/wasmtime/struct.Config.html
[WASI]: https://docs.rs/wasmtime-wasi/latest/wasmtime_wasi/
[Standards Compliant]: https://docs.wasmtime.dev/stability-wasm-proposals-support.html

## Language Support

You can use Wasmtime from a variety of different languages through embeddings of
the implementation:

* **[Rust]** - the [`wasmtime` crate]
* **[C]** - the [`wasm.h`, `wasi.h`, and `wasmtime.h` headers][c-headers], [CMake](crates/c-api/CMakeLists.txt) or [`wasmtime` Conan package]
* **C++** - the [`wasmtime-cpp` repository][wasmtime-cpp] or use [`wasmtime-cpp` Conan package]
* **[Python]** - the [`wasmtime` PyPI package]
* **[.NET]** - the [`Wasmtime` NuGet package]
* **[Go]** - the [`wasmtime-go` repository]

[Rust]: https://bytecodealliance.github.io/wasmtime/lang-rust.html
[C]: https://bytecodealliance.github.io/wasmtime/examples-c-embed.html
[`wasmtime` crate]: https://crates.io/crates/wasmtime
[c-headers]: https://bytecodealliance.github.io/wasmtime/c-api/
[Python]: https://bytecodealliance.github.io/wasmtime/lang-python.html
[`wasmtime` PyPI package]: https://pypi.org/project/wasmtime/
[.NET]: https://bytecodealliance.github.io/wasmtime/lang-dotnet.html
[`Wasmtime` NuGet package]: https://www.nuget.org/packages/Wasmtime
[Go]: https://bytecodealliance.github.io/wasmtime/lang-go.html
[`wasmtime-go` repository]: https://pkg.go.dev/github.com/bytecodealliance/wasmtime-go
[wasmtime-cpp]: https://github.com/bytecodealliance/wasmtime-cpp
[`wasmtime` Conan package]: https://conan.io/center/wasmtime
[`wasmtime-cpp` Conan package]: https://conan.io/center/wasmtime-cpp

## Documentation

[📚 Read the Wasmtime guide here! 📚][guide]

The [wasmtime guide][guide] is the best starting point to learn about what
Wasmtime can do for you or help answer your questions about Wasmtime. If you're
curious in contributing to Wasmtime, [it can also help you do
that][contributing]!

[contributing]: https://bytecodealliance.github.io/wasmtime/contributing.html
[guide]: https://bytecodealliance.github.io/wasmtime

---

It's Wasmtime.
