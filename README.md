<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Social Media Platform</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <!-- Header -->
        <header>
            <h1>Social Media</h1>
            <div class="user-info">
                <span>Welcome, User!</span>
                <button id="logoutBtn">Logout</button>
            </div>
        </header>

        <!-- Post Creation Section -->
        <div class="post-creation">
            <textarea id="postInput" placeholder="What's on your mind?"></textarea>
            <button id="postBtn">Post</button>
        </div>

        <!-- Feed Section -->
        <div class="feed">
            <h2>Feed</h2>
            <ul id="postList"></ul>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>



STYLES.CSS


/* General Styles */
body {
    font-family: Arial, sans-serif;
    background-color: #f0f2f5;
    margin: 0;
    padding: 0;
    color: #333;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

/* Header */
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

header h1 {
    margin: 0;
    font-size: 24px;
}

.user-info {
    display: flex;
    align-items: center;
    gap: 10px;
}

#logoutBtn {
    padding: 5px 10px;
    background-color: #ff4d4d;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#logoutBtn:hover {
    background-color: #cc0000;
}

/* Post Creation Section */
.post-creation {
    margin-bottom: 20px;
}

#postInput {
    width: 100%;
    height: 100px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    resize: none;
    font-family: Arial, sans-serif;
    font-size: 16px;
}

#postBtn {
    display: block;
    margin-top: 10px;
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#postBtn:hover {
    background-color: #0056b3;
}

/* Feed Section */
.feed h2 {
    margin-bottom: 10px;
    font-size: 20px;
}

#postList {
    list-style-type: none;
    padding: 0;
}

.post {
    background-color: #f9f9f9;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 4px;
    margin-bottom: 10px;
}

.post p {
    margin: 0;
    font-size: 16px;
}

.post small {
    color: #888;
    font-size: 12px;
}


script.js


document.addEventListener('DOMContentLoaded', () => {
    const postInput = document.getElementById('postInput');
    const postBtn = document.getElementById('postBtn');
    const postList = document.getElementById('postList');
    const logoutBtn = document.getElementById('logoutBtn');

    // Array to store posts (simulating a database)
    let posts = [];

    // Add a new post
    postBtn.addEventListener('click', () => {
        const postText = postInput.value.trim();
        if (postText !== '') {
            const newPost = {
                id: Date.now(),
                text: postText,
                timestamp: new Date().toLocaleString(),
            };
            posts.push(newPost);
            renderPosts();
            postInput.value = '';
        }
    });

    // Render posts
    function renderPosts() {
        postList.innerHTML = '';
        posts.forEach(post => {
            const li = document.createElement('li');
            li.className = 'post';
            li.innerHTML = `
                <p>${post.text}</p>
                <small>Posted on ${post.timestamp}</small>
            `;
            postList.appendChild(li);
        });
    }

    // Logout functionality (simulated)
    logoutBtn.addEventListener('click', () => {
        alert('Logged out!');
        // Redirect to login page or clear session (not implemented here)
    });

    // Initial render
    renderPosts();
});


