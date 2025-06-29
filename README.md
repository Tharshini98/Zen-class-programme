
users
{
  "_id": {
    "$oid": "6860deaab7549866dc369c1d"
  },
  "name": "Viswam",
  "email": "viswam@gmail.com",
  "mentor_name": "Raj",
  "codekata_score": 220
}

codekata
{
  "_id": {
    "$oid": "6860def7b7549866dc369c20"
  },
  "user_name": "Viswam",
  "problems_solved": 150
}
attendance
{
  "_id": {
    "$oid": "6860dfa5b7549866dc369c23"
  },
  "user_name": "Viswam",
  "date": "16-10-2020",
  "status": "absent"
}

topics 
{
  "_id": {
    "$oid": "6860e064b7549866dc369c2b"
  },
  "topic_name": "MongoDB",
  "date": "16-10-2020"
}

tasks
{
  "_id": {
    "$oid": "6860e0b5b7549866dc369c2e"
  },
  "task_name": "Zen class MongoDB",
  "topic_name": "MongoDB",
  "user_name": "Viswam",
  "date": "16-10-2020",
  "submitted": false
}

company_drives
{
  "_id": {
    "$oid": "6860e0feb7549866dc369c31"
  },
  "company": "ZOHO",
  "date": "2020-10-27",
  "attended_students": ["Viswam","Nivetha"]
}

mentors
{
  "_id": {
    "$oid": "6860e19ab7549866dc369c34"
  },
  "name": "Raj",
  "mentees": ["Viswam","Nivetha","Jai","David","Kumar","Santhosh","Priya","Joseph","Robin","George","Hari","Jacob","Mona","Shiny","Umar","Paul"]
}

1. Find all the topics and tasks which are thought in the month of October
db.topics.find({
  date: { $regex: ".*-10-2020" }
})
2. Find all the company drives which appeared between 15 oct-2020 and 31-oct-2020
   db.company_drives.find({
  date: {
    $gte: "2020-10-15",
    $lte: "2020-10-31"
  }
})

3. Find all the company drives and students who are appeared for the placement.
  db.company_drives.find({}, { company: 1, attended_students: 1 })

4. Find the number of problems solved by the user in codekata
   db.codekata.find({ user_name: "Viswam" }, { problems_solved: 1 })

5. Find all the mentors with who has the mentee's count more than 15
  db.mentors.find({
  $expr: {
    $gt: [{ $size: "$mentees" }, 15]
  }
})

6. Find the number of users who are absent and task is not submitted  between 15 oct-2020 and 31-oct-2020
db.attendance.find({ status: "absent" })
db.tasks.find({
  user_name: "Viswam",
  date: "16-10-2020",
  submitted: false
})
   

