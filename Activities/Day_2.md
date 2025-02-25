### **Day 2: Components and Lifecycle Hooks**

**Objective**: Learn about components and how they interact.

#### **Activities**

1. **Understand Component-Based Architecture**

   - Read the [Vue Components Guide](https://vuejs.org/guide/essentials/component-basics.html).
   - Learn about the importance of breaking down a UI into reusable components.

2. **Create Reusable Components**

   - Build reusable components:
     - A **TaskItem** component for individual tasks.
     - A **Header** component for the app's title.
     - A **Footer** component (optional).
   - Practice passing data to components using `props`.
     Example: Pass the task title and status as props to the `TaskItem` component.

3. **Explore Slots for Flexible Components**

   - Learn about default and named slots for dynamic content in components.
     Example: Add a slot to your `Header` component to allow custom content.

4. **Lifecycle Hooks**

   - Read about lifecycle hooks in the [Lifecycle Hooks Guide](https://vuejs.org/guide/essentials/lifecycle.html).
   - Experiment with hooks like:
     - `created`: Log a message when the component is initialized.
     - `mounted`: Fetch some sample data after the component is mounted.
     - `updated`: Track changes to the `tasks` list.
     - `unmounted`: Log cleanup messages when the component is destroyed.

5. **Enhance the "To-Do List" App**

   - Refactor your Day 1 "To-Do List" app:
     - Replace inline templates with reusable components.
     - Add dynamic props and event emitters for task actions (e.g., marking a task as done or deleting a task).
   - Example structure:
     ```plaintext
     App.vue
     ├── Header.vue
     ├── TaskList.vue
     ├── TaskItem.vue
     └── Footer.vue
     ```

6. **Optional Challenge**:
   - Add a feature to categorize tasks (e.g., "Work", "Personal").
   - Use props and events to implement a category filter in your app.

#### **Estimated Time**: 3–4 hours
