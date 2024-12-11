### **Day 4: State Management (Pinia)**

**Objective**: Manage application state efficiently.

---

#### **Activities**

1. **Understand the Need for State Management**

   - Learn why state management is important in complex apps:
     - Sharing data across components.
     - Managing global state like user authentication, shopping cart, etc.
     - Avoiding "prop drilling" (passing data through many nested components).
   - Read about state management patterns in Vue.js.

---

2. **Install and Set Up Pinia (Recommended State Management Library)**

   - Install Pinia:

     ```bash
     npm install pinia
     ```

   - Add Pinia to your Vue project:

     ```javascript
     import { createApp } from "vue";
     import { createPinia } from "pinia";
     import App from "./App.vue";

     const app = createApp(App);
     app.use(createPinia());
     app.mount("#app");
     ```

---

3. **Create a Global Store**

   - Define a store (e.g., `src/stores/cart.js`):

     ```javascript
     import { defineStore } from "pinia";

     export const useCartStore = defineStore("cart", {
       state: () => ({
         items: [],
       }),
       getters: {
         totalPrice: (state) =>
           state.items.reduce((sum, item) => sum + parseFloat(item.price), 0),
       },
       actions: {
         addItem(item) {
           this.items.push(item);
         },
         removeItem(index) {
           this.items.splice(index, 1);
         },
       },
     });
     ```

   - Use the store in a component:

     ```javascript
     import { useCartStore } from "@/stores/cart";

     export default {
       setup() {
         const cartStore = useCartStore();
         return { cartStore };
       },
     };
     ```

---

4. **Implement State Management in a Shopping Cart Feature**

   - Add functionality for:
     - Adding items to the cart.
     - Removing items from the cart.
     - Displaying the total price.
   - Example UI:

     ```html
     <template>
       <div>
         <h1>Shopping Cart</h1>
         <ul>
           <li v-for="(item, index) in cartStore.items" :key="index">
             {{ item.name }} - ${{ item.price }}
             <button @click="cartStore.removeItem(index)">Remove</button>
           </li>
         </ul>
         <button @click="addToCart">Add Random Item</button>
         <p>Total: ${{ cartStore.totalPrice }}</p>
       </div>
     </template>

     <script>
       import { useCartStore } from "@/stores/cart";

       export default {
         setup() {
           const cartStore = useCartStore();

           const addToCart = () => {
             const randomItem = {
               name: "Item " + Math.random(),
               price: (Math.random() * 100).toFixed(2),
             };
             cartStore.addItem(randomItem);
           };

           return {
             cartStore,
             addToCart,
           };
         },
       };
     </script>
     ```

---

5. **Optional Challenge**

   - Add Vue Router guards to ensure the cart is saved before navigation.
   - Implement persistent state storage using `localStorage` or `sessionStorage`.

---

#### **Estimated Time**: 3–4 hours
