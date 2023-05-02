* `exit($message)`: in ra màn hình `$message` và terminate script luôn
* `die($message)`: giống hàm `exit()`

# **PHP OOP**
## *Cách định nghĩa class:*
- Sử dụng từ khóa `class` với cú pháp:
```php
class <Class_name>{
    // thuộc tính và phương thức
}
```
- Ví dụ:
```php
class Fruit{
    // Thuộc tính - Property
    public $name;
    public $color;

    // Phương thức - Method
    function set_name($name){
        $this->name = $name;
    }
    function get_name(){
        return $this->name;
    }
}
```

## *Cách tạo object:*
- Sử dụng từ khóa `new` với cú pháp:
```php
$variable_name = new  Class_name();
```
- Ví dụ:
```php
$apple = new Fruit();
$banana = new Fruit();
$apple->set_name('Apple');
$banana->set_name('Banana');

echo $apple->get_name(); // Apple
echo '<br>';
echo $banana->get_name(); // Banana
```
- Từ khóa `$this` ý chỉ cái ***object hiện tại***
- Từ khóa `$instanceof` dùng để kiểm tra xem nếu object có thuộc class nào đó hay không với cú pháp:
```php
$object_name instanceof Class_name
```
- Ví dụ:
```php
var_dumb($apple instanceof Fruit) // bool(true)
```

## *Constructor:*
- Đây là phương thức giúp ***khởi tạo giá trị cho thuộc tính*** của object ***ngay từ lúc tạo*** object
- Phương thức này có tên `__construct()` và được ***gọi tự động*** khi tạo một object
- Ví dụ:
```php
class Fruit {
  public $name;
  public $color;

  function __construct($name, $color) {
    $this->name = $name;
    $this->color = $color;
  }
  function get_name() {
    return $this->name;
  }
  function get_color() {
    return $this->color;
  }
}

$apple = new Fruit("Apple", "red");
echo $apple->get_name();
echo "<br>";
echo $apple->get_color();
```

## *Destructor:*
- Đây là phương thức được gọi đến khi muốn xóa một object hoặc khi script stop hoặc exit
- Phương thức này có tên `__destruct()` và được ***gọi tự động*** mỗi khi script chạy đến cuối
- Ví dụ:
    ```php
    class Fruit {
        public $name;
        public $color;

        function __construct($name, $color) {
            $this->name = $name;
            $this->color = $color;
        }
        function __destruct() {
            echo "The fruit is {$this->name} and the color is {$this->color}.";
        }
    }

    $apple = new Fruit("Apple", "red");
    ```
    * Tại đây tuy không có hàm in ra màn hình một cách trực tiếp nào, nhưng trước khi script kết thúc, hàm `__destruct()` được gọi đến, và trong này mới xuất hiện hàm in

## *Các Access Modifiers:*
- Các Access Modifiers là các ***keyword*** gán cho các thuộc tính và phương thức để ***quản lý cách mà chúng được gọi/truy cập***
- Có 3 access modifiers:
    * `public`: thuộc tính và phương thức có thể được ***truy cập ở mọi nơi***. Đây là access modifier mặc định
    * `private`: thuộc tính và phương thức ***chỉ có thể được truy cập trong class***
    * `protected`: giống `private` nhưng có thể được truy cập thêm từ các ***class kế thừa***
- Ví dụ:
```php
class Fruit {
    public $name;
    protected $color;
    private $weight;
}

$mango = new Fruit();
$mango->name = 'Mango'; // OK
$mango->color = 'Yellow'; // ERROR
$mango->weight = '300'; // ERROR
```
- Ví dụ khác nhưng với phương thức:
```php
class Fruit {
    public $name;
    public $color;
    public $weight;

    function set_name($n) {  // a public function (default)
        $this->name = $n;
    }
    protected function set_color($n) { // a protected function
        $this->color = $n;
    }
    private function set_weight($n) { // a private function
        $this->weight = $n;
    }
}

$mango = new Fruit();
$mango->set_name('Mango'); // OK
$mango->set_color('Yellow'); // ERROR
$mango->set_weight('300'); // ERROR
```

