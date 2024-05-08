<details>
  <summary> index.html </summary></summary>
  import { toppings, renderToppings, toggleTopping } from "./hotdog.js"
  import "./index.css"
  
  document.addEventListener("DOMContentLoaded", () => {
      const rootElement = document.querySelector("#root");
      rootElement.appendChild(renderToppings());
  });

</details>