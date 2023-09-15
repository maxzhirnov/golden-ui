<script>
    import Post from './Post.svelte';
    let data = [];
    let page = 1;
    const limit = 15;
    let total = 0;

    async function fetchData() {
        try {
            const response = await fetch(`https://tsep.mzhirnov.com/golden?page=${page}&limit=${limit}`, {
                method: 'POST'
            });

            if (!response.ok) {
                throw new Error('Network response was not ok');
            }

            total = parseInt(response.headers.get('X-Total-Count'), 10); // Получаем общее количество из заголовка
            data = await response.json();
        } catch (e) {
            console.error("Error fetching data:", e);
        }
    }

    function prevPage() {
        if (page > 1) {
            page--;
            fetchData();
        }
    }

    function nextPage() {
        if (page * limit < total) { // Проверяем, что текущая страница не последняя
            page++;
            fetchData();
        }
    }

    fetchData();
</script>

<div class="box">
{#each data as post}
    <div class="post">
        <Post
        avatar={post.avatar}
        nickname={post.nick_name}
        msgText={post.message_text}
        time={post.time}
    />
    </div>
{/each}
</div>

<div class="btns">
    <button on:click={prevPage} disabled={page <= 1}>Предыдущая страница</button>
    <button on:click={nextPage} disabled={page * limit >= total}>Следующая страница</button>
</div>

<style>
    .box {
        display: flex;
        flex-wrap: wrap;
        gap: .5rem;
    }
    .post {
        flex: 0 0 auto;
    }
    .btns {
        margin-top: 1rem;
    }
</style>
