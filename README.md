require('dotenv').config();
const { Client } = require('pg');

const client = new Client(); // підтягує дані з .env автоматично

(async () => {
  await client.connect();
  const res = await client.query('SELECT $1::text as message', ['База працює!']);
  console.log(res.rows[0].message);
  await client.end();
})();
