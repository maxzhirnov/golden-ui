<script>
    export let avatar = "https://api.telegram.org/file/bot5995751290:AAGVnspmM1QOuNgvtT5nBtzHozNuS4goPVM/photos/file_0.jpg"
    export let nickname = "maximzc"
    export let msgText = "Test"
    export let time = "14:12"
</script>

<div class="telegram-container">
    <div class="content">
        <div class="avatar" style="background-image: url({avatar});"></div>
        <div class="telegram-bubble">
            <div class="sender-name">{nickname}</div>
            <div class="msg-text">{msgText}</div>
            <div class="msg-time">{time}</div>
        </div>
</div>
</div>

<style>
    .telegram-container {
        width: 330px;
        height: 330px;
        display: flex;
        justify-content: center; /* Центрирование содержимого по горизонтали */
        align-items: center;     /* Центрирование содержимого по вертикали */
        background: url('https://storage.yandexcloud.net/mzhirnov/tggen/bg.jpg') no-repeat center;
        background-color: #E5E5E5;
        position: relative;
        font-family: Arial, sans-serif;
        border-radius: 1rem;
    }

    .content {
        display: flex;
        gap: 1.5rem;
        align-items: end;
    }

    .telegram-bubble {
        max-width: 200px;
        background-color: #ffffff;
        border-radius: 18px 18px 18px 0px; /* Изменение скругления углов */
        padding: 10px 15px 10px 15px;
        position: relative;
    }

    .telegram-bubble:before {
        content: "";
        width: 20px;
        height: 20px;
        background-color: #ffffff;
        clip-path: polygon(100% 0%, 0% 100%, 100% 100%);
        position: absolute;
        bottom: 0px; 
        left: -20px;
    }

    .avatar {
        width: 42px;
        height: 42px;
        border-radius: 50%;
        left: 60px; 
        background-color: aqua;
        background-size: cover;
    }

    .sender-name {
        color: rgb(58, 58, 179);
        font-weight: 600;
        text-align: left;
        font-size: .85em;
    }
    .msg-time {
        color: gray;
        text-align: end;
        font-style: italic;
        font-size: 14px;
    }
    .msg-text {
        word-wrap: break-word;
        font-size: .85em;
        text-align: left;
    }

</style>