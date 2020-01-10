# Format Money

## Cách 1:

```javascript
const money = num => num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
console.log(money(120000));
```

```javascript
Kết quả:
120,000
```

## Cách 2:

```javascript
console.log(new Intl.NumberFormat('vn-VN').format(1000000));
```

```javascript
Kết quả:
1,000,000
```



