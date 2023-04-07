# ketan-shiyal
Fatal error: Uncaught TypeError: mysqli_num_rows(): Argument #1 ($result) must be of type mysqli_result, bool given in C:\xampp\htdocs\register\register.php:18 Stack trace: #0 C:\xampp\htdocsr\register.php(18): mysqli_num_rows(false) #1 {main} thrown in C:\xampp\htdocs\register\register.php on line 18


<?php
if (isset($_POST['save'])) 
{
    $conn=mysqli_connect("localhost","root","","complaints");
    $user=$_POST['user'];
    $email = $_POST['email'];
    $password = $_POST['password'];
    $cpassword = $_POST['cpassword'];
    $number = $_POST['number'];
    $adhar_number = $_POST['adhar_number'];
    $age = $_POST['age'];
    $address = $_POST['address'];
    $gender = $_POST['gender'];
    $sql="SELECT * FROM userdata WHERE emial='$email'";
    $res=mysqli_query($conn, $sql);

    if(mysqli_num_rows($res) > 0)
    {
        $row=mysqli_fetch_assoc($res);
        if($email==isset($row['email']))
        {
            echo"email already exists";
        }
        if($password===$cpassword)
        {
        }
        if($adhar_number==isset($row['adhar_number']))
        {
            echo"Adhar Number exists";
        }
        else
        {
            if($password===$cpassword)
            {
                $sql1="INSERT INTO userdata (username,email,password,number,adhar_number,age,address,gender) VALUES('{$user}','{$email}','{password}','{number}','{adhar_number}','{age}','{address}','{gender}')";
                if(mysqli_query($conn,$sql1))
                {
                    echo"Hello $user You have registered  successfull";
                }
                else
                {
                    echo"password are not matching"; 
                }
            }
        }
![Error](https://user-images.githubusercontent.com/96726376/230630879-61a63b86-2cf5-462f-981d-4070dd261f5a.png)
    }
}
?>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>REGISTER</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>
    <div class="popup-container" id="login-popup">
        <div class="popup">
            <form action="<?php echo $_SERVER['PHP_SELF'] ?>" method="POST">
                <h2>
                    <span>REGISTER</span>
                    <button type="reset" onclick="popup('login-popup')">X</button>
                </h2>
                <input type="text" placeholder="Username" name="user">
                <input type="email" placeholder="E-mail" name="email">
                <input type="password" placeholder="Password" name="password">
                <input type="password" placeholder="Confirm Password" name="cpassword" >
                <input type="tel" placeholder="Phone Number" name="number">
                <input type="text" placeholder="Adhar Number" name="adhar_number">
                <input type="number" placeholder="Age" name="age">
                <input type="textarea" placeholder="Address" name="address" >
                <label for="gender">Gender :</label>
                <select class="gender" name="gender" id="gender" >
                    <option value="" selected hidden>Select Gender</option>
                    <option value="Male">Male</option>
                    <option value="Female">Female</option>
                    <option value="Other">Other</option>
                </select>
                <br><br>
                <button type="submit" class="register-btn" name="save">REGISTER</button>
                <!-- <button type="reset" class="reset-btn" name="reset">RESET</button> -->
                <div class="register-link">
                    Already have an account <span><a href="index.php">Login</a></span>
                </div>
            </form>
        </div>
    </div>
</body>

</html>


//Error Show this Fatal error: Uncaught TypeError: mysqli_num_rows(): Argument #1 ($result) must be of type mysqli_result, bool given in C:\xampp\htdocs\register\register.php:18 Stack trace: #0 C:\xampp\htdocs\register\register.php(18): mysqli_num_rows(false) #1 {main} thrown in C:\xampp\htdocs\register\register.php on line 18
