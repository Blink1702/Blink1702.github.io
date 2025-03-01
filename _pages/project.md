---
permalink: /project/
title: "Senior Project"
author_profile: true
---
# LU Food Pantry Web App

For my senior project I developed a web app and its back-end for the Lawrence University Food Pantry.

## Why did I decide to do this?

For those who are unfamiliar, the LU Student Food Pantry is available to any current Lawrence University student who is in immediate need or does not have access to essential items. The Pantry includes food, hygiene products, and school supplies. Students can only submit 1 online request per week. When that order is fulfilled, the student will be sent a confirmation email with an assigned number also located on the Pantry bag.

Right now this system is mostly manual, with the use of some Microsoft software, like;

- Microsoft Forms
  
Where students fill out the items they'd like to receive.

- Outlook
  
Where students will receive a notification email to let them know their pantry order is ready.

- Excel
  
Where staff can keep track of orders.

### Goals
This is what I mainly wanted to improve by making my web-app.

  #### Streamlining
   I wanted this app to be able to streamline the process for the staff and students. The goal was to make this the only app staff need to use to check and fulfill student orders; and students to place and know the status of those pantry orders.

  #### Automation
  With that comes the automation. instead of staff needing to amnually input new orders from Office Forms to Excel, then after an order being fullfilled needing to write an email to the student letting them know it was ready. The app can do it for them.

## How It Was Made
With the following I decided to make the web app: 

Frameworks
* Front-end
  - React/Next.JS
  - Tailwind
* Back-end
  - SpringBoot
  - MySQL

I decided to learn React, specifically the Next.js framework, firstly because I've always been interested in a more dynamic way to program websites and apps, and React is one of the foundational frameworks for that at the moment. I chose the Next.js specifically since it seemed to give a lot of quality of life features which made mt coding experience easier. Specially file-based routing, where Next.js would create new pages based on the folder structure of my project. 

![image](https://github.com/user-attachments/assets/b78bf9b9-4a74-432d-baf6-49f9bdc721a5)

For the back-end I was already familiar with Springboot and MySQL, so I chose them since I wanted for the back-end to be reliable and not take much of my time since I wanted to focus more on the front-end and learning React.

### Features
* Home Page
  - Landign page, where staff can add any updates to the pantry.
  
![image](https://github.com/user-attachments/assets/d1a4de94-06db-4e7a-bd4c-313c2dd85e9e)
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

* Order Submission
  - This is a simple page where students will submit the items they want, and they will be uploaded to the database.

![image](https://github.com/user-attachments/assets/67985d5a-f4be-4b5c-b50f-7421a24310ee)
```react
export default function CreateForm() {
    const router = useRouter()
    
    const [item, setItem] = useState('')
    const [user, setUser] = useState('')
    const [fulfilled, setFulfilled] = useState(false)
    const [isLoading, setIsLoading] = useState(false)

    const handleSubmit = async (e) => {
        e.preventDefault()
        setIsLoading(true)

        const order = {
            item
        }

        const token = getToken()

        const res = await fetch('http://localhost:8085/orders', {
            method: "POST",
            headers: {"Authorization": `Bearer ${token}`,"Content-Type": "application/json"},
            body: JSON.stringify(order)
        })

        if (res.status === 201){
            router.refresh()
            router.push('/orders')
        }
    }
    
  return (
    <form onSubmit={handleSubmit} className="w-1/2">
        <label>
        <span>Items:</span>
        <input
          required 
          type="text"
          onChange={(e) => setItem(e.target.value)}
          value={item}
        />
      </label>
      <button 
        className="btn-primary" 
        disabled={isLoading}
      >
      {isLoading && <span>Submitting...</span>}
      {!isLoading && <span>Submit Order</span>}
    </button>
    </form>
  )
}
```

* Order Management
  - In this page, staff can see all the orders placed, and some information about them, specially their status of being fulfilled or not.

![image](https://github.com/user-attachments/assets/93154f77-decf-46a7-8d33-f4242e04f52b)
```react
async function getOrders() {
    const res = await fetch('http://localhost:8085/orders',{
      next: {
        revalidate : 0 //0 = no cache
      }
    })
    
    return res.json()
}

export default async function OrderList() {
    const orders = await getOrders()

  return (
    <>
        {orders.map((order) => (
          <div key={order.id} className="card my-5">
            <Link href={`/orders/${order.orderid}`}>
              <h3>{order.date}</h3>
              <p>{order.item.slice(0,200)}...</p>
              <div className={`pill ${order.fulfilled}`}>
                 Fullfilled
              </div>
            </Link>
          </div>  
        ))}
        {orders.length === 0 && (
            <p className="text-center">There are no open orders!</p>
        )}
    </>
  )
}
```

* Notification System
  - Each student will have their own profile page, where they will be able to see the orders they have made and their status.

![image](https://github.com/user-attachments/assets/8ddb1213-4690-4207-911f-2e129c0fb445)


### Future Updates
* Customazible notifications
  - I would like to expand the ways in which students can find out their pantry order is ready. Like having in-app notifications or automated email notifications. And let the students choose which type they would like to receive.
* Order Notes
  - I want to implemetn a feature where staff can add notes to fulfilled orders if they need/want to give some information to the student about the order.
* Order Editing
  - Right now the only thing staff can do with orders is changing their status from Not Fulfilled to Fulfilled. I would want to implement the feature of admins being able to edit orders if need be. 

### Repos
If you want to take a look at the code:

Front-end:
https://github.com/Blink1702/berny-seniorproject

Back-end:
https://github.com/Blink1702/berny-seniorproject-backend

