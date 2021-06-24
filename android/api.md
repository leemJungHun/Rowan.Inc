# 슈퍼브레인 API
## 메인 주소 : https://api.super-brain.co.kr/

### API
 
 
```로그인을 제외하면 항상 헤더에 로그인 때 받은 토큰을 담아보낸다.```   
```
 user/check/login
body:  
{
    "id":"admin3",  
    "password":"123"
 }
 ```
  ```
 user/reissue/token 
 헤더에 재발급 토큰만 담아보냄
 ```   
 ```
 learning/get/contents/{unique}
 unique = 과제 uuid
 ```
 ```
 video/get/path/{unique}
 unique = 영상 uuid 
 ```
 ```
 learning/put/history 
body:  
{  
   "assignment":"55448ce3aebc4b628798a69b7bf2a736",  
   "learning":"88fe59d8fb274488b312fee139ae7208",   
   "type":"INFORMATION",  
   "order":1,   
   "success":0,  
   "total":0, 
   "score":0,  
   "duration":100
}
```  
```
 learning/get/endpoint
body:  
{
  "assignment":"c8cdc455f66d40b694d1393286278147", 
  "learning":"f7ed399295404834876c125bc9724ed7"
} 
```
```
 assignment/get/list 
 헤더에 토큰 담아서 보냄 
 ```
 ```
 video/get/endpoint 
body:  
 {  
   "assignment": "85e5ff4bc80e4bfd86ff4e04e3fae168",    
   "video": "b9ddecb19948469a8597d253b65d41d4"
 }
 ```
 ```
 video/put/endpoint
body:  
{
  "assignment": "85e5ff4bc80e4bfd86ff4e04e3fae168", 
  "video": "b9ddecb19948469a8597d253b65d41d4", 
  "duration":5000,
  "end":5000
}
```
```
 survey/get/contents/{unique}
 unique = 과제 uuid
```
```
 survey/put/history 
body:  
 {
    "assignment": "418dbb559cee49deb7092fb38775f71e",
    "survey": "517d428a217b405b9b7538d42d4f7ca7",
    "records": {
        "3f195b67aefb43dc98e0954a5ac622a9": [
            {
                "order": 1,
                "score": 3,
                "div": 4,
                "weight": 13.5,
                "select": 5,
                "etc": null
            },
            {
                "order": 2,
                "score": 3,
                "div": 4,
                "weight": 14.7,
                "select": 5,
                "etc": null
            },
            {
                "order": 3,
                "score": 3,
                "div": 4,
                "weight": 25.8,
                "select": 5,
                "etc": null
            },
            {
                "order": 4,
                "score": 3,
                "div": 4,
                "weight": 19.8,
                "select": 5,
                "etc": null
            },
            {
                "order": 5,
                "score": 1,
                "div": 2,
                "weight": 5.3,
                "select": 5,
                "etc": null
            },
            {
                "order": 6,
                "score": 1,
                "div": 5,
                "weight": 20.9,
                "select": 5,
                "etc": null
            }
        ],
        "d16d583943cb4c099b0f49d8cddbe721": [
            {
                "order": 1,
                "score": 5,
                "div": 4,
                "weight": 14,
                "select": 5,
                "etc": null
            },
            {
                "order": 2,
                "score": 5,
                "div": 4,
                "weight": 22.7,
                "select": 5,
                "etc": null
            },
            {
                "order": 3,
                "score": 5,
                "div": 4,
                "weight": 9.9,
                "select": 2,
                "etc": "현재 음식을 섭취하기 전 손 씻기를 잘 실천하고 있습니다. 현재와 같이 좋은 습관을 꾸준히 유지하십시오."
            },
            {
                "order": 4,
                "score": 5,
                "div": 4,
                "weight": 12.2,
                "select": 5,
                "etc": "현재 좋은 운동습관을 유지하고 있습니다. 앞으로도 현재와 같이 꾸준하게 운동을 하십시오."
            },
            {
                "order": 5,
                "score": 5,
                "div": 4,
                "weight": 21.2,
                "select": 5,
                "etc": null
            },
            {
                "order": 6,
                "score": 5,
                "div": 4,
                "weight": 20,
                "select": 5,
                "etc": null
            }
        ],
        "3817853f6fa4469997b33d50367cd478": [
            {
                "order": 1,
                "score": 3,
                "div": 4,
                "weight": 43.2,
                "select": 5,
                "etc": null
            },
            {
                "order": 2,
                "score": 3,
                "div": 4,
                "weight": 29.5,
                "select": 5,
                "etc": null
            },
            {
                "order": 3,
                "score": 3,
                "div": 4,
                "weight": 8.4,
                "select": 5,
                "etc": null
            },
            {
                "order": 4,
                "score": 3,
                "div": 3,
                "weight": 18.9,
                "select": 5,
                "etc": null
            }
        ],
        "3f913a364f0d4ebf8807e34df65c1475": [
            {
                "order": 1,
                "score": 3,
                "div": 5,
                "weight": 34.5,
                "select": 5,
                "etc": null
            },
            {
                "order": 2,
                "score": 3,
                "div": 4,
                "weight": 33.9,
                "select": 5,
                "etc": null
            },
            {
                "order": 3,
                "score": 5,
                "div": 4,
                "weight": 31.6,
                "select": 5,
                "etc": null
            }
        ]
    }
}
```
```
 assignment/put/medal
 body :
 {
    "assignment": "b48741b7aba0408698999178c92167b6",
    "medal":"GOLD"
 }
```
```
 game/get/setting
 body :
 {
    "assignment":"85e5ff4bc80e4bfd86ff4e04e3fae168",
    "game":"2d5801e7966d4d538bbbf8db3a6f250d"
}
```
```
 game/put/history
 body :
 {
    "assignment":"85e5ff4bc80e4bfd86ff4e04e3fae168",
    "game":"2d5801e7966d4d538bbbf8db3a6f250d",
    "records":[
        {"correct": 0, "speed": 8.5},{"correct": 1, "speed": 1.5},{"correct": 1, "speed": 2.5},{"correct": 1, "speed": 3.5},{"correct": 0, "speed": 4.5}
    ],
    "level": 1,
    "limit": 180,
    "score": 200.0
}
 ```
 ```
 assignment/check/support 
 body :
 { 
   "assignment":"b48741b7aba0408698999178c92167b6"
 } 
 ```
 ```
 learning/get/result 
 body :
 {
    "assignment":"85e5ff4bc80e4bfd86ff4e04e3fae168",
    "learning":"2c32cf1c1cd04bf98b422fe980b6aac9"
 }
 ```
 ```
 stat/assignment 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/statistics 
 body :
 {
    "sections":["COGNITION"]
 }
 ```
 ```
 stat/blood/weight 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/blood/waist 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/blood/sugar 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/blood/pressure 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/blood/smoke 
 헤더에 토큰 담아서 보냄
 ```
 ```
 stat/blood/drink
 헤더에 토큰 담아서 보냄
 ```
