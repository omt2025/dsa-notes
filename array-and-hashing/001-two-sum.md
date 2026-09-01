# 1. Two Sum (Easy)

链接:https://leetcode.com/problems/two-sum/
标签:Array, Hash Table
日期:2026-09-01

## 题意
- Given an array of integers, return the indices of the two numbers that add up to the target.

## 暴力解
- 思路: Two nested loops — for each element, check every element after it to see if the two sum to the target.
- 时间 / 空间: O(n²) time, O(1) space since i and j are just two integer variables that don't grow with n.

## 瓶颈
（内层循环到底在干什么?）
The bottleneck is the inner loop. Once the first number is fixed, the second one is  already determined it must be `target - num` (the complement). So the inner loop  isn't enumerating pairs at all; it's answering a single question: does the complement  exist, and at which index? That's a lookup problem, and in an unsorted array a lookup  costs O(n). That O(n) per element is what makes the whole thing O(n²).

## 优化
（哈希表怎么消除瓶颈?key/value 为什么这么设计?）

Hash map 的查找是 O(1),可以把 O(n²) 降到 O(n)。

**key/value 怎么定:** 原则是 key = 查询时手里已有的东西,value = 查到后想拿走的东西。
这题查询时手里拿的是 complement(一个**数值**),想拿回的是它的 **index**。 
所以 key 存数值,value 存 index。

注意存和查的区别:
- 存:`seen[num] = i` —— 放进去的是当前的 num
- 查:`if comp in seen` —— 拿 complement 去查

两者都是数值,所以能对上。这一轮存的 num,正是未来某一轮的 complement。

**额外好处:** 因为是先查后存,当前元素查询时还不在表里,所以永远不会把一个元素
和它自己配对。重复值也能正确配对(如 [3,3])。

## 复杂度
- **时间 O(n)** — 只遍历一遍,每次 lookup 是 O(1)
- **空间 O(n)** — 最坏情况下 hash map 要存下全部 n 个元素

对比暴力解的 O(n²) 时间 / O(1) 空间:用空间换了时(space-time tradeoff)。
O(n) 也是这题的时间下界,因为至少要看每个元素一眼。

## 口述稿

**① Confirm**
"Let me confirm a couple of things: I'm returning indices rather than the values, 
and I can't use the same element twice, right?"

**② Brute force**
"The brute force approach is two nested loops — for each element, I check every 
element after it to see if the two sum to the target. That's O(n²) time and O(1) 
space, since I only need two index variables that don't grow with n."

**③ Bottleneck**
"The bottleneck is the inner loop. Once I fix the first number, the second one is 
already determined — it has to be target minus the first, the complement. So the 
inner loop isn't enumerating pairs; it's answering one question: does the complement 
exist, and at what index? That's a lookup problem, and in an unsorted array a lookup 
costs O(n)."

**④ Hash map**
"Lookups are what a hash map is for — that brings the cost down to O(1). My rule for 
key and value is: the key is what I have in hand when I search, and the value is what 
I want back. Here I'm searching with the complement, which is a number, and I want its 
index back. So the key is the number and the value is the index."

**⑤ One pass**
"I look up the complement first, then store the current element. So the map only ever 
holds elements I've already seen, and every pair gets checked when its second element 
arrives. This also means I can never pair an element with itself, since it isn't in 
the map yet."

**⑥ Complexity**
"Time is O(n) — one pass with O(1) lookups. Space is O(n), because in the worst case 
the map stores every element. So I'm trading space for time. O(n) is also the lower 
bound here, since you have to look at every element at least once."

## 踩过的坑
- 坑1: key/value 存反写成 dict[i] = comp
- 坑2: 用了 dict 当变量名(Python 内置)
- 坑3: 空间复杂度理由说错了,说成"走过n个元素",
       正确是"哈希表要存下n个元素"。遍历不花空间,存储才花
- 核心: 固定一个变量后另一个被唯一确定 → 内层是查找问题 → 上哈希表