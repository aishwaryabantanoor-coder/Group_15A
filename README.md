# Group_15A
# Blood Donor & Emergency Blood Availability Portal – Project Planning

Let's plan this as a simple, lightweight full-stack web application using Node.js, JavaScript, HTML, CSS, and a JSON file as the database.

We will build it step by step, run everything on localhost, and support multiple users with separate login accounts.

The goal is to make this a manageable student-level project without unnecessary complexity.

## 1. Project overview

Project-Donor (Blood Donation) :: Behance

[behance.net](<https://www.behance.net/gallery/128309253/Project-Donor-%28Blood-Donation%29?utm_source=chatgpt.com>)

# LifeLink – Blood Donor & Emergency Portal

A web portal that connects people who need blood with registered blood donors.Lightweight projectMulti-user loginLocalhost

Main purpose:

- Allow people to register as blood donors.
- Allow users to search for available blood donors.
- Allow patients or their relatives to post emergency blood requests.
- Allow donors to view emergency requests.
- Allow users to manage their profiles.

## 2. Technology stack

We will use a simple technology stack without React, Angular, or MongoDB.

| Layer | Technology |
| --- | --- |
| Frontend | HTML, CSS, JavaScript |
| Backend | Node.js |
| Backend framework | Express.js |
| Database | JSON file |
| Authentication | Express Session |
| Password security | bcrypt |
| API communication | Fetch API |
| Development | VS Code |
| Local server | localhost |

Why JSON database?

Instead of installing and configuring MySQL or MongoDB, we will store application data in JSON files.

For example:

- `users.json`
- `donors.json`
- `requests.json`

Node.js will read and update these files.

This is suitable for a small academic project, but not for a real emergency blood service with many simultaneous users.

## 3. User roles

Our application will have three types of users.

1. Normal User

- Register and log in.
- Search for blood donors.
- View donor contact details where permitted.
- Create emergency blood requests.
- View their request history.

2. Blood Donor

- Register as a donor.
- Add blood group and location.
- Update availability status.
- View emergency blood requests.
- Contact the requester.
- Update donor profile.

3. Admin

- View registered users.
- View all donors.
- View all blood requests.
- Remove fake or inappropriate requests.
- Manage donor accounts.

For simplicity, a user can also register as a donor. We don't need completely separate donor accounts.

## 4. Main modules

I recommend dividing the project into seven modules.

### Module 1: User Authentication

Penggunaan Data Pribadi | AdMedika

[admedika.co.id](<https://www.admedika.co.id/terms/penggunaan-data-pribadi?utm_source=chatgpt.com>)

Features:

- User registration.
- User login.
- Logout.
- Password hashing.
- Session management.
- Role-based access (user/admin).

### Module 2: User Dashboard

After login, users will see a dashboard containing:

- Welcome message.
- Search donors.
- Emergency blood requests.
- Become a donor.
- My profile.
- My requests.

### Module 3: Donor Registration

Donors provide:

| Field | Example |
| --- | --- |
| Full name | Rahul |
| Age | 25 |
| Gender | Male |
| Blood group | O+ |
| Phone number | 9876543210 |
| District | Shivamogga |
| City | Bhadravati |
| Availability | Available |

Additional functionality:

- Update profile.
- Change availability.
- Stop receiving contact requests.

### Module 4: Search Blood Donors

Blood Donation Website for Organizations by Coder IT Solution on Dribbble

[dribbble.com](<https://dribbble.com/shots/26724891-Blood-Donation-Website-for-Organizations?utm_source=chatgpt.com>)

Search filters:

- Blood group.
- District.
- City.
- Availability.

Example:

A patient needs O+ blood in Shivamogga.

The portal displays matching registered donors.

### Module 5: Emergency Blood Request

BloodLink: UX Design of a platform for finding and connecting blood donor instantly. | by Mafruh Faruqi | Medium

[medium.com](<https://medium.com/%40mafruh-faruqi/bloodlink-ux-design-of-a-platform-for-finding-and-connecting-blood-donor-instantly-fdaddba406f7?utm_source=chatgpt.com>)

Request form:

| Field | Example |
| --- | --- |
| Patient name | Arjun |
| Required blood group | O+ |
| Required units | 2 |
| Hospital name | City Hospital |
| Location | Shivamogga |
| Contact number | 9876543210 |
| Required date | 28-11-2026 |
| Emergency description | Urgent requirement |

Request status:

- Open
- Donor contacted
- Fulfilled
- Cancelled

### Module 6: Emergency Request Board

This is one of the most important features.

All active emergency requests will appear in a common dashboard.

Donors can:

- View urgent requests.
- Filter by blood group.
- Filter by location.
- Contact the requester.
- Mark that they are interested in helping.

### Module 7: Admin Dashboard

Admin can see:

- Total registered users.
- Total donors.
- Available donors.
- Total emergency requests.
- Pending requests.
- Completed requests.

Admin also has the ability to manage users and requests.

## 5. Application workflow

Here is the basic flow of our application.

Open website

localhost:3000

Register / Login

User Dashboard

Search Donors

Find blood donors

Emergency Request

Request blood

Become Donor

Register as donor

My Requests

Track requests

Connect donor and requester

## 6. Database planning (JSON files)

We will create four JSON database files initially.

1. users.json

Stores login information and account details.

json

```json
[
  {
    "id": 1,
    "name": "Rahul",
    "email": "rahul@gmail.com",
    "password": "hashed_password",
    "role": "user"
  }
]
```

2. donors.json

Stores donor information.

json

```json
[
  {
    "id": 1,
    "userId": 1,
    "bloodGroup": "O+",
    "age": 25,
    "city": "Shivamogga",
    "phone": "9876543210",
    "available": true
  }
]
```

3. requests.json

Stores emergency requests.

json

```json
[
  {
    "id": 1,
    "userId": 2,
    "patientName": "Arjun",
    "bloodGroup": "O+",
    "units": 2,
    "hospital": "City Hospital",
    "city": "Shivamogga",
    "status": "open"
  }
]
```

4. responses.json

Stores donor responses to emergency requests.

json

```json
[
  {
    "id": 1,
    "requestId": 1,
    "donorId": 1,
    "status": "interested"
  }
]
```

These are sample structures, not code we need to implement now.

## 7. Project folder structure

This is the structure I recommend we follow.

text

```text
Blood-Donor-Portal/
│
├── server.js
├── package.json
│
├── database/
│   ├── users.json
│   ├── donors.json
│   ├── requests.json
│   └── responses.json
│
├── routes/
│   ├── auth.js
│   ├── donor.js
│   ├── request.js
│   └── admin.js
│
├── middleware/
│   └── authMiddleware.js
│
├── public/
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   │
│   ├── css/
│   │   └── style.css
│   │
│   ├── js/
│   │   ├── login.js
│   │   ├── register.js
│   │   ├── dashboard.js
│   │   ├── donors.js
│   │   └── requests.js
│   │
│   └── pages/
│       ├── dashboard.html
│       ├── donors.html
│       ├── emergency.html
│       ├── my-requests.html
│       ├── profile.html
│       └── admin.html
│
└── README.md
```

## 8. Development plan – step by step

I recommend completing the project in eight phases.

1. Phase 1 – Project setup
   Foundation- Install Node.js.
   - Create project folder.
   - Initialize Express server.
   - Configure localhost.
   - Connect JSON files.
2. Phase 2 – Authentication
   - Registration page.
   - Login page.
   - Password hashing.
   - Multiple user sessions.
   - Logout functionality.
3. Phase 3 – Dashboard
   - Create navigation.
   - Create dashboard layout.
   - Add user profile section.
4. Phase 4 – Donor management
   - Donor registration.
   - Update donor information.
   - Availability management.
   - Donor listing.
5. Phase 5 – Donor search
   - Blood group filter.
   - Location filter.
   - Search results.
6. Phase 6 – Emergency requests
   - Create request.
   - View active requests.
   - Donor interest responses.
   - Update request status.
7. Phase 7 – Admin dashboard
   - View users.
   - Manage donors.
   - Manage requests.
   - Dashboard statistics.
8. Phase 8 – Testing and completion
   - Test multiple accounts.
   - Test login and logout.
   - Test donor searching.
   - Test emergency requests.
   - Fix errors and prepare documentation.

## 9. Important safety and technical considerations

Since this project involves emergency blood requirements, we should include some basic safeguards:

- Clearly state that donor availability is self-reported and must be confirmed.
- Do not guarantee blood compatibility based only on the portal's search results; hospitals must verify compatibility and eligibility.
- Protect passwords using bcrypt.
- Restrict admin functionality to admin accounts.
- Validate all user inputs on the server.
- Do not expose private user information unnecessarily.
- Use safe JSON file writes and avoid simultaneous-write corruption.

Also, this is a coordination portal, not a replacement for a hospital or blood bank. Emergency users should be advised to contact a hospital or licensed blood bank immediately.

## 10. Final project scope

To avoid making the project too complicated, let's divide features into two levels.

| Essential features | Optional future features |
| --- | --- |
| Multiple user login | Email notifications |
| Donor registration | SMS alerts |
| Search donors | Google Maps |
| Emergency requests | Live chat |
| Donor responses | OTP verification |
| Admin dashboard | Analytics |
| JSON database | MySQL migration |

My recommendation: Build only the essential features first. We can add optional features after the main application works.

## 11. Let's finalize the project requirements

Before starting Phase 1, I want to confirm three design decisions.

1. Who can register as a blood donor?

both Every registered user can also become a donor (recommended)

Separate registration for donors and normal users

2. How should donors contact emergency requesters?

phone Display phone number

Donor clicks Interested, then requester gets donor details

Both options

3. Do you want an admin login?

yes Yes, separate admin account

No, only normal users and donors

4. Overall project complexity

simple Simple – basic features only

Medium – better dashboard and additional features

 Confirm project requirements

Once we finalize these decisions, we can start Phase 1 and build the project one module at a time, understanding what each part does instead of simply copying code.
