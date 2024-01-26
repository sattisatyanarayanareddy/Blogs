# -
A blog, short for weblog, is a frequently updated web page used for personal commentary or business content. 


**Blog-BS001**

**Blog-BS001 for create a Post Endpoint using Mongodb**


First open Mongodb Atlas in clooud.mongodb.com
next open **App Services** as shown in figure
![Screenshot 2024-01-26 200946](https://github.com/sattisatyanarayanareddy/-/assets/113776283/54507c84-0b63-4ee2-819b-feb4ae90d44c)

After open App Service now click on **Create a New App** Service
![Screenshot 2024-01-26 201021](https://github.com/sattisatyanarayanareddy/-/assets/113776283/db1902a0-0e5a-4990-b6a5-3430d1403a67)

Now Name the Service and Click on **Create App Service**
![Screenshot 2024-01-26 201124](https://github.com/sattisatyanarayanareddy/-/assets/113776283/a61f8fa7-2440-4ab2-bc08-a0a629602a06)

Now open Created App Service as shown below
![Screenshot 2024-01-26 201229](https://github.com/sattisatyanarayanareddy/-/assets/113776283/8c687d7c-1ad2-4321-ae40-7865faee41f6)

Now open **HTTPS Endpoints** as shown in bellow
![Screenshot 2024-01-26 201245](https://github.com/sattisatyanarayanareddy/-/assets/113776283/80a90d28-33d9-47b4-8e40-defe44bbdfaf)

Now click on **Add An Endpoint**
![Screenshot 2024-01-26 201301](https://github.com/sattisatyanarayanareddy/-/assets/113776283/f606d4fc-4d51-429b-a231-d3b7522331e3)

Now Name the Route
![Screenshot 2024-01-26 201331](https://github.com/sattisatyanarayanareddy/-/assets/113776283/908293e6-8add-4855-8b95-fa2eecee6093)

Now Select the **post Method** and Enable **Respond With Result**
![Screenshot 2024-01-26 201400](https://github.com/sattisatyanarayanareddy/-/assets/113776283/e5c1ca0b-e2a8-4ed0-82c5-8f0b4768deed)

Now **Select a function**
![Screenshot 2024-01-26 201423](https://github.com/sattisatyanarayanareddy/-/assets/113776283/ab5b996d-d5c8-4f14-a18d-87e347da921c)

Name The Function as shown bellow and **don't tounch below function code**
![Screenshot 2024-01-26 201445](https://github.com/sattisatyanarayanareddy/-/assets/113776283/24be8dd6-83ea-4bd0-8cda-7243e1fbdeba)

No Click on **Save Draft**
![Screenshot 2024-01-26 201458](https://github.com/sattisatyanarayanareddy/-/assets/113776283/5c645d11-1efb-4bc7-90b2-1acde4ba4547)

Now go to **Functions** and Create New Function
![Screenshot 2024-01-26 201533](https://github.com/sattisatyanarayanareddy/-/assets/113776283/736272cb-6203-4406-96ab-b4ed7d70de0b)

Now Update the function code with your schema
**replace function code with below code**
exports = async function({ query, headers, body }, response) {
  const eventData = JSON.parse(body.text());


  if (!eventData.title || !eventData.description) {
    return response.badRequest("Title and description are required fields");
  }


  if (typeof eventData.title !== 'string' || typeof eventData.description !== 'string') {
    return response.badRequest("Title and description must be strings");
  }

  const result = await context.services
    .get("mongodb-atlas")
    .db("examples")
    .collection("people")
    .insertOne({
      title: eventData.title,
      description: eventData.description,
    });

  return result;
};

**Make sure you only set database name called .db and collection name also** and insert your schema

![Screenshot 2024-01-26 201559](https://github.com/sattisatyanarayanareddy/-/assets/113776283/8433dcce-afab-4211-964e-c34458cbac9e)

Now Open **Settings** and enable System at Authentication
![Screenshot 2024-01-26 201616](https://github.com/sattisatyanarayanareddy/-/assets/113776283/451fd449-ccaf-426a-864d-f7ce036a956c)

Finally your **Post Endpoint** is ready go back to HHTPS Endpoints and collect it
![Screenshot 2024-01-26 201645](https://github.com/sattisatyanarayanareddy/-/assets/113776283/acc0e2d6-0d51-4545-9a79-d1684e3db9fb)
