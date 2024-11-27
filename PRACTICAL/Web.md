 # 1. Design and validate this form with proper code.

![alt text](../img/image.png)
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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

        echo "<p style='color:green;'>Registration successful!</p>";
    } else {
        // Display errors
        foreach ($errors as $error) {
            echo "<p style='color:red;'>$error</p>";
        }
    }
}
?>
```

# 2. Build a HTML form and write PHP code to calculate Largest among three numbers using a) If_else b) conditional operator.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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

# 3. Build a HTML form and write PHP code to design a calculator program to show use of +,-,* ,/ operators.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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