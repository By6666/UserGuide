# **__那些年走过的坑__**
# C++ STL container 

> ## [__vector__]
> 1. resize 与 reserve 的区别: 前者不仅开辟了空间,并赋值元素为0; 后者只是开辟空间,并不赋初始值. 这就意味着,当我们使用resize进行开辟空间后,需要使用下表来进行相应值的修改, 使用reserve时, 仍需使用push_back来进行插入.
    >> | 区别 | resize(n) | reserve(n)|
    >> |:----:|:----:|:----:|
    >> |size() | n | 0|
    >> |capacity() | n | n|

> 2. 当使用resize进行容器大小的更改时,并没有释放额外的空间.而使用 <p> vector<type>(A).swap(A) </p> 这样的语句,可以将容器内存改为适当大小. 若需清空可使用 <p> vector<type>().swap(A) </p>
    >> __设：当前容器 *A* 中 size=10, capacity=100__
    >> | 区别 | resize(5) | vector<type>(A).swap(A) | vector<type>().swap(A) |
    >> |:----:|:----:|:----:|:----:|
    >> |size() | 5 | 5 | 0 |
    >> |capacity() | 100 | 5| 0 |

> 3. 使用 push_back 与 emplace_back 的区别
