
**Blog-BS002**

This Blog is for to create **get endpoint** in mongodb

Do all instruction as in ***Blog-BS001***

just replace function method and function code with below given code

exports = async function(arg) {
  try {
    let collection = context.services
      .get("mongodb-atlas")
      .db("")
      .collection("");

    const result = await collection.find({}).toArray();

    return result;
  } catch (error) {
    console.error('Error fetching data:', error);
    return null;
  }
};
