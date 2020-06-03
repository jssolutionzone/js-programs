# Programs
We have a variety of programs available for you, which may help you to crack your interviews. Here, programs are written in javascript, but you can see the logic and write it in your convenient language. 

### Problem - 1
> Write a function, which accepts array of objects (object having name and price as an attribute) as string and sort them
  in ascending order as per below rules. <br>
  **Rule 1.** If all the prices are unique then, sort that array in ascending order by price.<br>
  **Rule 2.** If all the prices are not unique then, sort that array in ascending order by name.<br>

```js

function hasDuplicatePrice(list) {
    const priceArr = [];
    let hasDuplicate = false;
    list.forEach(item => {
        if (!priceArr.includes(item.price)) {
            priceArr.push(item.price);
        } else {
            hasDuplicate = true;
        }

    });
    return hasDuplicate;
}

function sortByAscending(jsonString) {
    const priceList = JSON.parse(jsonString);
    let sortedPriceList = [];
    if (Array.isArray(priceList)) {
        if (hasDuplicatePrice(priceList)) {
            sortedPriceList = priceList.sort((a, b) => {
                if (a.name < b.name) { return -1; }
                if (a.name > b.name) { return 1; }
                return 0;
            });
        } else {
            sortedPriceList = priceList.sort((a, b) => {
                const p1 = a.price, p2 = b.price;
                return p1 - p2;
            });
        }
        return JSON.stringify(sortedPriceList);
    }
    return jsonString;
}

console.log(sortByAscending('[{"name":"eggs","price":1},{"name":"coffee","price":11.4},{"name":"rice","price":4.04}]'));
console.log(sortByAscending('[{"name":"eggs","price":1},{"name":"coffee","price":4.04},{"name":"rice","price":4.04}]'));
```  
