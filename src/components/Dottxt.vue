<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <!-- <Nav :navLinks="navLinks" :navConfig="navConfig" :btnConfig="btnConfig"> -->
        <Nav :navConfig="navConfig" :btnConfig="btnConfig">
            <img class="img" src="" alt="" />
            <a href="#" class="saveBtn" v-bind:class="saveButton" @click="saveText"> Save </a>
        </Nav>
        <div id="app">
            <ckeditor :editor="editor" v-model="editorData" :config="editorConfig" tag-name="textarea" id="editor1" class="editor1"></ckeditor>
        </div>
    </div>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
import Nav from "vue-nav-ui"


export default {
    name: 'Dottxt',
    components: {
        Nav,
        // ckeditor: ClassicEditor.component
    },
    props: {
        msg: String
    },
    methods: {
        saveText: function() {
            var text = document.getElementsByClassName("ck-content")[0].querySelectorAll("p");
            console.log(text[0].innerHTML);
        }
    },
    data() {
        return {
            // CKEditor
            editor: ClassicEditor,
            editorData: '<p>Text here..</p>',
            editorConfig: {
                // The configuration of the editor.
                //removePlugins: ['ImageToolbar', 'ImageUpload', 'MediaEmbed']
            },
            navConfig: {
                whitespace: true, /* GIVES PADDING TO YOUR NAV, IF SET TO FALSE, REMOVES PADDING */
                navBg: "#FAFAFA", /* BACKGROUND COLOR OF YOUR NAV  */
                navBorderRadius: "30px", /* BORDER RADIUS OF YOUR NAV */
                linkFont: "poppins", /* FONT FAMILY OF YOUR NAV */
                linkColor: "black", /* FONT COLOR OF YOUR NAV */
                responsivePosition: "TOP", /* FOR CHANGING THE POSITION OF YOUR NAV WHEN RESPONSIVE. BOTTOM or TOP | The only two options */
            },
            btnConfig: {
                btnLink: false, /* FOR INITIALIZING NAV BUTTON USAGE, IF SET TO FALSE, REMOVES THE NAV BUTTON  */
                btnUrl: "showMore", /* LINK URL OF YOUR NAV BUTTON */
                btnText: "Save", /* NAV BUTTON TEXT */
                btnBg: "#004d15", /* BACKGROUND COLOR OF YOUR NAV BUTTON  */
                btnTextColor: "white", /* FONT COLOR OF YOUR NAV BUTTON*/
                btnBorderWidth: "5", /* BORDER WIDTH OF YOUR NAV BUTTON */
                btnBorderColor: "black", /* BORDER COLOR OF YOUR NAV BUTTON */
                btnBorderRadius: "20px", /* BORDER RADIUS OF YOUR NAV BUTTON */
            }
        };
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h1 {
    font-style: italic;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: black;
    text-decoration: none;
    border: 2px solid black;
    padding: 7px;
    border-radius: 12px;
    transition-duration: 0.4s;
}

a:hover {
    background-color: #e8ffc6;
    color: #3e8e34;
    border-color: #51a372;
}
</style>
