# 术语表 Glossary

面向英文技术面试的中英对照表。目标：**中文能理解，英文能说出口。**

## 使用与维护规则

- 每做完一题 / 一节 SQL，顺手加 2-3 行，不追求一次写全
- **「我踩过的坑」这一栏最值钱** —— 写自己当时的具体报错或误解，不要抄词典释义
- 没亲手撞过的词不要加进来，术语表不是词典
- 按「首次遇到」日期做间隔复习：3 天前、1 周前、1 个月前各扫一遍
- 标 ⭐ 的是可以直接对面试官说的标准术语

---

## 一、Python 语言基础

| 中文 | English | 首次遇到 | 我踩过的坑 |
|---|---|---|---|
| 可哈希 | hashable ⭐ | 09-02 | `d[sorted("cat")] = 1` 报 `unhashable type: 'list'`。哈希值必须永不变，所以只有不可变对象能当 key |
| 不可变 / 可变 | immutable / mutable ⭐ | 09-02 | 可当 key：int、str、tuple、frozenset。不可当：list、dict、set |
| 字符串拼接 | join / concatenation ⭐ | 09-02 | 主语是分隔符不是列表：`"".join(lst)` 对，`lst.join("")` 错 |
| 键错误 | KeyError ⭐ | 09-02 | 首次 `d[key].append()` 时 key 还不存在 |
| 默认字典 | defaultdict ⭐ | 09-02 | `collections.defaultdict(list)`，省掉 `if key not in d` |
| 视图对象 | view object | 09-02 | `d.values()` 不是 list，要 `list(d.values())` |
| 字典默认遍历键 | dict iterates over keys | 09-02 | `list(d)` 给的是 keys 不是 values；`for k, v in d.items()` ⭐ |
| 缩进 | indentation ⭐ | 09-02 | REPL 里 `...` 状态要自己敲缩进 |
| 枚举 | enumerate ⭐ | 09-01 | 同时拿下标和元素 |

## 二、算法与复杂度

| 中文 | English | 首次遇到 | 我踩过的坑 |
|---|---|---|---|
| 暴力解 | brute force ⭐ | 08-31 | 面试先讲它再优化 |
| 时间 / 空间复杂度 | time / space complexity ⭐ | 08-31 | |
| 辅助空间 | auxiliary space ⭐ | 09-02 | 讨论的永远是 auxiliary，不含输入本身 |
| 时空权衡 | space-time tradeoff ⭐ | 08-31 | 242 两解的核心区别 |
| 一趟遍历 | one pass / single pass ⭐ | 09-01 | |
| 循环不变量 | loop invariant ⭐ | 09-01 | CLRS 术语。写在 for 上面，能一句话解释解法为什么正确 |
| 边界情况 | edge case ⭐ | 09-01 | |
| 约束条件 | constraints ⭐ | 09-01 | **别脑补题目没有的约束**（我曾以为 Two Sum 不含负数，其实含） |
| 线性级 | linear O(n) ⭐ | 08-31 | |
| 对数级 | logarithmic O(log n) ⭐ | 09-02 | = 折半几次。n 涨 1000 倍，log n 只涨 1 倍 |
| 线性对数级 | linearithmic O(n log n) ⭐ | 09-02 | = log n 轮 × 每轮 n 的活。紧贴 O(n)，离 O(n²) 极远 |
| 平方级 | quadratic O(n²) ⭐ | 08-31 | 真正要避免的是这个 |
| 提前返回 | early return ⭐ | 08-31 | 217 找到就返回，比 `len(set())` 快 |
| 比较排序下界 | comparison sort lower bound ⭐ | 09-02 | 基于比较的排序快不过 O(n log n) |

## 三、数据结构与题型模式

| 中文 | English | 首次遇到 | 我踩过的坑 |
|---|---|---|---|
| 哈希表 / 字典 | hash map / hash table ⭐ | 09-01 | Python 里叫 dictionary |
| 键 / 值 | key / value ⭐ | 09-01 | 别用 value 同时指「数组元素」和「字典的值」 |
| 集合 | set / hash set ⭐ | 08-31 | 只存「在不在」，所以叫 `seen` 没问题 |
| 下标 | index（复数 **indices**）⭐ | 09-01 | 不是 indexes |
| 补数 / 差值 | complement ⭐ | 09-01 | `target - num` |
| 规范键 | canonical key ⭐ | 09-02 | 49 的核心：`"".join(sorted(word))` |
| 桶 / 分组 | bucket / group ⭐ | 09-02 | 一个 key 挂多个东西 → value 用列表 |
| 去重 | deduplicate (dedupe) ⭐ | 08-31 | |
| 变位词 | anagram ⭐ | 08-31 | |
| 字符频次 | character frequency / count ⭐ | 08-31 | |
| 字母表大小 | alphabet size ⭐ | 09-02 | 计数解空间是 O(k)；k 炸了（Unicode）就该换排序解 |
| 哈希冲突 | hash collision ⭐ | 09-02 | 指两个不同 key 落同一个桶。**「key 被覆盖」不叫 collision**，叫 overwriting an existing key |

## 四、排序算法

