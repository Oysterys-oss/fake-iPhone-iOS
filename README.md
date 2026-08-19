<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>Software Update</title>
    <style>
        body {
            background-color: #000000;
            color: #ffffff;
            font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "SF Pro Text", "Helvetica Neue", Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            cursor: none;
            user-select: none;
        }
        /* 苹果标志性 Logo (纯 CSS 绘制简约白苹果轮廓) */
        .apple-logo {
            width: 60px;
            height: 74px;
            fill: #ffffff;
            margin-bottom: 80px;
            animation: pulse 2s infinite ease-in-out;
        }
        @keyframes pulse {
            0%, 100% { opacity: 0.6; }
            50% { opacity: 1; }
        }
        /* iOS 风格细进度条容器 */
        .progress-container {
            width: 220px;
            height: 4px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 2px;
            overflow: hidden;
        }
        /* 进度条滚动条 */
        .progress-bar {
            width: 0%;
            height: 100%;
            background-color: #ffffff;
            border-radius: 2px;
            transition: width 0.4s ease;
        }
        .text-tip {
            margin-top: 20px;
            font-size: 13px;
            color: #888888;
            font-weight: 400;
            letter-spacing: 0.3px;
        }
    </style>
</head>
<body onclick="toggleFullscreen()">

    <!-- 苹果 Logo SVG -->
    <svg class="apple-logo" viewBox="0 0 170 170">
        <path d="M150.37 130.25c-2.45 5.66-5.35 10.87-8.71 15.66-4.58 6.53-8.33 11.05-11.22 13.56-4.48 4.12-9.28 6.23-14.42 6.35-3.69 0-8.14-1.05-13.32-3.18-5.19-2.12-9.97-3.17-14.34-3.17-4.58 0-9.49 1.05-14.75 3.17-5.26 2.13-9.5 3.24-12.74 3.35-4.35.13-9.13-1.9-14.33-6.08-3.69-3.04-7.74-7.85-12.15-14.43-6.23-9.26-11.05-19.56-14.46-30.9-3.41-11.34-5.12-22.31-5.12-32.91 0-14.54 3.79-26.24 11.37-35.11 7.58-8.87 17.2-13.36 28.87-13.48 4.79 0 10.15 1.18 16.09 3.53 5.94 2.35 9.8 3.53 11.58 3.53 1.53 0 5.48-1.24 11.85-3.72 6.37-2.48 11.86-3.64 16.48-3.48 15.82.76 27.87 7.04 36.16 18.83-13.09 7.95-19.46 18.99-19.11 33.12.35 11.34 4.71 20.69 13.08 28.04 4.13 3.66 9.15 6.31 15.06 7.95-2.28 6.78-5.22 13.78-8.83 21zm-24.58-107.1c0 8.01-2.94 15.42-8.82 22.21-5.88 6.78-13.29 10.9-22.22 12.33-.24-1.53-.35-3.01-.35-4.45 0-7.79 3.09-15.52 9.27-23.19 6.18-7.68 13.76-12.01 22.75-13 0 .71.12 1.94.35 3.7l.02.38z"/>
    </svg>

    <!-- 进度条 -->
    <div class="progress-container">
        <div id="bar" class="progress-bar"></div>
    </div>
    
    <div class="text-title" style="margin-top: 25px; font-size: 15px; font-weight: 500;">軟體更新</div>
    <div class="text-tip">已接近完成...</div>

    <script>
        let progress = 15; // 从 15% 开始伪装更逼真
        const bar = document.getElementById('bar');
        bar.style.width = progress + '%';

        // 模拟真实 iOS 更新的慢速、卡顿、最后冲刺
        let timer = setInterval(() => {
            if (progress < 99) {
                // 越到后面涨得越慢
                let increment = Math.random() > 0.6 ? 1 : 0;
                if (progress > 85) increment = Math.random() > 0.85 ? 1 : 0;
                
                progress += increment;
                bar.style.width = progress + '%';
            }
        }, 1200); // 调整数字可以控制进度条走完的速度

        // 点击屏幕全屏（用手机打开时效果完美）
        function toggleFullscreen() {
            if (!document.fullscreenElement) {
                document.documentElement.requestFullscreen();
            } else {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                }
            }
        }
    </script>
</body>
</html>
