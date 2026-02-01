# StackOverflow Low Level Design (LLD)

This repository contains a Low Level Design (LLD) implementation of a simplified StackOverflow-like system.  
The project is intended for **LLD / Machine Coding interview evaluation**, focusing on object-oriented design, clarity, and extensibility.

---

## Objective

- Model core StackOverflow features
- Demonstrate strong OOP fundamentals
- Apply clean Low Level Design principles
- Build an interview-ready, extensible design

---

## High-Level Design

Domain Entities → Service Logic → DAO (In-memory Persistence)

---

## Core Entities

### User Hierarchy
- Guest
- Member
- Moderator

Inheritance is used to model role-based permissions and behavior.

---

### Question (Aggregate Root)
- Contains:
  - Answers
  - Comments
  - Tags
- Responsible for managing its child entities

---

### Answer
- Belongs to one Question
- Can contain Comments

---

### Comments
- Can belong to Question or Answer
- Stored independently but owned logically

---

### Tags & Badges
- Implemented as enums
- Ensures type safety and controlled values

---

## DAO Layer

Uses in-memory storage with maps:
- Map<QuestionId, Question>
- Map<AnswerId, Answer>
- Map<CommentId, Comment>

DAO abstracts persistence but currently handles some coordination logic.

---

## Design Patterns Used

- Builder / SuperBuilder for object construction
- Inheritance and Polymorphism
- Aggregate Root pattern
- DAO pattern

---

## LLD Evaluation

**Current Rating: 6.5 / 10**

---

## Strengths

- Clear domain modeling
- Proper entity relationships
- Correct use of inheritance
- Clean use of enums
- Interview-appropriate structure

---

## Areas for Improvement

- DAO layer contains business logic
- Missing service layer
- Single DAO handling multiple entities
- Limited thread safety
- No repository interfaces

---

## Improvements to Reach 8.5–9 / 10

- Introduce a Service layer
- Split DAO into QuestionDao, AnswerDao, CommentDao
- Use ConcurrentHashMap
- Enforce entity invariants
- Add repository interfaces
- Separate orchestration from persistence

---

## Scope & Limitations

- In-memory persistence only
- No REST APIs
- Focused on LLD, not production readiness
