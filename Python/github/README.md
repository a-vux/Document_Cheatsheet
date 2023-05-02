# Mục lục:
1. [Comment](#comment)
1. [Biến](#biến)
1. [Literals](#các-kiểu-giá-trị-literals)
1. [Data type](#các-kiểu-dữ-liệu)

# **Comment:**
```py
# Đây là comment 1 dòng

'''
Đây là comment nhiều dòng
'''

"""
Đây cũng là comment nhiều dòng
"""
```

# **Biến:**
- Python là ngôn ngữ thuộc kiểu type-inferred, tức không cần phải tường minh đặt kiểu dữ liệu cho biến. Tùy vào giá trị gán cho biến mà nó tự động biết kiểu dữ liệu là gì
- Python là case-sensitive
```py
    name = "Vux" # string
    name2 = 'Vux' # string
    num = 13 # number
    print(name, num) # cú pháp in
    name, num = 'Hello', 3 # gán giá trị cho nhiều biến
    name = name2 = "World" # gán cùng 1 giá trị cho nhiều biến
```

# Các kiểu giá trị (Literals):
## 1. Kiểu số (Numeric Literals):
- Có 3 lớp:
```py
    # Int
    dec = 13
    dec2 = -3
    bin_num = 0b101 # bắt đầu bằng 0b
    oct_num = 0o13 # bắt đầu bằng 0o
    hexa_num = 0x13 # bắt đầu bằng 0x

    # Float
    float_num = 13.3

    # Complex
    complex_num = 13 + 3j # có dạng a + bj

```
## 2. Kiểu Bool (Boolean Literals):
```py
    check = True
    check2 = False
```

## 3. String/Char:
```py
    char = 'a'
    string = 'abc'
    string2 = "abc"
```

## 4. Special Literal:
```py
    value = None # đại diện cho null
```

## 5. Literal Collection:
```py
    # list
    fruits = ['apple', 'banana']

    # tuple
    numbers = (1,2,3)

    # dict
    alphabets = {'a': 'apple', 'b': 'banana'}

    # set
    vowels = {'a','e','i','o','u'}
```

# Các kiểu dữ liệu:
- Do mọi thứ trong Python đều ở dạng đối tượng (object) nên bản chất data type trong python là các lớp (class). Vậy nên biến chính là một thực thể (instance) của class
- Cách kiểm tra kiểu dữ liệu: `type()`
```py
    a = 13 # <class 'int'>
    a = 13.3 # <class 'float'>
    b = 'a' # <class 'str'>
    c = True # <class 'bool'>
```

# List:
- Được khởi tạo bằng cặp ngoặc vuông `[]`
- Các phần tử trong list có thể khác kiểu dữ liệu