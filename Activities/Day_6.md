### **Day 6: Advanced Features and Third-Party Libraries**

**Objective**: Gain familiarity with advanced Vue.js features and commonly used libraries.

---

#### **Activities**

1. **Explore Form Validation with VeeValidate**

   - Install VeeValidate and Yup:

     ```bash
     npm install vee-validate yup
     ```

   - Validate a simple form:

     ```vue
     <template>
       <form @submit.prevent="submitForm">
         <div>
           <label for="name">Name:</label>
           <input v-model="name" type="text" id="name" />
           <span>{{ errors.name }}</span>
         </div>
         <button type="submit">Submit</button>
       </form>
     </template>

     <script setup>
     import { defineRule, useForm, useField } from "vee-validate";
     import * as yup from "yup";

     defineRule("required", (value) => !!value || "This field is required");

     const { handleSubmit } = useForm();
     const { value: name, errorMessage: errors } = useField("name", "required");

     const submitForm = handleSubmit(() => {
       alert(`Form submitted with name: ${name.value}`);
     });
     </script>
     ```

   - Enhance the form with schema-based validation using Yup.

---

2.  **Explore Component Libraries**

    - Choose a library like **Vuetify** or **Element Plus**:

      ```bash
      npm install vuetify
      ```

    - Set up Vuetify in your project and create a sample UI:

           ```vue
           <template>
             <v-app>
               <v-container>
                 <v-btn color="primary">Click Me</v-btn>
               </v-container>
             </v-app>
           </template>

           <script setup>

      // Ensure Vuetify is properly initialized (refer to the library's latest setup guide)
      </script>

      ```

      ```

    - Experiment with buttons, modals, and grids to create an appealing UI.

---

3. **Work with Vue's Built-in Transitions and Animations**

   - Add basic transitions:

     ```vue
     <template>
       <button @click="show = !show">Toggle</button>
       <transition name="fade">
         <p v-if="show">Hello, Vue.js transitions!</p>
       </transition>
     </template>

     <script setup>
     import { ref } from "vue";

     const show = ref(true);
     </script>

     <style>
     .fade-enter-active,
     .fade-leave-active {
       transition: opacity 0.5s;
     }
     .fade-enter-from,
     .fade-leave-to {
       opacity: 0;
     }
     </style>
     ```

   - Practice custom animations using `@keyframes` or CSS libraries like Animate.css.

---

4. **Integrate Third-Party Libraries**

   - Experiment with libraries like Axios for HTTP requests:

     ```bash
     npm install axios
     ```

     Example: Fetch data and display a list.

     ```vue
     <template>
       <div>
         <ul>
           <li v-for="item in items" :key="item.id">{{ item.name }}</li>
         </ul>
       </div>
     </template>

     <script setup>
     import { ref, onMounted } from "vue";
     import axios from "axios";

     const items = ref([]);

     onMounted(async () => {
       const response = await axios.get("https://api.example.com/items");
       items.value = response.data;
     });
     </script>
     ```

---

5. **Optional Challenge: Enhance an Existing App**
   - Take an app from earlier days (e.g., Blog App or Shopping Cart) and:
     - Add form validation with VeeValidate.
     - Enhance the UI with Vuetify or Element Plus.
     - Implement transitions for a smooth user experience.

---

#### **Estimated Time**: 3–4 hours
