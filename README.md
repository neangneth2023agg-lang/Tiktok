# Tiktok
Tiktok
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Social Profile Demo</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f5f5f5;
}

.demo {
    position: fixed;
    top: 10px;
    left: 10px;
    z-index: 99;
    background: #ff0050;
    color: white;
    padding: 7px 12px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: bold;
}

.app {
    width: 100%;
    max-width: 430px;
    min-height: 100vh;
    margin: auto;
    background: white;
}

.header {
    padding: 45px 20px 20px;
    text-align: center;
    border-bottom: 1px solid #eee;
}

.avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #eee;
}

.username {
    font-size: 21px;
    font-weight: bold;
    margin-top: 12px;
}

.handle {
    color: #777;
    margin-top: 4px;
}

.bio {
    margin: 12px auto;
    max-width: 300px;
}

.stats {
    display: flex;
    justify-content: space-around;
    margin: 20px 0;
}

.stat b {
    display: block;
    font-size: 18px;
}

.stat span {
    color: #777;
    font-size: 13px;
}

button {
    border: none;
    border-radius: 7px;
    padding: 10px 25px;
    cursor: pointer;
}

.edit {
    background: #111;
    color: white;
}

.panel {
    padding: 20px;
    background: #fafafa;
}

input {
    width: 100%;
    padding: 11px;
    margin: 6px 0 12px;
    border: 1px solid #ddd;
    border-radius: 7px;
}

.save {
    width: 100%;
    background: #ff0050;
    color: white;
    font-weight: bold;
}
</style>
</head>

<body>

<div class="demo">DEMO — KHÔNG PHẢI TÀI KHOẢN THẬT</div>

<div class="app">

    <div class="header">

        <img
            id="avatar"
            class="avatar"
            src="https://placehold.co/200x200"
        >

        <div id="name" class="username">Tên người dùng</div>
        <div id="handle" class="handle">@username</div>

        <div id="bio" class="bio">
            Đây là hồ sơ mô phỏng.
        </div>

        <div class="stats">

            <div class="stat">
                <b id="following">123</b>
                <span>Đang follow</span>
            </div>

            <div class="stat">
                <b id="followers">12.5K</b>
                <span>Follower</span>
            </div>

            <div class="stat">
                <b id="likes">98.7K</b>
                <span>Thích</span>
            </div>

        </div>

        <button class="edit" onclick="toggleEditor()">
            ✏️ Chỉnh sửa hồ sơ
        </button>

    </div>

    <div id="editor" class="panel" style="display:none">

        <label>Tên hiển thị</label>
        <input id="nameInput" placeholder="Nhập tên">

        <label>Username</label>
        <input id="handleInput" placeholder="@username">

        <label>Bio</label>
        <input id="bioInput" placeholder="Nhập bio">

        <label>Follower</label>
        <input id="followersInput" placeholder="12.5K">

        <label>Following</label>
        <input id="followingInput" placeholder="123">

        <label>Likes</label>
        <input id="likesInput" placeholder="98.7K">

        <label>Ảnh đại diện</label>
        <input
            type="file"
            id="avatarInput"
            accept="image/*"
        >

        <button class="save" onclick="saveProfile()">
            Lưu thay đổi
        </button>

    </div>

</div>

<script>

function toggleEditor() {

    const editor = document.getElementById("editor");

    editor.style.display =
        editor.style.display === "none"
        ? "block"
        : "none";
}

function saveProfile() {

    const name =
        document.getElementById("nameInput").value;

    const handle =
        document.getElementById("handleInput").value;

    const bio =
        document.getElementById("bioInput").value;

    const followers =
        document.getElementById("followersInput").value;

    const following =
        document.getElementById("followingInput").value;

    const likes =
        document.getElementById("likesInput").value;

    if (name)
        document.getElementById("name").textContent = name;

    if (handle)
        document.getElementById("handle").textContent =
            handle.startsWith("@") ? handle : "@" + handle;

    if (bio)
        document.getElementById("bio").textContent = bio;

    if (followers)
        document.getElementById("followers").textContent = followers;

    if (following)
        document.getElementById("following").textContent = following;

    if (likes)
        document.getElementById("likes").textContent = likes;

    const file =
        document.getElementById("avatarInput").files[0];

    if (file) {

        const reader = new FileReader();

        reader.onload = function(e) {

            document.getElementById("avatar").src =
                e.target.result;

        };

        reader.readAsDataURL(file);
    }
}

</script>

</body>
</html>
