# 1. Design and validate this form with proper code.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>User Registration</title>
</head>
<body>
    <h2>User Registration Form</h2>
    <form action="index.php" method="post">
        <label for="username">Username:</label><br>
        <input type="text" id="username" name="username" required><br><br>

        <label for="email">Email:</label><br>
        <input type="email" id="email" name="email" required><br><br>

        <label for="password">Password:</label><br>
        <input type="password" id="password" name="password" required><br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Capture form data
    $username = trim($_POST['username']);
    $email = trim($_POST['email']);
    $password = trim($_POST['password']);

    // Initialize an array to hold error messages
    $errors = [];

    // Validate username
    if (empty($username)) {
        $errors[] = "Username is required.";
    } elseif (strlen($username) < 3) {
        $errors[] = "Username must be at least 3 characters long.";
    }

    // Validate email
    if (empty($email)) {
        $errors[] = "Email is required.";
    } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errors[] = "Invalid email format.";
    }

    // Validate password
    if (empty($password)) {
        $errors[] = "Password is required.";
    } elseif (strlen($password) < 6) {
        $errors[] = "Password must be at least 6 characters long.";
    }

    // If there are no errors, process the data (e.g., save to database)
    if (empty($errors)) {
        // Here you would typically hash the password and save the user data to a database
        // For example:
        // $hashedPassword = password_hash($password, PASSWORD_DEFAULT);
        // Save $username, $email, and $hashedPassword to your database

        echo "<p>Registration successful!</p>";
    } else {
        // Display errors
        foreach ($errors as $error) {
            echo "<p style='color:red;'>$error</p>";
        }
    }
}
?>
```

![alt text](<../img/Screenshot 2024-11-28 200058.png>)

# 2. Build a HTML form and write PHP code to calculate Largest among three numbers using a) If_else b) conditional operator.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Find Largest Number</title>
</head>
<body>
    <h2>Find the Largest Among Three Numbers</h2>
    <form action="largest.php" method="post">
        <label for="num1">Number 1:</label><br>
        <input type="number" id="num1" name="num1" required><br><br>

        <label for="num2">Number 2:</label><br>
        <input type="number" id="num2" name="num2" required><br><br>

        <label for="num3">Number 3:</label><br>
        <input type="number" id="num3" name="num3" required><br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Capture form data
    $num1 = $_POST['num1'];
    $num2 = $_POST['num2'];
    $num3 = $_POST['num3'];

    // Method a: Using if-else
    $largest_if_else = $num1; // Assume num1 is the largest initially

    if ($num2 > $largest_if_else) {
        $largest_if_else = $num2; // Update if num2 is larger
    }
    if ($num3 > $largest_if_else) {
        $largest_if_else = $num3; // Update if num3 is larger
    }

    // Method b: Using conditional operator
    $largest_conditional = ($num1 > $num2) ? (($num1 > $num3) ? $num1 : $num3) : (($num2 > $num3) ? $num2 : $num3);

    // Display results
    echo "<h3>Results:</h3>";
    echo "<p>Largest number using if-else: $largest_if_else</p>";
    echo "<p>Largest number using conditional operator: $largest_conditional</p>";
}
?>
```

![alt text](<../img/Screenshot 2024-11-28 202801.png>)

# 3. Build a HTML form and write PHP code to design a calculator program to show use of +,-,* ,/ operators.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Simple Calculator</title>
</head>
<body>
    <h2>Simple Calculator</h2>
    <form action="index.php" method="post">
        <label for="num1">Number 1:</label><br>
        <input type="number" id="num1" name="num1" required><br><br>

        <label for="num2">Number 2:</label><br>
        <input type="number" id="num2" name="num2" required><br><br>

        <label for="operation">Select Operation:</label><br>
        <select id="operation" name="operation" required>
            <option value="+">Addition (+)</option>
            <option value="-">Subtraction (-)</option>
            <option value="*">Multiplication (*)</option>
            <option value="/">Division (/)</option>
        </select><br><br>

        <input type="submit" value="Calculate">
    </form>
