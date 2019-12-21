<template>
    <div id="app">
        <Container>
            <ChatWindow
                v-on:send-message="sendMessage($event)">
                <ChatMessage
                    v-for="(message, index) in messages"
                    v-bind:key="index"
                    v-bind:username="message.author"
                    v-bind:datetime="message.datetime">
                    {{ message.text }}
                </ChatMessage>
            </ChatWindow>
        </Container>
    </div>
</template>

<script>
    import Container from "@/components/Container";
    import ChatMessage from "@/components/ChatMessage";
    import ChatWindow from "@/components/ChatWindow";

    export default {
        name: 'app',
        components: {
            Container, ChatMessage, ChatWindow
        },
        data() {
            return {
                messages: []
            }
        },
        methods: {
            getMessages() {
                this.axios.get("http://188.225.47.187/api/chat/getmessages.php")
                    .then((response) => {
                        this.messages = response.data.reverse();
                    })
            },
            sendMessage(params) {
                this.axios.post("http://188.225.47.187/api/chat/sendmessage.php", {
                    author: params.username,
                    text: params.text
                }).then(() => {
                    this.getMessages();
                });
            }
        },
        mounted() {
            setInterval(this.getMessages, 1000);
        }
    }
</script>

<style>
    body {
        margin: 0;
        background-color: #f9f9fa;
    }
</style>
