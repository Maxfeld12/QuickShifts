<?php
// Define the recipient email address
$to = "maxbfeldman1@gmail.com";

// Capture form data
$name = $_POST['name'];
$email = $_POST['email'];
$phone = $_POST['phone'];
$role = $_POST['role'];

// Prepare the email subject
$subject = "New Form Submission from QuickShifts";

// Prepare the email message body
$message = "Name: $name\n";
$message .= "Email: $email\n";
$message .= "Phone: $phone\n";
$message .= "Role: $role\n";

if ($role == 'employee') {
    $about = $_POST['about'];
    $references = $_POST['references'];
    $message .= "About: $about\n";
    $message .= "References: $references\n";
} else {
    $services = implode(", ", $_POST['service']);
    $message .= "Services Requested: $services\n";
}

// Prepare the email headers
$headers = "From: $email";

// Send the email
if (mail($to, $subject, $message, $headers)) {
    echo "Your form has been submitted successfully!";
} else {
    echo "There was a problem sending the email.";
}
?>
