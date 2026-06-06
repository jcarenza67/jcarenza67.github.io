# Joseph Wilfong
**Field Technician | Software Developer | Computer Science, SNHU**

Shelton, Washington · [GitHub](https://github.com/jcarenza67)

---

## About

I am a field technician at Hood Canal Communications, a rural fiber ISP in Mason County, Washington, where I work on fiber installations, ONT provisioning, mesh network deployments, and infrastructure support. I am completing a Bachelor of Science in Computer Science at Southern New Hampshire University, graduating July 2026.

My goal is to grow into a hybrid role where infrastructure knowledge and software development overlap. I want to be the person who understands the physical plant and can also build the tooling around it. That combination is where I think I can add the most value in telecom and utilities.

---

## Skills

**Frontend:** React, JavaScript, HTML, CSS, Vite  
**Backend:** Node.js, Express, REST API design  
**Database:** MongoDB, Mongoose, SQLite  
**Mobile:** Java, Android Studio  
**Tools:** Git, GitHub Pages, MongoDB Compass, Postman  
**Other:** Fiber splicing, ONT provisioning, Plume mesh networks, network diagnostics

---

## ePortfolio: StockTrack

StockTrack is the capstone artifact for CS 499. It started as an Android inventory management app built in Java for CS 360 and has been migrated into a full-stack web application across three enhancements.

### Enhancement One: Software Design and Engineering
Migrated the Android UI from Java and XML to a React web application. Each Android Activity was translated into a React component with hooks-based state management replacing lifecycle callbacks and RecyclerView adapter patterns. The SMS-based low-stock notification was replaced by a real-time alert banner. Frontend input validation was implemented before any data operation.

**Live App:** [jcarenza67.github.io/stocktrack-web](https://jcarenza67.github.io/stocktrack-web/)  
**Source Code:** [github.com/jcarenza67/stocktrack-web](https://github.com/jcarenza67/stocktrack-web)

### Enhancement Two: Algorithms and Data Structures
Added server-side search, multi-field sorting, and a priority-based low-stock alert algorithm to a Node/Express backend API. The search endpoint performs case-insensitive string matching across item name and category. Sort fields are validated against an allowlist to prevent query string injection. The low-stock endpoint computes a deficit score for each understocked item and returns them sorted by severity.

**Source Code:** [github.com/jcarenza67/stocktrack-api](https://github.com/jcarenza67/stocktrack-api)

### Enhancement Three: Databases
Replaced the original SQLite on-device storage with a MongoDB database accessed through a Mongoose schema layer. The Item schema enforces field types, required constraints, minimum value rules, and default values at the application layer. Input validation runs at both the route handler and Mongoose model layers. The MongoDB connection string is managed through environment variables and never hardcoded in source files.

**Source Code:** [github.com/jcarenza67/stocktrack-api](https://github.com/jcarenza67/stocktrack-api)

---

## Education

**Bachelor of Science, Computer Science**  
Southern New Hampshire University, expected July 2026

Relevant coursework: Software Design, Data Structures and Algorithms, Mobile Architecture, Full Stack Development, Database Management, Secure Coding, Software Testing

---

## Contact

[github.com/jcarenza67](https://github.com/jcarenza67)
