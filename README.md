# login_page<?php
	$studentnumber = $_POST['studentnumber'];
	
	$password = $_POST['password'];

        
        if((! empty($studentnumber)|| !empty($password) ){

          $servername = "localhost";
          $username = "username";
          $password = "password";

		#code...
		
	} else {

          echo "field are required";

     die();

	// Database connection
	$conn = new mysqli('localhost','cool','','wajdi');
	if($conn->connect_error){
		echo "$conn->connect_error";
		die("Connection Failed : ". $conn->connect_error);
	} else {
		$stmt = $conn->prepare("insert into registration(studentnumber) values(?, ?, ?, ?, ?, ?)");
		$stmt->bind_param("****", $studentnumber,$password);
		$execval = $stmt->execute();
		echo $execval;
		echo "Registration successfully...";
		$stmt->close();
		$conn->close();
	}
?>
