### **Day 5: Vue 3 Composition API**

**Objective**: Learn modern Vue.js development practices.

---

#### **Activities**

1. **Understand the Basics of the Composition API**
   - Learn why the Composition API was introduced in Vue 3 (e.g., better scalability and reusability).
   - Explore the core features:
     - `ref` for reactive primitives.
     - `reactive` for reactive objects.
     - `computed` for derived state.
     - `watch` and `watchEffect` for reacting to changes.

---

2. **Practice with Reactive Variables**

   - Create a simple counter using `ref`:

     ```vue
     <template>
       <div>
         <p>Counter: {{ count }}</p>
         <button @click="increment">Increment</button>
       </div>
     </template>

     <script setup>
     import { ref } from "vue";

     const count = ref(0);

     const increment = () => {
       count.value++;
     };
     </script>
     ```

---

3. **Work with Reactive Objects**

   - Use `reactive` for more complex state:

     ```vue
     <template>
       <div>
         <p>{{ user.name }} ({{ user.age }} years old)</p>
         <button @click="updateName">Change Name</button>
       </div>
     </template>

     <script setup>
     import { reactive } from "vue";

     const user = reactive({ name: "John Doe", age: 30 });

     const updateName = () => {
       user.name = "Jane Smith";
     };
     </script>
     ```

---

4. **Explore Computed Properties**

   - Add computed properties to derive values from your state:

     ```vue
     <template>
       <div>
         <p>Full Name: {{ fullName }}</p>
       </div>
     </template>

     <script setup>
     import { reactive, computed } from "vue";

     const user = reactive({ firstName: "John", lastName: "Doe" });

     const fullName = computed(() => `${user.firstName} ${user.lastName}`);
     </script>
     ```

---

5. **Use Watchers to React to State Changes**

   - Practice with `watch` to perform side effects:

     ```vue
     <script setup>
     import { ref, watch } from "vue";

     const count = ref(0);

     watch(count, (newVal, oldVal) => {
       console.log(`Count changed from ${oldVal} to ${newVal}`);
     });

     const increment = () => {
       count.value++;
     };
     </script>
     ```

---

6. **Refactor an Existing App**
   - Refactor a project from earlier days (e.g., "To-Do List" or Shopping Cart) to use the Composition API.

---

7. **Optional Challenge**

   - Create a reusable hook (composable) for managing a timer:

     ```javascript
     import { ref, onMounted, onUnmounted } from "vue";

     export function useTimer() {
       const time = ref(0);
       let interval = null;

       const start = () => {
         interval = setInterval(() => time.value++, 1000);
       };

       const stop = () => {
         clearInterval(interval);
       };

       onMounted(start);
       onUnmounted(stop);

       return { time, start, stop };
     }
     ```

     Use it in your app:

     ```vue
     <template>
       <p>Time: {{ time }} seconds</p>
     </template>

     <script setup>
     import { useTimer } from "./useTimer";

     const { time } = useTimer();
     </script>
     ```

---

#### **Estimated Time**: 3–4 hours
