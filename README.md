# Insuline Diabetes Manager

[Article](https://gyhou.com/2019-08-30-Insuline-diabetes-manager/) on my website.

Our team deployed an app [Insuline Diabetes Manager](https://diabetesmanager.netlify.com/) to help diabetic patients track and predict blood glucose levels! [Front-End and Back-End Github](https://github.com/Build-Week-Diabetes-Manager)

![diabetes-manager-homepage](/img/diabetes-manager.png)

Using [Michael Kahn, MD, Ph.D.'s dataset](https://archive.ics.uci.edu/ml/datasets/diabetes), our data science team and I trained a model to predict the user's future blood glucose level base on insulin intake, previous blood glucose measurements and the time it was measured.

Our API(http://diabetes-manager-app.herokuapp.com) takes in a json string inside a list of measurements, minimum of 3 days worth of measurements around breakfast, lunch and dinner. After sending the input to our API, it will respond with measurements predicting the next day's blood glucose level before and after each meal.

The input codes represents the following:
```
33 = Regular insulin dose
34 = NPH insulin dose
35 = UltraLente insulin dose
58 = Pre-breakfast blood glucose measurement
59 = Post-breakfast blood glucose measurement
60 = Pre-lunch blood glucose measurement
61 = Post-lunch blood glucose measurement
62 = Pre-supper blood glucose measurement
63 = Post-supper blood glucose measurement
```

Example input:
```python
val = [{"id": 1,
        "timestamp": "2018-10-10 7:10",
        "code": 33,
        "value": 10.0,
        "user_id": 1},
       {"id": 2,
        "timestamp": "2018-10-10 9:10",
        "code": 59,
        "value": 100.0,
        "user_id": 1},
       {"id": 3,
        "timestamp": "2018-10-10 11:10",
        "code": 60,
        "value": 180.0,
        "user_id": 1},
       {"id": 4,
        "timestamp": "2018-10-10 19:10",
        "code": 63,
        "value": 250.0,
        "user_id": 1},
       {"id": 5,
        "timestamp": "2018-10-10 22:10",
        "code": 57,
        "value": 300.0,
        "user_id": 1},
       {"id": 6,
        "timestamp": "2018-10-11 9:10",
        "code": 33,
        "value": 5.0,
        "user_id": 1},
       {"id": 7,
        "timestamp": "2018-10-11 10:10",
        "code": 59,
        "value": 150.0,
        "user_id": 1},
       {"id": 8,
        "timestamp": "2018-10-11 13:10",
        "code": 60,
        "value": 200.0,
        "user_id": 1},
       {"id": 9,
        "timestamp": "2018-10-11 18:10",
        "code": 63,
        "value": 100.0,
        "user_id": 1},
       {"id": 10,
        "timestamp": "2018-10-11 00:10",
        "code": 57,
        "value": 180.0,
        "user_id": 1},
       {"id": 11,
        "timestamp": "2018-10-12 8:10",
        "code": 33,
        "value": 7.0,
        "user_id": 1},
       {"id": 12,
        "timestamp": "2018-10-12 8:10",
        "code": 59,
        "value": 90.0,
        "user_id": 1},
       {"id": 13,
        "timestamp": "2018-10-12 12:10",
        "code": 60,
        "value": 130.0,
        "user_id": 1},
       {"id": 14,
        "timestamp": "2018-10-12 20:10",
        "code": 63,
        "value": 150.0,
        "user_id": 1},
       {"id": 15,
        "timestamp": "2018-10-12 23:10",
        "code": 57,
        "value": 200.0,
        "user_id": 1}]
```
        
Example Output:
```python
{'Pre-breakfast measurement': 185.87, 'Post-breakfast measurement': 168.67, 
 'Pre-lunch measurement':     119.76, 'Post-lunch measurement':     201.92, 
 'Pre-supper measurement':    122.47, 'Post-supper measurement':    138.75}
```
