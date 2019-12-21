<template>
    <div id="app">
        <Container>
            <ChatWindow>
                <ChatMessage
                        username="Ivan"
                        datetime="21.12.2019 05:00:50">
                    Hello, World!
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
        }
    }
</script>

<style>
    body {
        margin: 0;
        background-color: #f9f9fa;
    }
</style>
