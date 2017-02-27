<div align="center">
  <a href="https://github.com/beauty-enjoy/dbmeinv-firebase-ap">
    <img width="200" heigth="200" src="https://olxvlcccu.qnssl.com/blog/1b1yv.png?imageslim">
  </a>
  <h1>dbmeinv-firebase-api</h1>
  <p>
    dbmeinv-firebase-api Provides a wealth of beautiful pictures, and stored in the firebase real time database
  <p>
</div>

<h2 align="center">Introduction</h2>
>  Firebase enables easy access from [Android](https://firebase.google.com/docs/android/setup), [iOS](https://firebase.google.com/docs/ios/setup) ，[web](https://firebase.google.com/docs/web/setup), and [Servers](https://firebase.google.com/docs/server/setup) .

We divided the beauty into several categories, and will be synchronized to the server .

like `breast` `leg`  `butts` and so on ... 

If you can not wait to see the beauty so [click on here](https://github.com/beauty-enjoy/beauty) to see the effect

<h2 align="center"> API</h2>
### Direct access to JSON
open https://beauty-ad056.firebaseio.com/dbmn/data/posts/-KcqIEF8cof93PBuQZ0m.json?print=pretty
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
### Use Firebase api 

### get a posts
above example is easy to understand but not graceful ，so we can use firebase web api

```js
// this  xample for js web and node server
import firebase from 'firebase/app'
import 'firebase/database'
firebase.initializeApp({ databaseURL: 'https://beauty-ad056.firebaseio.com' })
const ref = firebase.database().ref('/dbmn').child('/data/posts') 
ref.child('-KcqIEF8cof93PBuQZ0m').once('child_added')
.then((snap) => console.log(snap.val())) // the result 

```
client document [Android](https://firebase.google.com/docs/android/setup), [iOS](https://firebase.google.com/docs/ios/setup) ，[web](https://firebase.google.com/docs/web/setup), and [Servers](https://firebase.google.com/docs/server/setup) 
## Get Keys

|  cid    |  mean  |
| ---- | ---- |
| cid0    |  all    |
| cid2    |  breast  |
| cid3    |  leg      |
| cid4    |  face      |
| cid5    |  others      |
| cid6    |  buttocks      |
| cid7    |  stockings      |


open https://beauty-ad056.firebaseio.com/dbmn/data/cid7.json?print=pretty

or use firebase web api
```js
import firebase from 'firebase/app'
import 'firebase/database'
firebase.initializeApp({ databaseURL: 'https://beauty-ad056.firebaseio.com' })
const ref = firebase.database().ref('/dbmn').child('/data/cid7') 
ref.orderByKey().limitToLast(500).once('value')
.then(snap => console.log(Object.keys(snap.val())))
// result is ["KcqIA2PdjohXejHOzDz","KcqIEEeaKTfdQl0A0Tn","KcqIEEmm7x5b6chvfmn", ...]
```
[more examples](https://github.com/beauty-enjoy/dbmeinv-firebase-api/tree/master/example)

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



