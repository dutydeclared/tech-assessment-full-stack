# 🧪 Full Stack Engineer Technical Assessment

Welcome to the technical challenge. This test is designed to assess your ability to build a simple end-to-end application using **Next.js**, **TypeScript**, and **PostgreSQL**.

---

## 🎯 Objective

Develop a small web application that allows users to **book meeting rooms**. Each room can only be reserved by one person at a time — your task includes ensuring **overlapping bookings are prevented**.

---

## 🧰 Tech Stack

- Next.js 14+ (App Router)
- TypeScript
- PostgreSQL (local or cloud-based, e.g. Supabase)
- ORM (optional)

---

## 📂 Application Features

### 1. **Users**

- Allow users to be created via a simple form (`name`, `email`)
- No authentication is required

### 2. **Rooms**

- Prepopulate the database with a few rooms (e.g., `"Room A"`, `"Room B"`, `"Room C"`)

### 3. **Bookings**

- Users should be able to create a booking by selecting:
  - A room
  - A date
  - Start time
  - End time
- The system must **prevent room bookings that conflict with existing reservations**

---

## ⚙️ Pages

### Home

- Display a list of all rooms
- Each room links to its respective bookings page

### Bookings Page

- Show a list of upcoming bookings for the selected room
- Include a button to add a new booking

### Booking Form

- Form to create a new booking
- Validate against overlapping bookings
- If the room is already booked in the selected time slot, inform the user and prevent the booking

---

## 🧠 Business Rule: Booking Conflict Check

You must ensure a new booking does **not overlap** with any existing bookings for the same room and date.

If a conflict is found, the booking should be rejected and the user should receive an appropriate message.

---

## 🗃️ Suggested Database Schema (Prisma-style)

```ts
model User {
  id        String   @id @default(uuid())
  name      String
  email     String
  bookings  Booking[]
}

model Room {
  id        String   @id @default(uuid())
  name      String
  bookings  Booking[]
}

model Booking {
  id        String   @id @default(uuid())
  userId    String
  user      User     @relation(fields: [userId], references: [id])
  roomId    String
  room      Room     @relation(fields: [roomId], references: [id])
  date      DateTime
  startTime String
  endTime   String
}
```

> ℹ️ You may store `startTime` and `endTime` as strings (e.g., `"09:00"`) or as `DateTime`, depending on your preferred implementation.

---

## ✨ Nice to Have

- Application packaged with Docker

---

## ✅ What We’re Looking For

We’re interested not only in the final result, but in **how you approach the problem**.

We’ll pay attention to:

- How your code is structured and organised
- Your ability to reason through and implement business logic
- The use of TypeScript for type safety and data modelling
- Usability and clarity in the user interface
- How easy it is to set up and run your project

Bonus points for thoughtful handling of validation, errors, and user experience.

> Don’t worry about perfection — focus on clarity, structure, and demonstrating your thinking.

---

## 🚀 Submission Instructions

1. Create and push the code to a **private GitHub repository** under your account.
2. Give access to the following user:
   - [@andremoresco](https://github.com/andremoresco)

Once complete, please send an email to:

📩 **andre.moresco@dutydeclared.com**

---

Good luck — and if you have any questions during the process, feel free to reach out!