</body>
</html>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Capture form data
    $num1 = $_POST['num1'];
    $num2 = $_POST['num2'];
    $operation = $_POST['operation'];
    $result = "";

    // Perform the selected operation
    switch ($operation) {
        case '+':
            $result = $num1 + $num2;
            break;
        case '-':
            $result = $num1 - $num2;
            break;
        case '*':
            $result = $num1 * $num2;
            break;
        case '/':
            // Check for division by zero
            if ($num2 == 0) {
                $result = "Error: Division by zero is not allowed.";
            } else {
                $result = $num1 / $num2;
            }
            break;
        default:
            $result = "Invalid operation.";
            break;
    }

    // Display the result
    echo "<h3>Result:</h3>";
    echo "<p>$num1 $operation $num2 = $result</p>";
}
?>
```

![alt text](<../img/Screenshot 2024-11-28 234056.png>)

# 4. Design and validate the form-

```php
<?php
// Check if the form was submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Get the form data
    $name = $_POST["name"];
    $fatherName = $_POST["fatherName"];
    $postalAddress = $_POST["postalAddress"];
    $personalAddress = $_POST["personalAddress"];
    $sex = $_POST["sex"];
    $city = $_POST["city"];
    $course = $_POST["course"];
    $district = $_POST["district"];
    $state = $_POST["state"];
    $pinCode = $_POST["pinCode"];
    $email = $_POST["email"];
    $dob = $_POST["dob"];
    $mobileNo = $_POST["mobileNo"];

    // Validate the form data
    $errors = array();

    // Validate name
    if (empty($name)) {
        $errors["name"] = "Name is required.";
    }

    // Validate father's name
    if (empty($fatherName)) {
        $errors["fatherName"] = "Father's name is required.";
    }

    // Validate postal address
    if (empty($postalAddress)) {
        $errors["postalAddress"] = "Postal address is required.";
    }

    // Validate personal address
    if (empty($personalAddress)) {
        $errors["personalAddress"] = "Personal address is required.";
    }

    // Validate sex
    if ($sex != "Male" && $sex != "Female") {
        $errors["sex"] = "Sex must be either 'Male' or 'Female'.";
    }

    // Validate city
    if (empty($city)) {
        $errors["city"] = "City is required.";
    }

    // Validate course
    if (empty($course)) {
        $errors["course"] = "Course is required.";
    }

    // Validate district
    if (empty($district)) {
        $errors["district"] = "District is required.";
    }

    // Validate state
    if (empty($state)) {
        $errors["state"] = "State is required.";
    }

    // Validate pin code
    if (empty($pinCode)) {
        $errors["pinCode"] = "Pin code is required.";
    }

    // Validate email
    if (empty($email)) {
        $errors["email"] = "Email is required.";
    } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errors["email"] = "Invalid email format.";
    }

    // Validate date of birth
    if (empty($dob)) {
        $errors["dob"] = "Date of birth is required.";
    }

    // Validate mobile number
    if (empty($mobileNo)) {
        $errors["mobileNo"] = "Mobile number is required.";
    } elseif (!preg_match("/^[0-9]{10}$/", $mobileNo)) {
        $errors["mobileNo"] = "Invalid mobile number format.";
    }

    // If there are no errors, process the form data
    if (empty($errors)) {
        echo "Form submitted successfully!";
        // You can add code here to save the form data to a database or perform other actions
    } else {
        echo "Please fix the following errors:";
        foreach ($errors as $error) {
            echo "<br>" . $error;
        }
    }
}
?>

<!DOCTYPE html>
<html>
<head>
    <title>Student Registration Form</title>
</head>
<body>
    <h1>Student Registration Form</h1>
    <form method="post" action="index.php">
        Name: <input type="text" name="name" value="<?php echo isset($name) ? $name : '';?>"><br>
        Father Name: <input type="text" name="fatherName" value="<?php echo isset($fatherName) ? $fatherName : '';?>"><br>
        Postal Address: <input type="text" name="postalAddress" value="<?php echo isset($postalAddress) ? $postalAddress : '';?>"><br>
        Personal Address: <input type="text" name="personalAddress" value="<?php echo isset($personalAddress) ? $personalAddress : '';?>"><br>
        Sex: <input type="radio" name="sex" value="Male" <?php echo isset($sex) && $sex == "Male" ? 'checked' : '';?>>Male
             <input type="radio" name="sex" value="Female" <?php echo isset($sex) && $sex == "Female" ? 'checked' : '';?>>Female<br>
        City: <input type="text" name="city" value="<?php echo isset($city) ? $city : '';?>"><br>
        Course: <select name="course">
                    <option value="">Select Course</option>
                    <option value="Course1" <?php echo isset($course) && $course == "Course1" ? 'selected' : '';?>>Course1</option>
                    <option value="Course2" <?php echo isset($course) && $course == "Course2" ? 'selected' : '';?>>Course2</option>
                    <option value="Course3" <?php echo isset($course) && $course == "Course3" ? 'selected' : '';?>>Course3</option>
                </select><br>
        District: <input type="text" name="district" value="<?php echo isset($district) ? $district : '';?>"><br>
        State: <input type="text" name="state" value="<?php echo isset($state) ? $state : '';?>"><br>
        Pin Code: <input type="text" name="pinCode" value="<?php echo isset($pinCode) ? $pinCode : '';?>"><br>
        Email: <input type="email" name="email" value="<?php echo isset($email) ? $email : '';?>"><br>
        DOB: <input type="date" name="dob" value="<?php echo isset($dob) ? $dob : '';?>"><br>
        Mobile No: <input type="text" name="mobileNo" value="<?php echo isset($mobileNo) ? $mobileNo : '';?>"><br>
        <input type="submit" name="submit" value="Submit Form">
    </form>
