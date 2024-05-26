# Structure and functionality : 

## Pages:

### 1. New class popup

UX :  
Add the following details
- time + date of class
- Duration of class
- Topic
- Tags
- Course
- Brief Description of the class
- Professor
- Location

**Working :** 

- In JSON, dates and times are typically stored as strings in ISO 8601 format. i.e. ```{  "timestamp": "2024-05-26T14:15:22Z" }```   
This will be the unique id in the JSON.

- Duration of the class will be in minutes

- Enter the topic, the words of the topic is added as tags by default. eg: Addition in Fibonacii heap ;  
The tags will be `Addition` , `in` ,`Fibonacii` and `heap`.  
So if someone tries to search by tags "heap" , it will be easier.

- Custom tags : Space seperated, adds to the the tag

- Course: Can be chosen from a list of course but with a new course button,  
(Course name added as tag)

- Brief Decription of the class

- Add professor, with new professor button

> Note : Keep a pre built option of `unlisted` so that courses and professors list only has the most used options.

- Location tag

So 

### 2. Class page

- Shows a table which shows me a pagination table of 
- Sort by date
- Sort by last revised (by default value is time of class)
- Sort by level of revision
- Show a particular course only
- Sort by tag


## Realtime database (Using Firebase)

Deciding on JSON and objects structure:

>Note : (**CAUTION**) Unique key of each classes obeject will be its start date + time. This works because one cannot attend 2 classes at once.

1. Classes : Each class will have many parameters.
    1. Timestamp
    2. Duration
    3. Topic
    4. Tags
    5. Course
    6. Brief description of the what was taught
    7. Revision list object

2. Revision list object :
    List of revision objcts each containing:
    1. Timestamp of classes
    2. Timestamp of revision
    3. Duration
    4. Level of rev(1 to 10)

3. Courses List (Only those saved by User)
    1. Name of course
4. 


example of data : 

```json
{
  "classes": {
    "2024-05-26T14:15:22Z": {
      "timestamp": "2024-05-26T14:15:22Z",
      "duration": 90,
      "topic": "Introduction to JavaScript",
      "tags": ["JavaScript", "Programming", "Basics"],
      "course": "Web Development 101",
      "brief_description": "An introduction to JavaScript covering basic syntax, variables, and data types.",
      "revision_list": [
        "2024-05-28T10:00:00Z",
        "2024-05-30T15:30:00Z"
      ]
    },
    "2024-05-27T09:00:00Z": {
      "timestamp": "2024-05-27T09:00:00Z",
      "duration": 120,
      "topic": "Advanced CSS",
      "tags": ["CSS", "Web Design", "Advanced"],
      "course": "Web Development 101",
      "brief_description": "Advanced concepts in CSS, including Flexbox, Grid, and responsive design.",
      "revision_list": [
        "2024-05-29T11:00:00Z",
        "2024-06-01T14:00:00Z"
      ]
    }
  },
  "revisions": {
    "2024-05-28T10:00:00Z": {
      "class_timestamp": "2024-05-26T14:15:22Z",
      "revision_timestamp": "2024-05-28T10:00:00Z",
      "duration": 60,
      "level_of_rev": 5
    },
    "2024-05-30T15:30:00Z": {
      "class_timestamp": "2024-05-26T14:15:22Z",
      "revision_timestamp": "2024-05-30T15:30:00Z",
      "duration": 45,
      "level_of_rev": 7
    },
    "2024-05-29T11:00:00Z": {
      "class_timestamp": "2024-05-27T09:00:00Z",
      "revision_timestamp": "2024-05-29T11:00:00Z",
      "duration": 60,
      "level_of_rev": 6
    },
    "2024-06-01T14:00:00Z": {
      "class_timestamp": "2024-05-27T09:00:00Z",
      "revision_timestamp": "2024-06-01T14:00:00Z",
      "duration": 75,
      "level_of_rev": 8
    }
  }
}

```


