<?php
// Safaricom M-Pesa STK Push Integration in PHP

// Function to generate an access token
function generateAccessToken() {
    $consumerKey = 'YOUR_CONSUMER_KEY';  // Replace with your Consumer Key
    $consumerSecret = 'YOUR_CONSUMER_SECRET';  // Replace with your Consumer Secret

    // Base64 encode the consumer key and secret
    $credentials = base64_encode($consumerKey . ':' . $consumerSecret);

    // Safaricom OAuth URL for generating the access token
    $url = 'https://sandbox.safaricom.co.ke/oauth/v1/generate?grant_type=client_credentials';

    // Initialize cURL
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, $url);
    curl_setopt($curl, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . $credentials));
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

    // Execute cURL request and capture the response
    $curl_response = curl_exec($curl);
    curl_close($curl);

    // Decode the JSON response and return the access token
    $result = json_decode($curl_response);
    return $result->access_token;
}

// Function to perform the STK Push
function stkPush($phone, $amount) {
    // Generate an access token
    $accessToken = generateAccessToken();

    // Safaricom STK Push endpoint URL
    $url = 'https://sandbox.safaricom.co.ke/mpesa/stkpush/v1/processrequest';

    // Business details (replace with your own)
    $BusinessShortCode = 'YOUR_SHORTCODE'; // Replace with your Business Shortcode
    $LipaNaMpesaOnlinePasskey = 'YOUR_PASSKEY'; // Replace with your Passkey
    $TransactionType = 'CustomerPayBillOnline';
    $PartyA = $phone; // The phone number of the customer
    $PhoneNumber = $phone; // Same as PartyA
    $CallBackURL = 'https://yourdomain.com/callback'; // Replace with your callback URL
    $AccountReference = 'UniqueReference'; // For your own records
    $TransactionDesc = 'Payment for services';
    
    // Safaricom timestamp and password generation
    $Timestamp = date('YmdHis');
    $Password = base64_encode($BusinessShortCode . $LipaNaMpesaOnlinePasskey . $Timestamp);

    // Prepare the request payload
    $curl_post_data = array(
        'BusinessShortCode' => $BusinessShortCode,
        'Password' => $Password,
        'Timestamp' => $Timestamp,
        'TransactionType' => $TransactionType,
        'Amount' => $amount,  // Amount to be charged
        'PartyA' => $PartyA,
        'PartyB' => $BusinessShortCode,
        'PhoneNumber' => $PhoneNumber,
        'CallBackURL' => $CallBackURL,
        'AccountReference' => $AccountReference,
        'TransactionDesc' => $TransactionDesc
    );

    // Convert the payload to JSON
    $data_string = json_encode($curl_post_data);

    // Initialize cURL to make the STK Push request
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, $url);
    curl_setopt($curl, CURLOPT_HTTPHEADER, array('Content-Type:application/json', 'Authorization:Bearer ' . $accessToken));
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $data_string);

    // Execute cURL request and return the response
    $curl_response = curl_exec($curl);
    curl_close($curl);

    return $curl_response;
}

// Handle the callback from Safaricom
function handleCallback() {
    // Retrieve the callback data
    $callbackData = file_get_contents('php://input');
    $response = json_decode($callbackData, true);

    // Process the response (for example, update order status)
    if (isset($response['Body']['stkCallback']['ResultCode'])) {
        $resultCode = $response['Body']['stkCallback']['ResultCode'];
        $resultDesc = $response['Body']['stkCallback']['ResultDesc'];

        // Check for a successful payment (ResultCode 0 means success)
        if ($resultCode == 0) {
            $mpesaReceiptNumber = $response['Body']['stkCallback']['CallbackMetadata']['Item'][1]['Value'];
            // Successful payment. Update your database and mark the payment as successful.
            file_put_contents('callback_success.log', 'Payment successful. Receipt: ' . $mpesaReceiptNumber . PHP_EOL, FILE_APPEND);
        } else {
            // Payment failed. Log the error.
            file_put_contents('callback_error.log', 'Payment failed: ' . $resultDesc . PHP_EOL, FILE_APPEND);
        }
    }
}

// Example usage: Triggering STK Push
if (isset($_POST['phone']) && isset($_POST['amount'])) {
    $phone = $_POST['phone'];
    $amount = $_POST['amount'];

    // Call the stkPush function
    $response = stkPush($phone, $amount);
    echo $response; // Return the response from the STK push
}

