### Knowledge Check Answers 🎯

***

**Question: What problems can prop drilling cause?**

**Answer:** Prop drilling causes code clutter, makes maintenance difficult, and forces components to receive data they don't actually need just to pass it along.

**Why:** When you pass props through five layers of components just to reach the sixth, every component in that chain becomes "coupled" to that data. If you move a component or change the data structure, you have to update the entire chain.



**Remember:** It's like a **bucket brigade** 🪣; everyone has to touch the bucket, even if only the last person needs the water.

***

**Question: How can we avoid problems with prop drilling?**

**Answer:** We can avoid it by using **Component Composition** (passing components as children) or by using the **Context API**.

**Why:** Composition lets you keep state in the parent and just pass the result down. The Context API lets you "teleport" data past the intermediate components directly to the child that needs it.

***

**Question: What are the benefits of using the Context API over passing props down through multiple levels of components?**

**Answer:** The main benefit is that it allows you to share "global" data (like user auth, themes, or language settings) directly with any component in the tree, regardless of how deep it is.

**Why:** It eliminates the need for intermediate components to handle props they don't use, resulting in cleaner, less repetitive code that is easier to read.

**Remember:** Context acts like a **radio broadcast** 📡; anyone tuned in (consuming the context) gets the message instantly.

***

**Question: What are the drawbacks in using the Context API?**

**Answer:** The main drawbacks are potential **performance issues** and **reduced component reusability**.

**Why:**
1.  **Performance:** When context updates, *every* component consuming it re-renders, which can be slow if not managed correctly.
2.  **Clarity:** It hides data dependencies. A component using `useContext` can't be easily reused in a different part of the app (or tested) without wrapping it in a specific Provider first.

**Remember:** **Great power** comes with **complexity costs**. Use it for global state, not everything.