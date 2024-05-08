<details>
  <summary> index.js </summary></summary>
  
```javascript
  
  import { toppings, renderToppings, toggleTopping } from "./hotdog.js"
  import "./index.css"
  
  document.addEventListener("DOMContentLoaded", () => {
      const rootElement = document.querySelector("#root");
      rootElement.appendChild(renderToppings());
  });

</details>
```
<details>
  <summary> hotdog.js </summary></summary>
  
```javascript
  
export const toppings = [
    { name: 'Hořčice', price: 5, selected: false },
    { name: 'Kečup', price: 5, selected: false },
    { name: 'Cibule', price: 5, selected: false },
    { name: 'Okurka', price: 5, selected: false },
    { name: 'Paprika', price: 5, selected: false },
    { name: 'Rajče', price: 5, selected: false },
    { name: 'Chilli', price: 5, selected: false },
    { name: 'Sýr', price: 10, selected: false },
    { name: 'Slanina', price: 10, selected: false },
  ];

export const toggleTopping = (index)=>{
    if (toppings[index].selected){
        toppings[index].selected = false;
    }else{
        toppings[index].selected = true;
    }
}

export const renderToppings = () => {
    const rootElement = document.querySelector("#root");
    const prilohovyWrapper = document.createElement("div");
    prilohovyWrapper.classList.add("prilohy-wrapper");
    toppings.forEach(element => {
        let div = document.createElement("div");
        div.classList.add("topping");
        if (element.selected){
            div.classList.add("topping--selected");
        }
        let h3 = document.createElement("h3");
        h3.innerText = element.name;
        let p = document.createElement("p");
        p.innerText = element.price;
        div.appendChild(h3);
        div.appendChild(p);
        prilohovyWrapper.appendChild(div);
        div.addEventListener("click", (event)=>{
            rootElement.innerHTML = "";
            prilohovyWrapper.innerHTML = "";
            let index = toppings.indexOf(element);
            toggleTopping(index);
            rootElement.appendChild(renderToppings())
        })
    });
    return prilohovyWrapper;
}

```
<details>
  <summary> index.html </summary></summary>
  
  ```html
    
     <!DOCTYPE html>
    <html lang="cs">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        <h1>Výběr příloh k hotdogům</h1>
    
        <div id="root"></div>
    
        <script src="index.js" type="module"></script>
    </body>
  </html>
  </details>
```

<details>
  <summary> index.html </summary></summary>
  
  ```index.css
    
   *{
  box-sizing: border-box;
}
body{
  background-color: #494949;
  color: white;
}
h1{
  text-align: center;
}
h1::after{
  content: "";
  display: block;
  background-color: red;
  width: 130px;
  height: 2px;
  margin: 0 auto;
}
.topping{
  display: flex;
  gap: 20px;
  align-items: center;
}

.topping--selected{
  display: flex;
  justify-content: center;
  background-color: #f1f1f1;
  color: #494949;
  width: 100%;
  margin: 10px 0px;
}
.prilohy-wrapper{
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
  </details>
```

