<template>
    <div class="app">
        <div class="panel">
            <h2>Personnalisez votre signature</h2>
            
            <div class="button-group">
                <button @click="copyHTML"><i class="fa-solid fa-code"></i> Copier le code HTML</button>
                <button @click="copy"><i class="fa-solid fa-scissors"></i> Copier le script</button>
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-user"></i>
                <input type="text" v-model="fullName" placeholder="Entrez votre nom et prénom" />
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-briefcase"></i>
                <input type="text" v-model="title" placeholder="Entrez votre poste" />
            </div>
            
            <div class="input-group">
                <i class="fa-brands fa-facebook"></i>
                <input type="text" v-model="facebook" placeholder="Entrez votre lien Facebook" />
            </div>
            
            <div class="input-group">
                <i class="fa-brands fa-instagram"></i>
                <input type="text" v-model="instagram" placeholder="Entrez votre lien Instagram" />
            </div>
            
            <div class="input-group">
                <i class="fa-brands fa-x-twitter"></i>
                <input type="text" v-model="twitter" placeholder="Entrez votre lien Twitter" />
            </div>
            
            <div class="input-group">
                <i class="fa-brands fa-linkedin"></i>
                <input type="text" v-model="linkedin" placeholder="Entrez votre lien LinkedIn" />
            </div>
            
            <div class="input-group">
                <i class="fa-brands fa-github"></i>
                <input type="text" v-model="github" placeholder="Entrez votre lien GitHub" />
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-envelope"></i>
                <input type="text" v-model="email" placeholder="Entrez votre e-mail" />
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-phone"></i>
                <input type="text" v-model="phone" placeholder="Entrez votre numéro de téléphone" />
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-globe"></i>
                <input type="text" v-model="website" placeholder="Entrez votre site web" />
            </div>
            
            <div class="input-group">
                <i class="fa-solid fa-quote-left"></i>
                <select v-model="selectedQuote">
                    <option value="">Aucune citation</option> 
                    <option v-for="(quote, index) in quotes" :key="index" :value="quote">{{ quote.name }}</option>
                </select>
            </div>
            
        </div>
        
        <!-- Conteneur pour la signature -->
        <div class="signature-container" id="toCopy" style="display: flex; justify-content: center; align-items: center; height: 100vh; width: calc(100% - 400px); margin-left: 20%;">
            <table style="border-collapse: collapse; width: 100%; max-width: 400px; background-color: white; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);">
                
                <tr>
                    <td style="padding: 15px 15px 0px 15px; border: none; text-align: center;">
                        <div style="display: flex; align-items: center;">
                            <img src="../assets/logo-gr.png" alt="Logo" style="width: 100px; height: 100px; margin-right: 10px;" />
                            <div>
                                <div style="font-weight: bold; font-size: 1.5em;">{{ fullName }}</div>
                                <div style="font-style: italic; margin-top:4px; color:grey;">{{ title }}</div>
                            </div>
                        </div>
                    </td>
                </tr>
                
                <tr v-if="facebook || twitter || instagram || linkedin || github">
                    <td style="text-align: center; padding-bottom: 7px;">
                        <div style="display: flex; justify-content: center; gap: 25px; color: grey; height: 20px;">
                            <a v-if="facebook" :href="facebook" target="_blank" title="Lien vers compte Facebook" style="color: grey; text-decoration: none;">
                                <i class="fa-brands fa-facebook" style="color: orange; font-size: 18px;"></i>
                            </a>
                            <a v-if="twitter" :href="twitter" target="_blank" title="Lien vers compte X" style="color: grey; text-decoration: none;">
                                <i class="fa-brands fa-x-twitter" style="color: orange; font-size: 18px;"></i>
                            </a>
                            <a v-if="instagram" :href="instagram" target="_blank" title="Lien vers compte Instagram" style="color: grey; text-decoration: none;">
                                <i class="fa-brands fa-instagram" style="color: orange; font-size: 18px;"></i>
                            </a>
                            <a v-if="linkedin" :href="linkedin" target="_blank" title="Lien vers compte LinkedIn" style="color: grey; text-decoration: none;">
                                <i class="fa-brands fa-linkedin" style="color: orange; font-size: 18px;"></i>
                            </a>
                            <a v-if="github" :href="github" target="_blank" title="Lien vers compte GitHub" style="color: grey; text-decoration: none;">
                                <i class="fa-brands fa-github" style="color: orange; font-size: 18px;"></i>
                            </a>
                        </div>
                    </td>
                </tr>
                
                <tr>
                    <td v-if="email || phone || website " style="padding: 5px 20px; border: none; text-align: center;">
                        <hr style="border: none; height: 1px; background-color: #ddd;" />
                    </td>
                </tr>
                
                <tr>
                    <td style="border: none; text-align: center;">
                        <div v-if="email" style=" padding: 10px 20px; display: flex; align-items: center; color:grey; text-decoration: none;">
                            <i class="fas fa-envelope" style="margin-right: 10px; color: orange;"></i>
                            <a href="mailto:rigauxgauthier@gmail.com" title="Envoyer un mail" style="text-decoration:none; color:grey;">{{ email }}</a>
                        </div>
                    </td>
                </tr>
                
                <tr>
                    <td style=" border: none; text-align: center;">
                        <div v-if="phone" style="padding: 10px 20px; display: flex; align-items: center; color: grey; text-decoration: none;">
                            <i class="fas fa-phone" style="margin-right: 10px; color: orange;"></i>
                            <span>{{ phone }}</span>
                        </div>
                    </td>
                </tr>
                
                <tr>
                    <td style="border: none; text-align: center;">
                        <div v-if="website" style="padding: 10px 20px; display: flex; align-items: center; color: grey; text-decoration: none;">
                            <i class="fas fa-globe" style="margin-right: 10px; color: orange;"></i>
                            <a :href="'https://' + website" target="_blank" title="Lien vers site internet" style="color: grey; text-decoration: none; ">{{ website }}</a>
                        </div>
                    </td>
                </tr>
                
                <tr v-if="selectedQuote && selectedQuote.quote" style="background:#1e1e1e;">
                    <td style="padding: 10px 22px; border: none; text-align: left;">
                        <blockquote style="font-style: italic; color: lightgrey; margin: 0; padding: 10px; border-left: 2px solid orange; font-size: 0.75em">
                            "{{ selectedQuote.quote }}" <br>
                            <span style="font-weight: bold; font-style: normal; display: block; text-align: right; margin-top: 8px;">{{ selectedQuote.name }}</span>
                        </blockquote>
                    </td>
                </tr>
                
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SignatureBlock',
    data() {
        return {
            fullName: '',
            title: '',
            email: '',
            phone: '',
            website: '',
            facebook: '', 
            twitter: '',   
            instagram: '', 
            linkedin: '', 
            github: '', 
            selectedQuote: '',
            quotes: [
            { name: 'Albert Einstein', quote: 'La imagination est plus importante que la connaissance.' },
            { name: 'Isaac Newton', quote: 'Ce qui est fait est fait; ce qui est dit est dit.' },
            { name: 'Nelson Mandela', quote: 'Je ne perds jamais. Soit je gagne, soit j’apprends.' },
            { name: 'Steve Jobs', quote: 'Votre temps est limité, ne le gaspillez pas à vivre la vie de quelqu’un d’autre.' },
            { name: 'Maya Angelou', quote: 'Vous pouvez rencontrer de nombreuses défaites, mais vous ne devez pas être vaincu.' },
            { name: 'Marie Curie', quote: 'Rien dans la vie n’est à craindre, il est seulement à comprendre.' },
            { name: 'Walt Disney', quote: 'Si vous pouvez le rêver, vous pouvez le faire.' },
            { name: 'Henry Ford', quote: 'Que vous pensiez que vous pouvez ou que vous ne pouvez pas, vous avez raison.' },
            { name: 'Confucius', quote: 'Il est plus honteux de se poser des questions que de donner de fausses réponses.' },
            { name: 'Mark Twain', quote: 'Dans 20 ans, vous serez plus déçu par les choses que vous n’avez pas faites que par celles que vous avez faites.' },
            ]
        };
    },
    mounted() {
        
        if (localStorage.getItem('fullName')) {
            this.fullName = localStorage.getItem('fullName');
        }
        if (localStorage.getItem('title')) {
            this.title = localStorage.getItem('title');
        }
        if (localStorage.getItem('email')) {
            this.email = localStorage.getItem('email');
        }
        if (localStorage.getItem('phone')) {
            this.phone = localStorage.getItem('phone');
        }
        if (localStorage.getItem('website')) {
            this.website = localStorage.getItem('website');
        }
        if (localStorage.getItem('selectedQuote')) {
            this.selectedQuote = JSON.parse(localStorage.getItem('selectedQuote'));
        }
        if (localStorage.getItem('facebook')) {
            this.facebook = JSON.parse(localStorage.getItem('facebook'));
        }
        if (localStorage.getItem('instagram')) {
            this.instagram = JSON.parse(localStorage.getItem('instagram'));
        }
        if (localStorage.getItem('twitter')) {
            this.twitter = JSON.parse(localStorage.getItem('twitter'));
        }
        if (localStorage.getItem('linkedin')) {
            this.linkedin = JSON.parse(localStorage.getItem('linkedin'));
        }
        if (localStorage.getItem('github')) {
            this.github = JSON.parse(localStorage.getItem('github'));
        }
    },
    watch: {
        
        fullName(newVal) {
            localStorage.setItem('fullName', newVal);
        },
        title(newVal) {
            localStorage.setItem('title', newVal);
        },
        email(newVal) {
            localStorage.setItem('email', newVal);
        },
        phone(newVal) {
            localStorage.setItem('phone', newVal);
        },
        website(newVal) {
            localStorage.setItem('website', newVal);
        },
        selectedQuote(newVal) {
            localStorage.setItem('selectedQuote', JSON.stringify(newVal));
        }, 
        facebook(newVal) {
            localStorage.setItem('facebook', JSON.stringify(newVal));
        },
        instagram(newVal) {
            localStorage.setItem('instagram', JSON.stringify(newVal));
        },
        twitter(newVal) {
            localStorage.setItem('twitter', JSON.stringify(newVal));
        }, 
        linkedin(newVal) {
            localStorage.setItem('linkedin', JSON.stringify(newVal));
        },
        github(newVal) {
            localStorage.setItem('github', JSON.stringify(newVal));
        },
    }, 
    methods:{
        
        copy: function(event){
            this.copyElementToClipboard(document.getElementById('toCopy'));
            event.target.classList.add('actif');
            setTimeout(function(){ event.target.classList.remove('actif'); }, 1000);
        },
        
        copyHTML: function(event){
            this.copyToClipboard(document.getElementById('toCopy').outerHTML);
            event.target.classList.add('actif');
            setTimeout(function(){ event.target.classList.remove('actif'); }, 1000);
        },
        
        copyElementToClipboard(element){
            window.getSelection().removeAllRanges();
            let range = document.createRange();
            range.selectNode(typeof element === 'string' ? document.getElementById(element) : element);
            window.getSelection().addRange(range);
            document.execCommand('copy');
            window.getSelection().removeAllRanges();
        },
        
        copyToClipboard(text) {
            if(document.queryCommandSupported && document.queryCommandSupported("copy")) {
                var textarea = document.createElement("textarea");
                textarea.textContent = text;
                textarea.style.position = "fixed";
                document.body.appendChild(textarea);
                textarea.select();
                try {
                    return document.execCommand("copy");
                } catch (ex) {
                    console.warn("Copy to clipboard failed.", ex);
                    return false;
                } finally {
                    document.body.removeChild(textarea);
                }
            }
        }
    }
};