| 中文 | English | 首次遇到 | 备注 |
|---|---|---|---|
| 原地算法 | in-place algorithm ⭐ | 09-02 | 只用 O(1) 辅助空间 |
| 稳定排序 | stable sort ⭐ | 09-02 | 相等元素相对顺序不变 |
| 蒂姆排序 | Timsort ⭐ | 09-02 | 归并+插入混合。最好 O(n)，辅助空间 O(n)，稳定。**Python 3.11 起默认已换成 Powersort** |
| 堆排序 | Heapsort ⭐ | 09-02 | 全场景 O(n log n)，辅助空间 O(1)，不稳定 |
| 建堆 / 下沉 | heapify / sift down ⭐ | 09-02 | heapify 是 O(n) 不是 O(n log n) |
| 二叉堆 | binary heap ⭐ | 09-02 | 用数组下标模拟：左孩子 2i+1，右孩子 2i+2 |
| 内省排序 | introsort ⭐ | 09-02 | quicksort 退化时切 heapsort 兜底 |

> **Python 陷阱**：`sorted()` 新建列表 → O(n) 空间；`list.sort()` 原地但底层最坏仍需 O(n) 辅助内存。**在 Python 里做不到真正的 O(1) 空间排序。**

## 五、SQL

| 中文 | English | 首次遇到 | 我踩过的坑 |
|---|---|---|---|
| 关系型数据库 | relational database ⭐ | 08-31 | |
| 表 / 行 / 列 | table / row / column ⭐ | 08-31 | 行也叫 record，列也叫 field |
| 表结构 | schema ⭐ | 08-31 | 第 3 周迁 PostgreSQL 时要用 |
| 建表 / 插入 | CREATE TABLE / INSERT INTO ⭐ | 08-31 | |
| 查询 | query ⭐ | 09-01 | |
| 空值 | NULL ⭐ | 09-01 | `WHERE col != 'x'` **不会**选出 NULL 行 |
| 三值逻辑 | three-valued logic ⭐ | 09-01 | 上面那个坑的原理：结果有 true / false / **unknown** 三种 |
| 判空 | IS NULL / IS NOT NULL ⭐ | 09-01 | 不能写 `= NULL` |
| 通配符 | wildcard ⭐ | 09-01 | `LIKE` 里的 `%` 和 `_` |
| 排序 / 限条数 | ORDER BY / LIMIT ⭐ | 09-01 | 升降序 ASC / DESC |

## 六、工具与环境

| 中文 | English | 首次遇到 | 我踩过的坑 |
|---|---|---|---|
| 交互式解释器 | REPL (Read-Eval-Print Loop) ⭐ | 09-02 | 不确定就敲一下，别在脑子里推 |
| 提示符 | prompt ⭐ | 09-02 | 先看提示符判断「现在谁在听我说话」 |

**提示符对照**

| 提示符 | 环境 | 说什么话 |
|---|---|---|
| `PS C:\...>` | PowerShell | Windows 命令 |
| `$` / `%` | Mac/Linux 终端 | Unix 命令 |
| `>>>` | Python REPL | Python 代码 |
| `...` | Python 续行中 | 代码块没写完 → **空行回车**；括号没闭合 → **补括号**或 `Ctrl+C` |
| `sqlite>` | SQLite CLI | SQL 语句 |

---

## 七、面试口语句型

背这个比背单词有用。

**开场讲思路**
> "The brute force is O(n²) — we check every pair. We can do better by trading space for time."

**引入哈希表**
> "I'll use a hash map from value to index, so lookups are O(1) **on average**."
> （on average 三个字要说，哈希表最坏是 O(n)）

**解释顺序 / 正确性**
> "I check before I insert, so an element can't pair with itself."
> "Overwriting is safe here — the later index can serve any pair the earlier one could."

**复杂度收尾**
> "Time O(n), space O(n) — one pass, and in the worst case the map holds every element."

**被加空间约束时**
> "Sorting gives O(1) extra space in principle — but in Python, the built-in sort needs O(n) auxiliary space in the worst case. For true O(1), we'd need an in-place heapsort."

**讨论字符集**
> "Counting is O(n) time but O(k) space where k is the alphabet size. If the alphabet is huge — Unicode, for instance — sorting becomes the safer choice."

---

## 八、待学（留空，遇到再填）

**SQL**：INNER JOIN、LEFT JOIN、外键 foreign key、连接条件 join condition、笛卡尔积 Cartesian product

**算法**：双指针 two pointers、滑动窗口 sliding window、前缀和 prefix sum、二分查找 binary search

---

## 附：题目 → 模式速查

| 题号 | 题名 | 模式 | 日期 |
|---|---|---|---|
| 217 | Contains Duplicate | 存在性 → set | 08-31 |
| 242 | Valid Anagram | 计数 → hash map / 排序 | 08-31 |
| 1 | Two Sum | 边遍历边查 → hash map | 09-01 |
| 49 | Group Anagrams | 规范键归组 → hash map + list | 09-02 |

> **共同信号**：这四题都在问「存在性 / 计数 / 归组」，答案都是哈希结构。看到这类信号，先想 hash map。
