<div align="center">
  <a href="https://github.com/beauty-enjoy/dbmeinv-firebase-ap">
    <img width="200" heigth="200" src="https://olxvlcccu.qnssl.com/blog/1b1yv.png?imageslim">
  </a>
  <h1>dbmeinv-firebase-api</h1>
  <p>
    dbmeinv-firebase-api Provides a wealth of beautiful pictures (about 90K ) stored in the firebase real time database
  <p>
</div>

<h2 align="center">Introduction</h2>

I crawl data every day from [dbmeinv.com](http://dbmeinv.com) and store in firebase .  
this repo is to show you how to get beauty data from my firebase database . 
If you can't wait to see the beauty , [Click on here](https://github.com/beauty-enjoy/beauty) to see the effect !!

<h2 align="center"> API</h2>

> you could read [more examples](https://github.com/beauty-enjoy/dbmeinv-firebase-api/tree/master/examples) directly

### Direct access to JSON

restful : https://beauty-ad056.firebaseio.com/dbmn/data/posts/-KcqIEF8cof93PBuQZ0m.json?print=pretty
```json
{
  "authorname" : "泽尻笼儿",
  "avatar" : "https://img3.doubanio.com/icon/up96969241-20.jpg",
  "cid" : 6,
  "content" : "我不管我最可爱，我不管，我是小公主，要举高高要抱抱",
  "date" : 1481595825000,
  "id" : "1060224",
  "imageUrl" : "http://ww4.sinaimg.cn/bmiddle/0060lm7Tgw1fawbhcv5nwj30dw0iijtg.jpg",
  "images" : [ "http://ww4.sinaimg.cn/large/0060lm7Tgw1fawbhcv5nwj30dw0iijtg.jpg", "http://ww2.sinaimg.cn/large/0060lm7Tgw1fawbhcjxpwj30dw0iidhx.jpg", "http://ww3.sinaimg.cn/large/0060lm7Tgw1fawbhc86hwj30dw0iitaw.jpg", "http://ww3.sinaimg.cn/large/0060lm7Tgw1fawbhbwb2ij30dw0iiac5.jpg", "http://ww2.sinaimg.cn/large/0060lm7Tgw1fawbhb3y1yj30dw0iimz8.jpg", "http://ww2.sinaimg.cn/large/0060lm7Tgw1fawbhani8lj30dw0iiq50.jpg", "http://ww1.sinaimg.cn/large/0060lm7Tgw1fawbha5r7ej30dw0iiwgj.jpg", "http://ww1.sinaimg.cn/large/0060lm7Tgw1fawbh9ql1pj30dw0iidi1.jpg", "http://ww4.sinaimg.cn/large/0060lm7Tgw1fawbh99jcvj30dw0iitav.jpg", "http://ww2.sinaimg.cn/large/0060lm7Tgw1fawbh8w7gaj30dw0iigo3.jpg", "http://ww4.sinaimg.cn/large/0060lm7Tgw1fawbh8k5m3j30dw0iiju7.jpg" ],
  "location" : "常居: 北京",
  "title" : "【晒】喜欢的请夸我，不喜欢的请抠眼珠子哈哈哈哈"
}
```
### Use Firebase sdk


> js web sdk examples


```html
  
 <body>
    <script src="https://www.gstatic.com/firebasejs/3.4.0/firebase.js"></script>
    <script>
    firebase.initializeApp({ // init firebase App
        databaseURL: 'https://beauty-ad056.firebaseio.com',
    });             
    var dataRef = firebase.database().ref('dbmn/data')
    var cid = 'cid2'
    dataRef.child(cid) // cid* look at https://github.com/beauty-enjoy/dbmeinv-firebase-api#get-keys           
    .orderByKey()
    .limitToLast(2)
    .once('value')
    .then(function(snap){ return Object.keys(snap.val())}) // 2. get newest boob'posts keys
    .then(function(keys){               
        return Promise.all(keys.map(function(key){ // 3. get posts by keys                    
            return dataRef.child('posts').orderByKey().equalTo(key).once('child_added')
            .then(function(snap){ return snap.val() })
        }))
    })
    .then(function(result){
        // all result here
        console.log('all the posts which cid is : [%s] \n',cid,result)
    })
    
    </script>
 </body>

```

client document [Android](https://firebase.google.com/docs/android/setup), [iOS](https://firebase.google.com/docs/ios/setup) ，[web](https://firebase.google.com/docs/web/setup), and [Servers](https://firebase.google.com/docs/server/setup) 

###  Keys means

|  cid    |  mean  |
| ---- | ---- |
| cid2    |  breast  |
| cid3    |  leg      |
| cid4    |  face      |
| cid5    |  others      |
| cid6    |  buttocks      |
| cid7    |  stockings      |


<h2 align="center">Related Projects</h2>

> we will add a `Related Projects` for your repo which useing `dbmeinv-firebase-api`

- [x] [Vue](https://github.com/vuejs/vuex) Version : [Beauty](https://github.com/beauty-enjoy/beauty)
- [ ] [Weex](https://github.com/alibaba/weex) Version App
- [ ] [React Native](https://facebook.github.io/react-native/) Version App
- [ ] iOS Native Version App
- [ ] Android Native Version App


<h2 align="center">Core Team</h2>
<table>
  <tbody>
    <tr>
      <td align="center" valign="top">
        <img width="150" height="150" src="https://github.com/netpi.png?s=150">
        <br>
        <a href="https://github.com/netpi">Netpi Chen</a>
        <p>beauty spider</p>
        <br>
        <p>Founder for this repo</p>
      </td>      
     </tr>
  </tbody>
</table>



