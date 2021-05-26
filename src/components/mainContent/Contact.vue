<template>
    <div id="contact" class="contact">
        <div>
            <h5 v-text="data.contact_heading" />
            <form>
                <input type="text" :placeholder="data.name_label" v-model="mail.name" required 
                 :class="data.lang === 'ar' ? 'rtl' : '' " />
                <input type="email" :placeholder="data.email_label" v-model="mail.email" required
                 :class="data.lang === 'ar' ? 'rtl' : '' " />
                <textarea rows="8" :placeholder="data.message_label" v-model="mail.message"
                 :class="data.lang === 'ar' ? 'rtl' : '' " >

                </textarea>
                <p id="feedback" v-text="feedback"></p>
                <button @click.prevent="sendEmail">
                    {{ data.send_btn }}
                </button>
                
            </form>
        </div>
        <div>
            <a class="item" :href="'tel:' + data.phone">
                <img src="./../../assets/phone.png">
                <span v-text="data.phone" />
            </a>
            <a class="item" :href="'mailto:' + data.email">
                <img src="./../../assets/gmail.png">
                <span v-text="data.email" />
            </a>
            <a class="item" :href="'https://www.linkedin.com/in/' + data.linkedin + '/'" target="_BLANK">
                <img src="./../../assets/linkedin.png">
                <span v-text="data.linkedin" />
            </a>
            <a class="item" :href="'https://www.facebook.com/' + data.facebook + '/'" target="_BLANK">
                <img src="./../../assets/facebook.png">
                <span v-text="data.facebook" />
            </a>
            <a class="item" :href="'https://www.instagram.com/' + data.instagram + '/'" target="_BLANK">
                <img src="./../../assets/instagram.png">
                <span v-text="data.instagram" />
            </a>
        </div>
    </div>
</template>

<script>
import emailjs from 'emailjs-com';

    export default {
        name: 'Contact',
        props: ['data'],
        data() {
            return {
                mail: {}
            }
        },
        methods: {
            sendEmail() {
                var templateParams = {
                        name: this.mail.name,
                        email: this.mail.email + " ",
                        message: this.mail.message + " ",
                        
                }
                const serviceID = 'service_dyozx05';
                const templateID = 'template_pwyxb4s';
                const userID = 'user_aew1XU7c2JP3topXNbU9p';
                var feedback =document.getElementById('feedback');

                try {
                    emailjs.send(serviceID, templateID, templateParams, userID);
                    feedback.textContent = this.data.feedback_message;
                    feedback.style.display = "block";

                } catch(error) {
                    console.log({error})
                    feedback.textContent = this.data.error_message;
                    feedback.style.color = "#F00";
                    feedback.style.display = "block";
                }
            },
        },
    }
</script>


<style scoped>
    .rtl {
        direction: rtl;
    }

    .contact {
        padding: 3% 5%;
        display: flex;
        align-items: center;
    }

    .contact>div {
        width: 50%;
        padding: 40px;
    }

    .item {
        display: flex;
        align-items: center;
        margin-bottom: 20px;
        text-decoration: none;
        font-size: 1.6rem;
        font-weight: bold;
        color: #1f203a;
    }

    h5 {
        font-size: 2rem;
        font-weight: 400;
        color: #1f203a;
        margin-bottom: 40px;
        margin-top: 0;
        text-align: center;
    }

    img {
        margin-right: 20px;
        width: 60px;
        height: 60px;
        transition: all 0.4s ease-in-out;
    }

    form {
        display: block;
        margin: 0 auto;
        width: 80%;
    }

    form:after {
        content: '';
        clear: both;
    }

    input, textarea {
        display: block;
        width: 100%;
        margin-bottom: 15px;
        padding: 10px 20px;
        border-radius: 10px;
        border: 1px solid #1f203a;
        font-size: 1.1rem;
        font-family: Arial, Helvetica, sans-serif;
    }

    button {
        padding: 10px 30px;
        border-radius: 10px;
        border: 1px solid #1f203a;
        background-color: #1f203a;
        color: white;
        float: right;
        font-size: 1rem;
        cursor: pointer;
        transition: all 0.5s ease-in-out;
    }

    button:hover {
        background-color: white;
        color: #1f203a;
    }

    #feedback {
        display: none;
        float: left;
        margin-top: 14px;
        font-size: 14px;
        color: #080;
        font-style: italic;
    }

    @media(max-width: 767px) {
        .contact {
            flex-direction: column;
        }

        .contact>div {
            width: 100%;
            padding: 10px;
        }

        .contact>div:first-of-type {
            order: 2;
        }

        .item {
            font-size: 17px
        }

        img {
            width: 50px;
            height: 50px;
        }

        h5 {
            margin-top: 0;
            margin-bottom: 40px;
        }

        form {
            width: 100%;
            margin: 0;

        }

        input, textarea {
            width: 87%;
        }
    }

</style>
