<template>
    <div class="app">
        <div class="app__header">
            <main-btn style="margin: 0 auto; display: block" @click="openModal"
                >Создать новый пост 📝
            </main-btn>

            <custom-select
                v-model="selectedSortOption"
                :options="sortOptions"
            />
        </div>

        <modal-window v-model:isShow="isModalShow">
            <new-post-form @addNewPost="handleNewPost" />
        </modal-window>

        <post-list v-if="!isLoading" :posts="posts" @delete="deletePost" />
        <h3 v-else>Loading...</h3>
    </div>
</template>

<script>
import NewPostForm from "./components/NewPostForm.vue"
import PostList from "./components/PostList.vue"

export default {
    components: {
        NewPostForm,
        PostList,
    },

    // (+) Типо useMemo/useCallback
    computed: {
        // (-) Документация: "геттер вычисляемого свойства"
        // (?) данная функция будет возвращать отсортированные посты
        // sortedPosts() {
        //     let sortFunction
        //     switch (this.selectedSortOption) {
        //         case "title":
        //         case "body":
        //             sortFunction = (post1, post2) =>
        //                 post1[this.selectedSortOption].localeCompare(
        //                     post2[this.selectedSortOption]
        //                 )
        //             break
        //         case "date":
        //             sortFunction = (post1, post2) => post1.id - post2.id
        //             break
        //         default:
        //             return [...this.posts]
        //     }
        //     return [...this.posts].sort(sortFunction)
        // },
    },

    // (+) типо useEffect
    watch: {
        // (?) функция-наблюдатель должна иметь такое же имя как и значение за которым оно следит
        //     параметром в нее приходит новое значение

        selectedSortOption(sortType) {
            let sortFunction

            switch (sortType) {
                case "title":
                case "body":
                    sortFunction = (post1, post2) =>
                        post1[sortType].localeCompare(post2[sortType])

                    break
                case "date":
                    sortFunction = (post1, post2) => post1.id - post2.id
                    break
                default:
                    return
            }

            this.posts.sort(sortFunction)
        },
    },

    data() {
        return {
            posts: [],
            isModalShow: false,
            isLoading: true,
            selectedSortOption: "",
            sortOptions: [
                { value: "title", name: "По названию" },
                { value: "body", name: "По описанию" },
                { value: "date", name: "По дате добавления" },
            ],
        }
    },
    methods: {
        openModal() {
            this.isModalShow = true
        },
        handleNewPost(post) {
            this.posts = [post, ...this.posts]
            this.isModalShow = false
        },
        deletePost(postId) {
            this.posts = this.posts.filter(({ id }) => id !== postId)
        },
        async fetchPosts() {
            try {
                this.isLoading = true

                const data = await fetch(
                    "https://jsonplaceholder.typicode.com/posts?_limit=10"
                )
                const parsedPosts = await data.json()
                this.posts = parsedPosts.map(({ id, title, body }) => ({
                    id,
                    title,
                    body,
                }))
            } catch (error) {
                alert(error)
            } finally {
                this.isLoading = false
            }
        },
    },
    mounted() {
        this.fetchPosts()
    },
}
</script>

<style>
:root {
    --green: yellowgreen;
    --black: #303030;
}
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    background: var(--black);
    color: var(--green);
    overflow: overlay;
}
#app,
.app,
body {
    min-height: 100vh;
}
.app {
    padding: 20px 10px;
}
.app__header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
}
</style>