</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    display: flex;
}

.panel {
    position: fixed;
    top: 0;
    right: 0;
    width: 450px;
    height: 100%;
    background: #1e1e1e;
    box-shadow: -2px 0 5px rgba(0, 0, 0, 0.2);
    color: white;
    padding: 20px;
    border: 1px solid #ddd;
    overflow-y: scroll;
    
}

.panel h2 {
    margin-bottom: 10px;
    color: orange;
    text-align: center;
}

label {
    display: block;
    margin-bottom: 15px;
    font-weight: 600;
    text-align: left;
}

input[type="text"],
select {
    width: 100%;
    margin-top: 5px;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ddd;
    background: #fff;
    font-weight: 500;
    outline: none;
}

input[type="text"]:focus,
select:focus {
    border-color: orange;
    box-shadow: 0px 0px 15px rgba(255, 165, 0, 0.5);
}

.input-group:focus-within i {
    color: orange;
}

.button-group {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin: 20px 0;
}

button {
    letter-spacing: 0.5px;
    padding: 10px 6px;
    background-color: orange;
    color: white;
    text-transform: uppercase;
    border: 2px solid white;
    font-weight: 600;
    border-radius: 10px;
    transition : all 0.3s ease;
}

button:hover {
    background-color: white;
    color: orange;
}

.signature-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1; 
    margin-right: 750px;
    margin-top: -100px;
}

.signature-block {
    flex: 1; 
}

.input-group {
    position: relative;
    width: 100%;
    margin-bottom: 15px;
}

.input-group i {
    position: absolute;
    left: 10px;
    top: 50%;
    transform: translateY(-50%);
    color: grey;
    font-size: 18px;
    border-right: 1px solid #ccc; 
    padding-right: 10px;
    margin-top: 3px;
    margin-left:5px;
}

.input-group input, .input-group select {
    width: 100%;
    padding: 10px 10px 10px 45px; 
    border-radius: 5px;
    font-weight: 500;
    margin-left: 5px;
}

button.actif{
    background: white;
    color: #41b883;
    border: 2px solid #41b883; 
}


</style>
