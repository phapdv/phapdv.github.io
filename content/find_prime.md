Title: Số nguyên tố, kiểm tra một số nguyên tố hay không?
Author: PhapDV
Date: 2016-10-14
Category: Tutorial, python
Tags: Programming, Python

## Prime number (Số nguyên tố)
![](https://upload.wikimedia.org/wikipedia/commons/b/b8/Animation_Sieb_des_Eratosthenes_%28vi%29.gif)
> Ngày xưa đi học thì chỉ biết số nguyên tố là số chỉ chia hết cho 1 và chính nó. Sau khi đi học lớp python của [PyFML](http://pymi.vn) thì mới biết là ước tự nhiên khác 1 nhỏ nhất của một số tự nhiên là số nguyên tố. Hay nói cách khác là số tự nhiên chỉ có ước số là 1 và chính nó là số nguyên tố. Xa hơn chút nữa là chúng ta cần kiểm tra xem số tự nhiên đó có ước nào nữa ngoài ước 1 và chính nó.

## Kiểm tra có là một số nguyên tố?
Có nhiều cách để kiểm tra 1 số tự nhiên có phải là số nguyên tố hay không. Ở đây chúng ta sẽ sử dụng cách kiểm tra các ước của một số tự nhiên.

+ Đầu tiên thuật toán sẽ là kiểm tra các số có khả năng là ước của số `n` hay không? Dãy số có khả năng là ước của `n` nằm trong khoảng từ `1` đến `n`. Nhưng vì `1` và `n` thì luôn là ước của số đó nên có thể loại bỏ hai trường hợp này. Code python như sau:

```python
n = 13
def is_prime(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True
```
+ Tất cả các số tự nhiên có đúng với function trên hay không ? Nếu `n = 1` thì sao nhỉ?(True)..?..?? Số `1` không phải là số nguyên tố. Số `0` cũng không phải là số nguyên tố. Sửa một chút cho nó đúng.

```python
n = 1
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n):
        if n % i == ):
            return False
    return True
```
+ Ok rồi đó. Nhưng mà ước số của một số thì không lớn hơn số đó chia `2`. Code vẫn vậy chỉ  sửa vòng lặp cho đến `n/2`.

```python
n = 92
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n//2+1):
        if n % i == 0:
            return False
    return True
```
+ Đi học python [PyFML](http://pymi.vn) thầy giáo lại bảo chỉ cần kiểm tra đến căn bậc `2` của `n`. Đíu hỉu tại sao nữa? Thắc mắc mời đi học ở [PyFML](http://pymi.vn/python) để gặp thầy mình.

```python
n = 87
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**(1/2))):
        if n % i == 0:
            return False
    return True
```
## Tối ưu
Nếu `n % 2 == 0` hay `n % 3 == 0` thì n cũng không phải là số nguyên tố.

```python
n = 45
def is_prime(n):
    if n < 2:
        return False
    if n % 2 == 0 or n % 3 == 0 or n % 5 == 0:
        return False
    for i in range(5, int(n**(1/2)), 2): # Chỉ kiểm tra các số lẻ
        if n % i == 0:
            return False
    return True
```

## Tạo danh sách số nguyên tố.

+ `Sàng Eratosthenes`

+ Thuật toán như sau:
 - Bước 1: Tạo 1 danh sách các số tự nhiên liên tiếp từ 0 đến n: (0, 1, 2, 3, 4,..., n).
 - Bước 2: Giả sử tất cả các số trong danh sách đều là số nguyên tố. Trong đó, p = 2 là số nguyên tố đầu tiên.
 - Bước 3: Tất cả các bội số của p: 2p, 3p, 4p,... sẽ bị đánh dấu vì không phải là số nguyên tố.
 - Bước 4: Tìm các số còn lại trong danh sách mà chưa bị đánh dấu và phải lớn hơn p. Nếu không còn số nào, dừng tìm kiếm. Ngược lại, gán cho p giá trị bằng số nguyên tố tiếp theo và quay lại bước 3.
Khi giải thuật kết thúc, tất các số chưa bị đánh dấu trong danh sách là các số nguyên tố cần tìm.

Đoạn code dùng để generate prime numbers có sử dụng thuật toán `sàng`.

```python
def range_prime(n):
    numbers = [True] * n
    numbers[0] = False
    numbers[1] = False
    for i in range(2, int(n**(1/2))):
        k = i * 2 # Đánh dấu bội số của i
        while k < n:
            numbers[k] = False
            k = k + i

    primes = [i for i in range(2, n) if numbers[i]]
    return primes
```
> Chú ý:
> Ước số dương bé nhất khác 1 của một hợp số a là một số nguyên tố không vượt quá căn bậc 2 của nó.