## *Kế thừa (Inheritance):*
- Kế thừa là hiện tượng một class được ***kế thừa*** các ***thuộc tính*** và ***phương thức*** (***public*** và ***protected***) của class khác
- Các class kế thừa (con được gọi là ***class con*** - child class) không chỉ kế thừa mà còn có thể có thêm các thuộc tính và phương thức của riêng nó
- Được sử dụng với từ khóa `extends` với cú pháp sau:
```php
class Inheritance_class_name extends Class_name {
    // thuộc tính và phương thức mới
}
```
- Ví dụ:
```php
class Fruit {
    public $name;
    public $color;
    public function __construct($name, $color) {
        $this->name = $name;
        $this->color = $color;
    }
    public function intro() {
        echo "The fruit is {$this->name} and the color is {$this->color}.";
    }
}

// Strawberry is inherited from Fruit
class Strawberry extends Fruit {
    public function message() {
        echo "Am I a fruit or a berry? ";
    }
}

$strawberry = new Strawberry("Strawberry", "red");
$strawberry->message();
$strawberry->intro();
```
- Ở đây ta cần chú ý đến access modifier `protected`:
    * Các thuộc tính và phương thức với access modifier `protected` của class cha đều có thể được truy cập bởi các class con
    * Tuy nhiên, vẫn chỉ có thể ***được truy cập từ bên trong*** class con, chứ không thể truy cập trực tiếp bên ngoài được
- Ví dụ truy cập như sau là ***sai***:
```php
class Fruit {
    public $name;
    public $color;
    public function __construct($name, $color) {
        $this->name = $name;
        $this->color = $color;
    }
    protected function intro() {
        echo "The fruit is {$this->name} and the color is {$this->color}.";
    }
}

class Strawberry extends Fruit {
    public function message() {
        echo "Am I a fruit or a berry? ";
    }
}

$strawberry = new Strawberry("Strawberry", "red");  // OK. __construct() is public
$strawberry->message(); // OK. message() is public
$strawberry->intro(); // ERROR. intro() is protected
```
- Ví dụ truy cập như sau là ***đúng***:
```php
class Fruit {
    public $name;
    public $color;
    public function __construct($name, $color) {
        $this->name = $name;
        $this->color = $color;
    }
    protected function intro() {
        echo "The fruit is {$this->name} and the color is {$this->color}.";
    }
}

class Strawberry extends Fruit {
    public function message() {
        echo "Am I a fruit or a berry? ";
        // Call protected method from within derived class - OK
        $this -> intro();
    }
}

$strawberry = new Strawberry("Strawberry", "red"); // OK. __construct() is public
$strawberry->message(); // OK. message() is public and it calls intro() (which is protected) from within the derived class
```

## *Việc ghi đè (Overriding) các thuộc tính và giao thức được kế thừa:*
- Các thuộc tính và giao thức được kế thừa từ class cha có thể được ghi đè hoặc sửa đổi trong class con bằng cách ***định nghĩa lại*** (redefining) các thuộc tính/giao thức đó
- Ví dụ:
    ```php
    class Fruit {
        public $name;
        public $color;
        public function __construct($name, $color) {
            $this->name = $name;
            $this->color = $color;
        }
        public function intro() {
            echo "The fruit is {$this->name} and the color is {$this->color}.";
        }
    }

    class Strawberry extends Fruit {
        public $weight;
        public function __construct($name, $color, $weight) {
            $this->name = $name;
            $this->color = $color;
            $this->weight = $weight;
        }
        public function intro() {
            echo "The fruit is {$this->name}, the color is {$this->color}, and the weight is {$this->weight} gram.";
        }
    }

    $strawberry = new Strawberry("Strawberry", "red", 50);
    $strawberry->intro();
    ```
    * Ở đây, ***constructor*** của hàm cha bị ghi đè bởi hàm con (thế nên khi khởi tạo object ta truyền vào 3 biến)
    * Ngoài ra phương thức `intro()` cũng bị ghi đè, vậy nên khi gọi đến nó, bản chất là ta đang gọi đến `intro()` của class con
