---
permalink: /project/
title: "Senior Project"
author_profile: true
---
# LU Food Pantry Web App

![image](https://github.com/user-attachments/assets/d1a4de94-06db-4e7a-bd4c-313c2dd85e9e)


## How does the Food Pantry work right now?

For those who are unfamiliar, the LU Student Food Pantry is available to any current Lawrence University student who is in immediate need or does not have access to essential items. The Pantry includes food, hygiene products, and school supplies. Students can only submit 1 online request per week. When that order is fulfilled, the student will be sent a confirmation email with an assigned number also located on the Pantry bag.

Right now this system is mostly manual, with the use of some Microsoft software, like;

- Microsoft Forms
  
Where students fill out the items they'd like to receive.

- Outlook
  
Where students will receive a notification email to let them know their pantry order is ready.

- Excel
  
Where staff can keep track of orders.

### Goals

  #### Streamlining
   I wanted this app to be able to streamline the process for the staff and students. The goal was to make this the only app staff need to use to check and fulfill student orders; and students to place and know the status of those pantry orders.

  #### Automation
  With that comes the automation. instead of staff needing to amnually input new orders from Office Forms to Excel, then after an order being fullfilled needing to write an email to the student letting them know it was ready. The app can do it for them.

### How It Was Made
With the following I decided to make the web app: 

Frameworks
* Front-end
  - React/Next.JS
  - Tailwind
* Back-end
  - SpringBoot
  - MySQL

```react
export default function Home() {
  return (
    <main>
      <h2>Welcome!</h2>
      <p>Welcome to the Lawrence University Food Pantry!</p>

      <div className="flex justify-center my-8">
        <Link href="/orders/create">
          <button className="btn-primary">Submit a form</button>
        </Link>
      </div>

```
### Features
* Order Submission

![image](https://github.com/user-attachments/assets/67985d5a-f4be-4b5c-b50f-7421a24310ee)
* Order Management

![image](https://github.com/user-attachments/assets/93154f77-decf-46a7-8d33-f4242e04f52b)

* Notification System

![image](https://github.com/user-attachments/assets/8ddb1213-4690-4207-911f-2e129c0fb445)


### Challenges

### Problems

### Repos

Front-end:
https://github.com/Blink1702/berny-seniorproject

Back-end:
https://github.com/Blink1702/berny-seniorproject-backend

