# Format Money

```javascript
const money = num => num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")
console.log(money(120000))
```

```javascript
Kết quả:
120,000
```