- Để ***tránh việc*** class con ***ghi đè*** lên thuộc tính và phương thức của class cha, từ khóa `final` ra đời để làm việc đó. Ngoài ra từ khóa `final` còn giúp cho một class ***không thể được kế thừa*** từ class khác
- Để chặn kế thừa từ một class, ta ***đặt từ khóa ở đầu*** khi ***tạo class*** với cú pháp:
```php
//  _____ ở đây
// |
final class Class_name{
    // some code
}
```
- Ví dụ trong việc chặn kế thừa từ một class:
```php
final class Fruit {
  // some code
}

// This will result in error
class Strawberry extends Fruit {
  // some code
}
```
- Để chặn ghi đè thuộc tính hoặc phương thức, ta đặt từ khóa ở đầu thuộc tính và phương thức đó với cú pháp:
- Ví dụ trong việc chặn ghi đè thuộc tính hoặc phương thức:
```php
class Fruit {
    //  _____ ở đây
    // |
    final public function intro() {
        // some code
    }
}

class Strawberry extends Fruit {
  // This will result in error
  public function intro() {
    // some code
  }
}
```

## *Hằng (Constant) trong class:*
- Để tạo hằng trong class, sử dụng từ khóa `const`
- Để truy cập vào hằng, ta dùng toán tử `::` với cú pháp:
```php
Class_name::<hằng>
```
- Ví dụ:
```php
class Goodbye {
    const LEAVING_MESSAGE = "Thank you for visiting W3Schools.com!";
}

echo Goodbye::LEAVING_MESSAGE;
```
- Ngoài ra, hằng còn có thể được truy cập ngay bên trong class thông qua từ khóa `self` kèm với toán tử `::` như sau:
```php
class Goodbye {
    const LEAVING_MESSAGE = "Thank you for visiting W3Schools.com!";
    public function byebye() {
        echo self::LEAVING_MESSAGE;
    }
}

$goodbye = new Goodbye();
$goodbye->byebye();
```

## *Abstract class và method:*
- Method được gọi là `abstract` nếu như nó ***đã được khai báo*** nhưng chưa được implement code (tức là chưa có code gì trong nó)
- Class được gọi là `abstract` nếu có ***ít nhất một abstract method***
- Cái này được sử dụng khi class cha có các phương thức mà cần các class con của nó thực hiện
- Từ khóa được sử dụng là `abstract` với ví dụ:
```php
abstract class ParentClass {
    abstract public function someMethod1(); // ko yêu cầu tham số nào
    abstract public function someMethod2($name, $color); // yêu cầu 2 tham số
    abstract public function someMethod3() : string; // yêu cầu phải return về kết quả với kiểu string
}
```
- Mỗi khi ***kế thừa từ một abstract class***, các class con phải có các phương thức tương ứng với ***tên***, ***số tham số cần có*** (argument) và ***access modifier*** (cái này có thể thay đổi thành các access modifier flexible hơn). Tức là nếu abstract method mà là `protected` thì class con phải là `protected` hoặc `public`. Tóm lại là, cần các quy tắc sau khi kế thừa một abstract class:
    * Class con phải có các method với ***tên giống hệt*** như các abstract method của class cha và cũng ***phải định nghĩa chúng***
    * Các method này của class con phải có ***cùng access modifier*** (hoặc ***flexible hơn***) với abstract method của class cha
    * ***Số tham số tối thiểu*** của các method này trong class con phải ***tương ứng*** với của abstract method trong class cha. Ngoài ra có thể có thêm các ***tham số bổ sung***
- Ví dụ về ứng dụng của `abstract`:
```php
// Parent class
abstract class Car {
  public $name;
  public function __construct($name) {
    $this->name = $name;
  }
  abstract public function intro() : string;
}

// Child classes
class Audi extends Car {
  public function intro() : string {
    return "Choose German quality! I'm an $this->name!";
  }
}

class Volvo extends Car {
  public function intro() : string {
    return "Proud to be Swedish! I'm a $this->name!";
  }
}

class Citroen extends Car {
  public function intro() : string {
    return "French extravagance! I'm a $this->name!";
  }
}

// Create objects from the child classes
$audi = new Audi("Audi");
echo $audi->intro();
echo "<br>";

$volvo = new Volvo("Volvo");
echo $volvo->intro();
echo "<br>";

$citroen = new Citroen("Citroen");
echo $citroen->intro();
```

❗Ứng dụng: dùng để yêu cầu các class con phải có những method bắt buộc nào đó