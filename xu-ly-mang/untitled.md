---
description: >-
  Pluck javascript là một khái niệm được sử dụng khi chúng ta cần trích xuất dữ
  liệu của một thuộc tính trong một danh sách cho trước.
---

# Pluck Javascript

## Cách 1: Sử dụng from\(\) và map\(\)

```javascript
var goal = [
                {
                "category":"other",
                "title":"harry University",
                "value": 50000,
                "id":1
                },
                {
                "category":"traveling",
                "title":"tommy University",
                "value": 50000,
                "id":2
                },
                {
                "category":"education",
                "title":"jerry University",
                "value": 50000,
                "id":3
                },
                {
                "category":"business",
                "title":"Charlie University",
                "value": 50000,
                "id":4
                }
           ]
const pluck = key => array => Array.from(new Set(array.map(obj => obj[key])))
const getCategorys = pluck('category')
console.log(getCategorys(goal))
```

```javascript
Kết quả:
["other", "traveling", "education", "business"]
```

## Cách 2: Chỉ sử dụng map\(\)

```javascript
let result = goal.map(a => a.category);

or

let result = goal.map(({category}) => category);
```

```javascript
Kết quả:
["other", "traveling", "education", "business"]
```

## Cách 3: Dùng for..in

```javascript
function pluck(obj, name){
    var sol = [];
    for(var i in obj){
        if(obj[i].hasOwnProperty(name)){
            sol.push(obj[i][name]);
        }
    }
    return sol;
}
console.log(pluck(goal, 'category'));
```

```javascript
Kết quả:
["other", "traveling", "education", "business"]
```

## Cách 4: Reduce

```javascript
const pluck = (key, array) =>
    array.reduce((values, current) => {
        values.push(current[key]);
        return values;
    },[]);
console.log(pluck('category', goal));  
```

```javascript
Kết quả:
["other", "traveling", "education", "business"]
```

## Cách 5: Dùng thư viện như lodash hoặc Underscorejs \| pluck\(\)

```javascript
console.log(_.pluck(goal,'category'));
```

## Cách 6: Sử dụng Datatable JS

```javascript
var table = $('#example').DataTable({
	"data": [
	{
		"name": "Tiger Nixon",
		"hr":{
			"position":"System Architect",
			"salary":"$320800",
			"start_date":"2020/01/30"
		}
	},
	{
		"name":"Garrett Winters",
		"hr":{
			"position":"Accountant",
			"salary":"$170750",
			"start_date":"2020/02/09"
		}
	},
	{
		"name":"Ashton Cox",
		"hr":{
			"position":"Junior Technical Author",
			"salary":"$86000",
			"start_date":"2020/05/20"
		}
	}
	],
	"columns":[
		{
			"data":"name"
		},
		{
			"data":"hr.position"
		}
	]
});

var saleries = table
			   .rows()
			   .data()
			   .pluck('hr')
			   .pluck('salary');
```

