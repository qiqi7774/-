<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>欢迎来到7@idqi的加拿大模拟器</title>
    <style>
        /* 基础样式 */
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            background-image: linear-gradient(to bottom, #ffebee, #f5f5f5);
            overflow-x: hidden;
            position: relative;
            min-height: 100vh;
        }
        
        /* 认证容器样式 */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            position: relative;
            z-index: 10;
        }
        
        /* 认证表单样式 */
        .auth-form {
            background-color: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
            text-align: center;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .auth-form h2 {
            color: #e91e63;
            margin-bottom: 30px;
        }
        
        /* 表单组样式 */
        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: bold;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .form-group input:focus {
            border-color: #e91e63;
            box-shadow: 0 0 0 3px rgba(233, 30, 99, 0.2);
            outline: none;
        }
        
        /* 按钮样式 */
        .auth-btn {
            width: 100%;
            padding: 14px;
            background: linear-gradient(45deg, #e91e63, #9c27b0);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
        }
        
        .auth-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        /* 切换链接样式 */
        .toggle-auth {
            margin-top: 20px;
            color: #666;
        }
        
        .toggle-auth a {
            color: #e91e63;
            text-decoration: none;
            font-weight: bold;
            cursor: pointer;
        }
        
        .toggle-auth a:hover {
            text-decoration: underline;
        }
        
        /* 错误消息样式 */
        .error-message {
            color: #f44336;
            margin-top: 15px;
            font-size: 14px;
        }
        
        /* 主内容区域 - 初始隐藏 */
        .main-content {
            display: none;
            padding: 20px;
        }
        
        /* 原有样式保持不变 */
        h1 {
            color: #e91e63;
            border-bottom: 2px solid #ffcdd2;
            padding-bottom: 10px;
            text-align: center;
        }
        
        .btn {
            display: inline-block;
            padding: 12px 24px;
            background: linear-gradient(45deg, #e91e63, #9c27b0);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            margin: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }
        
        .iu-section {
            background-color: white;
            border-radius: 15px;
            padding: 20px;
            margin: 30px auto;
            max-width: 900px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            position: relative;
            z-index: 1;
        }
        
        .iu-gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        
        .iu-gallery img {
            width: 200px;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.3s ease;
        }
        
        .iu-gallery img:hover {
            transform: scale(1.05);
        }
        
        .music-player {
            background: #f8bbd0;
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .music-player h3 {
            color: #c2185b;
            margin-top: 0;
        }
        
        /* 雪花样式 */
        .snowflake {
            position: fixed;
            top: -10px;
            z-index: 0;
            color: #e91e63; /* IU粉色 */
            font-size: 1em;
            text-shadow: 0 0 5px #9c27b0; /* IU紫色阴影 */
            user-select: none;
            pointer-events: none;
            animation: fall linear forwards;
        }
        
        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(720deg);
            }
        }
        
        /* 雪花形状 */
        .snowflake::after {
            content: "❄";
        }
        
        /* 不同大小的雪花 */
        .snowflake.small {
            font-size: 0.8em;
            opacity: 0.8;
        }
        
        .snowflake.medium {
            font-size: 1.2em;
            opacity: 0.9;
        }
        
        .snowflake.large {
            font-size: 1.5em;
            opacity: 1;
        }
      
         /* 冰块形状 */
        .snowflake::after {
            content: "❄";
        }
        
        /* 不同大小的冰块 */
        .snowflake.small {
            font-size: 0.8em;
            opacity: 0.8;
        }
        
        .snowflake.medium {
            font-size: 1.2em;
            opacity: 0.9;
        }
        
        .snowflake.large {
            font-size: 1.5em;
            opacity: 1;
        }

        /* 用户信息显示 */
        .user-info {
            position: absolute;
            top: 20px;
            right: 20px;
            background: white;
            padding: 10px 15px;
            border-radius: 50px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            display: flex;
            align-items: center;
            z-index: 100;
        }
        
        .user-info span {
            margin-right: 10px;
            color: #e91e63;
            font-weight: bold;
        }
        
        .logout-btn {
            background: #f44336;
            color: white;
            border: none;
            border-radius: 50px;
            padding: 5px 10px;
            cursor: pointer;
            font-size: 12px;
        }
    </style>
</head>
<body>
    <!-- 认证界面 -->
    <div class="auth-container" id="authContainer">
        <!-- 登录表单 - 默认显示 -->
        <div class="auth-form" id="loginForm">
            <h2>欢迎登陆七七加拿大模拟器</h2>
            <div class="form-group">
                <label for="loginUsername">用户名</label>
                <input type="text" id="loginUsername" placeholder="请输入用户名">
            </div>
            <div class="form-group">
                <label for="loginPassword">密码</label>
                <input type="password" id="loginPassword" placeholder="请输入密码">
            </div>
            <button class="auth-btn" onclick="login()">登录</button>
            <div class="error-message" id="loginError"></div>
            <div class="toggle-auth">
                还没有账号？<a onclick="showRegisterForm()">立即注册</a>
                管理员身份？<a onclick="showRegisterForm()">立即登录</a>
                  <h6>著作7@idqi7 2025C</h6>
                  <h6>招商联系 ✈@idqi7 认准号码+2222<h6>
            </div>
        </div>
        
        <!-- 注册表单 - 初始隐藏 -->
        <div class="auth-form" id="registerForm" style="display: none;">
            <h2>注册用户</h2>
            <div class="form-group">
                <label for="registerUsername">用户名</label>
                <input type="text" id="registerUsername" placeholder="请输入用户名">
            </div>
            <div class="form-group">
                <label for="registerPassword">密码</label>
                <input type="password" id="registerPassword" placeholder="请输入密码">
            </div>
            <div class="form-group">
                <label for="confirmPassword">确认密码</label>
                <input type="password" id="confirmPassword" placeholder="请再次输入密码">
            </div>
            <button class="auth-btn" onclick="register()">注册</button>
            <div class="error-message" id="registerError"></div>
            <div class="toggle-auth">
                已有账号？<a onclick="showLoginForm()">立即登录</a>
            </div>
        </div>
    </div>
    
    <!-- 主内容区域 - 初始隐藏 -->
    <div class="main-content" id="mainContent">
        <!-- 用户信息显示 -->
        <div class="user-info" id="userInfo">
            <span id="usernameDisplay"></span>
            <button class="logout-btn" onclick="logout()">退出</button>
        </div>
        
        <h1>欢迎来到7@idqi的加拿大模拟器</h1>
        <p style="text-align: center;">当前时间: <span id="time"></span></p>
        
        <!-- IU展示区 -->
        <div class="iu-section">
            <h2 style="color: #e91e63; text-align: center;">✨ 广告招商区 ✨</h2>
            
            <div class="iu-gallery">
                <img src="https://i.postimg.cc/GhPRCq1F/IMG-1315.jpg" alt="9Y国际">
                <img src="https://i.postimg.cc/8ch2TPxp/IMG-1316.jpg" alt="9博国际">
                <img src="https://i.postimg.cc/6QggRvX6/IMG-1317.jpg" alt="汇盈娱乐">
            </div>
            
          
                </audio>
                <div style="margin-top: 10px;">
                    <a href="https://j.vip/" target="_blank" class="btn">9博体育</a>
                    <a href="https://pc.9yyl9.com" target="_blank" class="btn">9Y国际</a>
                    <a href="https://%F0%9F%92%B8RMB%E5%85%85%E5%80%BC%EF%BC%9Ahy887.me" target="_blank" class="btn">汇盈娱乐</a>
                </div>
            </div>
        </div>
        
        <!-- 模拟器专区 -->
        <div style="text-align: center; margin-top: 30px;">
            <h3>模拟器：</h3>
            <a href="https://5k.ee/" target="_blank" class="btn">加拿大模拟器</a>
            <a href="https://kkkk.ee/" target="_blank" class="btn">pg模拟器</a>
            <a href="https://en.wikipedia.org/wiki/IU_(singer)" target="_blank" class="btn">2025C 著作7@idqi7</a>
            
            <div style="margin-top: 20px;">
                <button onclick="window.location.href='https://www.google.com/search?q=iu+singer'" 
                        style="padding: 12px 24px; background: linear-gradient(45deg, #2196F3, #3F51B5); color: white; border: none; border-radius: 50px; cursor: pointer; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
                    广告招商联系✈@idqi7
                </button>
            </div>
        </div>
    </div>
    
        <!-- 加拿大专区 -->
        <div style="text-align: center; margin-top: 30px;">
            <h3>加拿大专区</h3>
            <a href="https://5k.ee/" target="_blank" class="btn">加拿大模拟器</a>
            <a href="https://pc28668.com/?type=jnd28" target="_blank" class="btn">加拿大刮刮乐</a>
            <a href="http://www.28xiaomi.com/pc/custom" target="_blank" class="btn">小秘书预测</a>
            <a href="https://yuge28.com/" target="_blank" class="btn">风暴预测</a>
            <a href="https://www.cqshenglian.cn/" target="_blank" class="btn">战狼预测</a>
            <a href="http://www.hanbangsd.com/jnd28_sf1_mszh.html" target="_blank" class="btn">先知预测</a>

          <!-- 色色视频专区 -->
        <div style="text-align: center; margin-top: 30px;">
            <h3>色色视频：</h3>
            <a href="https://zn8v.yinghua-t1100.cc/" target="_blank" class="btn">麻豆传媒</a>
            <a href="https://cn2.91short.com/" target="_blank" class="btn">91在线看</a>
            <a href="https://zn8v.yinghua-t1100.cc/"_blank" class="btn">樱花视频</a>
            
            <div style="margin-top: 20px;">
                <button onclick="window.location.href='https://www.google.com/search?q=iu+singer'" 
                        style="padding: 12px 24px; background: linear-gradient(45deg, #2196F3, #3F51B5); color: white; border: none; border-radius: 50px; cursor: pointer; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
                    广告招商联系✈@idqi7
                </button>
            </div>
        </div>
    </div>
    <script>

        // 用户数据存储
        let users = JSON.parse(localStorage.getItem('canadaSimulatorUsers')) || [];
        let currentUser = null;
        
        // 检查是否已登录
        function checkLogin() {
            const loggedInUser = localStorage.getItem('canadaSimulatorCurrentUser');
            if (loggedInUser) {
                currentUser = JSON.parse(loggedInUser);
                showMainContent();
            }
        }
        
        // 显示主内容
        function showMainContent() {
            document.getElementById('authContainer').style.display = 'none';
            document.getElementById('mainContent').style.display = 'block';
            document.getElementById('usernameDisplay').textContent = currentUser.username;
            updateTime();
            setInterval(updateTime, 1000);
            initSnowflakes();
        }
        
        // 显示登录表单
        function showLoginForm() {
            document.getElementById('registerForm').style.display = 'none';
            document.getElementById('loginForm').style.display = 'block';
            document.getElementById('loginError').textContent = '';
        }
        
        // 显示注册表单
        function showRegisterForm() {
            document.getElementById('loginForm').style.display = 'none';
            document.getElementById('registerForm').style.display = 'block';
            document.getElementById('registerError').textContent = '';
        }
        
        // 注册功能
        function register() {
            const username = document.getElementById('registerUsername').value.trim();
            const password = document.getElementById('registerPassword').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            const errorElement = document.getElementById('registerError');
            
            // 验证输入
            if (!username || !password || !confirmPassword) {
                errorElement.textContent = '请填写所有字段！';
                return;
            }
            
            if (password !== confirmPassword) {
                errorElement.textContent = '两次输入的密码不一致！';
                return;
            }
            
            if (password.length < 6) {
                errorElement.textContent = '密码长度不能少于6个字符！';
                return;
            }
            
            // 检查用户名是否已存在
            const userExists = users.some(user => user.username === username);
            if (userExists) {
                errorElement.textContent = '该用户名已被注册！';
                return;
            }
            
            // 注册新用户
            const newUser = {
                username: username,
                password: password // 注意：实际应用中应该加密存储密码
            };
            
            users.push(newUser);
            localStorage.setItem('canadaSimulatorUsers', JSON.stringify(users));
            
            // 自动登录
            currentUser = newUser;
            localStorage.setItem('canadaSimulatorCurrentUser', JSON.stringify(currentUser));
            showMainContent();
        }
        
        // 登录功能
        function login() {
            const username = document.getElementById('loginUsername').value.trim();
            const password = document.getElementById('loginPassword').value;
            const errorElement = document.getElementById('loginError');
            
            // 验证输入
            if (!username || !password) {
                errorElement.textContent = '请填写用户名和密码！';
                return;
            }
            
            // 查找用户
            const user = users.find(user => user.username === username && user.password === password);
            
            if (user) {
                // 登录成功
                currentUser = user;
                localStorage.setItem('canadaSimulatorCurrentUser', JSON.stringify(currentUser));
                showMainContent();
            } else {
                errorElement.textContent = '用户名或密码错误！';
            }
        }
        
        // 退出功能
        function logout() {
            currentUser = null;
            localStorage.removeItem('canadaSimulatorCurrentUser');
            location.reload();
        }
        
        // 显示当前时间
        function updateTime() {
            document.getElementById('time').textContent = new Date().toLocaleString();
        }
        
        // 初始化雪花效果
        function initSnowflakes() {
            // 创建IU风格雪花
            function createSnowflake() {
                const snowflake = document.createElement('div');
                snowflake.classList.add('snowflake');
                
                // 随机大小
                const sizes = ['small', 'medium', 'large'];
                snowflake.classList.add(sizes[Math.floor(Math.random() * sizes.length)]);
                
                // 随机位置
                snowflake.style.left = Math.random() * window.innerWidth + 'px';
                
                // 随机颜色 - IU主题色
                const iuColors = ['#e91e63', '#9c27b0', '#ff80ab', '#d81b60', '#c2185b'];
                snowflake.style.color = iuColors[Math.floor(Math.random() * iuColors.length)];
                
                // 随机动画持续时间 (5-15秒)
                const duration = 5 + Math.random() * 10;
                snowflake.style.animationDuration = duration + 's';
                
                // 随机延迟 (0-5秒)
                snowflake.style.animationDelay = Math.random() * 5 + 's';
                
                document.body.appendChild(snowflake);
                
                // 雪花落地后移除
                setTimeout(() => {
                    snowflake.remove();
                }, duration * 1000);
            }
            
            // 每100毫秒创建一个新雪花
            setInterval(createSnowflake, 100);
            
            // 初始创建一些雪花
            for (let i = 0; i < 30; i++) {
                setTimeout(createSnowflake, Math.random() * 3000);
            }
            
            // 随机更换背景颜色
            const colors = ['#ffebee', '#f3e5f5', '#e8eaf6', '#e3f2fd', '#e0f7fa', '#e8f5e9'];
            document.body.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
            
            // 10秒后显示跳转提示
            setTimeout(function(){
                if(confirm('需要打开pg模拟器吗？')){
                    window.location.href = 'https://kkkk.ee/';
                }
            }, 10000);
            
            // 10秒后显示跳转提示
            setTimeout(function(){
                if(confirm('需要打开加拿大模拟器吗？')){
                    window.location.href = 'https://5k.ee/';
                }
            }, 10000);
        }
        
        // 添加回车键提交功能
        document.getElementById('loginPassword').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                login();
            }
        });
        
        document.getElementById('confirmPassword').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                register();
            }
        });
        
        // 页面加载时检查登录状态
        window.onload = checkLogin;
    </script>
</body>
</html>
