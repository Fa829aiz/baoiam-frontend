# folder structure of frontend (React + vite )

biom-frontend-only/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── App.jsx
│   └── main.jsx
├── index.html
├── package.json
├── vite.config.js
├── .eslintrc.cjs
└── README.md

# Explanation of Each File/Folder
1. `public/`
  Contains static assets and the `index.html` file used as the entry point during build. Vite injects your React app into this file.
2. `src/ `
  This is the  (source folder) containing all the React application code.
  3. `components/`  
    Contains (reusable UI componen), like buttons, navbar, footer, etc. These are small, modular parts of the UI.
4. `pages/`  
    Contains (ull page components) like Login Page , Dashboard page , HomePage, etc. Each file usually represents a route or a major screen.
5. `App.jsx`  
    The (main React component) that defines routes and includes the layout of the app. It acts as the root component.

6. `main.jsx` The (entry point) of the React app. This file renders the `<App />` component into the DOM using `ReactDOM.createRoot`.

7. `index.html`  
  The HTML template file inside `public/`. Vite injects your React code here. It contains a root `<div>` element.

8. `package.json`  
  Defines the project's metadata and lists all (dependencies) and (scripts) used. For example:
   `react`, `react-dom`, `vite`
   Scripts like `npm run dev`, `npm run build`, etc.

9. `vite.config.js`  
  The configuration file for (Vite). It can include plugin setups (like React plugin), alias paths, environment configs, etc.

10. `.eslintrc.cjs`  
  ESLint configuration file. It defines the (coding standards and rules) that help maintain clean and consistent code.

11. `README.md`  
  This file (you're reading now). It explains the (project structure, setup instructions), and technologies used.

12. # How to Run  React Frontend Project Locally
1. Make sure Node.js is installed.

2. Install all dependencies. 
 .Example Like: npm install

3. Start the React project  server:
. npm run dev 

# Application Flow (How the React App Works)
1. The entry point is `main.jsx` in the `src/` folder.
2. It renders the `<App />` component using `ReactDOM.createRoot`.
3. The `App.jsx` component defines the main layout and routing logic.
4. Components and pages are imported inside `App.jsx` as per requirement.
5. Based on routing or logic, the corresponding page/component is displayed on screen.

# Important Files and Their Roles
### `src/main.jsx`
- Entry point of the app.
- Mounts the React App into the HTML DOM (usually on a `div#root`).

### `src/App.jsx`
- Main component that wraps all other components/pages.
- Routing logic (if React Router is used) is defined here.
- Acts like a layout component.

### `src/components/`
- Contains reusable components like:
  - `Navbar.jsx`: Navigation bar at the top
  - `Footer.jsx`: Bottom footer
  - Any custom button, card, input field, etc.

### `src/pages/`
- Contains full-page components like:
  - `Login.jsx`: Login form for users
  - `Dashboard.jsx`: Main user dashboard
  - `HomePage.jsx`: Landing page
- Each file represents a major screen in the app.

### `index.html`
- Located in `public/` folder
- Vite injects your React app into the `<div id="root"></div>` inside this file


# Routing (If Used)

. The project uses `react-router-dom` for routing between pages.
. Routes are usually defined inside `App.jsx`.
. Example:

# Components Used in App.jsx File:
.react-router-dom: For routing (BrowserRouter, Routes, Route)

.AuthModal: Signup/Login modal that appears 5 minutes after the user lands

.ProtectedRoute: Custom route wrapper to restrict access to authenticated users

.Navbar: Navigation bar shown on all general pages

.ScrollToTop: Ensures scroll resets on route change

.localStorage: Used to avoid showing signup modal repeatedly

# Authentication & Modal Flow:
.App shows a Signup Modal (AuthModal) after 5 minutes if the user hasn't seen it before.

.Modal visibility is managed via localStorage:

.signupModalShown is used to check whether modal was shown.

.On successful login/signup (handleAuthSuccess), the modal is closed and isLoggedIn is set to true.


# Protected Routes:
Some routes are wrapped with a ProtectedRoute component to ensure that they are only accessible after login.

 {/*
    <Route
  path="/DataScience"
  element={
    <ProtectedRoute isLoggedIn={isLoggedIn}>
      <DataSciencePage />
    </ProtectedRoute>
  }
/>

*/ }


# Protected pages
. DataAnalysis

. /DataScience

. /DigitalMarketing

. /SoftwareDevelopment.

# Public Routes
Route Path             Component

/	                    HomePage
/pride	                 PridePage
/blogs	                  BlogSectionPage
/aboutUs                  	AboutUSPage
/contact_us	               ContactUs
/terms&conditions	       TermsAndConditions
/Privacy&Policy	           PrivacyPolicy
/refundPolicy	           RefundPolicy
/refer&earn	               ReferEarnPage (public version)
/referral	                ReferralPage
/instructor              	Instructor
/GCEP	                    GcepPage
/Udaan90                 	Udaan90
/Successfusion	           SuccessFusion
/AIML	                     AIML
/PAP                      	Pap_Page


 # Nested Routing:
 .There's a nested <Routes> block inside the "*" (catch-all) route. It contains most of the public routes along with the Navbar and AuthModal.
 .
 <Route path="*" element={ ... }>
  <Navbar />
  <AuthModal />
  <Routes>
    ... all public routes ...
  </Routes>
</Route>


# src folder structure
src/
├── App.jsx
|---assets
├── components/
│   ├── Home/
│   ├── Blogs/
│   ├── Auth/
│   ├── ScrollToTop.jsx
│   ├── Footer/
│   └── ...
├── Pages/
│   ├── ContactForm.jsx
│   ├── TermsAndConditions.jsx
│   ├── PrivacyPolicy.jsx
│   ├── RefundPolicy.jsx
│   ├── Refer&Earn/
│   ├── KickstartCourses/
│   └── ...
├── routes/
│   └── ProtectedRoute.jsx
└── ...
