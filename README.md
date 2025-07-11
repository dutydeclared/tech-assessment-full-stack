# Full Stack Engineer Tech Assessment

Welcome to the technical challenge! This test is designed to evaluate your ability to build a simple end-to-end application using **Next.js**, **TypeScript**, and **PostgreSQL**.

---

## 🎯 Objective

Build a small web application that allows users to **book meeting rooms**. Each room can only be booked by one person at a time — **you must prevent overlapping bookings**.

---

## 🧰 Tech Stack

- Next.js 14+ (App Router)
- TypeScript
- PostgreSQL (can be local or cloud like Supabase)
- ORM (Optional)

---

## 📂 Features

### 1. **Users**

- Users can be created via a simple form with `name` and `email`
- No authentication needed

### 2. **Rooms**

- Prepopulate the database with a few rooms: e.g. `"Room A"`, `"Room B"`, `"Room C"`

### 3. **Bookings**

- A user can book a room by specifying:
  - Room
  - Date
  - Start time
  - End time
- Users should not be able to book a room that is already reserved during the same time range

---

## ⚙️ Pages

### Home

- List all rooms
- Link to view bookings per room

### Bookings Page

- List of upcoming bookings for a specific room
- Button to add a new booking

### Booking Form

- Form to create a new booking
- Should validate against existing overlapping bookings
- Show a message if the room is already booked in that time range

---

## 🧠 Business Rule: Booking Conflict Check

You **must ensure** that a new booking does not overlap with existing ones for the same room and date.
If a conflict exists, the user should be notified and the booking should not be created.

## Suggested Database Schema (Prisma-style)

```
model User {
  id String @id @default(uuid())
  name String
  email String
  bookings Booking[]
}

model Room {
  id String @id @default(uuid())
  name String
  bookings Booking[]
}

model Booking {
  id String @id @default(uuid())
  userId String
  user User @relation(fields: [userId], references: [id])
  roomId String
  room Room @relation(fields: [roomId], references: [id])
  date DateTime
  startTime String
  endTime String
}
```

You can store startTime and endTime as strings (e.g., "09:00") or use DateTime for precise handling.

## Nice To Have

- Application is packaged in Docker.

## ✅ Evaluation Criteria

We’re looking to understand **how you work**, not just the final result.

We’re paying attention to:

- How you structure and organize your code
- Your ability to implement and reason through business logic
- How you use TypeScript and handle data flow
- Your user experience decisions (navigation, validation, feedback)
- How clearly your project can be understood and run

Bonus points for good practices around error handling, validation, and thoughtful UI/UX.
Focus on clarity and functionality.

PS:
We don’t expect it to be perfect — focus on structure, logic, and clarity.

⸻

## 🚀 Submission Instructions

1. Create and push the code to a private repo in your account.
2. Give access to the following users:
   - [@andremoresco](https://github.com/andremoresco)

When you are done with the tech assessment, please send an email to:

- andre.moresco@dutydeclared.com

Good luck! If you have any questions, feel free to ask during the process.
