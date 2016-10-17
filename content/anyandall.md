Title: Bất kỳ và Tất cả
Author: PhapDV
Date: 2016-10-14
Category: Tutorial, python
Tags: Programming, Python

## Any(bất kỳ) and All(tất cả)

+ Trong python có hai hàm `built in` function là any() và all(). Cả hai hàm đều trả về giá trị `True`. Đầu vào là một iterable.
+ All return True if all elements of the iterable are true (or if the iterable is empty)
+ Any return True if any element of the iterable is true. If the iterable is empty, return False.
### 1. All()
+ Xét ví dụ, kiểm tra một chuỗi xem tất cả có phải là `t` hay không ?

Đơn giản nhưng khá dài:
```python
s = 'python'
for c in s:
    checks = []
    if not c == 't':
        print('Tất cả chuỗi không là t')
        break
    print('Tất cả chuỗi là t')
```

One line với all():

```python
print(all(c == 't' for c in 'python'))
```

### 2. Any()
+ Với ví dụ như trên, kiểm tra chuỗi có ít nhất 1 ký tự `t` hay không ?

One line với any()
```python
print(any(c == 't' for c in 'python'))
```

> `Any()` trả về True nếu đúng ít nhất một trường hợp. `All()` trả về True nếu tất cả các trường hợp đều đúng.
