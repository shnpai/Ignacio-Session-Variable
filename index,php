<?php
session_start();

// Handle login 
if (isset($_POST['login'])) {
    $username = $_POST['username'];
    $password = $_POST['password'];

    // Check if a user is already logged in
    if (isset($_SESSION['username'])) {
        // Set an error message if a different user tries to log in
        $login_error = $_SESSION['username'] . " is already logged in. Wait for them to logout first.";
    } else {
        // Hash the password 
        $hashed_password = password_hash($password, PASSWORD_BCRYPT);

        // Set session variables for the logged-in user
        $_SESSION['username'] = $username;
        $_SESSION['hashed_password'] = $hashed_password;

        // Clear any previous error message
        unset($login_error);
    }
}

// Handle logout
if (isset($_POST['logout'])) {
    // Destroy session data to log out the user
    session_destroy();
    // Redirect back to the same page to clear the session on reload
    header("Location: index.php");
    exit();
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
</head>
<br>
    <form action="index.php" method="post">
        <label for="username">Username</label>
        <input type="text" name="username" id="username"><br>

        <label for="password">Password</label>
        <input type="password" name="password" id="password"><br>

        <button type="submit" name="login">Login</button>
		<br><br>
        <button type="submit" name="logout">Logout</button>
    </form>

    <?php
        // Display logged-in user information
        if (isset($_SESSION['username'])) {
            echo "<p>User logged in: " . $_SESSION['username'] . "</p>";
            echo "<p>Password: " . $_SESSION['hashed_password'] . "</p>";

            // Display error message if set
            if (isset($login_error)) {
                echo "<p>" . $login_error . "</p>";
            }
        }
    ?>
</body>
</html>