// Example usage: Handling the callback
if ($_SERVER['REQUEST_METHOD'] === 'POST' && strpos($_SERVER['REQUEST_URI'], 'callback') !== false) {
    handleCallback();
}
?>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kredo Mall - Data Bundles</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap">
    <style>
        
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f4f7fa;
            color: #343a40;
            padding-top: 70px;
        }

        .hero {
            background: linear-gradient(135deg, #3cff00 0%, #0056b3 100%);
            color: white;
            padding: 80px 0;
            text-align: center;
            border-radius: 20px;
            width:80%;
            margin-left: 10%;
            margin-right: 30%;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 700;
        }

        .hero p {
            font-size: 1.2rem;
            font-weight: 400;
        }

        .bundle-card {
            transition: transform 0.2s;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .bundle-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        .footer {
            background-color: #343a40;
            color: #ffffff;
            padding: 1px 0;
            position: relative;
            bottom: 0;
            border-radius: 20px;
            
            
        }

        .footer a {
            color: #ffffff;
            text-decoration: none;
        }

        .footer a:hover {
            text-decoration: underline;
        }

        /* Modal styles */
        .modal-header {
            background-color: #007bff;
            color: white;
        }

        .modal-body {
            background-color: #f9f9f9;
        }

        .modal-footer {
            border-top: none;
        }
        
    </style>
</head>

<body>

   <!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-light bg-primary fixed-top blurred-navbar">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Kredomall Enterprises</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link active" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#about">About</a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#bundles" id="bundlesDropdown" role="button" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Data Bundles <i class="bi bi-chevron-down"></i>
            </a>
            <ul class="dropdown-menu" aria-labelledby="bundlesDropdown">
              <li><a class="dropdown-item" href="#bundles-mobile">Mobile Bundles</a></li>
              <li><a class="dropdown-item" href="#bundles-broadband">Broadband Bundles</a></li>
            </ul>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  
    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1 class="display-4">Welcome  to Kredomall Enterprises</h1>
            <p class="lead">Purchase  affordable  data bundles, Airtime, minutes  and Sms tailored for your &friend  needs </p>
            <a href="#bundles" class="btn btn-light btn-lg">View Data Bundles</a>
        </div>
    </section>
 <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background-color: #f8f9fa;
        }

        .bundle-card {
            transition: transform 0.2s;
        }

        .bundle-card:hover {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="my-4">Available Data Bundles</h1>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Bundle Title</th>
                    <th>Validity</th>
                    <th>Network Provider</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="bundleRows"></tbody>
        </table>
    </div>

    <!-- Modal for Buying Bundle -->
    <div class="modal fade" id="buyModal" tabindex="-1" aria-labelledby="buyModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="buyModalLabel">Buy Data Bundle</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <p id="bundleDescription"></p>
                    <form id="buyForm">
                        <div class="mb-3">
                            <label for="phoneNumber" class="form-label">Phone Number</label>
                            <input type="text" class="form-control" id="phoneNumber" placeholder="Enter your phone number" required>
                        </div>
                        <button type="submit" class="btn btn-primary">Confirm Purchase</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Load bundles from local storage or fallback to default data
        let bundlesToDisplay = JSON.parse(localStorage.getItem('bundles')) || [
            { title: '1.5GB @ Ksh 50', validity: 'Valid for 3 hours', provider: 'Safaricom' },
            { title: '350MB @ Ksh 49', validity: 'Valid for 7 days', provider: 'Airtel' },
            { title: '2.5GB @ Ksh 300', validity: 'Valid for 7 days', provider: 'Telkom' },
        ];

        function renderBundleRows() {
            const tableBody = document.getElementById('bundleRows');
            tableBody.innerHTML = ''; // Clear existing rows
            bundlesToDisplay.forEach((bundle, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${bundle.title}</td>
                    <td>${bundle.validity}</td>
                    <td>${bundle.provider}</td>
                    <td><button class="btn btn-success" onclick="openBuyModal(${index})">Buy</button></td>
                `;
                tableBody.appendChild(row);
            });
        }

        // Open the modal to buy the selected bundle
        function openBuyModal(index) {
            const bundle = bundlesToDisplay[index];
            document.getElementById('bundleDescription').innerText = `You are purchasing: ${bundle.title} - ${bundle.validity}`;
            const buyModal = new bootstrap.Modal(document.getElementById('buyModal'));
            buyModal.show();
        }

        // Handle the buy form submission
        document.getElementById('buyForm').onsubmit = function (e) {
            e.preventDefault(); // Prevent default form submission
            const phoneNumber = document.getElementById('phoneNumber').value;
            if (phoneNumber) {
                alert(`Purchase confirmed for ${phoneNumber}.`);
                const buyModal = bootstrap.Modal.getInstance(document.getElementById('buyModal'));
                buyModal.hide(); // Hide modal after confirmation
            }
        };

        renderBundleRows(); // Initial render
    </script>

    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js"></script>

    <!-- About Section -->
    <section id="about" class="py-5">
        <div class="container">
            <h2 class="mb-4">About Kredo Mall</h2>
            <p>Kredo Mall is your go-to marketplace for the best data bundle offers, tailored to your specific needs.
                From hourly bundles to month-long data packs, we've got you covered!</p>
        </div>
    </section>
    <!-- Footer -->
    <footer class="footer">
        <div class="container text-center">
            <p>&copy; 2024 Kredo Mall. All rights reserved.</p>
            <p><a href="#about">About</a> | <a href="#contact">Contact</a></p> <a href="admin.php">❤️</a></p>
        </div>
    </footer>

    <!-- Modal -->
    <div class="modal fade" id="bundleModal" tabindex="-1" aria-labelledby="bundleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="bundleModalLabel">Purchase Bundle</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <p><strong>Bundle:</strong> <span id="modalBundleName"></span></p>
                    <p><strong>Price:</strong> <span id="modalBundlePrice"></span></p>
                    <p><strong>Details:</strong> <span id="modalBundleDetails"></span></p>
                    <form>
                        <div class="mb-3">
                            <label for="phoneNumber" class="form-label">Phone Number</label>
                            <input type="tel" class="form-control" id="phoneNumber" placeholder="Enter your phone number">
                        </div>
                        <button type="submit" class="btn btn-primary">Proceed to Payment</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <script>
        function openModal(bundleName, bundlePrice, bundleDetails) {
            document.getElementById('modalBundleName').textContent = bundleName;
            document.getElementById('modalBundlePrice').textContent = bundlePrice;
            document.getElementById('modalBundleDetails').textContent = bundleDetails;
            var bundleModal = new bootstrap.Modal(document.getElementById('bundleModal'));
            bundleModal.show();
        }
    </script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>

    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js"></script>

<!-- Code injected by live-server -->
<script>
	// <![CDATA[  <-- For SVG support
	if ('WebSocket' in window) {
		(function () {
			function refreshCSS() {
				var sheets = [].slice.call(document.getElementsByTagName("link"));
				var head = document.getElementsByTagName("head")[0];
				for (var i = 0; i < sheets.length; ++i) {
					var elem = sheets[i];
					var parent = elem.parentElement || head;
					parent.removeChild(elem);
					var rel = elem.rel;
					if (elem.href && typeof rel != "string" || rel.length == 0 || rel.toLowerCase() == "stylesheet") {
						var url = elem.href.replace(/(&|\?)_cacheOverride=\d+/, '');
						elem.href = url + (url.indexOf('?') >= 0 ? '&' : '?') + '_cacheOverride=' + (new Date().valueOf());
					}
					parent.appendChild(elem);
				}
			}
			var protocol = window.location.protocol === 'http:' ? 'ws://' : 'wss://';
			var address = protocol + window.location.host + window.location.pathname + '/ws';
			var socket = new WebSocket(address);
			socket.onmessage = function (msg) {
				if (msg.data == 'reload') window.location.reload();
				else if (msg.data == 'refreshcss') refreshCSS();
			};
			if (sessionStorage && !sessionStorage.getItem('IsThisFirstTime_Log_From_LiveServer')) {
				console.log('Live reload enabled.');
				sessionStorage.setItem('IsThisFirstTime_Log_From_LiveServer', true);
			}
		})();
	}
	else {
		console.error('Upgrade your browser. This Browser is NOT supported WebSocket for Live-Reloading.');
	}
	// ]]>
</script>
</body>

</html>

