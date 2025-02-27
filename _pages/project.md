---
permalink: /project/
title: "Project"
author_profile: true
---
Info about my projects, maybe pictures, embed graphs...

# LU Food Pantry Web App

## Subtitle

For those who are unfamiliar, the LU Student Food Pantry is available to any current Lawrence University student who is in immediate need or does not have access to essential items. The Pantry includes food, hygiene products, and school supplies. Students can only submit 1 online request per week. When that order is fulfilled, the student will be sent a confirmation email with an assigned number also located on the Pantry bag.

Right now this system is mostly manual, with the use of some Microsoft software, like;

- Microsoft Forms
  
Where students fill out the items they'd like to receive
- Outlook
  
Where students will receive a notification email to let them know their pantry order is ready.
- Excel
  
Where staff can keep track of orders.

### Goals

### Features

### How It Was Made

Frameworks

- React/Next.JS
- Tailwind
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
### Challenges

#Problems
