<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بث مباشر</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #000;
        }
        .video-container {
            position: relative;
            width: 80%;
            max-width: 800px;
            padding-bottom: 56.25%; /* نسبة 16:9 */
        }
        .video-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: 0;
        }
    </style>
</head>
<body>
    <div class="video-container">
        <iframe src="https://player.viloud.tv/embed/channel/219ad7efa340aa8275135aebdb398998?autoplay=0&volume=1&controls=1&title=1&share=1&open_playlist=0&random=0" allow="autoplay" allowfullscreen></iframe>
    </div>
</body>
</html>
