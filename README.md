# The Rust Journey of a Person
**John Doe** | Aspiring Network Administrator | Learning Cisco VPN and Routing  
[LinkedIn](https://linkedin.com/in/your-profile) | [Cisco Learning Network](https://learningnetwork.cisco.com/your-profile)

![Cisco](https://img.shields.io/badge/Cisco-Networking-blue) ![VPN](https://img.shields.io/badge/Skill-VPN-green) ![CCNA](https://img.shields.io/badge/CCNA-In%20Progress-orange)

TABLE OF CONTENTS

1. Common Programming Concepts    
   1.1. Variables and Mutability    
   1.2. Data Types    
   1.3. Functions    
   1.4. Comments    
   1.5. Control Flow    
2. Understanding Ownership    
   2.1. What is Ownership?    
   2.2. References and Borrowing    
   2.3. The Slice Type    
3. Using Structs to Structrure Related Data    
   3.1. Defining and Instantiating Structs    
   3.2. An Example Program Using Structs    
   3.3. Method Syntax    
4. Enums and Pattern Matching    
   4.1. Defining an Enum    
   4.2. The match Control Flow Construct    
   4.3. Concise Control Flow with if let and let else    

---

## 1. Common Programming Concepts

### 1.1. Variables and Mutability
```rust
[dependencies]
rand = "0.8.5"
```
```rust
use std::io;
use rand::Rng;
use std::cmp::Ordering;
```
```rust
println!("Hello, world!");
let mut guess = String::new();
io::stdin().read_line(&mut guess).expect("Failed to read line");
let secret_number = rand::thread_rng().gen_range(1..=100);
let x = 5;
let mut x = 5;
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```
```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```
```rust
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");
}
```
```rust
fn main() {
    let spaces = "   ";
    let spaces = spaces.len();
}
```
```rust
let guess: u32 = "42".parse().expect("Not a number!");
```

### 1.2. Data Types
```rust
let y: f32 = 3.0; // f32
let f: bool = false; // with explicit type annotation
let z: char = 'ℤ'; // with explicit type annotation
```
```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);

let tup = (500, 6.4, 1);
let (x, y, z) = tup;
println!("The value of y is: {y}");

let x: (i32, f64, u8) = (500, 6.4, 1);
let five_hundred = x.0;
let six_point_four = x.1;
let one = x.2;

let a = [1, 2, 3, 4, 5];
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
let a: [i32; 5] = [1, 2, 3, 4, 5];
let a = [3; 5];

let a = [1, 2, 3, 4, 5];
let first = a[0];
let second = a[1];
```

### 1.3. Functions
**Functions**
```rust
fn main() {
    println!("Hello, world!");

    another_function();
}

fn another_function() {
    println!("Another function.");
}
```
**Parameters**
```rust
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("The value of x is: {x}");
}
```
```rust
fn main() {
    print_labeled_measurement(5, 'h');
}

fn print_labeled_measurement(value: i32, unit_label: char) {
    println!("The measurement is: {value}{unit_label}");
}
```
**Statements and Expressions**
```rust
fn main() {
    let y = {
        let x = 3;
        x + 1
    };

    println!("The value of y is: {y}");
}
```
**Functions with Return Values**
```rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();

    println!("The value of x is: {x}");
}
```
```rust
fn main() {
    let x = plus_one(5);

    println!("The value of x is: {x}");
}

fn plus_one(x: i32) -> i32 {
    x + 1
}
```

### 1.4. Comments
```rust
// So we’re doing something complicated here, long enough that we need
// multiple lines of comments to do it! Whew! Hopefully, this comment will
// explain what’s going on.
```

### 1.5. Control Flow
**if Expressions**
```rust
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```
```rust
fn main() {
    let number = 3;

    if number != 0 {
        println!("number was something other than zero");
    }
}
```
**Handling Multiple Conditions with else if**
```rust
fn main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```
**Using if in a let Statement**
```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {number}");
}
```
**Repeating Code with loop**
```rust
fn main() {
    loop {
        println!("again!");
    }
}
```
**Returning Values from Loops**
```rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {result}");
}
```
**Loop Labels to Disambiguate Between Multiple Loops**
```rust
fn main() {
    let mut count = 0;
    'counting_up: loop {
        println!("count = {count}");
        let mut remaining = 10;

        loop {
            println!("remaining = {remaining}");
            if remaining == 9 {
                break;
            }
            if count == 2 {
                break 'counting_up;
            }
            remaining -= 1;
        }

        count += 1;
    }
    println!("End count = {count}");
}
```
**Conditional Loops with while**
```rust
fn main() {
    let mut number = 3;

    while number != 0 {
        println!("{number}!");

        number -= 1;
    }

    println!("LIFTOFF!!!");
}
```
**Looping Through a Collection with for**
```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;

    while index < 5 {
        println!("the value is: {}", a[index]);

        index += 1;
    }
}
```
```rust
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a {
        println!("the value is: {element}");
    }
}
```
```rust
fn main() {
    for number in (1..4).rev() {
        println!("{number}!");
    }
    println!("LIFTOFF!!!");
}
```

## 2. Understanding Ownership

### 2.1. What is Ownership?
**The String Type**
```rust
fn main() {
    let mut s = String::from("hello");

    s.push_str(", world!"); // push_str() appends a literal to a String

    println!("{s}"); // This will print `hello, world!`
}
```
**Variables and Data Interacting with Clone**
```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {s1}, s2 = {s2}");
}
```
**Ownership and Functions**
```rust
fn main() {
    let s = String::from("hello");  // s comes into scope

    takes_ownership(s);             // s's value moves into the function...
                                    // ... and so is no longer valid here

    let x = 5;                      // x comes into scope

    makes_copy(x);                  // because i32 implements the Copy trait,
                                    // x does NOT move into the function,
    println!("{}", x);              // so it's okay to use x afterward

} // Here, x goes out of scope, then s. But because s's value was moved, nothing
  // special happens.

fn takes_ownership(some_string: String) { // some_string comes into scope
    println!("{some_string}");
} // Here, some_string goes out of scope and `drop` is called. The backing
  // memory is freed.

fn makes_copy(some_integer: i32) { // some_integer comes into scope
    println!("{some_integer}");
} // Here, some_integer goes out of scope. Nothing special happens.
```
**Return Values and Scope**
```rust
fn main() {
    let s1 = gives_ownership();         // gives_ownership moves its return
                                        // value into s1

    let s2 = String::from("hello");     // s2 comes into scope

    let s3 = takes_and_gives_back(s2);  // s2 is moved into
                                        // takes_and_gives_back, which also
                                        // moves its return value into s3
} // Here, s3 goes out of scope and is dropped. s2 was moved, so nothing
  // happens. s1 goes out of scope and is dropped.

fn gives_ownership() -> String {             // gives_ownership will move its
                                             // return value into the function
                                             // that calls it

    let some_string = String::from("yours"); // some_string comes into scope

    some_string                              // some_string is returned and
                                             // moves out to the calling
                                             // function
}

// This function takes a String and returns one
fn takes_and_gives_back(a_string: String) -> String { // a_string comes into
                                                      // scope

    a_string  // a_string is returned and moves out to the calling function
}
```
```rust
fn main() {
    let s1 = String::from("hello");

    let (s2, len) = calculate_length(s1);

    println!("The length of '{s2}' is {len}.");
}

fn calculate_length(s: String) -> (String, usize) {
    let length = s.len(); // len() returns the length of a String

    (s, length)
}
```

### 2.2. References and Borrowing
```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{s1}' is {len}.");
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

### 2.3. The Slice Type
**Objective**: Prioritize video streaming traffic over file downloads.  
**Steps**:  
- Enabled QoS in the RV160 web interface (QoS > Bandwidth Management).  
- Set a rule to prioritize traffic on port 1935 (used for RTMP streaming) over other traffic.  
**Result**: Streaming quality improved significantly during high network usage.  
[Screenshots](screenshots/rv160-qos-config.png)

## 3. Using Structs to Structrure Related Data

### 3.1. Defining and Instantiating Structs
**Issue**: Encountered a 502 Bad Gateway error after replacing the RV320’s default certificate with a newly generated one.  
**Impact**: Lost access to the admin interface (https://192.168.1.1).  
**Details**: The router’s Nginx server (v1.16.1) couldn’t communicate with the backend service, likely due to a certificate misconfiguration.

### 3.2. An Example Program Using Structs
**Steps**:  
- Pressed and held the reset button for 30 seconds, but the router didn’t fully reset.  
- Tried the 30-30-30 method (hold reset, unplug, hold, plug back in), but still no access.  
**Finding**: The RV320 has a known issue where hardware resets don’t clear custom certificates.

### 3.3. Method Syntax
**Solution**: Used TFTP to flash the firmware and regain access.  
**Steps**:  
- Downloaded the latest RV320 firmware (RV32X_v1.5.1.05_20191001-code.bin) from Cisco’s website.  
- Put the router into TFTP mode by holding the reset button while powering on.  
- Used Tftpd64 to upload the firmware to 192.168.1.1.  
**Result**: Router rebooted with factory settings, and I regained access to the admin interface.  
[See TFTP Log](logs/rv320-tftp-recovery.log)

## 4. Enums and Pattern Matching

### 4.1. Defining an Enum
- Set up OpenVPN on the RV160 for secure remote access.  
- Learned how to generate certificates and configure firewall rules for VPN traffic.

### 4.2. The match Control Flow Construct
- Configured VLANs on the RV160 to separate Work and Guest traffic.  
- Understood the importance of VLANs for security and performance.

### 4.3. Concise Control Flow with if let and let else
- Diagnosed and resolved a 502 Bad Gateway error on the RV320.  
- Learned how to use TFTP to recover a bricked router, a valuable skill for network administration.

---

## Connect with Me
- [LinkedIn](https://linkedin.com/in/your-profile)
- [YouTube](https://youtube.com/your-channel)
- [Personal Blog](https://your-blog.com)