</body>
</html>
```

# 5. Write a JavaScript function that checks whether a passed string is palindrome or not in a HTML form

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Palindrome Checker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 50px;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Palindrome Checker</h1>
    <form id="palindromeForm">
        <label for="inputString">Enter a string:</label>
        <input type="text" id="inputString" required>
        <button type="submit">Check</button>
    </form>

    <div id="result"></div>

    <script>
        function isPalindrome(str) {
            // Remove non-alphanumeric characters and convert to lowercase
            const cleanedStr = str.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
            const reversedStr = cleanedStr.split('').reverse().join('');
            return cleanedStr === reversedStr;
        }

        document.getElementById('palindromeForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission
            const inputString = document.getElementById('inputString').value;
            const resultDiv = document.getElementById('result');
            
            if (isPalindrome(inputString)) {
                resultDiv.textContent = `"${inputString}" is a palindrome.`;
                resultDiv.style.color = 'green';
            } else {
                resultDiv.textContent = `"${inputString}" is not a palindrome.`;
                resultDiv.style.color = 'red';
            }
        });
    </script>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-11-28 234420.png>)

# 6. Validate the form designed in HTML by PHP.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Contact Us</title>
</head>
<body>

    <h1>Contact Us</h1>

    <?php
    // Initialize variables and error messages
    $name = $email = $city = $description = $contact_number = "";
    $nameErr = $emailErr = $cityErr = $descriptionErr = "";

    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Validate name
        if (empty($_POST["name"])) {
            $nameErr = "Name is required";
        } else {
            $name = htmlspecialchars(trim($_POST["name"]));
        }

        // Validate email
        if (empty($_POST["email"])) {
            $emailErr = "Email is required";
        } else {
            $email = htmlspecialchars(trim($_POST["email"]));
            if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
                $emailErr = "Invalid email format";
            }
        }

        // Validate city
        if (empty($_POST["city"])) {
            $cityErr = "City is required";
        } else {
            $city = htmlspecialchars(trim($_POST["city"]));
        }

        // Validate description
        if (empty($_POST["description"])) {
            $descriptionErr = "Description is required";
        } else {
            $description = htmlspecialchars(trim($_POST["description"]));
        }

        // Optional contact number
        if (!empty($_POST["contact_number"])) {
            $contact_number = htmlspecialchars(trim($_POST["contact_number"]));
        }

        if (empty($nameErr) && empty($emailErr) && empty($cityErr) && empty($descriptionErr)) {
            echo "<h3>Thank you for contacting us, $name!</h3>";
        }
    }
    ?>

    <form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
        <fieldset>
            <legend>[Your details]</legend>
            <label for="name">Name <span class="error">*</span>:</label><br>
            <input type="text" id="name" name="name" value="<?php echo $name; ?>">
            <span class="error"><?php echo $nameErr; ?></span><br><br>

            <label for="email">Email <span class="error">*</span>:</label><br>
            <input type="email" id="email" name="email" value="<?php echo $email; ?>">
            <span class="error"><?php echo $emailErr; ?></span><br><br>

            <label for="city">City <span class="error">*</span>:</label><br>
            <input type="text" id="city" name="city" value="<?php echo $city; ?>">
            <span class="error"><?php echo $cityErr; ?></span><br><br>

            <label for="contact_number">Contact Number:</label><br>
            <input type="text" id="contact_number" name="contact_number" value="<?php echo $contact_number; ?>"><br><br>

            <label for="description">Description <span class="error">*</span>:</label><br>
            <textarea id="description" name="description"><?php echo $description; ?></textarea>
            <span class="error"><?php echo $descriptionErr; ?></span><br><br>
        </fieldset>
        
        <button type="submit">Submit</button>
        <button type="button" onclick="window.location.href='index.php';">Cancel</button>
    </form>

</body>

</html>
```

