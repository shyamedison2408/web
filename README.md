<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Job Application Form</title>
    <style>
        body { font-family: Arial, sans-serif; }
        .container { width: 50%; margin: auto; }
        .input-control { margin-bottom: 10px; }
        .error { color: red; font-size: 14px; }
        .input-control input { width: 100%; padding: 8px; margin-top: 5px; }
        .success { border: 2px solid green; }
        .error-input { border: 2px solid red; }
        button { background: black; color: white; padding: 10px 15px; border: none; cursor: pointer; }
    </style>
</head>
<body>

<div class="container">
    <h2>Submit your application</h2>
    <form id="jobForm">
        <div class="input-control">
            <label>Name (as per ID proof)*</label>
            <input type="text" id="name">
            <span class="error" id="nameError"></span>
        </div>

        <div class="input-control">
            <label>Father's Name*</label>
            <input type="text" id="fatherName">
            <span class="error" id="fatherNameError"></span>
        </div>

        <div class="input-control">
            <label>Email*</label>
            <input type="text" id="email">
            <span class="error" id="emailError"></span>
        </div>

        <div class="input-control">
            <label>Date of Birth*</label>
            <input type="date" id="dob">
            <span class="error" id="dobError"></span>
        </div>

        <div class="input-control">
            <label>Mobile No*</label>
            <input type="text" id="mobile">
            <span class="error" id="mobileError"></span>
        </div>

        <div class="input-control">
            <label>Current Address</label>
            <input type="text" id="address">
        </div>

        <div class="input-control">
            <label>Permanent Address</label>
            <input type="text" id="permanentAddress">
        </div>

        <div class="input-control">
            <label>City</label>
            <input type="text" id="city">
        </div>

        <div class="input-control">
            <label>State</label>
            <input type="text" id="state">
        </div>

        <div class="input-control">
            <label>Zip Code</label>
            <input type="text" id="zipCode">
        </div>

        <div class="input-control">
            <label>Upload Photo</label>
            <input type="file" id="photo">
        </div>

        <button type="submit">Submit</button>
    </form>
</div>

<script>
    document.getElementById("jobForm").addEventListener("submit", function (e) {
        e.preventDefault(); // Prevent form submission

        let isValid = true;

        // Get input values
        const name = document.getElementById("name").value.trim();
        const fatherName = document.getElementById("fatherName").value.trim();
        const email = document.getElementById("email").value.trim();
        const dob = document.getElementById("dob").value;
        const mobile = document.getElementById("mobile").value.trim();

        // Regex patterns
        const nameRegex = /^[a-zA-Z\s]+$/;
        const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        const mobileRegex = /^[0-9]{10}$/;

        // Validate Name
        if (!name.match(nameRegex)) {
            showError("nameError", "Only letters and spaces allowed.");
            isValid = false;
        } else {
            showSuccess("nameError", "name");
        }

        // Validate Father's Name
        if (!fatherName.match(nameRegex)) {
            showError("fatherNameError", "Only letters and spaces allowed.");
            isValid = false;
        } else {
            showSuccess("fatherNameError", "fatherName");
        }

        // Validate Email
        if (!email.match(emailRegex)) {
            showError("emailError", "Enter a valid email.");
            isValid = false;
        } else {
            showSuccess("emailError", "email");
        }

        // Validate DOB
        if (!dob) {
            showError("dobError", "Date of birth is required.");
            isValid = false;
        } else {
            showSuccess("dobError", "dob");
        }

        // Validate Mobile Number
        if (!mobile.match(mobileRegex)) {
            showError("mobileError", "Enter a valid 10-digit mobile number.");
            isValid = false;
        } else {
            showSuccess("mobileError", "mobile");
        }

        // Submit if all fields are valid
        if (isValid) {
            alert("Form submitted successfully!");
            document.getElementById("jobForm").reset();
        }
    });

    function showError(errorId, message) {
        document.getElementById(errorId).innerText = message;
        document.getElementById(errorId.replace("Error", "")).classList.add("error-input");
    }

    function showSuccess(errorId, inputId) {
        document.getElementById(errorId).innerText = "";
        document.getElementById(inputId).classList.remove("error-input");
        document.getElementById(inputId).classList.add("success");
    }
</script>

</body>
</html>
