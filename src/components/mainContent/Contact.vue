<template>
    <div id="contact" class="contact">
        <div>
            <h5>Send me message !</h5>
            <form>
                <input type="text" placeholder="Votre Nom" v-model="mail.name">
                <input type="tel" placeholder="Votre Telephone" v-model="mail.phone">
                <textarea rows="10" placeholder="Votre message" v-model="mail.message">

                </textarea>
                <button @click.prevent="sendEmail">
                    Envoyer
                </button>
                <div id="feedback" v-text="feedback"></div>
            </form>
        </div>
        <div>
            <a class="item" href="tel:+21650870256">
                <img src="./../../assets/phone.png">
                <span>+216 50 870 256</span>
            </a>
            <a class="item" href="mailto:grissa.maamoun@gmail.com">
                <img src="./../../assets/gmail.png">
                <span>grissa.maamoun@gmail.com</span>
            </a>
            <a class="item" href="https://www.facebook.com/maamoung/" target="_BLANK">
                <img src="./../../assets/facebook.png">
                <span>maamoung</span>
            </a>
            <a class="item" href="https://www.instagram.com/gmaamoun/" target="_BLANK">
                <img src="./../../assets/instagram.png">
                <span>gmaamoun</span>
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
                feedback: '',
                mail: {}
            }
        },
        methods: {
            sendEmail() {
                var templateParams = {
                        name: this.mail.name,
                        phone: this.mail.phone + " ",
                        message: this.mail.message + " ",
                        
                }
                const serviceID = 'service_dyozx05';
                const templateID = 'template_pwyxb4s';
                const userID = 'user_aew1XU7c2JP3topXNbU9p';

                try {
                    emailjs.send(serviceID, templateID, templateParams, userID);
                    this.feedback = 'Votre commande est effectuée !';


                } catch(error) {
                    console.log({error})
                    this.feedback = "Echeck ! Essayez ultiréurenment";
                    document.getElementById('feedback').style.color = "#F00";
                    setTimeout(() => {
                        this.$emit('closeModal')
                    }, 3000);

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

    h1 {
        font-size: 2.5rem;
        margin-bottom: 5px;
        color: #1f203a;
    }

    h2 {
        font-size: 2rem;
        font-weight: 400;
        margin-top: 10px;
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

    p {
        color: #333;
        font-size: 1.1rem;
        line-height: 1.6;
        height: 260px;
    }

    img {
        margin-right: 20px;
        width: 60px;
        height: 60px;
        transition: all 0.4s ease-in-out;
    }

    img:hover {
        filter: none
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

    .feedback {
        display: none;
        float: left;
        margin-top: 10px;
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

        h1 {
            text-align: center;
        }

        h2 {
            text-align: center;
        }

        h5 {
            margin-top: 0;
            margin-bottom: 40px;
        }

        p {
            font-size: 1.1rem;
            line-height: 1.6;
            text-align: center;
            height: auto;
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
