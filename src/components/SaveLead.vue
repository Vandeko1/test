<template>
    <div class="wrapper">
        <div class="layer">
            <h1>Add new lead</h1>
            <div>
                <form @submit="handleSubmit($event)">
                    <label for="name-form">Enter your name</label>
                    <span>
                        <input id="name-form" type="text" v-model="fields.name.value" @change="handleInput($event.target.value, 'name')" placeholder="https://goo.gl/maps/id" />
                        <div class="input-notice" v-if="fields.name.errorMessage">
                            {{ fields.name.errorMessage }}
                        </div>
                    </span>
                    <label for="email-form">Email</label>
                    <span>
                        <input id="email-form" type="email" v-model="fields.email.value" @change="handleInput($event.target.value, 'email')" />
                        <button class="add-btn" @click="addMail($event)">
                            <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M13 8H8V13C8 13.55 7.55 14 7 14C6.45 14 6 13.55 6 13V8H1C0.45 8 0 7.55 0 7C0 6.45 0.45 6 1 6H6V1C6 0.45 6.45 0 7 0C7.55 0 8 0.45 8 1V6H13C13.55 6 14 6.45 14 7C14 7.55 13.55 8 13 8Z" fill="white" />
                            </svg>

                            Add</button>
                        <div class="input-notice" v-if="fields.email.errorMessage">
                            {{ fields.email.errorMessage }}
                        </div>
                    </span>
                    <div class="tags" v-for="(email, index) in fields.email.mails" :key="index">
                        <div class="tag">
                            <span>{{ email }}</span>
                            <svg @click="removeEmail(index)" width="9" height="9" viewBox="0 0 9 9" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M7.11599 8.59101L4.26699 5.832L1.418 8.59101C1.105 8.89501 0.592003 8.89501 0.279003 8.59101C-0.0349972 8.28801 -0.0349972 7.79101 0.279003 7.48801L3.128 4.728L0.279003 1.96799C-0.0349972 1.66399 -0.0349972 1.16702 0.279003 0.864017C0.592003 0.560017 1.105 0.560017 1.418 0.864017L4.26699 3.624L7.11599 0.864017C7.42899 0.560017 7.94199 0.560017 8.25599 0.864017C8.56899 1.16702 8.56899 1.66399 8.25599 1.96799L5.40699 4.728L8.25599 7.48801C8.56899 7.79101 8.56899 8.28801 8.25599 8.59101C7.94199 8.89501 7.42899 8.89501 7.11599 8.59101Z" fill="#ABB5C3" />
                            </svg>
                        </div>
                    </div>
                    <label for="phone-form">Phone</label>
                    <span>
                        <input id="phone-form" type="tel" v-model="fields.phone.value" @change="handleInput($event.target.value, 'phone')" />
                        <button class="add-btn" @click="addPhone($event)">
                            <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M13 8H8V13C8 13.55 7.55 14 7 14C6.45 14 6 13.55 6 13V8H1C0.45 8 0 7.55 0 7C0 6.45 0.45 6 1 6H6V1C6 0.45 6.45 0 7 0C7.55 0 8 0.45 8 1V6H13C13.55 6 14 6.45 14 7C14 7.55 13.55 8 13 8Z" fill="white" />
                            </svg>
                            Add</button>
                    </span>
                    <div class="tags" v-for="(phone, index) in fields.phone.phones" :key="index">
                        <div class="tag">
                            <span>{{ phone }}</span>
                            <svg @click="removePhone(index)" width="9" height="9" viewBox="0 0 9 9" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M7.11599 8.59101L4.26699 5.832L1.418 8.59101C1.105 8.89501 0.592003 8.89501 0.279003 8.59101C-0.0349972 8.28801 -0.0349972 7.79101 0.279003 7.48801L3.128 4.728L0.279003 1.96799C-0.0349972 1.66399 -0.0349972 1.16702 0.279003 0.864017C0.592003 0.560017 1.105 0.560017 1.418 0.864017L4.26699 3.624L7.11599 0.864017C7.42899 0.560017 7.94199 0.560017 8.25599 0.864017C8.56899 1.16702 8.56899 1.66399 8.25599 1.96799L5.40699 4.728L8.25599 7.48801C8.56899 7.79101 8.56899 8.28801 8.25599 8.59101C7.94199 8.89501 7.42899 8.89501 7.11599 8.59101Z" fill="#ABB5C3" />
                            </svg>
                        </div>
                    </div>
                    <label for="manager-form">Manager</label>
                    <input type="text" id="manager-form" value="m1">
                    <label for="status-form">Status</label>
                    <input type="text" id="status-form" value="Lead">
                    <label for="comment-form">Comment</label>
                    <textarea name="comment-form" id="comment-form" cols="30" rows="10" placeholder="Text"></textarea>
                    <button type="submit" class="submit" :disabled="isError">Save Lead</button>

                </form>
            </div>
        </div>
        <div class="layer2">
           <form>
                    <label for="email">Email</label>
                    <input id="email" type="text" placeholder="Your email" />
                    <label for="email">Email</label>
                    <input id="email" class="error" type="text" placeholder="Your email" />
            <button class="default" @click.stop.prevent="">Login</button>
            <span>
               <button class="outline" @click.stop.prevent="">
                <svg width="10" height="13" viewBox="0 0 10 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 13H10V11.471H0V13ZM10 4.5887H7.1419V0H2.8566V4.5887H0L5 9.9427L10 4.5887Z" fill="#00D395" />
                </svg> Download Report</button>

            <button class="flat" @click.stop.prevent="">

                <svg width="10" height="13" viewBox="0 0 10 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 13H10V11.471H0V13ZM10 4.5887H7.1419V0H2.8566V4.5887H0L5 9.9427L10 4.5887Z" fill="#00D395" />
                </svg> Download Report</button>
            </span>
            <span>
            <button class="outline btn-opacity-bg" @click.stop.prevent="">
                <svg width="10" height="13" viewBox="0 0 10 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 13H10V11.471H0V13ZM10 4.5887H7.1419V0H2.8566V4.5887H0L5 9.9427L10 4.5887Z" fill="#00D395" />
                </svg> Download Report</button>
            <button class="flat btn-opacity-bg" @click.stop.prevent="">

                <svg width="10" height="13" viewBox="0 0 10 13" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 13H10V11.471H0V13ZM10 4.5887H7.1419V0H2.8566V4.5887H0L5 9.9427L10 4.5887Z" fill="#00D395" />
                </svg> Download Report</button>
            </span>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "SaveLead",
        data() {
            return {
                fields: {
                      name: {
                          title: "Username",
                          format: "а-я, А-Я",
                          regexp: /^[a-zA-Z\ ]+$/,
                          value: "",
                          required: true,
                          maxLength: 50,
                          errorMessage: ""
                      },
                      email: {
                          title: "Email",
                          format: "name@domain.com", 
                          regexp: /^([a-z\d\.-]+)@([a-z\d-]+)\.([a-z]{2,8})(\.[a-z]{2,8})?$/,
                          value: "",
                          required: true,
                          maxLength: 99,
                          errorMessage: "",
                          mails: []
                      },
                      phone: {
                          title: "Telephone",
                          format: "+380000000000", 
                          regexp: /\(?([0-9]{3})\)?([ .-]?)([0-9]{3})\2([0-9]{4})/,
                          value: "",
                          required: false,
                          maxLength: 99,
                          errorMessage: "",
                          phones: ["+380500000000","380500000000"]
                    }
                }
            }
        },
        computed: {
            isError: function() {
                return Boolean((this.fields.email.errorMessage || this.fields.name.errorMessage) || 
                               (this.fields.name.value === '' || this.fields.email.value === ''))
            }
        },
        methods: {
            handleSubmit(e) {
                e.preventDefault();                
                const inputs = Array.from(document.querySelectorAll('input')).map(inputElement => inputElement.value)
                console.table(inputs);
            },
            handleInput(value, field) {
                const {title, format, regexp, required, maxLength}  = this.fields[field];
                const valid = regexp.test(value);
                if (valid) {
                    if (maxLength && (value.length > maxLength)) {
                        this.fields[field].errorMessage = `In field "${title}" permissible no more  ${maxLength} characters`;
                        event.target.classList.add("error");
                    } else if (required && !Boolean(value.length)) {
                        this.fields[field].errorMessage = `Field "${title}" mandatory`;
                        event.target.classList.add("error");
                    } else {
                        this.fields[field].errorMessage = "";
                        event.target.classList.remove("error");
                        return true;
                    }
                } else {
                    this.fields[field].errorMessage = `"${title}" must be in the format "${format}" `;
                    event.target.classList.add("error");
                }
            },
            addMail(e){
                e.preventDefault();
                let value = this.fields.email.value;
                if (this.handleInput(value, 'email')) {
                    this.fields.email.mails.push(value)
                    document.querySelector('#email-form').classList.remove("error");
                } else {
                    document.querySelector('#email-form').classList.add("error");
                }
            },
            addPhone(e){
                e.preventDefault();
                let value = this.fields.phone.value;
                if (this.handleInput(value, 'phone')) {
                    this.fields.phone.phones.push(value)
                    document.querySelector('#phone-form').classList.remove("error");
                } else {
                    document.querySelector('#phone-form').classList.add("error");
                }
            },
            removePhone(index) {
                this.fields.phone.phones.splice(index, 1);
            },
            removeEmail(index) {
                this.fields.email.mails.splice(index, 1);
            }
        }
    }
</script>