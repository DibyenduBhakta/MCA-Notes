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

# 3. Build a HTML form and write PHP code to design a calculator program to show use of +,-,\* ,/ operators.

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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Registration Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            margin: 0;
        }
        .form-container {
            background-color: #b2fefa;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 400px;
            text-align: center;
            margin: auto;
        }
        form{
            text-align: left;
        }
        .form-container h2 {
            text-align: center;
            margin-bottom: 20px;
        }
        .form-container label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        .form-container input,
        .form-container select {
            width: 100%;
            padding: 8px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .form-container input[type="radio"] {
            width: auto;
            margin-right: 5px;
        }
        .form-container .buttons {
            display: flex;
            justify-content: space-between;
        }
        .form-container button {
            padding: 10px 20px;
            background-color: #007acc;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .form-container button:hover {
            background-color: #005f99;
        }

        .error {
            color: red;
            font-size: 0.9em;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Student Registration Form</h2>
        <?php
        $errors = [];
        $inputs = [];

        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            $inputs['name'] = trim($_POST['name']);
            $inputs['father_name'] = trim($_POST['father_name']);
            $inputs['postal_address'] = trim($_POST['postal_address']);
            $inputs['personal_address'] = trim($_POST['personal_address']);
            $inputs['sex'] = $_POST['sex'] ?? '';
            $inputs['city'] = $_POST['city'] ?? '';
            $inputs['course'] = $_POST['course'] ?? '';
            $inputs['district'] = $_POST['district'] ?? '';
            $inputs['state'] = $_POST['state'] ?? '';
            $inputs['pincode'] = trim($_POST['pincode']);
            $inputs['email'] = trim($_POST['email']);
            $inputs['dob'] = trim($_POST['dob']);
            $inputs['mobile_no'] = trim($_POST['mobile_no']);

            // Validation
            if (empty($inputs['name'])) $errors['name'] = "Name is required.";
            if (empty($inputs['father_name'])) $errors['father_name'] = "Father's name is required.";
            if (empty($inputs['postal_address'])) $errors['postal_address'] = "Postal address is required.";
            if (empty($inputs['personal_address'])) $errors['personal_address'] = "Personal address is required.";
            if (empty($inputs['sex'])) $errors['sex'] = "Please select your gender.";
            if (empty($inputs['city'])) $errors['city'] = "City is required.";
            if (empty($inputs['course'])) $errors['course'] = "Please select a course.";
            if (empty($inputs['district'])) $errors['district'] = "District is required.";
            if (empty($inputs['state'])) $errors['state'] = "State is required.";
            if (!preg_match('/^\d{6}$/', $inputs['pincode'])) $errors['pincode'] = "Pincode must be 6 digits.";
            if (!filter_var($inputs['email'], FILTER_VALIDATE_EMAIL)) $errors['email'] = "Invalid email format.";
            if (!preg_match('/^\d{10}$/', $inputs['mobile_no'])) $errors['mobile_no'] = "Mobile number must be 10 digits.";

            if (empty($errors)) {
                echo "<p style='color: green; text-align: center;'>Form submitted successfully!</p>";
            }
        }
        ?>
        <form action="" method="post">
            <label for="name">Name</label>
            <input type="text" name="name" id="name" value="<?= htmlspecialchars($inputs['name'] ?? '') ?>">
            <span class="error"><?= $errors['name'] ?? '' ?></span>

            <label for="father_name">Father Name</label>
            <input type="text" name="father_name" id="father_name" value="<?= htmlspecialchars($inputs['father_name'] ?? '') ?>">
            <span class="error"><?= $errors['father_name'] ?? '' ?></span>

            <label for="postal_address">Postal Address</label>
            <input type="text" name="postal_address" id="postal_address" value="<?= htmlspecialchars($inputs['postal_address'] ?? '') ?>">
            <span class="error"><?= $errors['postal_address'] ?? '' ?></span>

            <label for="personal_address">Personal Address</label>
            <input type="text" name="personal_address" id="personal_address" value="<?= htmlspecialchars($inputs['personal_address'] ?? '') ?>">
            <span class="error"><?= $errors['personal_address'] ?? '' ?></span>

            <label>Sex</label>
            <input type="radio" name="sex" value="Male" <?= (isset($inputs['sex']) && $inputs['sex'] === "Male") ? 'checked' : '' ?>> Male
            <input type="radio" name="sex" value="Female" <?= (isset($inputs['sex']) && $inputs['sex'] === "Female") ? 'checked' : '' ?>> Female
            <span class="error"><?= $errors['sex'] ?? '' ?></span>

            <label for="city">City</label>
            <select name="city" id="city">
                <option value="">select..</option>
                <option value="City1" <?= (isset($inputs['city']) && $inputs['city'] === "City1") ? 'selected' : '' ?>>City1</option>
                <option value="City2" <?= (isset($inputs['city']) && $inputs['city'] === "City2") ? 'selected' : '' ?>>City2</option>
            </select>
            <span class="error"><?= $errors['city'] ?? '' ?></span>

            <label for="course">Course</label>
            <select name="course" id="course">
                <option value="">select</option>
                <option value="Course1" <?= (isset($inputs['course']) && $inputs['course'] === "Course1") ? 'selected' : '' ?>>Course1</option>
                <option value="Course2" <?= (isset($inputs['course']) && $inputs['course'] === "Course2") ? 'selected' : '' ?>>Course2</option>
            </select>
            <span class="error"><?= $errors['course'] ?? '' ?></span>

            <label for="district">District</label>
            <select name="district" id="district">
                <option value="">select</option>
                <option value="District1" <?= (isset($inputs['district']) && $inputs['district'] === "District1") ? 'selected' : '' ?>>District1</option>
                <option value="District2" <?= (isset($inputs['district']) && $inputs['district'] === "District2") ? 'selected' : '' ?>>District2</option>
            </select>
            <span class="error"><?= $errors['district'] ?? '' ?></span>

            <label for="state">State</label>
            <select name="state" id="state">
                <option value="">select..</option>
                <option value="State1" <?= (isset($inputs['state']) && $inputs['state'] === "State1") ? 'selected' : '' ?>>State1</option>
                <option value="State2" <?= (isset($inputs['state']) && $inputs['state'] === "State2") ? 'selected' : '' ?>>State2</option>
            </select>
            <span class="error"><?= $errors['state'] ?? '' ?></span>

            <label for="pincode">PinCode</label>
            <input type="number" name="pincode" id="pincode" value="<?= htmlspecialchars($inputs['pincode'] ?? '') ?>">
            <span class="error"><?= $errors['pincode'] ?? '' ?></span>

            <label for="email">Email ID</label>
            <input type="email" name="email" id="email" value="<?= htmlspecialchars($inputs['email'] ?? '') ?>">
            <span class="error"><?= $errors['email'] ?? '' ?></span>

            <label for="dob">DOB</label>
            <input type="date" name="dob" id="dob" value="<?= htmlspecialchars($inputs['dob'] ?? '') ?>">
            <span class="error"><?= $errors['dob'] ?? '' ?></span>

            <label for="mobile_no">Mobile No</label>
            <input type="number" name="mobile_no" id="mobile_no" value="<?= htmlspecialchars($inputs['mobile_no'] ?? '') ?>">
            <span class="error"><?= $errors['mobile_no'] ?? '' ?></span>

            <div class="buttons">
                <button type="reset">Reset</button>
                <button type="submit">Submit Form</button>
            </div>
        </form>
    </div>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-12-01 010312.png>)

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
      <input type="text" id="inputString" required />
      <button type="submit">Check</button>
    </form>

    <div id="result"></div>

    <script>
      function isPalindrome(str) {
        // Remove non-alphanumeric characters and convert to lowercase
        const cleanedStr = str.replace(/[^A-Za-z0-9]/g, "").toLowerCase();
        const reversedStr = cleanedStr.split("").reverse().join("");
        return cleanedStr === reversedStr;
      }

      document
        .getElementById("palindromeForm")
        .addEventListener("submit", function (event) {
          event.preventDefault(); // Prevent form submission
          const inputString = document.getElementById("inputString").value;
          const resultDiv = document.getElementById("result");

          if (isPalindrome(inputString)) {
            resultDiv.textContent = `"${inputString}" is a palindrome.`;
            resultDiv.style.color = "green";
          } else {
            resultDiv.textContent = `"${inputString}" is not a palindrome.`;
            resultDiv.style.color = "red";
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

*Example string :* 'dog'  
*Expected Output :* d,do,dog,o,og,g

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
      <input type="text" id="inputString" required />
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

      document
        .getElementById("combinationForm")
        .addEventListener("submit", function (event) {
          event.preventDefault(); // Prevent form submission
          const inputString = document.getElementById("inputString").value;
          const resultDiv = document.getElementById("result");

          const combinations = generateCombinations(inputString);
          resultDiv.textContent = `Combinations: ${combinations.join(", ")}`;
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

// OUTPUT = The factorial of 4 is 24
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
const num1 = 48;
const num2 = 36;
const greatestCommonDivisor = gcd(num1, num2);
console.log(`The GCD of ${num1} and ${num2} is: ${greatestCommonDivisor}`);

// OUTPUT = The GCD of 48 and 36 is: 12
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

![alt text](<../img/Screenshot 2024-11-29 202059.png>)

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

![alt text](<../img/Screenshot 2024-11-29 201652.png>)

# 11. Design and validate the form.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5faff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .form-container {
            background-color: #eaf3fc;
            padding: 20px;
            border-radius: 10px;
            width: 400px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border: 1px solid #d1e7fd;
        }
        .form-container h2 {
            text-align: center;
            margin-bottom: 20px;
        }
        .form-container label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        .form-container input,
        .form-container select,
        .form-container textarea {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        .form-container input[type="radio"],
        .form-container input[type="checkbox"] {
            width: auto;
        }
        .form-container button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .form-container button:hover {
            background-color: #0056b3;
        }
        .error {
            color: red;
            font-size: 0.9em;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Registration Form</h2>
        <?php
        $errors = [];
        $inputs = [];

        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            $inputs['name'] = trim($_POST['name']);
            $inputs['email'] = trim($_POST['email']);
            $inputs['education'] = $_POST['education'] ?? '';
            $inputs['gender'] = $_POST['gender'] ?? '';
            $inputs['hobbies'] = $_POST['hobbies'] ?? [];
            $inputs['comment'] = trim($_POST['comment']);

            // Validation
            if (empty($inputs['name'])) $errors['name'] = "Name cannot be left blank.";
            if (empty($inputs['email']) || !filter_var($inputs['email'], FILTER_VALIDATE_EMAIL)) $errors['email'] = "Email cannot be left blank or must be valid.";
            if (empty($inputs['education'])) $errors['education'] = "Tell us about your education.";
            if (empty($inputs['gender'])) $errors['gender'] = "Specify your gender.";
            if (empty($inputs['hobbies'])) $errors['hobbies'] = "What are your hobbies?";
            if (empty($inputs['comment'])) $errors['comment'] = "This field is required.";

            if (empty($errors)) {
                echo "<p style='color: green; text-align: center;'>Form submitted successfully!</p>";
            }
        }
        ?>
        <form action="" method="post">
            <label for="name">Name</label>
            <input type="text" name="name" id="name" value="<?= htmlspecialchars($inputs['name'] ?? '') ?>">
            <span class="error"><?= $errors['name'] ?? '' ?></span>

            <label for="email">Email</label>
            <input type="email" name="email" id="email" value="<?= htmlspecialchars($inputs['email'] ?? '') ?>">
            <span class="error"><?= $errors['email'] ?? '' ?></span>

            <label for="education">Education</label>
            <select name="education" id="education">
                <option value="">...</option>
                <option value="High School" <?= (isset($inputs['education']) && $inputs['education'] === "High School") ? 'selected' : '' ?>>High School</option>
                <option value="Undergraduate" <?= (isset($inputs['education']) && $inputs['education'] === "Undergraduate") ? 'selected' : '' ?>>Undergraduate</option>
                <option value="Postgraduate" <?= (isset($inputs['education']) && $inputs['education'] === "Postgraduate") ? 'selected' : '' ?>>Postgraduate</option>
            </select>
            <span class="error"><?= $errors['education'] ?? '' ?></span>

            <label>Gender</label>
            <input type="radio" name="gender" value="Male" <?= (isset($inputs['gender']) && $inputs['gender'] === "Male") ? 'checked' : '' ?>> Male
            <input type="radio" name="gender" value="Female" <?= (isset($inputs['gender']) && $inputs['gender'] === "Female") ? 'checked' : '' ?>> Female
            <span class="error"><?= $errors['gender'] ?? '' ?></span>

            <label>Hobbies</label>
            <input type="checkbox" name="hobbies[]" value="Drawing" <?= (isset($inputs['hobbies']) && in_array("Drawing", $inputs['hobbies'])) ? 'checked' : '' ?>> Drawing
            <input type="checkbox" name="hobbies[]" value="Singing" <?= (isset($inputs['hobbies']) && in_array("Singing", $inputs['hobbies'])) ? 'checked' : '' ?>> Singing
            <input type="checkbox" name="hobbies[]" value="Dancing" <?= (isset($inputs['hobbies']) && in_array("Dancing", $inputs['hobbies'])) ? 'checked' : '' ?>> Dancing
            <span class="error"><?= $errors['hobbies'] ?? '' ?></span>

            <label for="comment">Comment</label>
            <textarea name="comment" id="comment" rows="4"><?= htmlspecialchars($inputs['comment'] ?? '') ?></textarea>
            <span class="error"><?= $errors['comment'] ?? '' ?></span>

            <button type="submit">Submit</button>
        </form>
    </div>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-12-01 011155.png>)

# 12.

## a. Write a JavaScript program to sort 50 natural numbers.

```js
// Function to generate an array of random natural numbers
function generateNumbers(count, max) {
  const numbers = [];
  for (let i = 0; i < count; i++) {
    // Generate a random natural number between 1 and max
    const randomNum = Math.floor(Math.random() * max) + 1;
    numbers.push(randomNum);
  }
  return numbers;
}

// Function to sort an array of numbers
function sortNumbers(arr) {
  return [...arr].sort((a, b) => a - b);
}

// Generate 50 random natural numbers
const randomNumbers = generateNumbers(50, 100); // Adjust max as needed

// Sort the numbers
const sortedNumbers = sortNumbers(randomNumbers);

// Output the sorted numbers
console.log("Random Natural Numbers:", randomNumbers);
console.log("Sorted Natural Numbers:", sortedNumbers);
```

![alt text](<../img/Screenshot 2024-11-29 201344.png>)

## b. Write a JavaScript program that accept two integers and display the larger.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Find Larger Integer</title>
  </head>
  <body>
    <h1>Find the Larger Integer</h1>
    <label for="num1">Enter first integer:</label>
    <input type="number" id="num1" required />
    <br />
    <label for="num2">Enter second integer:</label>
    <input type="number" id="num2" required />
    <br />
    <button onclick="findLarger()">Find Larger</button>
    <h2 id="result"></h2>

    <script>
      function findLarger() {
        // Get the values from the input fields
        const num1 = parseInt(document.getElementById("num1").value);
        const num2 = parseInt(document.getElementById("num2").value);
        // Check if the inputs are valid integers
        if (isNaN(num1) || isNaN(num2)) {
          document.getElementById("result").innerText =
            "Please enter valid integers.";
          return;
        }

        // Determine the larger number
        const larger = num1 > num2 ? num1 : num2;

        // Display the result
        document.getElementById(
          "result"
        ).innerText = `The larger integer is: ${larger}`;
      }
    </script>
  </body>
</html>
```

![alt text](<../img/Screenshot 2024-11-29 200838.png>)

# 13. Print the Patterns below using PHP in HTML form:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Pattern Generator</title>
</head>
<body>
    <h1>Pattern Generator</h1>
    <form method="POST">
        <label for="num">Enter number of rows:</label>
        <input type="number" name="num" id="num">
        <br><br>
        <input type="submit" value="Generate">
    </form>

    <div>
        <h2>Generated Pattern:</h2>
        <pre>
        <?php
        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            $row = $_POST['num'];
                echo "Pattern A <br>";
                for ($i = 1; $i <= $row; $i++) {
                    echo str_repeat('*', $i) . "\n";
                }
                // Pattern B
                echo "<br>Pattern B <br><br>";
                for ($i = $row; $i >= 1; $i--) {
                    echo str_repeat(' ', $row - $i) . str_repeat('*', $i) . "\n";
                }
        }
        ?>
        </pre>
    </div>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-11-29 205204.png>)

# 14. Write PHP code to print Grade card of Student using Switch case.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Student Grade Card</title>
</head>
<body>
    <form method="post" action="">
        <label for="name">Student Name:</label>
        <input type="text" id="name" name="name" required>
        <br>
        <label for="marks">Marks:</label>
        <input type="number" id="marks" name="marks" required>
        <br>
        <input type="submit" value="Submit">
    </form>

    <?php
    function printGrade($marks) {
        switch (true) {
            case ($marks >= 90):
                $grade = "A+";
                break;
            case ($marks >= 80):
                $grade = "A";
                break;
            case ($marks >= 70):
                $grade = "B+";
                break;
            case ($marks >= 60):
                $grade = "B";
                break;
            case ($marks >= 50):
                $grade = "C";
                break;
            case ($marks >= 40):
                $grade = "D";
                break;
            default:
                $grade = "F";
                break;
        }
        return $grade;
    }

    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $studentName = $_POST['name'];
        $studentMarks = $_POST['marks'];
        $studentGrade = printGrade($studentMarks);

        echo "<h1>Grade Card</h1>";
        echo "<p>Student Name: $studentName</p>";
        echo "<p>Marks: $studentMarks</p>";
        echo "<p>Grade: $studentGrade</p>";
    }
    ?>
</body>
</html>
```

# 15. Write PHP code to print Fibonacci series.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Pattern Generator</title>
</head>
<body>
    <?php
    function printFibonacci($n) {
        $a = 0;
        $b = 1;
        echo "$a $b ";
        for ($i = 2; $i < $n; $i++) {
            $c = $a + $b;
            echo $c . " ";
            $a = $b;
            $b = $c;
        }
    }

    // Print first 10 Fibonacci numbers
    printFibonacci(10);
    ?>
</body>
</html>
```

![alt text](<../img/Screenshot 2024-11-30 204758.png>)

# 16. Write a JavaScript program to display the current day and time in the following format.

_**Sample Output** : Today is : Wednesday._
_Current time is : 2 PM : 30 : 38_

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Time Generator</title>
  </head>

  <body>
    <script>
      // Get the current date and time
      const now = new Date();

      // Get the day of the week (0 = Sunday, 1 = Monday, ..., 6 = Saturday)
      const dayOfWeek = now.getDay();

      // Convert the day of the week to a string (e.g., "Sunday", "Monday", etc.)
      const days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];
      const dayString = days[dayOfWeek];

      // Get the hours, minutes, and seconds
      const hours = now.getHours();
      const minutes = now.getMinutes();
      const seconds = now.getSeconds();

      // Convert the hours to 12-hour format (e.g., 13 -> 1 PM)
      const ampm = hours >= 12 ? "PM" : "AM";
      const hour12 = hours % 12 || 12;

      // Display the current day and time
      document.write(`Today is : ${dayString}.<br>`);
      document.write(
        `Current time is : ${hour12} ${ampm} : ${minutes} : ${seconds}`
      );
    </script>
  </body>
</html>
```

![alt text](<../img/Screenshot 2024-11-29 233308.png>)

# 17. Write a JavaScript program to print the contents of the current window.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Print Window</title>
  </head>

  <body>
    <h2>Hello</h2>
    <h3>World</h3>
    <button onclick="printWindow()">Print this page</button>

    <script>
      function printWindow() {
        window.print();
      }
    </script>
  </body>
</html>
```

![alt text](<../img/Screenshot 2024-11-30 204042.png>)

# 18. Write a JavaScript function that reverses a number

```js
function reverseNum(num) {
  let rev = 0;
  while (num) {
    let dig = num % 10;
    rev = rev * 10 + dig;
    num = Math.floor(num / 10);
  }
  return rev;
}
console.log(reverseNum(32415));
console.log(reverseNum(100));

// OUTPUT
// 51423
// 1
```

# 19. Write a JavaScript function that checks whether a passed string is palindrome or not?

_**already answered in no(5) question**_

# 20. Write a JavaScript program that accept two integers and display the larger.

_**already answered in no(12.b) question**_

# 21. Write a JavaScript function to check whether an `input` is an array or not.

```js
function is_array(arr) {
  const res = Array.isArray(arr);
  if (res) return `${arr} is an Array`;
  else return `${arr} is not an Array`;
}
console.log(is_array("www.hit.in"));
console.log(is_array([1, 2, 4, 0]));
```

![alt text](<../img/Screenshot 2024-11-30 210728.png>)

# 22. Write a java script program to sort 50 natural numbers.

_**already answered in no(5) question**_
