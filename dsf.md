# API Reference

## Resources

#### 1.Trainee

/archisacademy/v1/trainee

##### 1.1. Get the creation date of traineeship

​ GET /archisacademy/v1/trainee/creation_date/{id}

​ GET /archisacademy/trainee/creation_date/{unique_name}

Path parameters

| Path parameter  | Description                                                                                                             | Example          |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `{id}`          | The ID of trainee you want to look up. All IDs are available from our site at archisacademy.com.                        | 123              |
| `{unique_name}` | The unique name for the trainee you want to look up. All unique names are available from our site at archisacademy.com. | furious_einstein |

**Request Example**

```javascript
curl -X GET \https://api.archisacademy.com/v1/trainee/creation_date/{id}`
```

**Response** **Example**

Code: 200

```
{
  "results": {
    "creation_date": "06.02.2021"
  },
  "status": "OK"
}
```

##### 1.2. Delete traineeship

​ DELETE /archisacademy/v1/trainee/{id} //

​ DELETE /archisacademy/v1/trainee/{unique_name}

| Path parameter  | Description                                                                                                             | TYPE    | EXAMPLE          |     |     |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------- | ------- | ---------------- | --- | --- |
| `{id}`          | The ID of trainee you want to look up. All IDs are available from our site at archisacademy.com.                        | Integer | 123              |     |     |
| `{unique_name}` | The unique name for the trainee you want to look up. All unique names are available from our site at archisacademy.com. | String  | furious_einstein |     |     |

**Request Example**

```javascript
curl -X DELETE \https://api.archisacademy.com/v1/trainee/{unique_name}`
```

**Response Example**

Code: 200

```
{
  "results": {

  },
  "status": "OK"
}
```

##### 1.3. Get trainees' and candidates' list

​ GET /archisacademy/v1/trainee/

| Query string parameter | Required / optional | Description                                                                                                                                 | Type    |
| :--------------------- | :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------ | :------ |
| `days`                 | Optional            | The number of days to include in the response. Default is 7. It receives the candidates or trainees included in the list that days.         | Integer |
| `first`                | Optional            | If you include the first, it will give the list of the first X trainees or candidates.                                                      | Integer |
|                        |                     |                                                                                                                                             |         |
| `last`                 | Optional            | If you include the last, it will give the list of the last X trainees or candidates.                                                        | Integer |
|                        |                     |                                                                                                                                             |         |
| `training_type`        | Optional            | This parameter can take 4 different strings: "paid_by_trainee", "investible_sponsorship", "renewable_sponsorship", "donatable_sponsorship". | String  |
|                        |                     |                                                                                                                                             |         |
| `status`               | Optional            | This parameter can take 2 different strings: "trainee", "candidate".                                                                        | String  |

​

**Request Example**

```javascript
curl -X GET /https://api.archisacademy.com/v1/trainee/?days=<NUMBER_OF_DAYS>&first=<FIRST_HOW_MANY_DAYS>&training_type=<STRING_TRAINING_TYPE>
```

**Response Example**

Code: 200

```
{
  "results": {
  	"trainees_and_candidates": {
  		"status": "trainee",
  		"id": "1",
  		"unique_name": "loving_goldstine" ,
  		"creation_date": "05.02.2021",
  		"country": "Turkey",
        "training_type":"renewable_sponsorship"},

  		{
  		"status": "trainee",
  		"id": "2",
  		"unique_name": "jovial_yalow" ,
  		"creation_date": "10.01.2020",
  		"country": "Greece",
        "training_type": "paid_by_trainee"},

  		{
  		"status": "candidate",
  		"unique_name": "romantic_curie"  ,
  		"creation_date": "10.17.2020" ,
  		"country": "Greece" }

  },
  "status": "OK"
}
```

##### 1.4. Post sponsorship request form

​ POST /archisacademy/v1/form/{id}

​ POST /archisacademy/v1/form/{unique_name}

| Path parameter  | Description                                                                                                             | Type    | example          |     |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------- | ------- | ---------------- | --- |
| `{id}`          | The ID of trainee you want to look up. All IDs are available from our site at archisacademy.com.                        | Integer | 123              |     |
| `{unique_name}` | The unique name for the trainee you want to look up. All unique names are available from our site at archisacademy.com. | String  | furious_einstein |     |

| query parameter | Opt./req. | Description                                                          | Type    | example            |     |
| :-------------- | --------- | :------------------------------------------------------------------- | ------- | ------------------ | --- |
| `{country}`     | Required  | The country of the trainee you want to put in the form.              | String  | Turkey             |     |
| `{age}`         | Required  | The age of the trainee you want to put in the form.                  | Integer | 20                 |     |
| `{university}`  | Optional  | The university of the trainee you want to put in the form.           | String  | Harvard University |     |
| `{education}`   | Required  | Choose course that you want. Options will be "software" or "english" | String  | software           |     |

Request Example

```javascript
curl -X POST /https://api.archisacademy.com/v1/form/{id}?country=<YOUR_COUNTRY>&age=<YOUR_AGE>&university=<YOUR_UNIVERSITY>&education=<EDUCATION_TYPE>&id_kart=<ID_LINK>
```

**Response Example**

Code: 200

```
{
  "results": {

  },
  "status": "OK"
}
```

#####

##### 1.5. Change the candidate status after payment

​ PUT /archisacademy/trainee/{id}

​ PUT /archisacademy/trainee/{unique_name}

| Path parameter  | Description                                                                                                             | Type    | example          |     |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------- | ------- | ---------------- | --- |
| `{id}`          | The ID of trainee you want to look up. All IDs are available from our site at archisacademy.com.                        | Integer | 123              |     |
| `{unique_name}` | The unique name for the trainee you want to look up. All unique names are available from our site at archisacademy.com. | String  | furious_einstein |     |

| query parameter | Opt./req. | Description                                | Type   | example |     |
| :-------------- | --------- | :----------------------------------------- | ------ | ------- | --- |
| `{status}`      | Required  | Parameter options: "trainee", "candidate". | String | trainee |     |

Request Example

```javascript
curl -X PUT /https://api.archisacademy.com/v1/form/{id}?status=<CHOOSE_EDUCATION_STATUS>
```

**Response Example**

Code: 200

```
{
  "results": {

  },
  "status": "OK"
}
```
