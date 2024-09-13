<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Must Membership Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            font-size: 11px;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }

        .main {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: auto;
        }

        .banner {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }

        h1 {
            text-align: center;
            color: #333;
        }

        .form-group {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }

        label {
            font-weight: bold;
            flex: 1;
            margin-right: 10px;
        }

        input[type="text"],
        input[type="tel"],
        input[type="email"],
        input[type="date"],
        input[type="number"],
        textarea,
        select {
            flex: 2;
            padding: 3px;
            border: 1px solid #ccc;
            border-radius: 4px;
            transition: border-color 0.3s;
            font-size: 11px;
        }

        input[type="text"]:focus,
        input[type="tel"]:focus,
        input[type="email"]:focus,
        input[type="date"]:focus,
        input[type="number"]:focus,
        textarea:focus,
        select:focus {
            border-color: #66afe9;
            outline: none;
        }

        button {
            background-color: #28a745;
            color: white;
            padding: 5px 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 11px;
            display: block;
            margin: auto;
        }

        button:hover {
            background-color: #218838;
        }

        .inline {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .inline input {
            width: calc(50% - 10px);
            margin-right: 10px;
        }

        .inline input:last-child {
            margin-right: 0;
        }

        .membership-radio {
            display: flex;
            align-items: center;
            margin: 10px 0;
        }

        .membership-radio label {
            margin-left: 5px;
            margin-right: 15px;
        }

        .bank-details {
            background: #e9ecef;
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        h3 {
            color: #333;
        }

        .payment-info {
            font-size: 11px;
            color: #555;
            margin-top: -5px;
        }
    </style>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const membershipRadios = document.querySelectorAll('input[name="membershipType"]');
            const amountInput = document.getElementById('amount');
            const paymentModeSelect = document.getElementById('paymentMode');
            const submissionDate = document.getElementById('submissionDate');

            function updateAmount() {
                if (document.getElementById('yearly').checked) {
                    amountInput.value = 200;
                } else if (document.getElementById('lifetime').checked) {
                    amountInput.value = 1100;
                }
            }

            membershipRadios.forEach(radio => {
                radio.addEventListener('change', updateAmount);
            });

            paymentModeSelect.addEventListener('change', function() {
                let paymentMode = paymentModeSelect.value;
            });

            function updateSubmissionDate() {
                const now = new Date();
                const formattedDate = now.toISOString().substring(0, 10);
                const hours = now.getHours().toString().padStart(2, '0');
                const minutes = now.getMinutes().toString().padStart(2, '0');
                const seconds = now.getSeconds().toString().padStart(2, '0');
                submissionDate.value = `${formattedDate} ${hours}:${minutes}:${seconds}`;
            }

            updateSubmissionDate();
            updateAmount();

            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function(position) {
                    document.getElementById('latitude').value = position.coords.latitude;
                    document.getElementById('longitude').value = position.coords.longitude;
                });
            }
        });
    </script>
</head>
<body>
    <div class="main">
        <div class="banner">
            <img src="mustbanner.jpg" alt="Must Banner" style="max-width: 100%; height: auto;" />
        </div>
        <form method="post" id="membershipForm">
            <h1>Must Membership Form</h1>
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="middleName">Middle Name:</label>
                <input type="text" id="middleName" name="middleName" required>
            </div>
            <div class="form-group">
                <label for="surname">Surname:</label>
                <input type="text" id="surname" name="surname" required>
            </div>
            <div class="form-group">
                <label for="mobileNumber">Mobile Number:</label>
                <input type="tel" id="mobileNumber" name="mobileNumber" pattern="[0-9]{10}" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="designation">Designation:</label>
                <input type="text" id="designation" name="designation" required>
            </div>
            <div class="form-group">
                <label for="subject">Subject:</label>
                <input type="text" id="subject" name="subject" required>
            </div>
            <div class="form-group">
                <label for="residenceAddress">Residence Address:</label>
                <textarea id="residenceAddress" name="residenceAddress" required></textarea>
            </div>
            <div class="form-group">
                <label for="officeAddress">Office Address:</label>
                <textarea id="officeAddress" name="officeAddress" required></textarea>
            </div>
            <div class="form-group">
                <label for="appointmentDate">Date of Appointment:</label>
                <input type="date" id="appointmentDate" name="appointmentDate" required>
            </div>
            <div class="form-group inline">
                <label for="lengthOfServiceYears">Length of Service:</label>
                <input type="number" id="lengthOfServiceYears" name="lengthOfServiceYears" placeholder="Years" required>
                <input type="number" id="lengthOfServiceMonths" name="lengthOfServiceMonths" placeholder="Months" required>
            </div>
            <div class="membership-radio">
                <label>Membership Type:</label>
                <strong>Entry fee (Rs 100.00) ++</strong>
                <input type="radio" id="yearly" name="membershipType" value="Yearly" required>
                <label for="yearly">Yearly (Rs 100.00)</label>
                <input type="radio" id="lifetime" name="membershipType" value="Lifetime" required>
                <label for="lifetime">Lifetime (Rs 1000.00)</label>
            </div>
            <div class="form-group">
                <label for="amount">Amount in Rupees:</label>
                <input type="number" id="amount" name="amount" required>
            </div>
            <div class="form-group">
                <label for="paymentMode">Mode of Payment:</label>
                <select id="paymentMode" name="paymentMode" required>
                    <option value="NEFT / RTGS / BANK TRANSFER">NEFT / RTGS / BANK TRANSFER</option>
                    <option value="UPI">WALLET UPI(GPAY / PHONEPE / CRED)</option>
                    <option value="CHEQUE">CHEQUE</option>
                </select>
            </div>
            <div class="form-group">
                <label for="submissionDate">Date of submission:</label>
                <input type="text" id="submissionDate" name="submissionDate" readonly>
            </div>
            <!-- Hidden fields for geolocation -->
            <input type="hidden" id="latitude" name="latitude">
            <input type="hidden" id="longitude" name="longitude">

            <button type="submit">Submit Form</button>
            <div class="bank-details">
                <h3>Bank Details:</h3>
                <p>
                    A/c Name: Maharashtra's Union of Secular Teachers<br>
                    Bank Name: Union Bank of India<br>
                    A/c Number: 317302010756594<br>
                    NEFT/IFSC Number: UBIN0531731<br>
                    MICR Code: 400026033<br>
                    UPI ID: QR918356895595-6594@unionbankofindia<br>
                </p>
            </div>
        </form>
    </div>
    <script>
        let url = 'https://script.google.com/macros/s/AKfycbygse33QQXX6IQcIc_M1YxXTi9jDPxjJ7olCml5VMgzP4yQrOh_69AFcRlz2_jHIcH8DQ/exec';
        let form = document.querySelector('#membershipForm');
        form.addEventListener("submit", (e) => {
            let d = new FormData(form);
            fetch(url, {
                method: "POST",
                body: d
            }).then((res) => res.text())
            .then((finalRes) => {
                console.log(finalRes);
                alert("Form submitted successfully!"); // Popup message
                form.reset(); // Clear the form
                const now = new Date();
                const formattedDate = now.toISOString().substring(0, 10);
                const hours = now.getHours().toString().padStart(2, '0');
                const minutes = now.getMinutes().toString().padStart(2, '0');
                const seconds = now.getSeconds().toString().padStart(2, '0');
                document.getElementById('submissionDate').value = `${formattedDate} ${hours}:${minutes}:${seconds}`; // Reset the submission date with time
                window.location.href = 'https://example.com'; // Redirect to the desired URL
            });
            e.preventDefault();
        });
    </script>
</body>
</html>
