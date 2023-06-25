<template>
    <div class="row">
        <div class="col-md-12">
            <div class="footer">
                <p><a id="one-word" @click="refresh">{{ oneWord }}</a></p>
                <p>
                    <a>Copyright&nbsp;&copy;&nbsp;2021&nbsp;-&nbsp;{{ year }}</a>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Footer",
        data() {
            return {
                year: new Date().getFullYear(),
                oneWord: this.getOne(),
            }
        },
        mounted() {
            this.getOne().then(result => {
                this.oneWord = result;
            })
        },
        methods: {
            getOne() {
                return this.api.get('https://v1.hitokoto.cn/?encode=text', false);
            },
            refresh() {
                this.getOne().then(result => {
                    this.oneWord = result;
                });
            }
        }
    }
</script>

<style scoped>
    .footer {
        font-size: .8em;
        text-align: center;
    }

    .footer p {
        margin: 1em;
    }

    .footer a:link, .footer a:visited {
        color: #000000;
    }

    #one-word {
        -webkit-touch-callout: none;
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        cursor: pointer;
    }

    #one-popover {
        font-family: Menlo, Monaco, "Andale Mono", "lucida console", "Courier New", monospace;
    }

    #donate img {
        width: 100%;
    }

    .logo img {
        height: 2em;
    }
    .logo svg {
        height: 2em;
    }
    .logo {
        margin: .8em;
    }
</style>
