[TOC]

## General

### List

- [Algorithm Notes 1 字符串](https://blog.csdn.net/bzjr_Log_x/article/details/125566832?spm=1001.2014.3001.5501)
- [Algorithm Notes 2 数据结构](https://blog.csdn.net/bzjr_Log_x/article/details/126081807?spm=1001.2014.3001.5501)
- [Algorithm Notes 3 数论](https://blog.csdn.net/bzjr_Log_x/article/details/126081730?spm=1001.2014.3001.5501)
- [Algorithm Notes 4 动态规划 计算几何](https://blog.csdn.net/bzjr_Log_x/article/details/126081867?spm=1001.2014.3001.5501)
- [Algorithm Notes 5 图论](https://blog.csdn.net/bzjr_Log_x/article/details/126190068?spm=1001.2014.3001.5501)
- [Algorithm Notes 6 多项式](https://blog.csdn.net/bzjr_Log_x/article/details/126379530?spm=1001.2014.3001.5501)
- [Algorithm Notes 7 组合数学](https://blog.csdn.net/bzjr_Log_x/article/details/126461931?spm=1001.2014.3001.5502)
- [Algorithm Notes 8 分治](https://blog.csdn.net/bzjr_Log_x/article/details/126973182?spm=1001.2014.3001.5502)
- [Algorithm Notes 9 数学相关](https://blog.csdn.net/bzjr_Log_x/article/details/130350279?spm=1001.2014.3001.5502)
### 考前必读

- 保证每题有至少两人读过，且在给出解法后最好确认一下题意。
- 想不出正经做法时可以仔细考虑一下暴搜，最好能有准确的复杂度分析。
- 实在调试不过的时候可以试下 `#define int ll` 和调大数组，注意输入是 `ll` 的情况。
- 提交前检查：
  - 类型
  - 取模/模数
  - 数组范围/溢出
  - 空间
  - 极限数据（极大和极小）
  - 若采用 `cin/cout` 读入输出大量数据，是否关闭了同步流。
  - 若选择分支较多，对每种分支都需构造样例检查。
  - 所有函数都写了返回值（可能导致各种未知错误）。

### 缺省源

```cpp
#include <bits/stdc++.h>

template <class T>
inline void read(T &res)
{
	char ch; bool flag = false; res = 0;
	while (ch = getchar(), !isdigit(ch) && ch != '-');
	ch == '-' ? flag = true : res = ch ^ 48;
	while (ch = getchar(), isdigit(ch))
		res = res * 10 + ch - 48;
	flag ? res = -res : 0;
}

template <class T>
inline void nonnegative_put(T x)
{
	if (x > 9)
		nonnegative_put(x / 10);
	putchar(x % 10 + 48);
}

template <class T>
inline void put(T x)
{
	if (x < 0)
		x = -x, putchar('-');
	nonnegative_put(x);
}

template <class T>
inline void CkMin(T &x, T y) {x > y ? x = y : 0;}
template <class T>
inline void CkMax(T &x, T y) {x < y ? x = y : 0;}
template <class T>
inline T Min(T x, T y) {return x < y ? x : y;}
template <class T>
inline T Max(T x, T y) {return x > y ? x : y;}
template <class T>
inline T Abs(T x) {return x < 0 ? -x : x;}
template <class T>
inline T Sqr(T x) {return x * x;} 
//call Sqr((ll)x) when the type of returned value is "long long".

using std::map;
using std::set;
using std::pair;
using std::bitset;
using std::string;
using std::vector;
using std::complex;
using std::multiset;
using std::priority_queue;

typedef long long ll;
typedef long double ld;
typedef complex<ld> com;
typedef pair<int, int> pir;
const ld pi = acos(-1.0);
const ld eps = 1e-8;
const int Maxn = 1e9;
const int Minn = -1e9;
const int mod = 998244353; 
const int N = 1e5 + 5;
int T_data, n;

inline void solve()
{
	
}

int main()
{
	read(T_data);
	while (T_data--)
		solve();
}
```

### 关闭同步流

```cpp
using std::ios;
using std::cin;
using std::cout;

int main()
{
	ios::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);
}
```

### 随机打乱

```cpp
	std::mt19937 rng(time(0));
	std::shuffle(a + 1, a + n + 1, rng);
```

### linux 下对拍

- 以 A + B problem 对拍为例，编译器环境为 codeblocks。

- test/main.cpp

```cpp
#include <bits/stdc++.h>

using std::vector;

int main()
{
    int a, b;
    freopen("../test_gen/test.in", "r", stdin);
    freopen("../test_check/test.out", "w", stdout);

    scanf("%d%d", &a, &b);
    printf("%d\n", a + b);

    fclose(stdin); fclose(stdout);
    return 0;
}
```

- test_bf/main.cpp

```cpp
#include <iostream>

using namespace std;

int main()
{
    freopen("../test_gen/test.in", "r", stdin);
    freopen("../test_check/test_bf.out", "w", stdout);

    int a, b;
    std::cin >> a >> b;
    std::cout << a + b << std::endl;

    fclose(stdin); fclose(stdout);
    return 0;
}
```

- test_gen/main.cpp

```cpp
#include <iostream>

using namespace std;
const int mod = 1e9;
int main()
{
    freopen("test.in", "w", stdout);

    srand(time(0));
    printf("%d %d\n", rand() % mod + 1, rand() % mod + 1); // 64bit 的 ubunutu  rand 的最大值一般是 2^31 - 1
    return 0;
}
```

- test_check/main.cpp

```cpp
#include <iostream>

using namespace std;

int main()
{
    while (1)
    {
        system("g++ ../test_gen/main.cpp -o test_gen");
        system("g++ ../test/main.cpp -o test");
        system("g++ ../test_bf/main.cpp -o test_bf");

        system("./test_gen");
        system("./test");
        system("./test_bf");

        if (system("diff test.out test_bf.out"))
            break ;
        puts("checking");
    }
    return 0;
}
```

### bitset

![8](D:\Folder.CSU\ACM\notes\8.png)

![9](D:\Folder.CSU\ACM\notes\9.png)

### Python

- 读入多个以空间间隔的整数：

```python
string = input().split() #a list of strings
n = int(string[0])
k = int(string[1])
```

- 取整数长度：

```python
Len = len(str(n))
```

- 格式化输出：

```cpp
print(f'hello world {n} {k}')
```

- 数组的简单使用：

```python
ex = [1]
for i in range(1, 101):
    ex.append(ex[i - 1] * 10)
```

- `range(l,r,d)` 分别表示起点、终点和步幅：

```python
>>> list(range(-10, -100, -30))
[-10, -40, -70]
```

- 按格式输出

```python
print('.2f' % a)
```

### 高精度

- 仅供参考，且仅支持非负整数，有需求优先考虑 Python。

```cpp
#include<bits/stdc++.h>

using std::pair;
using std::make_pair; 
const int N_bigint = 2500;
char s[N_bigint * 10];

template <class T>
inline T Max(T x, T y) {return x > y ? x : y;}

int askLenx(int x)
{
	x = abs(x);
	int cnt = 0;
	while (x)
	{
		x /= 10;
		++cnt;
	}
	return cnt;
}

struct bigint
{
    typedef long long ll;
    const ll base = 1e8;
    ll a[N_bigint];
	int len;
    
	void Clear() {memset(a, 0, sizeof(a)); a[len = 1] = 0;}
	bigint() {Clear();}
    bigint(ll x) {*this = x;}
    bigint operator = (const bigint &b)
	{
		memset(a, 0, sizeof(a));
        len = b.len;
		for (int i = 1; i <= len; ++i)
			a[i] = b.a[i]; 
		return *this;
    }
    
    bigint operator + (const bigint &b) const
	{
        int L = Max(len, b.len); 
		bigint tmp;
        for (int i = 1; i <= L; ++i)
		{
            if (i > len) 
				tmp.a[i] += b.a[i];
            else if (i > b.len)
				tmp.a[i] += a[i];
            else 
			{
                tmp.a[i] += a[i] + b.a[i];
                if (tmp.a[i] >= base)
				{
                    tmp.a[i] -= base;
                    ++tmp.a[i + 1];
                }
            }
        }
        if (tmp.a[L + 1]) tmp.len = L + 1;
        	else tmp.len = L;
        return tmp;
    }
    bigint operator - (const bigint &b) const 
	{
        int L = Max(len, b.len);
		bigint tmp;
        for (int i = 1; i <= L; ++i)
		{
            tmp.a[i] += a[i] - b.a[i];
            if (tmp.a[i] < 0)
			{
                tmp.a[i] += base;
                --tmp.a[i + 1];
            }
        }
        while (L > 1 && !tmp.a[L]) --L;
        tmp.len = L;
        return tmp;
    }
    bigint operator * (const bigint &b) const
	{
        int L = len + b.len; 
		bigint tmp;
        for (int i = 1;i <= len; ++i)
            for (int j = 1;j <= b.len; ++j)
			{
                tmp.a[i + j - 1] += a[i] * b.a[j];
                if (tmp.a[i + j - 1] >= base)
				{
                    tmp.a[i + j] += tmp.a[i + j - 1] / base;
                    tmp.a[i + j - 1] %= base;
                }
            }
        tmp.len = len + b.len;
        while (tmp.len > 1 && !tmp.a[tmp.len])
			--tmp.len;
        return tmp;
    }
	pair<bigint, bigint> Divide(const bigint &a, bigint b) const
	{
        int L = a.len; bigint c, d;
        for (int i = L; i; --i)
		{
            c.a[i] = 0;
			d = d * base; 
			d.a[1] = a.a[i];
            ll l = 0, r = base - 1, mid;
            while (l < r)
			{
                mid = (l + r + 1) >> 1;
                if (b * mid <= d) l = mid;
                	else r = mid - 1;
            }
            c.a[i] = l; 
			d -= b * l;
        }
        while (L > 1 && !c.a[L])
			--L;
		c.len = L;
        return make_pair(c, d);
    }
    bigint operator / (ll x) const 
	{
        ll d = 0; bigint tmp;
        for (int i = len; i; --i)
		{
            d = d * base + a[i];
            tmp.a[i] = d / x;
            d %= x;
        }
        tmp.len = len;
        while (tmp.len > 1 && !tmp.a[tmp.len])
			--tmp.len;
        return tmp;
    }
    ll operator % (ll x) const
	{
        ll d = 0;
        for (int i = len; i; --i) d = (d * base + a[i]) % x;
        return d;
    }
    bigint operator / (const bigint &b) const {return Divide(*this, b).first;}
    bigint operator % (const bigint &b) const {return Divide(*this, b).second;}
    bigint &operator += (const bigint &b) {*this = *this + b; return *this;}
    bigint &operator -= (const bigint &b) {*this = *this - b; return *this;}
    bigint &operator *= (const bigint &b) {*this = *this * b; return *this;}
    bigint &operator ++() {bigint T; T = 1; *this = *this + T; return *this;} //前缀++ 
    bigint &operator --() {bigint T; T = 1; *this = *this - T; return *this;} //前缀-- 
    bigint operator ++(int) {bigint T, tmp = *this; T = 1; *this = *this + T; return tmp;} //后缀++ 
    bigint operator --(int) {bigint T, tmp = *this; T = 1; *this = *this - T; return tmp;} //后缀-- 
    bigint operator + (ll x) const {bigint T; T = x; return *this + T;}
    bigint operator - (ll x) const {bigint T; T = x; return *this - T;}
    bigint operator * (ll x) const {bigint T; T = x; return *this * T;}
    bigint operator *= (ll x) {*this = *this * x; return *this;}
    bigint operator += (ll x) {*this = *this + x; return *this;}
    bigint operator -= (ll x) {*this = *this - x; return *this;}
    bigint operator /= (ll x) {*this = *this / x; return *this;}
    bigint operator %= (ll x) {*this = *this % x; return *this;}
    bool operator == (ll x) const {bigint T; T = x; return *this == T;}
    bool operator != (ll x) const {bigint T; T = x; return *this != T;}
    bool operator <= (ll x) const {bigint T; T = x; return *this <= T;}
    bool operator >= (ll x) const {bigint T; T = x; return *this >= T;}
    bool operator < (ll x) const {bigint T; T = x; return *this < T;}
    bool operator > (ll x) const {bigint T; T = x; return *this > T;}
    bigint operator = (ll x)
	{
        len = 0;
        while (x)
			a[++len] = x % base, x /= base;
        if (!len) a[++len] = 0;
        return *this;
    }
    bool operator < (const bigint &b) const 
	{
        if (len < b.len) return 1;
        if (len > b.len) return 0;
        for (int i = len; i; --i)
		{
            if (a[i] < b.a[i]) return 1;
            if (a[i] > b.a[i]) return 0;
        }
        return 0;
    }
    bool operator == (const bigint &b) const 
	{
        if (len != b.len) return 0;
        for (int i = len; i; --i)
            if (a[i] != b.a[i]) return 0;
        return 1;
    }
    bool operator != (const bigint &b) const {return !(*this == b);}
    bool operator > (const bigint &b) const {return !(*this < b || *this == b);}
    bool operator <= (const bigint &b) const {return (*this < b) || (*this == b);}
    bool operator >= (const bigint &b) const {return (*this > b) || (*this == b);}
    
    void str(char *s)
	{	
        int l = strlen(s);
		ll x = 0, y = 1; len = 0;
        for (int i = l - 1; i >= 0; --i)
		{
            x = x + (s[i] - '0') * y; 
			y *= 10;
            if (y == base)
			{
				a[++len] = x;
				x = 0;
				y = 1;
			}
        }
        if (!len || x)
			a[++len] = x;
    }
    void read()
	{
        scanf("%s", s);
		this->str(s);
    }
    void print() const 
	{
        printf("%d", (int)a[len]);
        for (int i = len - 1; i; --i)
		{
            for (int j = base / 10; j >= 10; j /= 10)
			{
                if (a[i] < j) putchar('0');
                	else break;
            }
            printf("%d", (int)a[i]);
        }
		putchar('\n');
    }
	int askLen() const 
	{ 
		return (len - 1) * 8 + askLenx(a[len]);
	}
}a, b;
 
int main()
{
	a.read();
	b.read();
	(a + b).print();
	if (a >= b)
		(a - b).print();
	else 
	{
		putchar('-');
		(b - a).print();
	}
	(a * b).print();
	pair<bigint, bigint> t = a.Divide(a, b);
	t.first.print(); t.second.print();
}
```

