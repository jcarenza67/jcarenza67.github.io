# Joseph Wilfong

Field Technician | Software Developer | Computer Science, SNHU

Shelton, Washington · [GitHub](https://github.com/jcarenza67)

---

## Contents

- [Professional Self-Assessment](#professional-self-assessment)
- [About](#about)
- [Skills](#skills)
- [Code Review](#code-review)
- [ePortfolio: StockTrack](#eportfolio-stocktrack)
  - [Original Artifact](#original-artifact)
  - [Enhancement One: Software Design and Engineering](#enhancement-one-software-design-and-engineering)
  - [Enhancement Two: Algorithms and Data Structures](#enhancement-two-algorithms-and-data-structures)
  - [Enhancement Three: Databases](#enhancement-three-databases)
- [Education](#education)
- [Contact](#contact)

---

## Professional Self-Assessment

I started the Computer Science program at SNHU thinking I would end up as a straightforward software engineer. Somewhere in the middle of the program, I landed a field technician job at a local telecommunications company, and that changed the direction of what I am aiming for. I'm not trying to leave the infrastructure side of things. I just want to grow into a hybrid role that combines hands-on fieldwork with building the internal tools and systems that make that fieldwork better. This program, and this capstone in particular, has been the proof of concept for that goal.

**Collaborating in a Team Environment**

A lot of my coursework has been independent, but the collaboration skills I've built come just as much from my job as from group discussion posts. At my company I built a bulk scanner for our mesh system so we could see diagnostics across our customers' home networks, and I built it with my boss's workflow in mind. That meant thinking about who else would use the tool, not just whether it worked for me. I've also leaned on classmates for things outside my comfort zone, like Angular conventions in CS 465, where peer tips filled gaps that documentation alone didn't cover. Both experiences taught me the same lesson: code that only makes sense to the person who wrote it isn't finished.

**Communicating with Stakeholders**

Translating technical problems for non-technical people is most of my job. I've walked customers through network issues that took real digging to diagnose, like a two-year-old WiFi interference problem I eventually traced to a competing signal from a pet GPS collar base station, without burying them in radio frequency jargon. That same instinct carries over into how I write documentation and narratives for this program. I've learned to explain what a system does and why it matters before getting into how it works, which is a skill that matters just as much in a code review as it does standing on someone's porch explaining why their internet was slow.

**Data Structures and Algorithms**

My coursework in data structures and reinforcement learning, including building a deep Q-learning agent in CS 370, gave me a foundation to reason about efficiency and trade-offs rather than just getting code to run. That shows up directly in this capstone's algorithm enhancement, where I built a deficit-scoring prioritization system instead of a basic sort, because the actual goal was surfacing the most urgent low-stock items instead of just listing them.

**Software Engineering and Database**

CS 465 had me build a full MEAN stack application from scratch, including a Mongoose-backed MongoDB database and a complete Angular SPA admin interface. That project and this capstone's database enhancement both pushed me to think about schema design, validation, and the separation between data, API, and UI layers, rather than treating a database as just a place to dump information.

**Security**

Security mindset is something I've had to build deliberately rather than something that came naturally. Working through input validation, environment-based credential management, and layered validation between routes and models on this capstone forced me to think like someone trying to break the system. That mindset now shapes how I think about credential handling and provisioning security at my actual job, not just in my coursework.

**Summary**

The three artifacts in this ePortfolio are all the same app, StockTrack, an Android inventory app I originally built in CS 360, taken through three different lenses: a full UI migration to React for software design and engineering, a server-side search and prioritization algorithm for algorithms and data structures, and a MongoDB-backed REST API for databases. I chose one artifact across all three categories on purpose, to show that a single piece of software can be evolved end to end rather than patched in isolated pieces. The code review below walks through where StockTrack started, and the narratives that follow explain what changed and why. Together, they're the clearest evidence I have that I can take on the kind of technical and development role I am working toward.

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

## Code Review

**Video:** [Code review walkthrough](https://youtu.be/jvoiPf4G50s)

This walkthrough covers the original StockTrack codebase before any enhancements: existing functionality, an analysis of where the code fell short (single-device storage, no search or prioritization logic, no API layer, default styling), and the plan for each of the three enhancements below.

---

## ePortfolio: StockTrack

StockTrack is the capstone artifact for CS 499. It started as an Android inventory management app built in Java for CS 360 and has been migrated into a full-stack web application across three enhancements.

### Original Artifact

**Source Code:** [github.com/jcarenza67/CS-360](https://github.com/jcarenza67/CS-360)

This is the StockTrack app as originally submitted in CS 360: Java, Android Studio, a local SQLite database, a RecyclerView for displaying inventory, full CRUD operations, and an SMS-based low-stock notification with graceful permission degradation. Each enhancement below starts from this codebase.

### Enhancement One: Software Design and Engineering

**Live App:** [jcarenza67.github.io/stocktrack-web](https://jcarenza67.github.io/stocktrack-web/) (login with `demo` / `demo`)
**Source Code:** [github.com/jcarenza67/stocktrack-web](https://github.com/jcarenza67/stocktrack-web)

**Artifact Description**

The artifact is StockTrack, an Android inventory management app I built in CS 360. The original app was written in Java using Android Studio. It used a local SQLite database for data persistence, a RecyclerView for displaying inventory items, full CRUD operations for managing items, and an SMS-based low-stock notification system with graceful permission degradation if the user denied SMS access.

**Justification for Inclusion**

I selected StockTrack because it was the most complete, layered application I built in school, and it gave me a meaningful starting point for all three enhancement categories. For this enhancement specifically, I migrated the Android UI layer from Java and XML into a React web app. The result is a browser-accessible inventory management system that improves on the original in deployability, accessibility, and usability without being tied to a single Android device.

The components that showcase my skills are the React component architecture, state management using hooks, and the frontend input validation system. Each major screen from the Android app maps to a React component. LoginActivity became Login.jsx. MainActivity and InventoryAdapter became Dashboard.jsx. The add and edit dialog became ItemForm.jsx. SmsSettingsActivity and SmsHelper were replaced entirely by an always-visible low-stock alert banner that displays in real time as quantities drop below their thresholds, which is a better fit for a web context than SMS notifications tied to a phone number.

State management in the original app relied on Android lifecycle callbacks and RecyclerView adapter patterns. In the React version, all of that is handled with `useState` and `useMemo` hooks. The low-stock items list, the search filter, and the display list are all derived state computed from a single source, which is cleaner and easier to reason about than the original approach.

Input validation was applied on the frontend before any data operation, which mirrors the graceful degradation approach used for SMS permissions in the original app. The ItemForm component validates that item name is present, quantity is a non-negative number, and threshold is a non-negative number before allowing a save, and surfaces inline error messages next to the problem fields rather than relying on Toast messages like in the Android version. The login credentials are currently handled as a frontend placeholder since there's no backend yet at this stage.

The visual design was also a deliberate part of the enhancement. The original app used a basic green and white Material Design theme, which was functional but not something I wanted to put in a professional portfolio. The React version uses a dark industrial aesthetic with a monospace font system, an amber accent color, and a grid-pattern login background. The design language was chosen to reflect the kind of internal tooling a technical operations team would actually use, which is consistent with the career direction I describe in my self-assessment above. A portfolio piece should look like something built intentionally, not a default template.

**Course Outcomes**

This enhancement addresses the outcomes I planned in Module One. I demonstrated the ability to use well-founded and innovative techniques by translating an Android architecture into a modern React component structure and making deliberate decisions about where patterns needed to change versus where they could carry over directly. I addressed the security outcome by implementing frontend input validation as the first line of defense against malformed data before it reaches the backend. The professional communications outcome is addressed through this narrative and the code review above.

My outcome coverage plan from Module One didn't need any updates. The plan I submitted holds up against what I actually built.

**Reflection**

The most useful thing I learned during this enhancement was how to think about architectural translation rather than direct porting. The temptation when migrating from Android to React is to try and reproduce the original structure one-to-one, but Android's Activity lifecycle and RecyclerView adapter patterns don't have direct React equivalents. I had to step back and ask what each piece was doing, then figure out the right React way to accomplish the same thing. That reframing was more valuable than just knowing React syntax.

The main challenge I ran into was a React hook warning related to calling `setState` inside a `useEffect`, which I had used to populate the ItemForm when editing an existing item. The fix was to initialize the form state lazily using an initializer function passed to `useState`, which reads the item prop at mount time instead of syncing it through an effect. It's a small thing, but it reflected a real gap in my understanding of when effects are appropriate versus when state initialization is the right tool.

Getting the app deployed to GitHub Pages also required debugging a base path issue where the built assets were returning 404s. The fix was setting the `base` field in `vite.config.js` to match the repo name, which tells Vite to prefix all asset paths correctly for the subdirectory the app is served from. That's the kind of deployment detail that doesn't always come up in school exercises.

### Enhancement Two: Algorithms and Data Structures

**Source Code:** [github.com/jcarenza67/stocktrack-api](https://github.com/jcarenza67/stocktrack-api)

**Artifact Description**

The artifact is StockTrack, an Android inventory management app I built in CS 360. The original app was written in Java using Android Studio. It used a local SQLite database for data persistence, a RecyclerView for displaying inventory items, and full CRUD operations for managing items. The low-stock notification system was a flat binary trigger: if any item dropped below a hardcoded threshold, an SMS was sent out. There was no search capability, no sort control, and no prioritization of alerts.

**Justification for Inclusion**

I selected StockTrack for this enhancement because the original app had almost no algorithmic logic worth calling out. Items loaded in insertion order and stayed there. The low-stock check was a single boolean comparison with no intelligence behind it. This enhancement adds three meaningful algorithmic features to a Node/Express backend API, which is also the foundation for the MongoDB integration in Enhancement Three.

The first feature is server-side search. The `GET /api/items` endpoint accepts an optional search query parameter and filters the item list using case-insensitive string matching across both the name and category fields. This runs on the server rather than the client, which keeps the React frontend lightweight and makes the search composable with the other parameters.

The second feature is multi-field sorting. The same endpoint accepts `sortBy` and `order` params. The `sortBy` value is validated against an allowlist of permitted fields before it's used, which prevents query string injection through that parameter. Sorting supports ascending and descending order across name, category, and quantity.

The third feature is the priority-based low-stock alert algorithm. The `GET /api/items/low-stock` endpoint filters items to those below their threshold and then computes a deficit score for each one by subtracting the current quantity from the threshold. The results are sorted by deficit score descending, so the most critically understocked items surface first rather than returning a flat, unordered list. This is a direct improvement over the original SMS trigger, which had no concept of severity.

**Course Outcomes**

This enhancement addresses the algorithmic thinking and computing solutions outcomes from Module One. The search and sort logic demonstrates my ability to design composable query processing that handles real-world use cases cleanly. The deficit-scoring algorithm demonstrates my ability to translate a practical problem into a computable solution and evaluate the trade-offs involved, in this case choosing server-side processing over client-side filtering to keep the frontend separate from the business logic. The input validation on query parameters addresses the security outcome. The sort field allowlist is a direct defense against a user passing an arbitrary field name through the query string to probe the data structure.

My outcome coverage didn't need any updates.

**Reflection**

The most valuable thing I learned during this enhancement was how to think about API design as its own discipline. It's easy to treat a backend as just a data pipe, but the decisions you make about how parameters are accepted, validated, and composed have a real impact on how useful and secure the API actually is. Choosing to run search and sort on the server side rather than the frontend required me to reason about where logic belongs in a layered architecture.

The deficit-scoring algorithm was straightforward to implement but required thinking through edge cases. An item with zero quantity and a threshold of one has a deficit score of one. An item with zero quantity and a threshold of twenty has a deficit score of twenty. Sorting by that score descending means the most critically understocked item always shows at the top regardless of what the threshold values are across other items, which is what makes the alert useful in a real warehouse.

The main challenge was making sure search, sort, and filter could be combined in any order without breaking each other. The solution was to treat them as sequential pipeline steps on the same array: filter first, then search, then sort, which kept everything clean and predictable regardless of what parameters were set.

### Enhancement Three: Databases

**Source Code:** [github.com/jcarenza67/stocktrack-api](https://github.com/jcarenza67/stocktrack-api)

**Artifact Description**

The artifact is StockTrack, an Android inventory management app I built in CS 360. The original app was written in Java using Android Studio. It used a local SQLite database for data persistence, a RecyclerView for displaying inventory items, and full CRUD operations for managing items. The low-stock notification system was a flat binary trigger: if any item dropped below a hardcoded threshold, an SMS was sent out. There was no search capability, no sort control, and no prioritization of alerts.

**Justification for Inclusion**

I selected StockTrack for this enhancement because replacing SQLite with MongoDB represents a complete architectural shift in how the app handles data. The original database was embedded in the Android app itself. The new database is a proper server-side MongoDB instance accessed through a Node/Express REST API with Mongoose handling the schema model and validation. That's a completely different approach to data persistence, and it directly demonstrates the database skills this category is looking for.

The Mongoose schema is the first thing worth calling out. MongoDB is schema-flexible by default, which means nothing stops bad data from being stored if structure isn't enforced at the application layer. The Item schema defines field types, required constraints, minimum value rules, trim behavior on strings, and default values for optional fields. This means a document can't be saved without a name, can't have a negative quantity, and will always have a category and threshold even if the client doesn't set them. That enforcement lives at the model layer regardless of which route is called.

Input validation runs at two layers. The route handlers check incoming request data before it ever reaches Mongoose, returning a 400 with a clear error message if required fields are missing or values are out of range. Mongoose then runs its own validation as a second check when the document is saved. This layered approach means malformed or malicious data has two chances to get caught before it touches the database.

The MongoDB connection string is stored in a `.env` file and loaded through `dotenv`. It's never hardcoded in any source file, and `.gitignore` excludes the `.env` file from version control. This is standard secure configuration management, and it means credentials can't be accidentally exposed in a public repository.

The REST API routes map cleanly to CRUD operations. GET retrieves items with optional search, sort, and filter parameters carried over from Enhancement Two. POST creates a new item. PUT updates an existing item by its MongoDB ObjectId after validating the ID format with a regex check. DELETE removes an item by ID. Every route handles errors explicitly and returns meaningful status codes rather than just crashing.

**Course Outcomes**

This enhancement completes the outcome coverage I planned in Module One. The database design and Mongoose schema work addresses the computing solutions outcome by demonstrating the ability to enforce data consistency in a schema-flexible environment. The input validation at both the route and model layers addresses the security outcome, specifically the requirement to anticipate adversarial exploits and mitigate design flaws before data reaches storage. The environment-based credential management closes out the secure configuration piece noted as pending in earlier milestones. With this enhancement, all three layers of the stack are in place, and all five course outcomes have been addressed across all three enhancements.

**Reflection**

The most important thing I learned during this enhancement was the difference between relying on the database to enforce consistency versus building that enforcement into the app layer. MongoDB will happily store anything thrown at it if you let it. Mongoose schemas are how you prevent that, and writing the schema meant thinking carefully about what the data actually needs to look like and what should happen when it doesn't match. That's why it's worth knowing the trade-offs between schema flexibility and data integrity.

The Node version caused the most friction during this enhancement. Mongoose 7 requires Node 18 or higher, but my environment is pinned to Node 16 because CS 465 requires it. Downgrading to Mongoose 6 resolved the compatibility issue without having to change any app logic, but it was a good reminder that dependency management is a real concern in a multi-project environment and that pinning versions has consequences that show up at unexpected times.

One thing I would do differently for the ePortfolio version is migrate from a local MongoDB instance to MongoDB Atlas so the API can be hosted on a platform and accessed from anywhere. The current setup requires a local MongoDB install to run, which limits who can actually test it out. That's not a problem for this code submission, but it's something I've been thinking about.

---

## Education

**Bachelor of Science, Computer Science**
Southern New Hampshire University, expected July 2026

Relevant coursework: Software Design, Data Structures and Algorithms, Mobile Architecture, Full Stack Development, Database Management, Secure Coding, Software Testing

---

## Contact

[github.com/jcarenza67](https://github.com/jcarenza67)