![alt text](<../img/Screenshot 2024-11-28 233708.png>)

# 7. In a HTML form write a JavaScript function that generates all combinations of a string.

_Example string :_ 'dog'  
_Expected Output :_ d,do,dog,o,og,g

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>String Combinations Generator</title>
</head>
<body>
    <h1>String Combinations Generator</h1>
    <form id="combinationForm">
        <label for="inputString">Enter a string:</label>
        <input type="text" id="inputString" required>
        <button type="submit">Generate Combinations</button>
    </form>

    <div id="result"></div>

    <script>
        function generateCombinations(str) {
            const combinations = [];
            const length = str.length;

            // Generate combinations
            for (let i = 0; i < length; i++) {
                for (let j = i + 1; j <= length; j++) {
                    combinations.push(str.slice(i, j));
                }
            }
            return combinations;
        }

        document.getElementById('combinationForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission
            const inputString = document.getElementById('inputString').value;
            const resultDiv = document.getElementById('result');
            
            const combinations = generateCombinations(inputString);
            resultDiv.textContent = `Combinations: ${combinations.join(', ')}`;
        });
    </script>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-11-28 234654.png>)

# 8. Write these programs in PHP.

## a. Swap two numbers using function in PHP.

```php
<?php
function swapNumbers(&$a, &$b) {
  // Swapping the values using pointers
  $temp = $a;
  $a = $b;
  $b = $temp;
}

// Example usage
$num1 = 10;
$num2 = 20;

echo "Before swapping: num1 = $num1, num2 = $num2\n";

// Calling the swapNumbers function to swap the values
swapNumbers($num1, $num2);

echo "After swapping: num1 = $num1, num2 = $num2\n";
?>
```

## b. Factorial of a number using function in PHP.

```php
<?php
function factorial($n) {
  if ($n == 0) {
    return 1;
  } else {
    return $n * factorial($n - 1);
  }
}

// Get the number from the user
$number = 5;

// Calculate the factorial of the number
$result = factorial($number);

// Display the result
echo "The factorial of $number is $result";
?>
```

# 9. Use recursion to solve the following exercises.

## a. Write a JavaScript program to calculate the factorial of a number.

```js
function factorial(n) {
  if (n === 0) {
    return 1;
  } else {
    return n * factorial(n - 1);
  }
}

// Example usage:
let num = 5;
let result = factorial(num);
console.log(`The factorial of ${num} is ${result}`);
```

## b. Write a JavaScript program to find the greatest common divisor (gcd) of two positive numbers.

```js
function gcd(a, b) {
  // Base case: If b is 0, then a is the GCD
  if (b === 0) {
    return a;
  }
  // Recursive case: Find the GCD of b and the remainder of a divided by b
  return gcd(b, a % b);
}

// Example usage:
const num1 = 24;
const num2 = 36;
const greatestCommonDivisor = gcd(num1, num2);
console.log(`The GCD of ${num1} and ${num2} is: ${greatestCommonDivisor}`);
```

# 10. In a HTML form using PHP 

## a. Check a number whether it is even or odd.

```php
<!DOCTYPE html>
<html>
<head>
    <title>Even/Odd Checker</title>
</head>
<body>
    <form method="post">
        Enter a number: <input type="number" name="number" required>
        <input type="submit" value="Check">
    </form>

    <?php
    if (isset($_POST['number'])) {
        $number = $_POST['number'];
        if ($number % 2 == 0) {
            echo "$number is even.";
        } else {
            echo "$number is odd.";
        }
    }
    ?>
</body>
</html>
```

## b. Check a year whether it is leap year or not.

```php
<!DOCTYPE html>
<html>
<head>
    <title>Leap Year Checker</title>
</head>
<body>
    <form method="post">
        Enter a year: <input type="number" name="year" required>
        <input type="submit" value="Check">
    </form>

    <?php
    if (isset($_POST['year'])) {
        $year = $_POST['year'];
        if ((($year % 4 == 0) && ($year % 100 != 0)) || ($year % 400 == 0)) {
            echo "$year is a leap year.";
        } else {
            echo "$year is not a leap year.";
        }
    }
    ?>
</body>
</html>
```
