### JSON Conversions

#### Define map interface any type

```Go
  data := map[string]interface{}{
    "success": true,
    "message": "livess response",
    "data": map[string]interface{}{
        "result":       true,
        "fail_message": "",
        "uuid":                  uuidu,
        "url":                   "http://api-server.com/client_id=xxxxxxx",
        "code":           nil,
    },
}


json.Marshal(data)
```

```Go
   data := `{
       "name":             "abcd",
       "code":             "code",
       "description":      "desc",
       "record_id":        111,
       "creation_date":   "02/28/2024",
   }`


   json.Unmarshal([]byte(data), &Data)
```

```Go
type Event struct {
   UserID           int64  `json:"user_id"`
   CompanyID        int64  `json:"company_id"`
   IDEmployee       string `json:"id_employee"`
   FirstName        string `json:"first_name"`
   LastName         string `json:"last_name"`
   JoinDate         string `json:"join_date"`
   JobID            int    `json:"job_id"`
   JobName          string `json:"job_name"`
   BranchID         int    `json:"branch_id"`
   JobLevelID       int    `json:"job_level_id"`
   OrganizationID   int    `json:"organization_id"`
   EmploymentStatus int    `json:"employment_status"`
   Religion         int    `json:"religion"`
   SBUList          []int  `json:"sbu_list"`
}

type EventInfo struct {
   Attributes Event `json:"attributes"`
}

type Payload struct {
   Data EventInfo `json:"data"`
}
```

```Go
func main() {
   payload := []byte(`{
       "data": {
           "attributes": {
               "user_id": 997697574,
               "company_id": 3620,
               "id_employee": "SDET-002",
               "first_name": "SDET",
               "last_name": "Employee",
               "join_date": "2018-01-08",
               "job_id": 241283,
               "job_name": "Staff IT",
               "branch_id": 0,
               "job_level_id": 35868,
               "organization_id": 79753,
               "employment_status": 675,
               "religion": 2,
               "sbu_list": []
           }
       },
       "options": {
           "event_type": "update_personal",
           "action": "update",
           "is_update_criteria": false,
           "timestamp": 1707703628896
       }
   }`)
  
   var payloadData Payload
   err := json.Unmarshal(payload, &payloadData)
   if err != nil {
       panic(err)
   }

   fmt.Printf("Config: %+v\n", payloadData.Data.Attributes)
```

```Go
func CreateRestaurants(w http.ResponseWriter, r *http.Request) {
	params := mux.Vars(r)
	var person Restaurant
	_ = json.NewDecoder(r.Body).Decode(&person) // Recommended way to convert json to struct
	person.ID = params["id"]
	restaurants = append(restaurants, person)
	json.NewEncoder(w).Encode(restaurants)
}
```





### Links
https://blog.logrocket.com/using-json-go-guide/

http://gregtrowbridge.com/golang-json-serialization-with-interfaces/


