Learning Audit 

On-boarding

- Git and Github (GREEN)
- High performance Routines (GREEN)
- AI and LLMs (GREEN)
- Computational Thinking (GREEN)
- CSS (GREEN)
HTML (GREEN)

Software

- JavaScript basics (ORANGE)
- JS Objects (GREEN)
- JS Arrays (ORANGE)
- JS Functions (RED)

 Frontend

- Semantic HTML and Basic of CSS Layouts (GREEN)
- DOM selectors (GREEN)
- Button click and Form Submit (GREEN)
- Fetch (ORANGE)
- Async JavaScript (ORANGE)
- Async/Await (RED)

Backend

- Node.js (ORANGE)
- Importing and Exporting (ORANGE)
- Express (ORANGE)
- RESTful APIs (ORANGE)
- API routes (RED) 
- Reading files (ORANGE)



Database

- Databases (GREEN)
- SQL basics (GREEN)
- SQL Joins (RED)
- SQL - Node.js & Postgres (ORANGE)



Learning Plan: 

- Revising JS functions with notes and doing some practice exercises ✅

- a function is defined with the function keyword, followed by a name, followed by parentheses ().
- // eg  Define a function called multiplyFive which accepts a number and returns that number multiplied by 5.

function multiplyFive(number) {
  return number * 5;
}

console.log(multiplyFive(2)); 

Write a function named minutesToHours that receives a number of minutes as parameter and returns a number representing the same amount of time but in hours.

function minutesToHours(minutes) {
    return minutes / 60; 
}

export { minutesToHours };

Write a function named max5 that receives 5 numbers as parameters and returns the biggest one between them.

function max5(nr1, nr2, nr3, nr4, nr5) {
  return Math.max(nr1, nr2, nr3, nr4, nr5);
}

export { max5 };








- Revising SQL Joins with notes and doing some practice exercises 












- Revising API routes - doing some practice exercises using hackathon from W4 - completing unfinished routes ✅

- Remember to import functions 💡 - this was error holding up progress in hackathon 


        Completing GET by ID request from hackthon: 

farmers.js: 
export async function getSingleFarmer(id) {
  // Query the database and return the resource with a matching id or null
  const eggQueryText = "SELECT * FROM farmers WHERE farmer_id = $1"
  const eggResult = await pool.query(eggQueryText, [id]);
  return eggResult.rows[0] || null;
}

app.js:
// Endpoint to retrieve a farmer by id
app.get("/egg/farmers/:id", async function (req, res) {
  try {
  const id = req.params.id;
  console.log(id);
  
// Retrieve farmer data using the provided ID
const singleFarmerData = await getSingleFarmer(id);
  
// Check if farmer data is found
    if (!singleFarmerData) {
    return res.status(404).json({
      status: "fail",
      data: { msg: "Farmer not found" }
    });
  }

// Send the farmer data in the response
res.status(200).json({
  status: "eggcellent",
  data: singleFarmerData
});
} catch (error) {
console.log(error);
res.status(500).json({
  status: "bad egg",
  data: null
});
}
});  