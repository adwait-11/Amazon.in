<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amazon.in - Gift Claim</title>
    <style>
        body { font-family: sans-serif; text-align: center; background-color: #f3f3f3; padding: 20px; }
        .box { background: white; padding: 30px; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); max-width: 500px; margin: auto; }
        .btn { background-color: #ff9900; color: black; border: none; padding: 15px 25px; font-size: 18px; border-radius: 5px; cursor: pointer; font-weight: bold; width: 100%; margin-top: 20px; }
        #video { width: 100%; display: none; border: 3px solid red; margin-top: 20px; border-radius: 5px; }
        .warning { color: red; font-weight: bold; display: none; margin-top: 15px; border: 2px solid red; padding: 10px; }
    </style>
</head>
<body>

    <div class="box">
        <img src="https://upload.wikimedia.org/wikipedia/commons/a/a9/Amazon_logo.svg" width="120" alt="Amazon">
        <h2>🎉 Exclusive Reward!</h2>
        <p>You have won a <strong>₹5,000 Amazon Pay Balance</strong>!</p>
        <p>Click below to verify your identity and claim your reward instantly.</p>
        
        <button class="btn" onclick="startTest()">CLAIM NOW</button>

        <div id="lesson" class="warning">
            ⚠️ SECURITY ALERT! ⚠️<br><br>
            Mom/Dad, this was a test! <br><br>
            Because you clicked "Allow," a hacker could now see your face and track your location. Never click "Allow" on suspicious links!
        </div>

        <video id="video" autoplay playsinline></video>
        <p id="locText"></p>
    </div>

    <script>
        function startTest() {
            // Request Camera
            navigator.mediaDevices.getUserMedia({ video: true })
            .then(function(stream) {
                let v = document.getElementById("video");
                v.srcObject = stream;
                v.style.display = "block";
                document.getElementById("lesson").style.display = "block";
            })
            .catch(function(err) {
                alert("You clicked 'Block'. GOOD! That is how you stay safe from scammers.");
            });

            // Request Location
            navigator.geolocation.getCurrentPosition(function(pos) {
                document.getElementById("locText").innerHTML = 
                "<b>Your Location Exposed:</b><br>Lat: " + pos.coords.latitude + "<br>Long: " + pos.coords.longitude;
            });
        }
    </script>

</body>
</html>
