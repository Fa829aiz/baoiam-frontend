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


**************************************************************************************************************


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


**********************************************************************
# src folder
src/ Directory

This is the main source folder containing all the core logic and components of the project. It includes multiple feature-specific folders, each responsible for a different part of the application. The structure is organized in such a way that developers can easily navigate and understand the responsibilities of each section


# src/assets folder
src/assets/

The assets folder inside src is dedicated to storing all static resources used across the project — primarily images, icons, and sometimes fonts or other media files. Organizing images in this centralized location helps in reusing assets across components and maintaining consistency in the UI.

You’ll find images categorized (if applicable) for better accessibility.

Any shared media used across different parts of the application is placed here to avoid duplication.

This approach also helps in keeping non-logic files separate from the actual business logic or UI components


************************************************************************************************************
# src/components/Auth/AuthModal.jsx (AuthModal.jsx is a file name of react js )

 # Code Explanation – Line by Line (React Auth Modal)

  1. Imports – Required Libraries
import { FaEye, FaEyeSlash } from "react-icons/fa";
import { IoClose } from "react-icons/io5";
import { useState } from "react";
import { GoogleOAuthProvider, GoogleLogin } from "@react-oauth/google";
import { API_ENDPOINTS } from "../../Config/api";
FaEye, FaEyeSlash: OTP input mein password show/hide icon ke liye.

.IoClose: Modal band karne ke cross icon ke liye.

.useState: React ka hook – state banane ke liye.

.GoogleOAuthProvider, GoogleLogin: Google login integrate karne ke liye.

.API_ENDPOINTS: Alag-alag backend APIs ke URLs import kiye gaye hain.

2. Component Start
.const AuthModal = ({ isOpen, onClose, onAuthSuccess }) => {}

.AuthModal ek React functional component hai.

.Props:
    .isOpen: Modal dikhana hai ya nahi.
   .onClose: Modal close karne ke liye function.
    .onAuthSuccess: Jab login/signup success ho jaye to kya karna hai.

3. React States

const [isLogin, setIsLogin] = useState(false);        // Login or Signup
const [showOtp, setShowOtp] = useState(false);        // OTP visible ya hidden
const [email, setEmail] = useState("");               // User email/mobile
const [otp, setOtp] = useState("");                   // OTP value
const [isOtpSent, setIsOtpSent] = useState(false);    // OTP bheja gaya ya nahi
const [agreeTerms, setAgreeTerms] = useState(false);  // Terms accept kiye ya nahi
const [loading, setLoading] = useState(false);        // Loading indicator

4. Modal Close Condition
if (!isOpen) return null;
Agar modal ka isOpen = false ho, to kuch bhi render mat karo.

5. Toggle Login/Signup Mode

const toggleMode = () => {
  setIsLogin(!isLogin);
  setShowOtp(false);
  setIsOtpSent(false);
  setEmail("");
  setOtp("");
};
.Login aur Signup mode switch karne ke liye.

.Saare inputs reset kiye ja rahe hain.

6. Send OTP Function
const handleSendOtp = async () => {
  setLoading(true);
  const endpoint = isLogin ? API_ENDPOINTS.LOGIN : API_ENDPOINTS.SIGNUP;

  try {
    const response = await fetch(endpoint, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ email }),
    });

    const data = await response.json();
    if (response.ok) {
      alert(data.message);
      setIsOtpSent(true);
    } else {
      alert(data.error || "Failed to send OTP.");
    }
  } catch (err) {
    alert("Something went wrong. Please try again.");
    console.error(err);
  } finally {
    setLoading(false);
  }
};

.OTP bhejne ka kaam karta hai.

.Agar isLogin = true, to login OTP API call hoti hai.

.Agar isLogin = false, to signup OTP API call hoti hai.

.Agar success ho gaya, to OTP input enable ho jata hai.

7. Verify OTP Function
const handleVerifyOtp = async () => {
  setLoading(true);
  const endpoint = isLogin ? API_ENDPOINTS.VERIFY_LOGIN : API_ENDPOINTS.VERIFY_SIGNUP;

  try {
    const response = await fetch(endpoint, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ email, otp }),
    });

    const data = await response.json();
    if (response.ok) {
      alert(data.message);

      if (data.tokens) {
        localStorage.setItem("access", data.tokens.access);
        localStorage.setItem("refresh", data.tokens.refresh);
      }

      if (onAuthSuccess) onAuthSuccess();
      onClose && onClose();
    } else {
      alert(data.error || "Invalid OTP");
    }
  } catch (err) {
    alert("Something went wrong. Please try again.");
    console.error(err);
  } finally {
    setLoading(false);
  }
};
OTP verify karta hai.

Agar OTP valid ho, to backend JWT tokens return karta hai, jo localStorage mein store hote hain.

Auth success hone par modal close hota hai.

🔽 8. Google Login Handler
js
Copy code
const handleGoogleLogin = async (credentialResponse) => {
  const credential = credentialResponse.credential;
  try {
    const res = await fetch(API_ENDPOINTS.GOOGLE_LOGIN, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ id_token: credential }),
    });

    const data = await res.json();

    if (res.ok) {
      if (data.tokens) {
        localStorage.setItem("access", data.tokens.access);
        localStorage.setItem("refresh", data.tokens.refresh);
      } else if (data.token) {
        localStorage.setItem("access", data.token);
      }

      alert(data.created
        ? "🎉 Welcome! Your account has been created with Google."
        : "👋 Welcome back! Logged in successfully.");

      if (onAuthSuccess) onAuthSuccess();
      onClose && onClose();
    } else {
      console.error("Google login failed:", data);
    }
  } catch (err) {
    console.error("Google login error:", err);
  }
};
Google login ke credential ko backend bhejta hai.

Backend token return karta hai jo localStorage mein store hota hai.

Modal close hota hai aur success message aata hai.

9. Return JSX – UI Design

return (
  <div className="fixed inset-0 z-[999] ...">
    {/* Background Black Overlay */}
    <div className="absolute inset-0 bg-black opacity-50" onClick={onClose}></div>

    {/* Modal Box */}
    <div className="relative z-10 bg-white rounded-2xl ...">
      {/* Close Button */}
      <button onClick={onClose}>
        <IoClose />
      </button>

      {/* Heading */}
      <h2>Welcome to Baoiam</h2>
      <h1>{isLogin ? "Log In" : "Sign Up"}</h1>

      {/* Email Input */}
      <input value={email} onChange={(e) => setEmail(e.target.value)} />

      {/* OTP Input */}
      <button onClick={handleSendOtp}>{isOtpSent ? "Resend OTP" : "Send OTP"}</button>
      <input value={otp} type={showOtp ? "text" : "password"} />
      <button onClick={() => setShowOtp(!showOtp)}>{showOtp ? <FaEyeSlash /> : <FaEye />}</button>

      {/* Terms Checkbox (Signup only) */}
      {!isLogin && <input type="checkbox" checked={agreeTerms} onChange={(e) => setAgreeTerms(e.target.checked)} />}

      {/* Submit Button */}
      <button onClick={handleVerifyOtp}>
        {isLogin ? "Log In" : "Sign Up"}
      </button>

      {/* Switch Login/Signup */}
      <p>{isLogin ? "Don't have an account? Sign Up" : "Already have an account? Log In"}</p>

      {/* Divider */}
      <div>Or continue with</div>

      {/* Google Login */}
      <GoogleOAuthProvider clientId="...">
        <GoogleLogin onSuccess={handleGoogleLogin} />
      </GoogleOAuthProvider>
    </div>
  </div>
);

# Summary – Kya Kya Karta Hai Ye Component?
| Feature             | Description                                                |
| ------------------- | ---------------------------------------------------------- |
| Login/Signup Switch | Ek hi modal se dono functionality                          |
| Email Input         | User se email ya phone input leta hai                      |
| OTP Send/Verify     | OTP bhejna aur verify karna                                |
| Google Login        | Google OAuth se login                                      |
| JWT Store           | Access/refresh token localStorage mein store karta hai     |
| Modal UI            | Fully responsive and styled modal with close functionality |

**********************************************
# src/component/Blog/BlogCard1.jsx 
****   BlogCard1 Component is a function     **** 
1. Imports
import React from "react";
import { FaClock, FaEye, FaFacebook, FaTwitter, FaPinterest, FaHome } from "react-icons/fa";
import { FiBarChart2 } from "react-icons/fi";
import blogImg from "../../assets/Pride/Blogs/blog15.png"; 
import img1 from "../../assets/Pride/Blogs/img11.png";
import { Link } from "react-router-dom";


What this does:

Imports required icons from react-icons.

Imports 2 images: one for the blog hero (blogImg), one for background (img1).

Link is imported from react-router-dom for navigation.
2. Component Definition

const BlogCard1 = () => {}


This is a React functional component named BlogCard1.
3. Container

<div className="min-h-screen bg-white text-[#333]">


Full-screen white background.

Text color is dark gray.

4. Top Navigation Bar

<nav style={{ backgroundImage: `url(${img1})` }} className="...">
  <div className="bg-black/40 px-4 py-4 ">
    <div className="flex items-center justify-between ">
      <Link to="/">
        <FaHome className="text-2xl cursor-pointer" />
      </Link>
      <h1 className="text-2xl font-semibold">Blogs</h1>
      <div></div>
    </div>
  </div>
</nav>


What this does:

Adds a top navbar with:

A background image (img1)

Home icon (clickable, navigates to homepage)

Page title: Blogs

5. Blog Hero Section

<div className="max-w-[1100px] mx-auto mt-20 rounded-xl overflow-hidden shadow-md">


Big featured blog card with:

Blog main image (blogImg)

Blog title and subheading

Author and metadata:

Author name

Read time

Views

Share icons (Facebook, Twitter, Pinterest) with share count

<img src={blogImg} />
<h1>Blog title</h1>
<p>Sub heading</p>

<span>by Tanishka Bajpai</span>
<span><FaClock /> 10 minute read</span>
<span><FiBarChart2 /> 11.6K views</span>
<span><FaFacebook /> <FaTwitter /> <FaPinterest /> 1.2K shares</span>

6. Blog Content

<div className="max-w-[1050px] mx-auto font-poppins py-10 text-base text-justify px-6 leading-relaxed">


Main blog text/content with paragraphs.

Content is about:

Non-binary students

How schools/colleges need to go beyond just saying they’re inclusive

<p>More people are finally talking about gender identity...</p>
<p>For non-binary students, the answer is often no...</p>

 7. Export Component
export default BlogCard1;


Makes this component available to use in other files.

| Section          | Purpose                                                           |
| ---------------- | ----------------------------------------------------------------- |
| **Imports**      | Icons, images, routing                                            |
| **Navbar**       | Top bar with Home icon and title                                  |
| **Hero Section** | Big blog image, title, subheading, author info, read time, shares |
| **Content**      | Paragraphs explaining the blog topic                              |
| **Design**       | Uses Tailwind CSS for spacing, layout, and responsiveness         |

*********************************************************
#  scr/components/Blogs/BlogCart3.jsx

BlogCard3 Component 

1. Imports
import React from "react";
import img1 from "../../assets/Pride/Blogs/img1.png"; 
import img2 from "../../assets/Pride/Blogs/img2.png";


React is imported to use JSX.

Two images (img1 and img2) are imported from the assets folder.

These images will be shown at the bottom of the blog card.

 2. Component Declaration
const BlogCard3 = () => {}


This declares a React functional component named BlogCard3.

 3. Container Div is contain another html element
<div className="max-w-[980px] bg-white rounded-xl shadow-md p-6 mb-10 mx-auto space-y-4">


Main container:


# it is taiwind css class name and styling a function components
max-w-[980px]: max width

bg-white: white background

rounded-xl: rounded corners

shadow-md: shadow effect

p-6: padding inside

mb-10: margin bottom

mx-auto: center horizontally

space-y-4: vertical spacing between children

 4. Blog Title
<h2 id="section-1" className="px-2 text-orange-500 text-2xl font-semibold">
  Everyday Systems Speak Louder Than Statements
</h2>


Title of the blog section.

id="section-1" is added (maybe for anchor links).

Styled with:

Padding

Orange text

Font size 2xl

Bold font

5. Blog Paragraphs
<p className="...">
  There are the obvious things. Forms that only give “male” and “female” options...
</p>


There are three <p> tags, each containing a paragraph of the blog.

Each paragraph:

Is text-justified

Has max width

Uses a standard font size and line height

Uses a consistent dark text color (#121416)

These paragraphs explain:

Obvious issues in gendered systems (like forms, bathrooms).

Small but repetitive issues (e.g., “girls and boys” announcements).

The mental toll of not feeling included in everyday systems.

6. Images Section
<div className="grid grid-cols-2 gap-2 pt-2 px-10">
  <img src={img1} ... />
  <img src={img2} ... />
</div>


A 2-column grid layout that shows 2 images side by side.

Each image:

Uses img1 and img2 sources.

Is responsive with fixed width.

Has rounded-md corners.

 7. Export the Component
export default BlogCard3;


This allows the component to be used in other files.

8. Summary Table
Section	What it Does
Imports	React, 2 images from assets
Component	Defines a reusable blog section card (BlogCard3)
Title	Displays section heading in orange
Paragraphs	Explains real-world gender identity challenges in schools
Images	Two images displayed in a responsive grid
Export	Makes the component available for use elsewhere


************************************

#  scr/components/Blogs/BlogCart4.jsx
.BlogCard4 Component – Explanation (Line by Line)

1. Imports
    import React from "react";


      Importing React to use JSX and create a functional component.

 2. Component Declaration
          const BlogCard4 = () => {}


           Declares a functional component named BlogCard4.

 3. Main Container Div
          <div className="max-w-[980px] bg-white rounded-xl shadow-md p-6 mb-10 mx-auto space-y-4">


          This is the main wrapper for the blog section.

          max-w-[980px]: Maximum width of the card

           bg-white: White background

           rounded-xl: Rounded corners

          shadow-md: Subtle shadow for card look

            p-6: Padding inside

            mb-10: Margin at the bottom

            mx-auto: Center align horizontally

             space-y-4: Space between child elements

 4. Blog Title
             <h2 id="section-2" className="px-2 text-orange-500 text-2xl font-semibold">
              Start With Listening and Really Mean It
              </h2>


               h2: Heading for this blog section

                  id="section-2": Can be used for anchor navigation

                  Text is styled:

                    Orange color

                     Font size: 2xl

                      Bold

 5. Paragraph 1
                    <p className="mx-auto max-w-3xl text-[16px] text-justify teaxt-[#121416]">
                    So, what can be done? First, listen.
                    </p>


                     Short paragraph prompting the first step toward inclusion — listening.

                   Note: You have a small typo in the class: teaxt-[#121416] should be text-[#121416]

 6. Paragraph 2
                 <p className="mx-auto max-w-3xl text-jutify text-[#121416] text-[16px] leading-relaxed">
                Not just to pretend. Not as a token gesture during Pride Month...
                 </p>


                Emphasizes genuine listening to non-binary students — not just performative.

 7. Paragraph 3
                <p className="mx-auto max-w-3xl text-justify text-[#121416]">
                 That starts with giving students a space where they can speak openly...
                   </p>


                     Explains the need for safe, open spaces for non-binary students to share experiences, even if it's uncomfortable tohear.

                    Highlights the importance of empathy and acknowledgment of trauma.

 8. Export the Component
                  export default BlogCard4;


                    Exports BlogCard4 so it can be imported and used in other parts of the app.

# Summary Table
                         Section    |	 Purpose
                                    |
                        Imports     |    Section heading with orange style
                      Paragraph     |    Educates on the importance of truly listening to non-binary students
                       Styling	    |    Uses Tailwind CSS for layout, colors, spacing, typography
                       Export       |	   Makes the component usable elsewhere 

# What This Blog Section Talks About

                         This section ("Start With Listening and Really Mean It") encourages schools and colleges to:

                        Genuinely listen to non-binary students

                         Create safe spaces to share their experiences

                        Accept that feedback might be hard to hear, but it's necessary for change


 *************************************************************************
 # src/componenets/Blogs/BlogCart6.jsx 

***** BlogCard6 Component – Code Explanation ******

1. Import React
           import React from "react";


            React is imported so you can use JSX and define components.

 2. Component Declaration
              const BlogCard6 = () => {}


            A functional React component named BlogCard6 is declared.

            It will return a styled blog content section.

 3. Main Container Div
            <div className="max-w-[980px] font-poppins bg-white rounded-xl shadow-md p-6 mb-10 mx-auto space-y-4">


          This is the main wrapper of the blog card.

          max-w-[980px]: Sets the maximum width of the card.

          font-poppins: Uses the Poppins font for text.

         bg-white: White background color.

          rounded-xl: Rounded corners.

         shadow-md: Shadow around the box.

         p-6: Padding inside the box.

         mb-10: Margin bottom for spacing from the next element.

          mx-auto: Centers the box horizontally.

         space-y-4: Adds vertical spacing between child elements inside.

 4. Blog Title
         <h2 id="section-3" className="text-orange-500 px-2 text-2xl font-semibold">
         Fixing the Basics Isn’t Optional
        </h2>


            This is the section heading/title of this blog part.

          id="section-3": Used for anchor linking or scrolling to this section.

         Styled with:

          Orange text

          Padding on x-axis (px-2)

          Font size 2xl

          Bold text (font-semibold)

 5. First Paragraph
             <p className="mx-auto max-w-3xl text-justify text-[#121416] text-[16px] leading-relaxed">
              It’s also about changing what’s within the school’s control...
             </p>

 
             Talks about system-level changes schools should make, such as:

              Forms that include more gender options.

               Databases and ID systems that support name and pronoun changes.

              Reducing bureaucratic barriers for non-binary or trans students.

# Styling  tailwind css is a utility classes  it is framwork of css it is pre define classes :

                text-justify: Aligns text evenly on both sides.

                text-[#121416]: Dark gray/black color.

                text-[16px]: Font size.

                leading-relaxed: Line spacing for better readability.

 6. Second Paragraph
              <p className="mx-auto max-w-3xl text-justify text-[#121416] text-[16px] leading-relaxed">
                And yes, restrooms matter...
                  </p>
     

                   Focuses on the importance of accessible gender-neutral restrooms:

                One hidden restroom isn’t enough.

              They should be easy to find, inclusive, and treated as normal, not “special exceptions”.

              Same styling is applied as in the first paragraph for consistent look and readability.

 7. Export the Component
              export default BlogCard6;


              Makes this component reusable in other parts of the React app (e.g., blog page).

# Summary
| Section         | Description                                                          |
| --------------- | -------------------------------------------------------------------- |
| **Imports**     | React is imported for JSX use                                        |
| **Main Div**    | A styled white card with padding, shadow, and spacing                |
| **Title**       | Blog section title: *"Fixing the Basics Isn’t Optional"*             |
| **Paragraph 1** | Talks about improving forms, systems, and pronoun support in schools |
| **Paragraph 2** | Emphasizes proper restroom access for gender inclusivity             |
| **Export**      | Makes the `BlogCard6` component usable in the rest of the app        |

******************************************
# src/components/Blogs/BlogCart7.jsx

** BlogCard7 Component — Full Code Explanation **
1. Imports
import React from "react";
import img1 from "../../assets/Pride/Blogs/img18.jpg"; 


React is imported so you can write JSX.

img1 is imported — this is the image shown at the bottom of the blog card (e.g., a pride-related image).

 2. Function Declaration
const BlogCard7 = () => {}


A React functional component named BlogCard7 is created.

It returns JSX that represents one section of a blog article.

 3. Main Container Div
<div className="max-w-[980px] font-poppins text-justify bg-white rounded-xl shadow-md p-6 mb-10  mx-auto space-y-4">


This div wraps the entire blog card content and applies Tailwind CSS styles:

max-w-[980px]: Limits width of the content

font-poppins: Uses the Poppins font

text-justify: Justifies paragraph text

bg-white: White background

rounded-xl: Rounded corners

shadow-md: Adds a soft shadow for elevation

p-6: Padding inside

mb-10: Bottom margin to create space below

mx-auto: Centers it horizontally

space-y-4: Adds vertical space between child elements

 4. Section Title
<h2 id="section-4" className="px-2 text-orange-500 text-2xl font-semibold">
  Culture Can’t Be Faked
</h2>


This is the title of the blog section.

id="section-4": Useful for anchor links or scrolling to this section

text-orange-500: Orange-colored text

text-2xl: Font size

font-semibold: Bold style

px-2: Horizontal padding

 5. Paragraph 1
<p className=" mx-auto max-w-3xl  text-[#121416] text-[16px] leading-relaxed">
  Policies matter, no doubt, but they are just the starting point...
</p>


This paragraph discusses:

Policies alone aren’t enough.

If the environment is still unwelcoming or people are disrespectful, then changes on paper feel meaningless.

Styling:

text-[#121416]: Dark text

text-[16px]: Font size

leading-relaxed: Increases line spacing for readability

text-justify: Aligns text evenly on both sides

 6. Paragraph 2
<p className=" mx-auto max-w-3xl text-[#121416] text-[16px] leading-relaxed">
  Inclusion doesn’t live in paperwork...
</p>


Explains that real inclusion is shown in behavior, not just documents.

Examples:

Teacher reactions

Classmates respecting pronouns

Everyday behavior when no one’s watching

Same styles as above are applied.

 7. Paragraph 3
<p className=" mx-auto max-w-3xl text-[#121416] text-16px leading-relaxed">
  This is why learning about gender diversity cannot be optional...
</p>


Highlights the need for gender diversity education.

Everyone in the school system (not just teachers) should be involved.

Ends with the point that students shouldn’t always have to explain themselves just to be accepted.

Note: Small typo — text-16px should be text-[16px] in Tailwind CSS.

 8. Image Section
<div className="flex item-center justify-center gap-4 pt-2">
  <img
    src={img1}
    alt="Pride flag"
    className="w-[800px] h-[400px] object-cover rounded-md"
  />
</div>


A container that holds an image centered on the page.

Image Styling:

w-[800px] h-[400px]: Fixed size

object-cover: Ensures the image covers the box without stretching

rounded-md: Medium rounded corners

Note: Small typo — item-center should be items-center in Tailwind.

 9. Export the Component
export default BlogCard7;


Makes BlogCard7 available for use in other files, like your main Blog Page component.

# Summary Table
| Section            | Purpose                                                          |
| ------------------ | ---------------------------------------------------------------- |
| **Imports**        | Loads React and image used in the blog                           |
| **Main Container** | Wraps content with styling (white card, centered, padding, etc.) |
| **Title**          | Section heading: "Culture Can’t Be Faked"                        |
| **Paragraphs**     | Explains that inclusion is a daily culture, not just policy      |
| **Image**          | Displays a supporting pride-themed image                         |
| **Export**         | Makes the component reusable across the project                  |

********************************************************************************************
# src/components/Blogs/BlogCart8.jsx
** BlogCard8 – Code Explanation **
1. Imports
import React from "react";


React is imported so that you can use JSX to build this component.

2. Function Declaration

const BlogCard8 = () => {}


This defines a React functional component called BlogCard8.

This component is used to display one blog section with a title and two paragraphs.

3. Main Wrapper Div
<div className="max-w-[980px] font-poppins bg-white rounded-xl shadow-md p-6 mb-10 mx-auto space-y-4">


This div is the main container for the blog card.

Tailwind CSS classes used:
Class	Meaning
max-w-[980px]	Sets maximum width to 980px
font-poppins	Applies the "Poppins" font to the text
bg-white	White background
rounded-xl	Rounded corners
shadow-md	Adds a soft shadow around the box
p-6	Padding inside the card
mb-10	Adds bottom spacing
mx-auto	Centers the card horizontally
space-y-4	Adds vertical spacing between children
4. Blog Title
<h2 id="section-5" className="px-2 text-orange-500 text-xl font-poppins font-semibold">
  Stop Putting the Work on the Ones Already Exhausted
</h2>


This is the title of the blog section.

id="section-5" allows linking or scrolling to this part of the page.

Styled with:

Orange text

Slight padding

Font size: text-xl

Font weight: bold (font-semibold)

5. Paragraph 1
<p className="mx-auto max-w-3xl text-justify font-poppins text-[#121416] text-[16px] leading-relaxed">
  There’s a common mistake that schools make...
</p>


Describes how non-binary students are often forced to:

Explain their identity

Lead difficult conversations

Fight for recognition and respect

Message: This is unfair because the system was not built by them.

Styling:

text-justify: Aligns text evenly on both sides

text-[#121416]: Dark gray text

text-[16px]: Font size

leading-relaxed: Line spacing for easy reading

6. Paragraph 2
<p className="mx-auto max-w-3xl text-justify font-poppins text-[#121416] text-[16px] leading-relaxed">
  Real support isn’t just about saying the right things...
</p>


Explains that real support means taking responsibility:

Schools should take action (not just talk)

Don’t wait for students to ask for respect or basic rights

Institutions should take the lead, not the already-tired students

Message: It’s the school’s job to create inclusive, respectful environments — not the students'.

7. Export Statement
export default BlogCard8;


Makes this component available to be used in other files like your BlogsPage or main app.
8. summary
| Part            | Description                                                                                    |
| --------------- | ---------------------------------------------------------------------------------------------- |
| **Component**   | `BlogCard8` – A section of the blog post                                                       |
| **Title**       | *"Stop Putting the Work on the Ones Already Exhausted"*                                        |
| **Paragraph 1** | Explains how schools unfairly expect non-binary students to do all the explaining and advocacy |
| **Paragraph 2** | Real support means **action** by schools, not just waiting for students to keep asking         |
| **Image?**      | No image is used in this component                                                           |
| **Export**      | Component is exported for use elsewhere     
                                                   |
*************************************************************
# src/components/Blogs/BlogCart9.jsx
** BlogCard9 – Code Explanation **

1. Imports
import React from "react";
import img1 from "../../assets/Pride/Blogs/img16.jpg";
import img2 from "../../assets/Pride/Blogs/img17.jpg";
import img3 from "../../assets/Pride/Blogs/img19.jpg";


React is imported to use JSX.

Three images are imported from your assets folder. These will be displayed inside the blog card.

2. Component Declaration
const BlogCard9 = () => {


A functional React component named BlogCard9 is created.

This component represents one section of your blog focused on how real inclusion should feel.

3. Main Wrapper Div
<div className="max-w-[980px] text-poppins bg-white rounded-xl shadow-md p-6 mb-10 mx-auto space-y-4">


This div is the main card container.

It uses Tailwind CSS classes to style it:

Class	Description
max-w-[980px]	Maximum width is 980px
text-poppins	Uses "Poppins" font
bg-white	White background
rounded-xl	Rounded corners
shadow-md	Adds shadow around the card
p-6	Padding inside the card
mb-10	Margin bottom (spacing between cards)
mx-auto	Center horizontally
space-y-4	Adds vertical spacing between elements inside the card
4. Title
<h2 id="section-6" className="px-2 text-orange-500 text-2xl font-semibold">
  What Inclusion Actually Feels Like
</h2>


This is the heading of this blog section.

It explains the main idea: how real inclusion impacts non-binary students emotionally and socially.

id="section-6" allows linking to this section from a table of contents.

Styling:
Class	Description
text-orange-500	Makes text orange
text-2xl	Font size
font-semibold	Bold text
5. Paragraph 1
<p className="...">
  In the end, it’s not just about making students feel comfortable...
</p>


This paragraph explains:

Inclusion isn’t just about comfort.

It’s about removing fear, stress, and tension.

Non-binary students should be able to focus on learning, not on avoiding judgment.

6. Paragraph 2
<p className="...">
  When a school truly includes non-binary students...
</p>


Talks about the positive impact of inclusion on everyone:

Students feel safe, respected, and free to be themselves.

Friendships, learning, and classroom environments all improve.

Inclusion benefits the whole community, not just LGBTQ+ students.

7. Images Grid
<div className="grid grid-cols-3 gap-4 pt-4 px-4">
  <img src={img1} ... />
  <img src={img2} ... />
  <img src={img3} ... />
</div>


Displays three supportive images side-by-side in a 3-column grid layout.

Each image uses:

w-[280px]: Sets width

object-cover: Ensures image fills its space properly

rounded-md: Rounded corners

Layout:
Class	Description
grid	Uses CSS Grid layout
grid-cols-3	3 columns
gap-4	Gap between columns
pt-4 px-4	Padding top and horizontal
8. Export Component
export default BlogCard9;


Makes the component reusable across your project (e.g., import in BlogsPage.js or main page).
 
 # Summary
| Part             | Description                                                                          |
| ---------------- | ------------------------------------------------------------------------------------ |
| **Component**    | `BlogCard9`                                                                          |
| **Topic**        | How real inclusion should feel                                                       |
| **Main Message** | Inclusion removes fear and stress, helping students learn and connect more naturally |
| **Images**       | 3 supportive images related to LGBTQ+ inclusion                                      |
| **Exported?**    |  Yes, for use in other files                                                        |

**************************************************************************************************************

 # src/components/Blogs/ BlogCard10.jsx

** Code Explanation: BlogCard10.jsx **
 1. import React from "react";


This imports React from the react library so we can create a functional component.

const BlogCard10 = () => {


2. Declares a functional component named BlogCard10.

return (
  <div className="max-w-[980px] ...">


Returns a <div> element styled using Tailwind CSS classes.

max-w-[980px]: limits the max width.

text-justify, font-poppins, rounded-xl, shadow-md, p-6: add styling, spacing, and font.

3. Title Section
<h2 id="section-7" className="...">
  Keep Showing Up Even When It’s Quiet
</h2>


.This is the main title of the blog section.

.The id="section-7" allows linking to this section from other parts of the page (like a Table of Contents).

4. Paragraphs
<p className="...">This was never about getting it all right...</p>


3 <p> tags contain the actual blog content.

.The paragraphs talk about:

.The importance of consistency in inclusion efforts.

.Inclusion isn't just during Pride Month — it should happen every day, even when it's not visible.

.Non-binary students deserve respect and inclusion now, not later.

4. export default BlogCard10;


This line exports the component, so it can be used in other files (like a parent blog page).

**********************************************************
# src/components/Blogs/BlogCart11.jsx

** Full Code Explanation  **
1. import React from "react";
Importing React (needed to use JSX and create a functional component).

mport img1 from "../../assets/Pride/Blogs/blog12.png"; 
import img2 from "../../assets/Pride/Blogs/blog13.png";
import img3 from "../../assets/Pride/Blogs/blog14.png";
 Importing 3 blog images from the local files. These will be used in the blog cards.
# BlogCard11 Component
const BlogCard11 = () => {
 Creating a functional React component called BlogCard11.

 # Blog Data (Array)
 const blogs = [
    {
      id: 1,
      date: "9 July, 2025",
      title: "Making Room:",
      subtitle: "How Schools and Colleges can Better Support Non-Binary Students",
      content: "More people are finally talking about gender identity in schools and colleges, which is an encouraging and strong step in this... ",
      img: img1,
    },]

    An array of blog objects.
Each object represents a blog post and contains:

id – unique identifier

date – when it was posted

title – main title

subtitle – extra detail

content – short blog description

img – image for the blog

# JSX Layout
  return (
    <div className="max-w-[980px] font-poppins shadow-md mb-10 mx-auto px-4 py-8">


# Outer container of the component:

max-w-[980px] = max width

font-poppins = font styling

shadow-md, mb-10, mx-auto, etc. = spacing and styling

# Heading: Table of Contents
      <h2 className="text-2xl text-[#121416] font-normal mb-6">TABLE OF CONTENTS</h2>


# Displays a heading “TABLE OF CONTENTS” at the top.

# Blog Grid Layout
      <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">


# Sets a grid layout:

1 column on small screens

2 on medium (sm)

3 on large (lg)

gap-4 = spacing between cards

# Mapping Through Blogs
        {blogs.map((blog) => (


# Loop through each blog in the blogs array using .map().

# Blog Card
          <div key={blog.id} className="bg-white rounded-xl shadow-md overflow-hidden">


# For each blog:

Create a div (box)

Give background, border radius, shadow

# Blog Image
            <img src={blog.img} alt={blog.title} className="w-full h-50 object-cover" />


# Show blog image using img tag.

📄 Blog Info
            <div className="p-4 flex flex-col gap-2">


# Container for blog text content.

# Date + Author
              <div className="flex items-center justify-between text-xs mb-1">
                <div className="text-white bg-[#FF6501] px-2 py-[2px] rounded-md w-fit">
                  {blog.date}
                </div>
                <p className="text[#000000] font-semibold">By Name</p>
              </div>


# Shows:

Blog date inside an orange badge

Placeholder “By Name” (can be updated to actual author)

 Title, Subtitle, Content
              <h3 className="text-[16px] font-bold text-black leading-tight">{blog.title}</h3>
              <p className="text-[14px] text-semibold text-black">{blog.subtitle}</p>
              <p className="text-[10px] text-justify text-black">
                {blog.content}
              </p>


# Shows:

Blog title (bold)

Subtitle (smaller text)

Short paragraph content

# Read More Button
              <button className=" ml-auto bg-black text-white text-sm px-4 py-1 rounded-md">
                Read More
              </button>


# A button at the bottom right of each card, styled with black background and white text.

# You can later add onClick or Link here to open full blog post.

# Final Export
export default BlogCard11;


# Makes the component usable in other files.

***********************************************
# src/componenets/Blogs/BlogSectionPage.jsx
# Full Code Explanation
/ Importing all the blog content cards
import BlogCard1 from "./BlogCard1";
import BlogCard3 from "./BlogCard3";
import BlogCard4 from "./BlogCard4";
import BlogCard6 from "./BlogCard6";
import BlogCard7 from "./BlogCard7";
import BlogCard8 from "./BlogCard8";
import BlogCard9 from "./BlogCard9";
import BlogCard10 from "./BlogCard10";
import BlogCard11 from "./BlogCard11";

// Importing Sidebar and ImageGrid components
import BlogSidebar from "./BlogSidebar";
import ImageGrid from "./ImageGrid";
# These are all separate components (small parts of the UI) that will be displayed inside this one main page.

# BlogSectionPage Component Layout

const BlogSectionPage = () => {
  return (
    <div className="w-full  mx-auto px-4 py-8">
This outer <div> wraps the whole blog page.

w-full: full width

mx-auto: center aligned horizontally

px-4 py-8: padding

# All Blog Components Rendered

      <div>
        <BlogCard1 />       // Hero section blog card
        <BlogSidebar />     // Sidebar with links or navigation
        <BlogCard3 />       // Blog section about systems
        <BlogCard4 />       // Blog section about listening
        <ImageGrid />       // Grid of images (likely related to the blog)
        <BlogCard6 />       // Blog section about fixing basics
        <BlogCard7 />       // Blog about school culture
        <BlogCard8 />       // Blog about student burden
        <BlogCard9 />       // Blog about real inclusion
        <BlogCard10 />      // Final motivational message
        <BlogCard11 />      // Table of contents or blog previews
      </div>
Each of these components is a separate blog topic section, already explained before. They're rendered in order, one after the other.

# Export Component

export default BlogSectionPage;
Allows this component to be used elsewhere in your React app, like in routing or as part of a layout.

# Simple Summary
BlogSectionPage is the main blog page.

It shows all blog cards like BlogCard1, BlogCard3, etc.

It includes a sidebar, an image grid, and table of contents.

Each section focuses on a different topic related to non-binary student inclusion.

This page stitches all the parts together to build a full blog experience.

***********************************************************************
# src/componenets/Blogs/BlogSidebar.jsx

1. Importing Social Media Icons
import { FaFacebookF, FaTwitter, FaInstagram, FaYoutube } from "react-icons/fa";


These are icon components for Facebook, Twitter, Instagram, and YouTube, used below in the social section.

2. contents Array – Table of Contents Data
const contents = [
  { id: "section-1", title: "Everyday Systems Speak Louder Than Statements" },
  ...
];


Each item here represents a blog section.

id matches the id of blog titles (e.g., section-1),

title is the display name.
3. Main Container
<div className="max-w-[980px] ... flex-col md:flex-row gap-8 ...">


Main layout wrapper for the sidebar.

Flex direction changes based on screen size: column on mobile, row on desktop.

Contains 2 child sections: Table of Contents and Social Links.

4. Table of Contents Section
<div className="bg-white rounded-md shadow-md p-6 w-full md:w-[713px]">


A white box with padding and shadow.

Width is full on small screens, fixed width on larger screens.

# Title:
<h2>TABLE OF CONTENTS</h2>

# List (with numbering and links):
<ol className="...">
  {contents.map((item, index) => (
    <li key={index} className="flex px-10 gap-4">
      <span>{index + 1}</span>
      <a href={`#${item.id}`}>{item.title}</a>
    </li>
  ))}
</ol>


map() loops through the contents array

index + 1 shows serial number (1, 2, 3, ...)

<a href="#section-x"> scrolls to that section of the blog

# Example output:

1  Everyday Systems Speak Louder Than Statements
2  Start With Listening and Really Mean It
...

5. Social Media Section
<div className="bg-white rounded-md shadow-md p-6 md:w-[292px]">


Separate white box for showing social links

Fixed width on large screens

# Title:
<h2>SOCIAL LINKS</h2>

# Grid layout:
<div className="grid grid-cols-2 gap-12">


2 columns of social platform cards

Each card has:

Icon in a colored circle

Platform name (e.g. Facebook)

Followers/Likes count + label

# Example Facebook block:

<FaFacebookF />
<p>Facebook</p>
<p>96K Likes</p>


Other platforms:

Twitter → 60K Followers

Instagram → 20K Followers

YouTube → 625K Subscribers
# summary

| # | Section            | What It Does                                                |
| - | ------------------ | ----------------------------------------------------------- |
| 1 | `import`           | Loads icon components                                       |
| 2 | `contents` array   | Stores section titles and anchor IDs                        |
| 3 | Main container     | Wraps both TOC and social cards                             |
| 4 | Table of Contents  | Clickable links to jump to blog sections                    |
| 5 | Social Media Cards | Shows Facebook, Twitter, etc., with icons and follower info |

********************************************
# src/componenets/Blogs/ImageGrid.jsx
1. Imports
import React from "react";
import img1 from "../../assets/Pride/Blogs/img3.png"; 
import img2 from "../../assets/Pride/Blogs/img4.png"; 
import img3 from "../../assets/Pride/Blogs/img5.png"; 
import img4 from "../../assets/Pride/Blogs/img6.png"; 
You're importing 4 images to display in the grid.

2. Outer Wrapper
<div className="w-full mx-auto px-4 py-4">


w-full: full width container

mx-auto: centers it horizontally

px-4 py-4: padding on x and y sides

 3. Grid Container
<div className="max-w-[1040px] mx-auto p-4 grid gap-[10px] h-auto mb-16 
grid-cols-2 md:grid-cols-2 
lg:grid-cols-[380px_300px_320px] lg:grid-rows-[326px_310px] bg-white">


Here’s what each part does:

Class	Purpose
max-w-[1040px]	Limits the max width of the grid
grid	Enables CSS Grid layout
gap-[10px]	10px gap between grid items
grid-cols-2	2 columns on small and medium screens
lg:grid-cols-[...]	On large screens, custom column widths
lg:grid-rows-[...]	On large screens, custom row heights
bg-white	White background for the grid
 4. Image Boxes

Each image is inside a div with:

className="rounded-[10px] overflow-hidden h-[200px] sm:h-[250px] lg:h-full ..."


That means:

Rounded corners

Prevents overflow

Height adjusts by screen size

Image fills the box using object-cover

 Image 1
<div className="... col-span-1 sm:col-span-2 lg:col-span-2">


On large screens, this image takes 2 columns

It’s wider than others

 Image 2
<div className="...">


Takes normal space in the grid

On large screens, fits into 3rd column

 Image 3
<div className="... col-start-1 row-start-2">


Starts from first column, second row

Positions image manually in grid

 Image 4
<div className="... col-start-2 row-start-2 col-span-2">


Starts from second column in second row

Spans two columns to become wider

 Final Layout (on Large Screens)

It roughly looks like this:

[ Img1 ][ Img1 ][ Img2 ]
[ Img3 ][ Img4 ][ Img4 ]


Responsive: On mobile/tablet, becomes 2 columns
# summary

Clean UI: Rounded corners, proper spacing
| Part          | Purpose                            |
| ------------- | ---------------------------------- |
| `img1`        | Large image across 2 columns (top) |
| `img2`        | Top-right column                   |
| `img3`        | Bottom-left                        |
| `img4`        | Bottom, spans 2 columns            |
| Tailwind Grid | Responsive layout control          |
| Object-cover  | Keeps image from stretching        |

***********************************************
# src/componenets/DataAnalysis/BoughtTogether.jsx

1. BoughtTogether (Main Component)
2. import
    You're importing:

   .React (to create components)

   .Icons for rating and time

    .3 images for the courses

3. Courses Data (Array)
   .You have a list of 3 course objects. Each object contains:

  .Course title, rating, number of lessons, duration, and image

  .This data will be used to create each card

  4. CourseCard Component
  CourseCard is a reusable component that shows one course.

  You pass a course object to it as props

  It displays course image, title, description, lessons, duration, and rating
  5. BoughtTogether Component
  This is the main section.
  6. Heading Section
  Displays the heading and subheading for the section

  7. Course Cards + Symbol
  Loop through the first 3 courses:

Display each course using CourseCard

Add a "+" symbol between the first and second, and second and third

After all cards, display "=" symbol

8. Pricing Section
A price box that shows:

The original price (with a line through it)

The discounted bundle price

A button to buy the full bundle
9. Bottom Line Divider
<hr />
➡️ Adds a line at the bottom of the section to separate it from other content.


10. Developer Notes

Props are used to make CourseCard dynamic and reusable

React Icons improve visual UX (star for rating, clock for time)

Tailwind CSS is used for all styling (colors, layout, font, responsiveness)

Responsive Design: Cards stack vertically on small screens and align horizontally on larger screens
11. summary
his React component shows a group of 3 related courses as a bundle with a discounted price. Each course is shown using a reusable card layout with title, description, image, duration, and rating.

It is designed to:
- Upsell related courses
- Offer discount pricing
- Visually explain that all 3 courses are part of a growth path

It uses Tailwind CSS for styling and React Icons for better user interface.

*************************************************
# src/components/DataAnalysis/DataAnalysisPage.jsx
🔹 Imports
   You're importing React to create a functional component.
   You're importing individual UI components that will be shown on this page:

Hero section

Footer

FAQ

Experts section

Navbar

Course bundle section (BoughtTogether)

Discount banner

Certificate section

Learning journey timeline

Flexible courses info
info

🔹 Component: DataAnalysisPage
This is the full layout of your Data Analysis course landing page.
Each line inside the <div> is a section of the page, such as:

<Navbar_C />
→ Top navigation bar of the page

<HeroSection_C />
→ Big top banner with course overview, title, etc.

<LearningJourney />
→ Section showing what users will learn or the step-by-step journey

<BoughtTogether />
→ Shows 3 bundled courses + discount pricing

<Experts />
→ Shows the mentors or instructors for the course

<CertificateSection />
→ Displays the certificate a learner will receive

<FlexibleCourses />
→ Info about learning flexibility (anytime, self-paced, etc.)

<FAQ_C />
→ Frequently asked questions

<DiscountBanner />
→ Promotional banner for discounts

<Footer />
→ Page footer with links, copyright

## 📄 DataAnalysisPage Component

This is the main page component for the Data Analysis course landing page.  
It combines all key sections into one single, scrollable view.

### 🔧 What it includes:

- `Navbar_C` – Top navigation bar
- `HeroSection_C` – Top banner with course intro
- `LearningJourney` – Timeline of what you'll learn
- `BoughtTogether` – Shows bundled course offer
- `Experts` – Section showing expert instructors
- `CertificateSection` – Info about the certificate you’ll receive
- `FlexibleCourses` – Highlights course flexibility
- `FAQ_C` – Frequently Asked Questions
- `DiscountBanner` – Offer banner
- `Footer` – Page footer with extra links

This component makes it easy to manage the full course page as a single React component composed of reusable parts.  


********************************************************
# src/components/DataAnalysis/DiscountBanner.jsx

✅ DiscountBanner Component – Simple Developer Explanation
📌 What is this component?

The DiscountBanner is a referral promotion section that encourages users to refer students and earn rewards.

It contains a heading, description, email input field, a button, and a promotional image of a coin bag.

🧱 What is used in this component?
✅ 1. React Functional Component

This is a stateless functional component written using React.

✅ 2. React Icon
import { FiSearch } from "react-icons/fi";


Uses the FiSearch icon (a magnifying glass) from react-icons, placed inside the email input box.

✅ 3. Image Asset
import coinsBag from ".../CoinBag.png";


Imports an image of coins/bag to visually support the "earn rewards" concept.

✅ 4. Tailwind CSS for Styling

All styling is done using Tailwind CSS classes.

It's responsive and adapts across screen sizes (md, sm, etc.)

🔎 Component Structure Breakdown
🔸 Outer Wrapper
<div className="w-full py-6 flex justify-center mb-8 sm:mt-18 sm:mb-18">


Adds spacing above and below

Centers the banner horizontally

🔸 Main Orange Banner
<div className="w-[1200px] h-[186px] bg-[#FF6501] rounded-xl flex md:flex-row items-center justify-between">


Fixed width and height

Orange background (#FF6501)

Rounded corners

Displays content in a flex row (on medium+ screens)

🔸 Left Section: Text + Input + Button
<h2>Your Network = Your Net Worth!</h2>
<p>Refer students. Earn rewards.</p>


Motivational heading and description to encourage referrals

<input type="email" placeholder="Enter your email" />
<FiSearch />
<button>Refer Now</button>


Input Field: Lets user enter email

Search Icon inside input

Button: To submit referral or trigger some action (though no handler is added in this code)

🔸 Right Section: Image
<img src={coinsBag} alt="Coins and Bag" />


Shows a visual icon related to rewards

💡 Developer Notes

✅ Clean layout with proper responsiveness

✅ Good use of icons to enhance UI

✅ Email input + CTA button = ready for future functionality

❌ Currently, no logic/functionality is added for form submission — it’s just static

📄 How to Write This in README.md
## 💰 DiscountBanner Component

This component displays a referral banner to encourage users to refer friends or students and earn rewards. It includes:

- A heading and short description
- An email input field with a search icon
- A "Refer Now" button
- A visual image of a coin bag

### ✅ Features:
- Fully responsive using Tailwind CSS
- React Icon used for search icon
- Eye-catching call-to-action (CTA)
- Ready for future referral logic integration

### 📦 Usage:
Place this component anywhere in your page layout to show a referral offer section.


*************************************************************
# src/components/DataAnalysis/Experts.jsx


1. Import statements:



React and its hooks (useState, useEffect) are imported — these help create components and manage their state.

Arrow icons and star icons are imported — these are used for buttons and showing ratings.

useMediaQuery is imported — this helps detect the screen size (mobile, tablet, desktop).

Slider and its CSS files are imported — this is for creating the slider/carousel on mobile.

4 trainer images are imported — these are the pictures of the trainers.

2. Trainers data:



This is a list (array) containing details for each trainer: name, job role, experience, rating, number of students, and photo.

3. TrainerCard Component:



This creates a card for each trainer.

It calculates star icons for the rating:

Full star for each full rating point.

Half star for half points.

Empty star if no rating point.

The card shows the trainer’s photo, name, role, experience, and number of students.

4. Experts Component (main part):



currentIndex keeps track of which card is currently at the front (like the scroll position).

transition controls the animation speed for sliding.

cardsPerPage stores how many cards to show on one screen.

cardWidth, smCardWidth, cardGap define card size and space between cards.

isDesktop and isTablet check the screen size to adjust layout.

5. Slider settings for mobile:
  


Settings for the slider on mobile devices.

Shows one card at a time.

Automatically slides to the next card.

Does not show arrow buttons, only dots.

6. Handling screen resize:
  
When screen size changes, this code decides how many cards to show at once (1, 2, or 3).

Resets the scroll position to the start.

Adds and removes event listeners for resize events.

7. Scroll button logic:
  

When the left arrow is clicked, it moves one card backward, but does not go before the first card.

When the right arrow is clicked, it moves one card forward, but does not go beyond the last possible card.

8. Calculating container width and sliding transform:
 
  

These functions calculate:

How far to slide the cards left or right based on current scroll.

How wide the container should be to fit all visible cards with gaps.

9. Rendering the component:
 

Shows a heading and description at the top.

If the screen is desktop or tablet:

Shows left arrow button.

Shows the cards side by side inside a horizontally scrollable container.

Shows right arrow button.

If the screen is mobile:

Shows a slider/carousel that slides cards automatically.

10. Export statement:
export default Experts;


Exports this component so it can be used in other parts of the app.

Summary in very simple words:

This code displays a list of trainer cards.

On big screens, you can click arrows to slide left and right through trainers.

On small screens, you see one trainer at a time in an automatic slider.

Each card shows the trainer’s photo, name, experience, rating stars, and students count.

The layout changes automatically based on the device screen size.



****************************

# src/components/DataAnalysis/FAQ_C.jsx


1. Imports
import { useState } from "react";
import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";


You import React’s useState hook to keep track of which FAQ is open.

You import some icons (plus, times, arrow) to show next to each question.

2. Component and State
const FAQ_C = () => {} componenet function
  const [openIndex, setOpenIndex] = useState(null); it is state


This is your main FAQ component.

You create a state variable openIndex that stores which question is currently open (expanded).

Initially, no question is open (null).

3. Toggle function
  const toggleIndex = (index) => {
    setOpenIndex(openIndex === index ? null : index);
  };


This function is called when you click a question.

If you click on the same open question, it closes it (null).

If you click a closed question, it opens that one (sets openIndex to that question's index).

4. FAQ Data



This is the list of questions and answers.

Each item has a question and an answer.

5. Splitting FAQs into two columns
  const leftFaqs = faqData.slice(0, 3);
  const rightFaqs = faqData.slice(3);


You divide the FAQs into two groups:

First 3 questions go to the left column.

Remaining questions go to the right column.

6. Render each FAQ item


This function builds each FAQ card.

It shows the question always.

Clicking the question toggles whether the answer is shown.

If the question is open, it shows the answer below.

The plus icon changes to a times (X) icon when open.

It also adjusts the card height depending on open/closed.

7. Main render
return(.......)

Shows the page title and a contact email.

Displays the FAQ questions in two columns on medium+ screens, stacked on small screens.

Each column shows its half of the FAQ questions.

At the bottom, there’s a button for “See All FAQ’s” (currently just a button with no action).

8. Export
export default FAQ_C;


Makes the FAQ component available for use elsewhere in your app.

Summary in simple words:

The FAQ section shows a list of questions.

You click a question to open or close its answer.

Only one answer can be open at a time.

The questions are split into two columns on bigger screens.

It uses plus and times icons to show open/closed state.

There is a “See All FAQ’s” button at the bottom for future use.

*************************************************************

# src/components/DataAnalysis/FlexibleCourses.jsx
## import
You're importing React to use JSX (the UI code).

useState is a tool to create and manage state (e.g. which slide is active, is a course bookmarked).

useEffect lets you run code when the component loads or updates (like checking screen size).

### 1. Courses List
const courses = [ ... ];


This is a list of courses with the following details for each:

title: Main course title

subtitle: Sub-topic

lessons: Number of lessons

time: Duration

rating: Out of 5

image: Image for the course

2. CourseCard Component

This shows each course box with:

Image

Bookmark button

Title, subtitle, number of lessons

Duration (with clock icon)

Rating (with star icon)

Bookmark Logic:
const [isBookmarked, setIsBookmarked] = useState(false);


Each card can be bookmarked by clicking the icon.

Bookmark color changes when clicked (orange if active).

Rating Display:
const formattedRating = Number(rating).toFixed(1);


Ensures rating is shown like 4.5 even if number was 4.5001.

3. FlexibleCourses Component

This is the main component that shows the course list.

📱 Mobile Responsiveness Setup:
const [isMobile, setIsMobile] = useState(false);


Checks if screen width is less than 768px (md breakpoint).

If yes → mobile view is shown.

useEffect(() => {
  const handleResize = () => {
    setIsMobile(window.innerWidth < 768);
  };
  ...
}, []);


Listens to window resizing so layout updates on screen size change.

💡 Carousel State:
const [currentIndex, setCurrentIndex] = useState(0);


Keeps track of the currently visible card on mobile.

nextSlide() and prevSlide() update the index accordingly.

4. Layout Rendering
💻 Desktop View (md and up):
<div className="hidden md:flex flex-wrap justify-center ...">
  {courses.map(...)}
</div>


Hides this section on mobile.

Shows all course cards in a grid layout.

📱 Mobile View (carousel):
<div className="md:hidden relative">
  ...
</div>


Hides this on desktop.

Displays one course at a time, sliding left/right.

Carousel Slide Logic:
style={{ transform: `translateX(-${currentIndex * 100}%)` }}


Moves the slider by -100%, -200%, etc. to show the correct course based on index.

Arrows:

ChevronLeft and ChevronRight allow user to move back and forth between slides.

Indicators:
{courses.map((_, index) => (
  <button
    className={currentIndex === index ? 'bg-orange-500' : 'bg-gray-300'}
  />
))}


Small dots show which slide is active.

You can also click a dot to jump to a slide.

5. Divider at the bottom
<hr className="..." />


A horizontal line added after the courses section to visually separate it from the next content.

✅ Summary (Very Simple):
Feature	What it Does
Course List	Holds all the course data (title, rating, etc.)
CourseCard	Displays a single course card with info and bookmark
FlexibleCourses Component	Shows all courses (grid on desktop, slider on mobile)
Mobile Slider	Only one course card visible at a time with next/prev buttons
Bookmark Toggle	Lets user mark/unmark a course visually

*******************************************

# src/components/DataAnalysis/HeroSection_C.jsx
✅ 1. Importing Modules
import React from "react";


Loads React to use JSX and build components.



✅ 2. HeroSection_C Component

The main UI layout for the course details page (e.g., "Master Data Analysis").

🔶 Left Side Content
<div className="flex-1">...</div>


This contains the main information about the course:

📍 Breadcrumb Navigation:
<nav>
  <Link to="/">
    <AiFillHome />
  </Link>
  <AiOutlineRight />
  <span>Master Data Analysis</span>
</nav>


Helps users know their current location inside the site (Home > Course Name).

📚 Course Title and Subtitle:
<h1>Master Data Analysis</h1>
<p>From <span>Data to Decisions</span> That <span>Matter</span></p>


Shows main course heading and a catchy subtitle.

📎 Download Brochure Button:
<a href="/Brochure/DA.pdf" download>
  Download Brochure
</a>


Lets users download a course PDF.

👤 Instructor Info:
<img src={Expert} />
<p>Data Analysis Expert</p>
<img src={globe} />
<p>Hindi, English</p>
<img src={laptop} />
<p>Last updated - June 2025</p>


Shows course creator, available languages, and last update info.

# Course Stats Section:
Got Placed | Reviews | Learners


Uses flexbox to display:

Placement count (2000+)

Rating (4.5 ⭐)

Learners (10,000+)

# "What Will You Learn?" Tags:
["Python", "SQL", "Calculus", ...].map(...)


Dynamically shows course topics as tags.

# Prerequisites Section:
<ul>
  <li>Mathematics Fundamentals.</li>
  ...
</ul>


Lists requirements for taking this course.

# Right Side Panel (Course Purchase Info)
<aside className="md:w-[550px]">...</aside>


This contains conversion-focused content like buying, watching preview, and summary.

# Highlight Banner:
"20,000+ Openings. ₹7 LPA Median."
"Start your journey to a high-paying job..."


A persuasive message to encourage enrollment.

# Course Preview Image:
<img src={DA} />


Shows a preview image (might be a placeholder for a video thumbnail).

# Purchase Summary Section:
<p>Course Fee: ₹4,999 (One-time payment)</p>


Clearly shows pricing.

# Features List:
<ul>
  <li>Lifetime access</li>
  <li>Refund policy</li>
  ...
</ul>


Lists key benefits of enrolling.

# Buy / Add to Cart / Bookmark Buttons:
<button>Buy Now</button>
<button>Add to Cart</button>
<BookmarkButton />
<FiSend />


Call-to-action buttons.

Buy Now → opens Razorpay link

Add to Cart → saves course to cart

Bookmark → saves to user wishlist

Send icon → for sharing (not yet functional)

# Horizontal Divider:
<hr />


Visually separates the section from the rest of the page.

*********************************************************
# src/components/DataAnalysis/LearningJourney.jsx

** Component Name: LearningJourney

Purpose:
Display a step-by-step expandable roadmap for a Data Science learning path, broken into modules (like a curriculum timeline).

# DATA STRUCTURE: modules

You’ve defined an array of objects where:

Each object is a module (like a course section).

Each module has a title and a list of items.

Example:

{
  title: "Module 1: Foundation & Skill Building (Month 1–2)",
  items: [
    "Introduction to Data & Data Analytics",
    "Types of Data & Analytical Thinking",
    ...
  ]
}


# Fix needed: Some items have double commas ,, which result in empty strings in the array. You should remove those for a clean UI:

"Types of Data & Analytical Thinking", , "Microsoft Excel / Google Sheets..." 


→ should be:

"Types of Data & Analytical Thinking", "Microsoft Excel / Google Sheets..."

# STATE MANAGEMENT
const [openIndex, setOpenIndex] = useState(null);


openIndex tracks which module is currently expanded.

setOpenIndex(index) updates it.

If the user clicks the same module again → it collapses.

const toggleModule = (index) => {
  setOpenIndex(openIndex === index ? -1 : index);
};

# UI STRUCTURE
🔸 Wrapper <div>
<div className="flex flex-col items-center ...">


Centered layout, white background.

Uses Poppins font.

🔹 Header
<h1>Your <span>Data Science</span> Growth Path</h1>
<p>Follow an expertly curated roadmap...</p>


The headline introduces the journey.

Subtitle encourages the user to explore the modules.

🔹 Module Accordion

This block shows clickable module titles, and when clicked, expands to show items.

<div className="w-full md:max-w-2xl ...">
  {modules.map((module, index) => (
    <div key={index}>
      {/* Title section */}
      <div onClick={() => toggleModule(index)}>
        {module.title}
        ▼
      </div>

      {/* Conditionally render module content if open */}
      {openIndex === index && (
        <div>
          {module.items.map(item => (
            <div>• {item}</div>
          ))}
        </div>
      )}
    </div>
  ))}
</div>

# Dropdown Arrow

You’ve used a custom SVG to show a toggle arrow:

<svg className={`... ${openIndex === index ? "rotate-180" : ""}`}>...</svg>


Rotates when the section is open.

Adds a nice touch to the UI.

# STYLING & RESPONSIVENESS

You used Tailwind CSS to:

Make text sizes adjust across devices (text-[14px], md:text-[18px])

Set dynamic widths and paddings

Animate dropdown arrow

Add hover and background transitions

It’s clean, mobile-friendly, and readable.

 CLEAN-UP / IMPROVEMENTS
1.  Fix Invalid Items

In your first module:

items: [
  "Introduction to Data & Data Analytics",
  "Types of Data & Analytical Thinking",
  , // ← remove these empty commas
  "Microsoft Excel / Google Sheets for Data Cleaning",
  ...
]

2.  Optional Improvements
a. Add numbering to sub-items

Make the modules more structured:

`${idx + 1}. ${item}`

b. Smooth scroll to open module

When a module opens, you can scroll it into view for better UX.

c. Support multiple modules open (optional)

Currently, only one can be open. If you want multiple expandable sections, use an array of open indices instead of a single number.

d. Icons or status badges

Add icons (✅, 🔧, 📊) or labels like “Beginner”, “Hands-on”, etc. to each module or item.

*******************************************************************************
# src/components/DataAnalysis/Navbar_C.jsx
Major parts of the component:
1. Imports:

Various icons like FiMenu, FiSearch, etc. from react-icons.

Images: logo and Profile.

Link from react-router-dom is used for navigation without refreshing the page.

# State variables:
const [isHovered, setIsHovered] = useState(false);
const [mobileMenuOpen, setMobileMenuOpen] = useState(false);


isHovered: Controls whether the "Explore" dropdown is open.

mobileMenuOpen: Controls whether the mobile menu is open.

# JSX (What gets rendered):
✅ Top Navbar Section:
<div className="max-w-[1440px] ...">


This contains:

Logo (left side):

Clicking it takes you to the homepage.

Explore Dropdown (only on large screens):

A text "Explore" with an arrow icon (up or down).

When clicked, shows a dropdown (currently only has "None" as an item).

Opens and closes using the isHovered state.

Search Bar (medium and large screens only):

Lets users type what they want to learn.

Search icon next to it.

Icons on the Right (desktop view):

Bookmark

Shopping cart

Bell icon (notification with a red dot)

Profile picture (clickable)

Mobile Menu Button (hamburger icon):

Shown only on small screens.

Clicking toggles mobileMenuOpen state.

📱 Mobile Dropdown Menu:

If mobileMenuOpen is true, show this section:

A mobile version of:

Explore dropdown

Search bar

Icons (bookmark, cart, bell, profile)

It’s the same functionality as desktop, but adjusted for mobile layout.

# Summary (in points):

Responsive navbar component.

Works on both desktop and mobile.

Includes logo, dropdown menu, search bar, icons, and profile image.

Dropdown and mobile menu are toggled using useState.

Would you like a version with comments inside the code too?

*******************************************************************

#  src/components/DataAnalysis/Signup.jsx

1. Importing Icons:
import { FaEye, FaEyeSlash } from "react-icons/fa";
import { IoClose } from "react-icons/io5";


.These are icons used in the UI, imported from the react-icons library:

.FaEye: 👁️ An eye icon – used to show OTP.

.FaEyeSlash: 👁️❌ An eye with a slash – used to hide OTP.

.IoClose: ❌ A close ("X") icon – used to close the modal.

. react-icons lets you use icons from popular icon sets like Font Awesome (fa) and Ionicons (io5) directly in React.

 2. Importing an Image:
import Google from "../../assets/google.png";


This imports the Google logo image from your project folder.

It’s used as a clickable button for "Continue with Google" login.

 3. Importing React Hook:
import { useState } from "react";


useState is a React Hook that allows you to create state variables inside functional components.

In this file, it’s used to:

Switch between login and sign-up.

Show/hide the OTP field.

Props (Inputs from parent component)
const Login = ({ isOpen, onClose }) => { ... }


isOpen: A boolean to control whether the modal is shown.

onClose: A function to close the modal when clicked outside or on the close icon.

# useState Hooks
const [isLogin, setIsLogin] = useState(false);
const [showOtp, setShowOtp] = useState(false);


isLogin: Tracks whether the user is in Login or Sign-Up mode.

showOtp: Controls visibility of OTP (like show/hide password).

# What gets displayed?
🔲 Modal Container

This component covers the full screen with a semi-transparent black background and a white pop-up box in the center.

❌ Close Button

Top-right X icon that calls onClose() to close the modal.

📝 Heading

Displays:

"Welcome to Baoiam"

Either "Log In" or "Sign Up" depending on the mode

📩 Input for Email/Mobile

A basic input box where the user types their email or mobile number.

# OTP Section

A "Send OTP" button

An input to enter the OTP

An eye icon to show or hide the OTP using showOtp state.

# Terms & Conditions Checkbox

User must agree to the Terms & Conditions by checking the box.
It includes a link to the T&C page.

# Submit Button

A button to submit the form:

It says "Log In" if in login mode

Or "Sign Up" if in sign-up mode

(But note: the actual form functionality like validation or submission is not implemented here.)

# Switch Mode

A text below the button that lets the user switch between Login and Sign-Up modes by clicking the link.

# OR Divider

A horizontal line with "Or continue with" in the middle.

# Google Login

A Google icon that the user can click to sign in using Google.
(Currently it points to a placeholder URL: https://your-google-auth-url.com)

# Summary in Points

. Modal opens only when isOpen is true.

❌ Close it by clicking outside or the X button.

. Toggle between Login and Sign-Up.

. Collects email/phone and OTP.

. OTP can be shown/hidden.

. Checkbox for agreeing to Terms & Conditions.

. Option to sign in with Google.

**********************************************************************************
# src/components/DataScience/BoughtTogether.jsx

Imports at the top:
import React from "react";
import { FaStar } from "react-icons/fa";
import { MdAccessTime } from "react-icons/md";
import img1 from "../../assets/CoursesLayout/DataScience/ds1.png";
import img2 from "../../assets/CoursesLayout/DataScience/ds2.png";


FaStar = ⭐ icon to show the course rating.

MdAccessTime = ⏰ icon to show the course duration.

img1 and img2 = images for the courses.

# Course Data:
const courses = [ ... ]


This is an array of two course objects. Each course has:

title – the course name

rating – user rating (like 4.8 stars)

lesson – number of lessons

description – short description

duration – how long the course is

image – image shown for the course

🧩 CourseCard Component:

This component shows one course card:

Displays the course image

Shows title and description

Shows:

Duration with a clock icon

Rating with a star icon

. It receives a course via props: ({ course })

. BoughtTogether Component:

.This is the main component.

.It displays:

. A heading:

"Your Data Science Growth Path"

💬 Subheading:

."Bundle up the best skillsets for faster career growth & higher ROI"

🧾 Courses section:

.Shows each course using CourseCard

.Between courses, it shows a + sign

.After the last course, it shows an = sign

💰 Price Box:

.Original price: Rs 30,000 (crossed out)

.Discounted price: Rs 9,999

.A button: "Purchase Now"

. A horizontal line (divider) at the bottom

📱 Responsive Design:

.On mobile, courses stack vertically

.On desktop, they appear in a row

.The + and = signs only show on larger screens

**************************************************************
# src/components/DataScience/CertificateSection.jsx

# Imports:

.import React from "react";
.import certificateImage from "../../assets/CoursesLayout/CoursesPage/certificate.jpg";


.React: Required for using JSX and building components.

.certificateImage: Imports an image of the certificate from your project files.

📄 What does it show on the screen?
# Outer Container
<div className="w-full max-w-[1440px] mx-auto ...">


Sets the section's width and spacing.

Makes it look good on all screen sizes.

Adds a bottom border for separation.

# Heading Section
<h2>
  <span>Earn Certificates</span> That Speak for Your <span>Skills</span>
</h2>
<p>Showcase your achievement...</p>


A big headline:

Words like "Earn Certificates" and "Skills" are orange colored for emphasis.

A description below it:

"Showcase your achievement with an industry-recognized certificate from Baoiam."

🖼️ Certificate Image Section
<img src={certificateImage} alt="Certificate" />


Displays the actual image of the certificate.

It's:

Centered

Responsive (adjusts to screen size)

Slightly rounded with borders for better styling

✅ Summary:
| Section     | What It Does                                                    |
| ----------- | --------------------------------------------------------------- |
| Heading     | Tells users they'll get a certificate that proves their skills  |
| Description | Explains that it's an official certificate from Baoiam          |
| Image       | Shows what the certificate will actually look like              |
| Styling     | Looks clean, modern, and works on all screen sizes (responsive) |

********************************************************************

# src/components/DataScience/DataSciencePage.jsx

What is this file?

This React component is called DataSciencePage.
It builds the complete webpage for a Data Science course page using many smaller components.

Think of it like putting together LEGO blocks to build a full page.

🔁 Imports:
import React from 'react'


Brings in React so we can write a component.

Then it imports several components used to build different sections of the page:

| Component Name       | What it likely does                         |
| -------------------- | ------------------------------------------- |
| `Navbar_C`           | The top navigation bar                      |
| `HeroSection_C`      | The top banner section with key info        |
| `LearningJourney`    | Shows the learning path / course roadmap    |
| `BoughtTogether`     | Shows bundled courses to buy together       |
| `Experts`            | Shows the instructors or mentors            |
| `CertificateSection` | Shows the certificate users will earn       |
| `FlexibleCourses`    | Lists flexible course options               |
| `FAQ_C`              | Frequently Asked Questions section          |
| `DiscountBanner`     | A banner showing current discounts/offers   |
| `Footer`             | Bottom of the page – links, copyright, etc. |

# Inside the DataSciencePage component:
return (
  <div>
    <Navbar_C/>
    <HeroSection_C/>
    <LearningJourney/>
    <BoughtTogether/>
    <Experts/>
    <CertificateSection/>
    <FlexibleCourses/>
    <FAQ_C/>
    <DiscountBanner/>
    <Footer/>
  </div>
)


This renders all the imported components one after the other, creating a complete, scrollable web page for users interested in Data Science.

✅ Summary 

This is the main page for a Data Science course.

It brings together many smaller sections like:

Navigation bar

Course overview

Learning journey

Bundle offers

Teacher info

Certificate info

FAQs

Discount banners

Footer

Each section is built as a separate component to keep things clean and organized.

****************************************************************************

# src/components/DataScience/FAQ_C.jsx

✅ Purpose of the Component:

This FAQ_C component displays a Frequently Asked Questions (FAQ) section on a webpage.
It shows a list of questions and answers, and when you click a question, it expands to show the answer.

# Imports:
.import { useState } from "react";
.import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";


.useState: React hook to manage the open/close state of the FAQ items.

.FaPlus, FaTimes, FaArrowRight: Icons used for plus sign (➕), close (×), and arrow (→) from react-icons.

# State Management:
.const [openIndex, setOpenIndex] = useState(null);


.openIndex tracks which FAQ item is open.

.If openIndex is null, no answer is open.

.Clicking a question will open/close it using this state.

# FAQ Data (List of Questions & Answers):
.    const faqData = [
    { question: "...", answer: "..." },
     ...
    ];


.This array contains 6 questions and answers related to the Data Science course.

# toggleIndex() function:
const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


If the user clicks the same question, it will close.

If the user clicks a different question, that one will open.

# Splitting FAQ into Two Columns:
const leftFaqs = faqData.slice(0, 3);
const rightFaqs = faqData.slice(3);


Divides the FAQs into two parts:

First 3 questions → left column

Last 3 questions → right column

# renderFAQItem() function:

This function renders each FAQ item. For each one:

Always visible:

The question

A plus icon (➕) if it’s closed

A close icon (×) if it’s open

If open:

Shows the answer

Optional: shows a button or link (commented out here)

# Layout on Screen:
<div className="flex flex-col md:flex-row gap-8">


On small screens: FAQ items are shown in a single column.

On larger screens: they are shown in two columns side-by-side.

# Contact Info:
<p className="...">
  Still you have any questions? Contact our Team via
  <br />
  <a href="mailto:support@baoiam.com">support@baoiam.com</a>
</p>


Message shown above the questions

Provides an email link for further help

# "See All FAQ’s" Button:
<button className="...">See All FAQ’s</button>


A simple button at the bottom

Currently doesn’t do anything, but it could be used to load more FAQs in fu
# summary
| Feature                | What It Does                                 |
| ---------------------- | -------------------------------------------- |
| `useState`             | Tracks which question is open                |
| `faqData`              | Stores questions and answers                 |
| `toggleIndex()`        | Opens/closes a question on click             |
| `renderFAQItem()`      | Builds each FAQ block (question + answer)    |
| Responsive Design      | One column on mobile, two columns on desktop |
| Icons                  | Plus (➕) and Close (×) icons for toggle      |
| Contact Info           | Email link if you still have questions       |
| "See All FAQ’s" Button | Placeholder for future expansion             |


*************************************************************************

# src/components/DataScience/FlexibleCourses.jsx


# Purpose of This Code

.This component (FlexibleCourses) shows a list of courses using cards.
.It works differently on:

.Desktop: shows all course cards side-by-side.

.Mobile: shows one card at a time in a carousel/slider format with left/right arrows.

.Each course card includes:

.Course title and subtitle

.Total lessons

.Duration

.Rating

.Bookmark icon

# File Imports at the Top
.import React, { useState, useEffect } from "react";
.import { Bookmark, Clock, Star, ChevronLeft, ChevronRight } from "lucide-react";
.import Img1 from "../../assets/CoursesLayout/CoursesPage/Courses.png";


.useState, useEffect: React hooks to manage state and side effects (like window size).

.Icons (Bookmark, Clock, Star, Arrows) from lucide-react.

.Img1: Imported image used in all course cards.

# Course Data
const courses = [ ... ]


.This is an array of course objects — each course has:

.title

.subtitle

.lessons (number of lessons)

.time (duration)

.rating (out of 5)

.image

# CourseCard Component

.This small reusable component displays one course card.

.Features:

.Image at the top

.Bookmark icon (click to save/unsave)

.Course Title + Subtitle

.Lesson Count

.Time with clock icon

.Rating with star icon

.const [isBookmarked, setIsBookmarked] = useState(false);


.Clicking the bookmark icon toggles the saved status.

<Bookmark className={isBookmarked ? "filled-orange" : "outline-orange"} />


.Icon fills with orange color when bookmarked.

# FlexibleCourses Component (Main Component)
const [currentIndex, setCurrentIndex] = useState(0);
const [isMobile, setIsMobile] = useState(false);


.currentIndex: keeps track of the current slide (on mobile view).

.isMobile: checks if the screen size is mobile.

# useEffect to Detect Mobile
useEffect(() => {
  const handleResize = () => {
    setIsMobile(window.innerWidth < 768);
  };

  handleResize(); // call once when page loads
  window.addEventListener('resize', handleResize);

  return () => window.removeEventListener('resize', handleResize);
}, []);


.It listens to screen size changes and sets isMobile to true if width < 768px.

# Desktop View (MD and up)
<div className="hidden md:flex flex-wrap justify-center gap-8 px-4">
  {courses.map(...)}
</div>


.Shows all course cards side-by-side (using flex-wrap).

.Hidden on small devices (hidden md:flex).

# Mobile View – Carousel/Slider
<div className="md:hidden relative">


.Only visible on mobile screens.

# How the slider works:
<div className="flex transition-transform duration-500" style={{ transform: `translateX(-${currentIndex * 100}%)` }}>


.All cards are in a row.

.translateX moves the row left/right based on currentIndex.

# Navigation Buttons

.Left Arrow: goes to previous slide

.Right Arrow: goes to next slide

.Dots (Indicators): show current slide and let users jump to any course

# Bottom Line Divider
<hr className="w-full border-t-[2px] border-gray-100 mt-10 md:mt-14" />


. a line below the section for visual separation.
# summary

| Feature                  | What It does                                                     |
|  | ---------------------------------------------------------------------- |
| `CourseCard` Component   | Displays a single course card with image, title, rating, time, etc.    |
| `Bookmark` Icon          | Lets user mark a course as saved (just visually, not saved in backend) |
| `useEffect` Hook         | Detects screen size and updates layout accordingly                     |
| **Desktop View**         | Shows **all** courses in a flex layout                                 |
| **Mobile View**          | Shows **1 course at a time** in a slider with navigation arrows        |
| Navigation Arrows + Dots | Lets users navigate between courses on mobile                          |
| Responsive Design        | Layout adjusts automatically based on screen size                      |

************************************************************************************
#  src/components/DataScience/HeroSection_C.jsx


# What is import?

import is used to bring code, components, images, icons, etc. from other files into your current file.

🔹 Example 1: Import React
import React from "react";


✔ Brings in React so you can use JSX and create components.

🔹 Example 2: Import Component
import Footer from "../Footer/Footer";


✔ Lets you use the Footer component from another file.

🔹 Example 3: Import Image
import avatar from "../../assets/avatar.png";


✔ Imports an image so you can use it in <img src={avatar} />.

🔹 Example 4: Import Icons
import { FaStar } from "react-icons/fa";


✔ Imports a star icon from the react-icons library.

# Why use import?

To reuse code

Keep code organized

Use external libraries (React, icons, etc.)

# Overview

.This component is the top (hero) section of a Data Science course page.
.It gives users a quick overview of the course, including:

.Course title & tagline

.Instructor & language info

.Statistics (ratings, learners, placements)

. you'll learn

.Prerequisites

.Purchase box (buy/add to cart)

.Download brochure

.Course preview image

# Component Name
export default function HeroSection_C()


.This is a React functional component named HeroSection_C.

# Page Sections Breakdown
1.  Breadcrumb Navigation
<Link to="/">
  <AiFillHome />
</Link>
<AiOutlineRight />
<span>Master Data Science</span>


.Shows the current path: Home > Master Data Science

.AiFillHome = home icon

.Helps users know where they are on the site.

2.  Course Title + Tagline
.<h1>Master Data Science</h1>
.<p>From Zero to Data Hero – In just 12 Months!</p>


.Main heading of the course.

.Describes that it's beginner-friendly and lasts 12 months.

3.  Download Brochure Button
<a href="/Brochure/DS.pdf" download>Download Brochure</a>


.Allows users to download the course brochure as a PDF.

4. 👨 Instructor & Course Info

# Shows key metadata:

. Instructor image and name ("Data Science Expert")

. Language: Hindi, English

# Last updated: June 2025

.Uses icons/images like:

.Expert, globe, laptop

5.  Statistics Section
<div>
  <p>2000+ Got Placed</p>
  <p>4.5 ★ (31,782 reviews)</p>
  <p>10,000+ Learners</p>
</div>


.Shows credibility and success metrics of the course.

.Uses stars, avatars, and numbers to build trust.

6.  What Will You Learn?
.["Python", "SQL", "Pandas", "GitHub", ...]


.Displays a list of skills and topics you will learn.

.Styled like tags or badges (colorful rounded boxes).

7.  Prerequisites
<ul>
  <li>Basic Math</li>
  <li>Any Programming Basics (Python preferred)</li>
  <li>Curiosity to Learn</li>
  <li>No prior experience needed</li>
</ul>


.Lists what learners should know before starting the course.

.Encourages beginners by being friendly and simple.

8.  Right Side: Purchase Summary Box

This section is like a course checkout summary.

# Promotional Banner
<p>20,000+ Openings. ₹7 LPA Median. You Could Be Next!</p>


.Motivates users with potential job outcomes.

# Video Preview Image
.<img src={DS} />


.Shows a course image (placeholder for preview video).

# Course Fee
.<p>₹4,999 (One-time payment)</p>

# What's Included
<ul>
  <li>Lifetime access</li>
  <li>Cancel within 2 days</li>
  <li>Projects + mentorship</li>
  <li>Career coaching</li>
  <li>Certificate</li>
</ul>

🛒 Buttons

Buy Now → opens Razorpay payment link in a new tab.

Add to Cart → adds to user's cart (no logic shown here).

BookmarkButton → a custom component (likely saves it to favorites).

FiSend Icon → maybe for sharing (not yet functional here).

📎 Other Notes

Uses icons from react-icons (FaStar, AiFillHome, etc.).

Uses images like avatar, course banner, globe icon, etc.

Uses Tailwind CSS for styling (e.g., text-[18px], bg-[#FF6501], etc.).
# summary
| Section                          | Purpose                                          |
| -------------------------------- | ------------------------------------------------ |
| Breadcrumb Navigation            | Helps users understand their page path           |
| Course Title + Tagline           | Shows what the course is and who it's for        |
| Brochure Download                | Let users download course brochure               |
| Instructor Info                  | Shows who teaches the course                     |
| Stats (Placed, Rating, Learners) | Builds credibility and trust                     |
| What You'll Learn                | Lists key skills taught                          |
| Prerequisites                    | Describes what users should know before starting |
| Purchase Summary Box             | Lets users buy or bookmark the course easily     |

***********************************************************
#  /components/DataScience/LearningJourney.jsx
1. Data: modules array

This array contains the curriculum information:

Each module has a title (string) and a list of items (strings) representing topics or sub-modules.

There are 4 modules, each focused on different stages of learning data science — from foundational skills to interview preparation.

Example of one module object:

{
  title: "Module 1: Core Learning – Foundations & Tools",
  items: [
    "Python for Data Science",
    "Data Manipulation & Visualization",
    // more items...
  ]
}

2. Component State: openIndex
const [openIndex, setOpenIndex] = useState(null);


openIndex tracks which module is currently expanded.

Initially, no module is open (null).

Clicking a module title toggles its open/closed state by updating openIndex.

3. Function: toggleModule
const toggleModule = (index) => {
  setOpenIndex(openIndex === index ? -1 : index);
};


When a module is clicked, if it's already open (openIndex === index), it closes (sets openIndex to -1).

Otherwise, it opens that module (sets openIndex to the clicked index).

This logic ensures only one module is open at a time (accordion behavior).

4. Rendering the component
return (
  <div className="flex flex-col items-center justify-start bg-white pt-10 px-4 font-['Poppins']">
    {/* Header */}
    ...
    
    {/* Main Module Container */}
    <div className="w-full md:max-w-2xl lg:w-[723px] max-h-[790px] rounded-[10px] flex flex-col gap-[2px] bg-white shadow overflow-auto border border-gray-200">
      {modules.map((module, index) => (
        <div key={index}>
          {/* Module Title */}
          <div
            className="w-full h-[64px] px-[15px] py-[20px] flex items-center justify-between bg-[#E6E6E633] cursor-pointer rounded"
            onClick={() => toggleModule(index)}
          >
            <span className="text-[14px] md:text-[18px] font-medium font-poppins text-black">
              {module.title}
            </span>
            <svg
              className={`w-4 h-4 text-gray-700 transform transition-transform duration-300 ${
                openIndex === index ? "rotate-180" : ""
              }`}
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                strokeLinecap="round"
                strokeLinejoin="round"
                strokeWidth="2"
                d="M19 9l-7 7-7-7"
              />
            </svg>
          </div>

          {/* Sub-items */}
          {openIndex === index && module.items.length > 0 && (
            <div className="flex flex-col gap-2 px-2 py-2 bg-white">
              {module.items.map((item, idx) => (
                <div
                  key={idx}
                  className="border border-gray-200 rounded px-4 py-2 text-orange-500 sm:font-medium hover:bg-orange-50 transition text-[14px] md:text-[18px]"
                >
                  • {item}
                </div>
              ))}
            </div>
          )}
        </div>
      ))}
    </div>

    <hr className="w-full border-t-[2px] border-gray-100 mt-12 mb-6" />
  </div>
);

# Header section:

Displays the main title and a subtitle with some responsive font sizes and spacing.

Module container:

A vertically stacked list (flex flex-col gap-[2px]) with scroll overflow enabled (overflow-auto).

# Each module:

Shows the module title inside a clickable div (cursor-pointer).

Clicking toggles the module open/closed.

The arrow icon rotates 180 degrees when the module is open.

If open, it displays the list of topics/items inside a bordered box with some hover effect and orange text color for emphasis.

# Styling notes:

Uses Tailwind CSS for styling (e.g., text-orange-500, flex, rounded, etc.).

Responsive font sizes adjust with screen size (text-[14px] md:text-[18px]).

Smooth transition on the arrow icon's rotation (transition-transform duration-300).

# Summary:

This component offers a clean, user-friendly accordion view of a multi-module learning path:

Shows only one expanded module at a time.

Click on module headers to expand/collapse the list of topics.

Visually indicates expanded state by rotating the arrow.

Uses Tailwind CSS for clean and responsive styling.

Provides a clear, step-by-step learning roadmap for users interested in data science.

************************************************************************************
# src/components/DigitalMarketing/BoughtTogether.jsx

Component Structure Overview

The component is made of:

Course Data – An array of 3 digital marketing-related courses.

CourseCard – A reusable component that renders each course.

BoughtTogether – The main layout that organizes the courses, "+" and "=" symbols, pricing, and purchase button.

📦 courses Array
const courses = [
  {
    id: 1,
    title: "Ad campaign",
    rating: 4.8,
    lesson: 15,
    ...
  },
  {
    id: 2,
    title: "Video & Photo editing",
    ...
  },
  {
    id: 2, // ⚠️ Duplicate ID (Should be unique)
    title: "Graphic Designing",
    ...
  },
];


Contains 3 courses, each with:

title, rating, lesson count

description, duration, and an image.

⚠️ Issue: The last two objects have the same id: 2, which can cause problems in React (keys must be unique). It should be corrected.

# CourseCard Component

.This renders an individual course card.

. Props

# Takes a course object and displays:

. Image

. Title and description

. Number of lessons

. Duration (with time icon)

⭐ Rating (with star icon)

# Styling

tailwindcss is used for styling

Has hover effects and rounded borders

# BoughtTogether Component

This is the main layout that brings everything together.

# Heading
<h2>
  Your <span className="text-orange-500">Digital Marketing</span> Growth Path
</h2>


Large title with a highlighted keyword.

Subtitle describing the benefit: bundling for better ROI.

# Course Cards Layout
{courses.slice(0, 3).map((course, index, arr) => (
  <React.Fragment key={course.id}>
    <CourseCard course={course} />
    {index < arr.length - 1 && <span>+</span>}
  </React.Fragment>
))}


Loops through the 3 courses and renders each one with a + in between (on desktop).

After the last course, it adds an "=" block with price details.

# Pricing Block
<div className="...">
  <p className="line-through">Rs 30,000</p>
  <p className="text-[#FF6501]">Rs 9,999</p>
  <button>Purchase Now</button>
</div>


Shows original price (strikethrough) and discounted price.

Contains a Purchase Now button.

# Responsive Behavior

Uses flex-col for mobile and flex-row for desktop (via md: classes).

The + and = symbols are hidden on small screens (hidden md:block).

# Divider
<hr className="..."/>


Horizontal rule at the bottom for visual separation.
# summary 
| Feature                | Description                                       |
| ---------------------- | ------------------------------------------------- |
| **Purpose**            | Display a bundle of related courses with discount |
| **Components**         | `CourseCard`, used inside `BoughtTogether`        |
| **Styling**            | TailwindCSS, responsive design                    |
| **Interactivity**      | Purchase button (not wired to a backend yet)      |
| **Icons**              | `react-icons` (star and time)                     |
| **Improvement Needed** | Fix duplicate `id` values in the `courses` array  |

*****************************************************************
# src/components/DigitalMarketing/DM_Page.jsx

🔹 Component Overview
const DM_Page = () => {
  return (
    <div>
      ...
    </div>
  )
}


This is a functional component that returns a structured <div> containing multiple child components. Each of those represents a section of the web page.

# Imported Components

Here’s what each import likely does, based on naming conventions:

# Top of the Page

Navbar_C
Custom Navigation bar for this page — probably includes links like Home, Courses, About, etc.

HeroSection_C
The top section (hero banner), usually includes:

Big heading

Subheading

CTA button ("Enroll now")

Background image or animation

# Content Sections

LearningJourney
A step-by-step curriculum or roadmap of the course.

Example: "Week 1: Basics", "Week 2: SEO", etc.

BoughtTogether
Previously shared with you.

Shows 3 bundled courses

Highlights discounted pricing

Allows a user to purchase them together

Experts
Showcases mentors or instructors for the course.

Usually includes images, bios, expertise.

CertificateSection
A section promoting the certificate students will get upon completion.

Adds value/trust.

FlexibleCourses
Highlights course flexibility:

Self-paced?

Lifetime access?

Learn anytime, anywhere?

# Extras & Support

FAQ
Frequently Asked Questions.

Covers things like refund policy, who can join, prerequisites, etc.

DiscountBanner
Likely a limited-time discount offer banner.

CTA to enroll quickly before offer ends.

# Footer

Footer
Final part of the page. Typically includes:

Links to Terms, Privacy Policy

Contact info

Social media icons

# How It All Comes Together

This code renders a complete landing page for a Digital Marketing course by stacking prebuilt, reusable components in order.

<Navbar_C/>          // Top navigation
<HeroSection_C/>     // Main banner
<LearningJourney/>   // Curriculum layout
<BoughtTogether/>    // Bundle & pricing
<Experts/>           // Instructor showcase
<CertificateSection/>// Certificate highlight
<FlexibleCourses/>   // Flexibility benefits
<FAQ/>               // Q&A support
<DiscountBanner/>    // Final call to action
<Footer/>            // Bottom of the page

# Final Notes

Modular structure: Each section is its own component — this makes the page easier to maintain.

No state or logic inside DM_Page: It just arranges visual components — logic likely lives inside the subcomponents.

Easy to extend: You could easily add testimonials, a contact form, etc., just by inserting another component.



********************************************************************************************

# src/components/DigitalMarketing/FAQ.jsx

Overview
# Purpose:

To display common questions users might have about the course — in a collapsible accordion format using React state and Tailwind CSS.

# User Features:

Click to expand/collapse answers

FAQ items arranged in 2 columns on desktop

Button at the bottom to view all FAQs (though not yet functional)

# 1. State Management
const [openIndex, setOpenIndex] = useState(null);


openIndex: Stores the index of the currently open FAQ.

null means no FAQ is open initially.

const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


Clicking the same question again closes it.

Clicking a different one opens that new one.

# 2. FAQ Data
const faqData = [
  { question: "...", answer: "..." },
  ...
];


Array of 6 FAQ objects with:

question: Text shown to the user

answer: Hidden text shown when expanded

(Optional) button: If present, shows a call-to-action link (currently unused)

# 3. Layout Structure
Split into 2 columns:
const leftFaqs = faqData.slice(0, 3);
const rightFaqs = faqData.slice(3);


First 3 FAQs go to left column

Remaining go to right column

Overall Page Layout:
<div className="w-full p-8 font-['Poppins']">
  <h2>Frequently Asked Questions</h2>
  <p>Contact info</p>
  <div className="flex flex-col md:flex-row gap-8">
    <div className="md:w-1/2">{...left}</div>
    <div className="md:w-1/2">{...right}</div>
  </div>
</div>

# 4. Individual FAQ Item

Rendered via:

const renderFAQItem = (item, index) => (
  <div className={`...`}>
    <button onClick={() => toggleIndex(index)}>
      <span>{item.question}</span>
      {openIndex === index ? <FaTimes /> : <FaPlus />}
    </button>

    {openIndex === index && (
      <div>
        <p>{item.answer}</p>
      </div>
    )}
  </div>
);

# Behavior:

When clicked:

If closed: Opens the answer

If open: Closes it

Uses FaPlus and FaTimes icons to indicate state

# Conditional Styles:
openIndex === index ? "bg-white shadow" : "bg-white"


Adds shadow when open

# Optional Button (Commented):

There’s a placeholder for a CTA button under the answer (currently commented out), like:

<div className="bg-gray-100">
  <p>Enrollment Process</p>
  <button><FaArrowRight /></button>
</div>


Could be reused for extra links under certain FAQs.

# 5. Final "See All FAQ’s" Button
<button className="...">
  See All FAQ’s
</button>


Button exists but has no functionality yet.

Could be wired to scroll to a full FAQ page or open a modal.

# Styling

TailwindCSS for layout, colors, typography

Responsive:

Mobile: Single column

Desktop (md+): Two-column layout

Icons from react-icons:

FaPlus: Add/open

FaTimes: Close

FaArrowRight: (currently unused)
# summary
| Feature         | Description                               |
| --------------- | ----------------------------------------- |
| `useState`      | Tracks open/closed state of FAQs          |
| `faqData`       | List of question/answer objects           |
| `renderFAQItem` | Renders each collapsible item             |
| Columns         | 2 on desktop, 1 on mobile                 |
| Icons           | Plus/Close for expand/collapse            |
| CTA             | Placeholder for future links or actions   |
| Button          | “See All FAQs” — currently non-functional |

************************************************************************
# src/components/DigitalMarketing/HeroSection_C.jsx

Component: HeroSection_C

This is a React functional component named HeroSection_C, and it does not use state or props — just static layout with imported assets.

 PAGE STRUCTURE OVERVIEW

The layout has two major columns:

Left Side – Course Info	Right Side – Purchase Info
- Breadcrumb + Title	- Course video/image
- Subtitle	- Purchase Summary
- Brochure Download Button	- "Buy Now" / "Add to Cart" Buttons
- Instructor & Language Info	- Bookmark & Share icons
- Course Stats (Ratings, Learners)	
- What You Will Learn (Skill Tags)	
- Prerequisites	
 1. Breadcrumbs + Title Section
<nav className="...">
  <Link to="/"><AiFillHome /></Link>
  <AiOutlineRight />
  <span>Master Digital Marketing</span>
</nav>


Shows:

Home icon → "Master Digital Marketing"

Lets the user know their current page path

# Below the breadcrumb:
<h1>Master Digital Marketing</h1>
<p>Build <span>AI-Powered</span> Brand & <span>Grow Digitally</span></p>


Title and catchy subtitle

Orange highlighted keywords for emphasis

 2. Brochure Download
<a href="/Brochure/DM.pdf" download="DigitalMarketing_Brochure.pdf">Download Brochure</a>


Triggers PDF download

Button is styled with Tailwind and visible on all devices

 3. Instructor Info

.Shows three icons (each with text):

Icon	Text
🧑‍🏫 Expert	Digital Marketing Expert
🌐 Globe	Hindi, English
💻 Laptop	Last updated – June 2025
 4. Course Stats Summary (Black Box)
<div className="... bg-black text-white">
  <div>2000+ Got Placed</div>
  <div>4.5 ⭐ 31782 Reviews</div>
  <div>10,000+ Learners + avatar image</div>
</div>


Visually bold summary to build trust

Dynamically shows:

Placement success

Star ratings using FaStar

Learner count with icon

 5. What Will You Learn? (Skill Tags)
[
  "SEO", "Google Ads", "Funnel Creation", ...
]


Mapped to badge-style UI elements:

<span className="...">SEO</span>


Skills are highlighted using a styled rounded button-style badge

6. Prerequisites List

Basic user-friendly list:

<ul>
  <li>Basic Computer Skills</li>
  <li>Creative Mindset</li>
  ...
</ul>


Uses a bullet list styled for readability

Great for beginners — emphasizes no prior experience needed

 7. Right Side (Purchase Section)
🔸 CTA Header:
<p>20,000+ Openings. ₹7 LPA Median.</p>
<p>Start your journey with Baoiam's expert-led training.</p>


Builds urgency and aspiration using outcomes

🔸 Preview Image:
<img src={DM} alt="Course Preview" />


Could be replaced with a video in the future

Static for now

# Purchase Summary:
<p>Course Fee: ₹4,999 (One-time)</p>
<ul>
  <li>Lifetime access</li>
  <li>2-day refund</li>
  <li>Expert mentorship</li>
  ...
</ul>


Clear value proposition to justify price.

# Action Buttons
<button onClick={() => window.open(...)}>Buy Now</button>
<button>Add to Cart</button>
<BookmarkButton />
<FiSend />  // Share icon


Buy Now: Opens Razorpay checkout

Add to Cart: Placeholder (needs logic)

BookmarkButton: Custom component for saving course

FiSend: Share button (no logic attached yet)

# Final Divider
<hr className="..." />


Visual break before next section (modular design)
# summary

| Section                | Purpose                                         |
| ---------------------- | ----------------------------------------------- |
| Breadcrumb + Title     | Help users navigate and know where they are     |
| Brochure Button        | Quick download for offline access               |
| Stats                  | Social proof to build trust                     |
| Skills & Prerequisites | Set clear expectations                          |
| Right Panel            | Drives conversions (buy, cart, download)        |
| CTA Copywriting        | High-conversion language (₹7 LPA, 20K openings) |
| Responsive Layout      | Flexibly adapts to all screen sizes             |

********************************************************************************
# src/components/DigitalMarketing/LearningJourney.jsx

# Component Summary

Purpose: To display an accordion-style layout of a digital marketing course roadmap.

Main Features:

Responsive design using Tailwind CSS.

Accordion behavior (one module expands at a time).

Toggle to expand/collapse module details.

🔹1. Data (Modules Array)
const modules = [
  {
    title: "Module 1: ...",
    items: [
      "Item 1",
      "Item 2",
      ...
    ]
  },
  ...
];


A structured array of course modules.

Each module has a title and a list of items (topics).

🔹2. State Management
const [openIndex, setOpenIndex] = useState(null);


openIndex holds the index of the currently open module.

Initially, no module is open (null).

🔹3. Toggle Function
const toggleModule = (index) => {
  setOpenIndex(openIndex === index ? -1 : index);
};


If the clicked module is already open, close it.

Else, open the clicked module.

🔹4. JSX Rendering
# Header
<h1>Your <span className="text-orange-500">Data Science</span> Growth Path</h1>
<p>Follow an expertly curated roadmap...</p>


Displays a heading and subtext.

Note: The heading says “Data Science”, but your modules are about Digital Marketing — is that a typo?

# Modules List (Accordion)
{modules.map((module, index) => (
  <div key={index}>
    <div onClick={() => toggleModule(index)}> ... </div>

    {openIndex === index && (
      <div>
        {module.items.map(item => (
          <div>• {item}</div>
        ))}
      </div>
    )}
  </div>
))}


Maps through the modules array.

When a module is clicked:

If already open, it collapses.

Otherwise, it opens and displays its items.

# Styling (Tailwind CSS)

text-[14px] md:text-[18px]: Responsive text size.

bg-[#E6E6E633]: Light gray background for module header.

shadow, rounded, overflow-auto: Card-style box with scroll for longer content.

hover:bg-orange-50: Hover effect for module items.

Chevron SVG icon rotates when module is open.

# Final Touch (HR Line)
<hr className="w-full border-t-[2px] border-gray-100 mt-12 mb-6" />


Decorative horizontal line at the bottom.

⚠️ Minor Suggestion

In the header:

<h1 className="...">
  Your <span className="text-orange-500">Data Science</span> Growth Path
</h1>


But the modules are about Digital Marketing.

# Change to:

<span className="text-orange-500">Digital Marketing</span>

# Summary of What This Does

Displays a clean, interactive, mobile-friendly learning path.

Easy to navigate with collapsible sections.

Professional and simple layout using Tailwind CSS.

**********************************************************
# src/components/Footer/Contact.jsx
Imports and Setup
import logo from "../../assets/Home/Navbar/logoLight.webp";
import MobileMockup from "../../assets/Footer/Contact/Mobile_Mockups.png";
import ThankYou from "../../assets/Footer/Contact/ThankYou.png";
import { useState } from "react";
import { API_ENDPOINTS } from "../../Config/api";


logo, MobileMockup, ThankYou: Local image assets.

useState: React hook to manage component state.

API_ENDPOINTS: Contains your backend API URLs.

⚙️ State Variables
const [showModal, setShowModal] = useState(false);
const [mobileNumber, setMobileNumber] = useState("");
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);


showModal: Controls visibility of the "Thank You" modal.

mobileNumber: Stores user input.

isLoading: Shows loading state while API call is in progress.

error: Displays validation or server errors.

📞 handleGetCallback Function
🔹 Purpose

Triggered when user clicks “Get Callback”.

🔹 Flow
if (!mobileNumber.trim()) {
  setError("Please enter a valid mobile number");
  return;
}


Empty Check – Ensures the user has entered something.

const mobileRegex = /^[0-9]{10}$/;
if (!mobileRegex.test(mobileNumber.trim())) {
  setError("Please enter a valid 10-digit mobile number");
  return;
}


Regex Validation – Checks for a valid 10-digit mobile number.

const response = await fetch(API_ENDPOINTS.CONTACT_SUBMIT, { ... });


API Call – Sends a POST request with:

{
  "mobile_number": "9876543210",
  "country_code": "+91"
}

if (response.ok) {
  openModal();         // Show Thank You modal
  setMobileNumber(""); // Clear input
} else {
  setError(...);       // Show error if backend responds with failure
}


Handles success and error cases gracefully.

🧱 Component Layout
🧭 Layout Overview
<div className="w-full bg-gray-100 ...">
  <div className="flex flex-col md:flex-row ...">
    {/* Text Column */}
    {/* Image Column */}
  </div>
</div>


Responsive design:

On mobile: Stack items (flex-col)

On desktop: Side-by-side (md:flex-row)

📑 Text Column (Left)
🔹 Logo and Description
<img src={logo} ... />
<p>BAOIAM is India's leading ...</p>


Shows company logo and description of the platform.

🔹 Callback Prompt
<p>Confused where to start? ...</p>


Encourages user to request a callback by entering a number.

🔹 Input + Button
<select>+91</select>
<input value={mobileNumber} ... />
<button onClick={handleGetCallback}>Get Callback</button>


Input Group:

Country code (static select for now)

Phone number input

Get Callback button (disabled during API call)

🔹 Error Message
{error && (
  <div className="text-red-500">{error}</div>
)}


Displays any validation or server-side error below the button.

🔹 Contact Info
<p>08062181972</p>
<p>support@baoiam.com</p>


Static contact details for phone and email.

🖼️ Image Column (Right)
<img src={MobileMockup} alt="..." />


Responsive mobile mockup image to visually balance the contact section.

✅ Modal – Thank You Screen
{showModal && (
  <div className="fixed inset-0 z-50 flex items-center justify-center">
    <div className="relative animate-bounceUpToCenter">
      <button onClick={closeModal}>×</button>
      <img src={ThankYou} />
    </div>
  </div>
)}


Appears after successful submission.

Includes:

Close (×) button

“Thank You” image

animate-bounceUpToCenter: Likely a custom animation class (not native Tailwind).

🎨 Styling Notes (Tailwind CSS)

rounded-lg, border, bg-white, shadow, hover:bg-orange-600 etc. are used for clean modern UI.

Responsive design handled with sm:, md:, w-full, flex-col etc.

Accessible form with clear feedback.

# summary
| Feature                      | Description                                                     |
| ---------------------------- | --------------------------------------------------------------- |
| . Mobile number input       | Users can enter their number to request a callback              |
| #. Validates 10-digit numbers | Ensures only proper numbers are submitted                       |
| . API POST request          | Sends number to server for callback                             |
| . Modal on success           | Shows a friendly “Thank You” pop-up                             |
| . Error feedback            | Shows inline error messages for invalid input or network issues |
| . Visual + brand design     | Uses company logo, mobile mockup, and nice visuals              |


****************************************************************************************

# src/components/Footer/Footer.jsx

Component Structure Overview

The Footer has 3 main sections:

Top Footer

Logo + Description

Social Media Icons

Dynamic Footer Links (via reusable component)

App Download Buttons

Divider

Bottom Footer

Copyright

Language Selector

🔁 Reusable Subcomponent: FooterLinksSection
const FooterLinksSection = ({ heading, items }) => {
  ...
};

🔹 Purpose:

Renders a titled list of links.

Makes the Footer modular and easy to update.

🔹 Props:

heading: Section title like "SUPPORT", "TOP 4 CATEGORY".

items: An array of objects with label and href.

🔹 Styling and UX:

Uses Tailwind for spacing and hover styles.

Includes a subtle FaArrowRight icon animation that:

Slides in on hover

Uses opacity and translate-x for smooth transition

# Main Component: Footer
const Footer = () => { ... }

 1. Data Setup
const footerData = [
  { heading: "TOP 4 CATEGORY", items: [...] },
  { heading: "QUICK LINKS", items: [...] },
  { heading: "SUPPORT", items: [...] },
];


Each section will be rendered by FooterLinksSection.

 2. Logo + Social Media Icons
<img src={logo} alt="Baoiam Logo" />
<p>Follow us for the latest updates...</p>
<Link to="facebook.com/..."><FaFacebookF /></Link>
...


Social Icons (Facebook, Instagram, LinkedIn, Twitter, YouTube)

Each wrapped in a Link (probably should be an <a> with href)

External links open in new tabs (target="_blank")

Styling:

Icons in a gray background bg-[#363B4766]

On hover: changes to orange (hover:bg-orange-500)

 3. Dynamic Footer Sections
{footerData.map((section, index) => (
  <FooterLinksSection
    key={index}
    heading={section.heading}
    items={section.items}
  />
))}


Each section of links is created from footerData using the reusable component.

 4. App Download Buttons
<img src={applelogo} alt="App Store" />
<img src={googlelogo} alt="Google Play" />


Links to App Store / Play Store (though both currently point to Play Store).

Tailwind-controlled sizing for responsive design.

 5. Divider
<hr className="w-full border-t border-gray-700" />


Visually separates top and bottom footer.

# 6. Bottom Footer Section
<p>© 2021 - Designed by Baoiam...</p>
<select name="language">...</select>


.Left: Copyright

.Right: Language Selector

.Options: English, Hindi, Marathi, Bengali

.UI only (no logic implemented for language switching)

🖼️ Styling Highlights

.Font: 'Poppins'

.Background: bg-[#1D2026] (dark gray)

.Responsive:

.flex-wrap ensures good layout on small screens

.md: and sm: breakpoints for better spacing

.Text color:

.Default: text-gray-500

.Headings: text-white

.Hover states: hover:text-white, hover:underline, icon animation

. Suggestions & Improvements
. Code Optimizations

# Use <a href=...> for external links instead of Link from react-router-dom.

<a href="https://x.com/baoiam1" target="_blank" rel="noopener noreferrer">
  <FaTwitter />
</a>


⚠️ Both app download links currently go to Play Store — fix the Apple one if available:

<a href="https://apps.apple.com/..."> <!-- for Apple logo -->

# Language Selector Functionality

Currently, it’s just a UI dropdown.

You could add i18n support with react-i18next or similar to make it functional.

# Accessibility

Add aria-labels to social icons for screen readers.

Ensure alt texts on images are descriptive.

***************************************************************************
# src/components/Home/DataScienceBanner.jsx
Component Setup
import React, { useState } from "react";
import rocket from "../../assets/Home/DataScienceBanner/rocket.webp";
import human from "../../assets/Home/DataScienceBanner/human.webp";
import { Link } from "react-router-dom";
import ContactForm from "../../Pages/ContactForm";


Imports necessary assets and tools:

rocket and human: Images used in the banner

Link: For internal routing (React Router)

ContactForm: A modal form for users to contact a counsellor

Uses useState to control modal visibility (showModal)

 2. Main Wrapper <div>
<div className="...">...</div>

# Purpose:

Full-width container with rounded corners, shadow, responsive padding, and orange gradient background

Tailwind is used heavily for styling

max-w-[1200px] centers the content and prevents it from stretching too wide

# Background Style:
background: linear-gradient(
  180deg,
  rgba(255, 101, 1, 0.06) 0%,
  rgba(255, 101, 1, 0.6) 100%
)


Smooth orange gradient from light (top) to dark (bottom)

 3. Left Section (Text + Buttons)
<div className="flex flex-col flex-1 min-w-[250px]">...</div>

a. 🔸 Rocket + Headline
<img src={rocket} />
<h1>Data Science Career</h1>
<p>Starts at ~₹79,999~ ₹4,999</p>


The rocket image emphasizes "career launch"

Responsive heading and price info

Old price: crossed out

New price: highlighted in orange

b. 🔸 Features Row
<p>
  <span className="text-orange-500">12 Months</span> | 
  <span className="text-black">Live classes</span> | 
  <span className="text-orange-500">Projects</span> | 
  <span className="text-black">Placement Support</span>
</p>


A quick value summary of what’s included

Alternating colors for visual appeal

c. 🔸 Buttons
<Link to="/DataScience">
  <button className="bg-black text-white">Enroll Now</button>
</Link>


"Enroll Now": Routes user to the Data Science program page

<button onClick={() => setShowModal(true)}>Talk to our Counsellor</button>


"Talk to our Counsellor": Opens a modal with a contact form

 4. Modal Logic (Contact Form)
{showModal && (
  <div className="fixed inset-0 z-50 flex items-center justify-center bg-opacity-50" onClick={...}>
    <div className="relative max-w-xl w-full" onClick={(e) => e.stopPropagation()}>
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}

# Features:

Covers full screen (fixed inset-0)

Dark transparent overlay (bg-opacity-50)

Clicking outside the form closes the modal

Clicking inside does not close it (e.stopPropagation())

 5. Right Section (Human Image)
<img src={human} alt="Data Analytics" />


Displays a human character image, likely used to humanize the banner

Positioned to the right using margin (sm:ml-6 md:ml-8)

Responsive sizing from mobile to desktop
# summary
| Feature                    | Details                                                        |
| -------------------------- | -------------------------------------------------------------- |
|  **Goal**                | Promote the Data Science program visually                      |
|  **Styling**             | Uses orange gradients, bold text, rounded corners              |
|  **CTAs**             | “Enroll Now” (navigation) and “Talk to our Counsellor” (modal) |
|  **Modal Functionality** | Clean and accessible with escape on background click           |
|  **Imagery**            | Rocket (aspiration) and Human (relatability)                   |


*****************************************************************************************

# src/components/Home/FAQSection.jsx
1. Imports
import React, { useState } from "react";
import FAQ_Img from "../../assets/Home/FAQ/FAQ_Img.webp";
import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";


FAQ_Img: Image used for visual design

Icons: Plus (+) to expand, Times (×) to collapse, Arrow (for optional link)

2. FAQ Data Array
const faqData = [ { question: "...", answer: "..." }, ... ];


Each FAQ has:

question: The title of the FAQ

answer: The detailed explanation

Optional:

Some items can contain a button (commented out in your code)

3. State Hook for Toggle
const [openIndex, setOpenIndex] = useState(null);


Tracks which question is currently expanded

null means none are open

Toggle Logic:
const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


Clicking a question:

Opens it if it was closed

Closes it if it was already open

🖼️ 4. Left Panel (Image + Text)
<div className="w-full md:w-1/2 ...">
  <h2>Frequently Asked Questions</h2>
  <p>Contact info</p>
  <button>See All FAQs</button>
  <img src={FAQ_Img} />
</div>

✅ Highlights:

Heading + Subheading

Contact email link

Placeholder button (non-functional)

Static image with gradient fade at bottom for aesthetics

📋 5. Right Panel (FAQ Accordion)
<div className="space-y-4">
  {faqData.map((item, index) => (
    <div className="...">
      <button onClick={() => toggleIndex(index)}>
        <span>{item.question}</span>
        <span>{openIndex === index ? <FaTimes /> : <FaPlus />}</span>
      </button>

      {openIndex === index && (
        <div className="...">
          <p>{item.answer}</p>
          {item.button && <a href={...}>...</a>}
        </div>
      )}
    </div>
  ))}
</div>

✅ Behavior:

Each item shows the question and an icon (plus/close)

On click, it toggles the answer visibility

If open, the answer shows below with optional CTA link

✨ Styling:

Rounded corners, shadows, padding

Clean visual transitions
# summary
| Feature              | Description                                    |
| -------------------- | ---------------------------------------------- |
| . Accordion behavior | Only one FAQ is open at a time                 |
| . Responsive design | Mobile-friendly layout                         |
| . Visual feedback   | Icons + shadows + transition                   |
| . Contact link      | Directs users to email for help                |
| . Clean separation  | Left = Info; Right = FAQs                      |
| . Extensible       | Can add `button` per FAQ (currently commented) |

**************************************************************************
# src/components/Home/FeaturedCourses.jsx
1. Imports
import React, { useState } from "react";
import { FaStar, FaUserGraduate, FaClock } from "react-icons/fa";
import { FiBarChart } from "react-icons/fi";
import { Link } from "react-router-dom";
import { useMediaQuery } from "react-responsive";
import Slider from "react-slick";
import ContactForm from "../../Pages/ContactForm";


react-icons: Icons for ratings, students, level, and duration

ContactForm: Modal that appears when clicking "Explore more"

useMediaQuery: For responsive layout detection (desktop vs mobile)

Slider: Slick carousel for mobile view

2. Course Data
const courses = [
  {
    id: 1,
    title: "Data Science",
    rating: 4.8,
    description: "Build models and extract insights.",
    students: "150.3K",
    level: "Intermediate",
    duration: "45 hours",
    image: DS,
  },
  ...
];


Hardcoded course information

You could replace this with data from an API later if needed

3. Component Setup & State
const [showModal, setShowModal] = useState(false);
const isDesktop = useMediaQuery({ query: "(min-width: 1024px)" });


showModal: Controls whether the contact modal is shown

isDesktop: Detects if the user is on a desktop screen (>=1024px)

4. Slider Settings (Mobile Carousel)
const sliderSettings = {
  dots: true,
  infinite: true,
  speed: 500,
  slidesToShow: 1,
  slidesToScroll: 1,
  autoplay: true,
  ...
};


Used only in mobile view (isDesktop === false)

5. Main Section Layout
<section className="...">...</section>


Uses Tailwind for spacing, font, border, and shadow

This container wraps everything: heading, course grid/slider, and button

6. Header
<h2 className="text-center ...">
  Featured <span className="text-orange-500">Courses</span>
</h2>
<img src={Group} alt="" />


Visual heading for the section + decorative image

7. Desktop View (Grid)
{isDesktop ? (
  <div className="grid grid-cols-4 ...">
    {courses.map((course) => (
      <div key={course.id} className="card">
        ...
      </div>
    ))}
  </div>


A 4-column grid layout for desktop

For each course, shows:

✅ Title
✅ Rating with stars
✅ Image
✅ Description
✅ Number of students enrolled
✅ Course level + duration
✅ Start Learning button linked to a page (/DataScience, etc.)

8. Mobile View (Slider)
) : (
  <Slider {...sliderSettings}>
    {courses.map((course) => (
      <div key={course.id}>...</div>
    ))}
  </Slider>
)}


Carousel-based layout using react-slick

Same content as the desktop grid, but scrollable in a carousel format

9. "Start Learning" Button
<Link to={
  course.id === 1 ? "/DataScience" :
  course.id === 2 ? "/DataAnalysis" :
  ...
}>
  Start Learning
</Link>


Navigates to respective course page

Button styling includes background hover animation

10. "Explore More" Button + Modal
<button onClick={() => setShowModal(true)}>Explore more →</button>

{showModal && (
  <div className="modal" onClick={...}>
    <div onClick={(e) => e.stopPropagation()}>
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}


Appears below all course cards

When clicked, opens a modal (ContactForm)

Modal background click closes it
# summary
| Feature                 | Description                                               |
| ----------------------- | --------------------------------------------------------- |
| . Responsive           | Uses `react-responsive` to switch between grid and slider |
| . Visually rich cards | Tailwind + box shadows + icons                            |
| . Carousel             | Mobile-friendly scrollable cards                          |
| . Routing              | Each course button links to a dedicated route             |
| . Modular modal        | Contact form pops up for "Explore more"                   |
| . Clean data           | Separated course info in `courses` array                  |


*********************************************************************************
# src/components/Home/FoundersNote.jsx
1. Imports
import React from "react";
import Group from "../../assets/Home/Lines/Group.webp";
import Founder from "../../assets/Home/Founder/Founder.png";
import { FaQuoteLeft, FaQuoteRight } from "react-icons/fa";


Group & Founder: Image assets used in the layout

FaQuoteLeft, FaQuoteRight: Decorative quote icons from FontAwesome for aesthetic enhancement

2. Wrapper Container
<div className="mx-auto px-6 py-12 font-['Poppins']">


Center aligned container with padding

Font set to Poppins

3. Header Title: “Founder Note”
<div className="flex items-center justify-center w-full">
  <h2 className="text-3xl md:text-[48px] text-orange-500 font-semibold">
    Founder <span className="text-black">Note</span>
  </h2>
  <img src={Group} alt="" className="w-9 mb-4" />
</div>


Title is large and bold with color emphasis: “Founder” in orange and “Note” in black

Decorative line image (Group) beside the heading

4. Subtitle: From the Desk of Siddharth Tomar
<p className="text-lg sm:text-xl md:text-2xl mt-2 text-center mb-6">
  From the Desk of <span className="text-orange-500">Siddharth Tomar,</span> Founder <span className="text-orange-500">– BAOIAM</span>
</p>


Informal but respectful introduction of the founder

Uses orange highlights for name and brand emphasis

5. Main Content Box (Split Layout)
<div className="flex items-center justify-center min-h-screen">
  <div className="bg-white rounded-xl shadow-md ... flex flex-col md:flex-row">


White background box with rounded corners + shadow

Responsive flexbox: vertical on mobile, horizontal on desktop (md:flex-row)

Contains two main sections: left (image + intro), right (note content)

6. Left Section – Image and Founder Info
<div className="text-white flex flex-col items-center ... bg-gradient-to-t from-orange-500 to-pink-200">
  <img src={Founder} alt="Siddharth Tomar" />
  <h2>Siddharth Tomar</h2>
  <p>Founder and CEO – BAOIAM</p>
</div>


Displays founder's image in a circle

Gradient background from orange to a light tone

Text: Name, Title, and short bio including roles like Speaker and Mentor

7. Right Section – Full Note (Only on Desktop)
<div className="hidden md:flex ...">
  <FaQuoteLeft />
  <p>...detailed message...</p>
  <FaQuoteRight />
</div>


Hidden on mobile (hidden md:flex)

Includes left and right quote icons

Long-form motivational message explaining:

Why BAOIAM was founded

The issue with overpriced education

Emphasis on affordable, practical, outcome-driven learning

Ends with a personal commitment from the founder

8. Right Section – Mobile View (Short Note)
<div className="block md:hidden p-6 ...">
  <h3>A Note from the Founder</h3>
  <p>Short summary of the message...</p>
</div>


Visible only on mobile (block md:hidden)

Summarized version of the founder’s message

Focused, punchy, and easier to read on small screens

Ends with – Siddharth Tomar, Founder
# summary
| Feature                | Implementation                                                   |
| ---------------------- | ---------------------------------------------------------------- |
| . Gradient Background | Orange-to-light tone for the founder section                     |
| . Image Styling      | Circle, responsive sizes                                         |
| . Rich Typography     | Tailwind text utilities + Poppins font                           |
| . Responsive Layout   | Full note on desktop, summarized note on mobile                  |
| . Personal Tone      | Makes the message trustworthy and relatable                      |
| . Purposeful Quotes   | Left/right icons add a professional, testimonial-like appearance |


*************************************************************************************************
# src/components/Home/HeroSection.jsx
IMPORTS
import React, { useState } from "react";
import StatsSection from "./StatsSection"; // (not used here)
import { motion } from "framer-motion"; // for animations
import img1 - img6 from assets... // images used in scrollers
import ContactForm from "../../Pages/ContactForm"; // modal content
import { Link } from "react-router-dom"; // for navigation (some parts commented)

# COMPONENT: HeroSection
# useState
const [showModal, setShowModal] = useState(false);


Tracks whether the modal (with contact form) is visible.

# STRUCTURE
<section className="...">...</section>


This is the main container with padding, max width, centered, and custom fonts. Inside:

1️# Content Section (Left Column)
<div className="flex flex-col w-full md:w-[650px]">

# Headline
<h3>Learn. Build. <span className="text-orange-500">Get Hired.</span></h3>


Bold, responsive typography with highlight color.

# Subheading
<p>Where talent meets training and dreams take off...</p>


Motivational paragraph describing what Baoiam offers.

# "What brings you to Baoiam" Section

Lists reasons a user might be visiting the site:

<ul>
  <li>Launch my career with job-ready skills</li>
  ...
</ul>


Each item is a radio input styled with hover effects and better visuals.

# Action Buttons

Two buttons:

Apply Now

Talk to our Counsellor

<button onClick={() => setShowModal(true)}>Apply Now →</button>


Both buttons open a modal using the same showModal state.

📬 MODAL Logic
{showModal && (
  <div className="fixed inset-0 ...">
    <div onClick={(e) => e.stopPropagation()}>
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}


The modal is a full-screen overlay.

Clicking outside the form closes the modal.

Clicking inside (stopPropagation) keeps it open.

The actual form is in ContactForm, which receives an onClose callback.

🟠 Issue: Modal is duplicated for both buttons and shares the same state. So clicking either shows the same modal. If you want two different modals, use separate state variables.

2️⃣ Image Scrollers (Right Column)
<div className="flex justify-center sm:gap-8 ...">

🎞️ Two vertical scrollers

Each uses framer-motion's motion.div to animate a vertical scroll.

The images scroll continuously from top to bottom (looped animation).

A delay is added on the second scroller to make them offset visually.

<motion.div animate={{ y: ["0%", "-50%"] }} transition={{ duration: 15, repeat: Infinity }}>
  <img src={img1} ... />
  ...
</motion.div>


The scrollers have gradient overlays at top and bottom (bg-gradient-to-b, etc.) to create a fade effect.


************************************************************************************************

#
Imports
import ComponentName from './ComponentPath';


You're importing multiple components, each likely representing a section of the home page.

🎯 COMPONENT: HomePage
export default function HomePage() {
  return (
    <div>
      ...
    </div>
  );
}


This functional component renders a sequence of sections using JSX, laid out top to bottom in a <div>. It's essentially assembling a page from smaller building blocks.

# BREAKDOWN OF COMPONENTS
| Component             |      Purpose                                                          |
------------------------------------------------------------------------ |
| **HeroSection**       | The top section: main headline, animated images, call-to-action buttons. |
| **StatsSection**      | Likely shows key stats — e.g. number of students, mentors, job offers.   |
| **OurProgram**        | Introduces the program or curriculum offered.                            |
| **Webinars**          | Might display upcoming or past webinars/events.                          |
| **FeaturedCourses**   | Highlights selected or popular courses.                                  |
| **DataScienceBanner** | Probably a banner promoting a Data Science course or path.               |
| **InsightsSection**   | Could include blogs, articles, or student success stories.               |
| **StandOut**          | Might show how the platform stands out from competitors.                 |
| **Partner**           | Displays logos or mentions of hiring/training partners.                  |
| **TeamSection**       | Introduces mentors, founders, or teaching team.                          |
| **FoundersNote**      | A message or story from the founder(s).                                  |
| **Prestige**          | Showcases awards, recognitions, or media features.                       |
| **Testimonial**       | User reviews or success stories.                                         |
| **FAQSection**        | Frequently Asked Questions.                                              |
| **Contact**           | Contact form or inquiry section.                                         |
| **Footer**            | Footer with links, copyright, etc.                                       |

🔁 JSX Rendering Order

The components are rendered in this order:

Hero → Stats → Our Program → Webinars → Featured Courses → Data Science Banner →
Insights → StandOut → Partners → Team → Founders Note → Prestige → Testimonials → FAQ → Contact → Footer


This layout matches the natural flow of a modern conversion-focused landing page:

Grab Attention (Hero)

Establish Credibility (Stats, Testimonials)

Present Value (Program, Courses, Insights)

Drive Trust (Team, Founders Note, Prestige, Partners)

Handle Objections (FAQs)

Prompt Action (Contact, Footer)
*******************************************************************************
# src/components/Home/InsightsSection.jsx
IMPORTS
import React from "react";
import img1 to img7 from "../../assets/Home/InsightsSection/..."
import HeadingImage from "../Lines/HeadingImages";


img1 to img7: Images used in the visual gallery.

HeadingImage: Likely a custom component that renders a styled heading like "Our Insights" with part of it (e.g. "Insights") highlighted.

# COMPONENT STRUCTURE
export default function InsightsSection() {
  return (
    <section className="...">
      <div className="...">
        {/* Heading */}
        <HeadingImage title="Our" highlight="Insights" />
        <p>...</p>

        {/* Grid Layout with Images */}
        <div className="grid ...">
          {/* 7 Image Containers */}
        </div>
      </div>
    </section>
  );
}

# STYLING LAYERS
<section>
<section className="mt-12 bg-gray-100 py-8 px-4 flex justify-center min-h-[1040px]">


Adds vertical margin, background color, and padding.

Ensures content is centered horizontally.

Minimum height for the section.

# Inner Container (<div> inside section)
<div className="rounded-[30px] ... max-w-[1180px]">


Adds padding and a rounded container.

Sets a max-width of 1180px to control layout size.

Adjusts height on large screens (lg:h-[745px]).

# Heading Section
<HeadingImage title="Our" highlight="Insights" />
<p>We teach real-world skills...</p>


A prominent title ("Our Insights") styled by HeadingImage.

Descriptive subtext beneath the title, centered.

# GRID IMAGE LAYOUT

The most complex part is the responsive grid layout for images.

<div className="grid ... grid-cols-1 sm:grid-cols-2 lg:grid-cols-[294px_268px_468px] ...">

# Grid Config:

Mobile (grid-cols-1): 1 column

Tablet (sm:grid-cols-2): 2 columns

Desktop (lg:grid-cols-[294px_268px_468px]): 3 custom-width columns

Rows: 2 rows on desktop (lg:grid-rows-[326px_364px])

Custom row positions (row-start-*) used for layout

# IMAGE BLOCKS

There are 7 image blocks. Here's how they are laid out:

# Image 1
<img src={img1} />


Basic full-width image in the grid.

# Image 2
<div className="... sm:col-span-2 lg:col-span-2">
  <img src={img2} />
</div>


Spans 2 columns on tablet and desktop.

Large wide image block.

# Images 3, 4, 5
row-start-3 / row-start-4 / row-start-5


Strategically placed to create a staggered effect.

Height controlled (h-[250px] to lg:h-full).

# Image 5 is special: it contains 3 stacked images
<div className="flex flex-col gap-2">
  <div><img src={img5} /></div>
  <div className="flex gap-2">
    <div><img src={img6} /></div>
    <div><img src={img7} /></div>
  </div>
</div>


Top part: 1 image (img5)

Bottom part: 2 side-by-side images (img6, img7)

Layout creates a visual ending block on the bottom-right

***********************************************************************
#  src/components/Home/Navbar.jsx
Imports Explained
import React, { useState } from "react";
import { IoMoon } from "react-icons/io5"; // Theme toggle (not implemented fully)
import { FaChevronDown, FaChevronUp } from "react-icons/fa"; // Dropdown icons

// Logo and gif for Refer & Earn
import lightLogo from "../../assets/Home/Navbar/logoLight.webp";
import giftbox from "../../assets/Home/Navbar/gift.gif";

// Routing components
import { NavLink, Link, useNavigate } from "react-router-dom";

// Avatar images for random profile selection
import avatar1 to avatar12 from "../../assets/Home/Navbar/...";

# State Variables Used
const [isKickstarterHovered, setIsKickstarterHovered] = useState(false);
const [isCompanyHovered, setIsCompanyHovered] = useState(false);
const [isProgramsHovered, setIsProgramsHovered] = useState(false);
const [selectedCategory, setSelectedCategory] = useState(null);
const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
const [mobileKickstarterOpen, setMobileKickstarterOpen] = useState(false);
const [mobileCompanyOpen, setMobileCompanyOpen] = useState(false);
const [mobileProgramsOpen, setMobileProgramsOpen] = useState(false);
const [openSubcategory, setOpenSubcategory] = useState(null);
const [showProfileDropdown, setShowProfileDropdown] = useState(false);


These handle dropdowns, toggles, and hover states for both desktop and mobile.

# Kickstarter Courses Object

A nested object to define course categories and subcategories:

const kickstarterCourses = {
  "Success Fusion Program": [ ... ],
  "Udaan 90": [ ... ],
  "AI & ML": [ ... ]
}


Used in both desktop and mobile dropdowns dynamically.

# Random Profile Image
const [profileImage] = useState(() => {
  const randomIndex = Math.floor(Math.random() * profileImages.length);
  return profileImages[randomIndex];
});


Selects a random avatar on component mount.

Used to display the user profile image if logged in.

# Main Rendered JSX Structure
# <nav> Element

Sticky navbar with:

Logo on the left

Links/menu in the center (only visible on desktop)

Sign up / Profile / Hamburger button on the right

# Center Navigation Links

Rendered using <ul><li> elements:

Link/Dropdown	Behavior
PAP	Simple link
Kickstarter	Hover dropdown (multi-level)
Programs	Hover dropdown (3 items)
Pride	Styled link (gradient)
Refer & Earn	Animated gift icon + link
Company	Hover dropdown
# Kickstarter Dropdown Logic

Hover reveals categories like "Udaan 90"

Clicking a category toggles subcategories

Icons (FaChevronUp, FaChevronDown) show expanded/collapsed state

# Programs and Company Dropdowns

Simple single-level dropdowns

Uses hover for desktop, click for mobile

# Right Section
🔘 Sign-Up / Profile Button

If logged in: Shows a random profile avatar

Clicking it shows a profile dropdown with:

Profile

Dashboard

Logout

If not logged in: Shows "Sign Up" button

# Hamburger Menu (mobile only)

Shows an icon (☰ or ❌) to open/close mobile dropdown

Controlled with mobileMenuOpen

# Mobile Dropdown Menu

Only rendered when mobileMenuOpen === true

Contains:

All main links (PAP, Programs, Kickstarter, Pride, Company, etc.)

Uses setMobileProgramsOpen, setMobileKickstarterOpen, etc. for expanding submenus

Structured in vertical stacked layout

Includes all nested course categories from the object

# Logout Function
const handleLogout = () => {
  onLogout(); // callback from parent
  setShowProfileDropdown(false);
  navigate("/"); // redirect to homepage
};

# Tailwind Styling

Used throughout for:

Spacing (mt-20, px-4, py-2)

Responsive classes (md:hidden, lg:flex)

Colors and borders (bg-[#FFFAF7], hover:bg-orange-500)

Layout (flex, grid, space-x-4, rounded-full)

Text styles (text-black, text-[18px], font-poppins)

# Props Received
const Navbar = ({ onSignUpClick, isLoggedIn, onLogout }) => { ... }


These are expected from the parent:

onSignUpClick: function to open sign-up modal or redirect

isLoggedIn: boolean, controls profile/sign-up display

onLogout: callback to handle logout logic

********************************************************
# src/components/Home/OurProgram.jsx
IMPORTS
import udaanImg from "../../assets/Home/OurProgram/Udaan2.png";
import fusionImg from "../../assets/Home/OurProgram/SFP_02.png";
import Head from "../../assets/Home/OurProgram/head.webp";
import HeadingImage from "../Lines/HeadingImages";
import SubHeadImg from "../Lines/SubHeading";
import ContactForm from "../../Pages/ContactForm";
import { useState } from "react";


Images: Program images (Udaan2.png, SFP_02.png) and a header icon (head.webp)

Custom components:

HeadingImage — likely renders a section title like Our Programs

SubHeadImg — likely renders a subheading

ContactForm — a form that opens in a modal when "Explore" is clicked

React hook: useState for modal state control

# MAIN STRUCTURE
<section className="...">
  {/* Section Header */}
  {/* Program Card 1: Udaan 90 */}
  {/* Program Card 2: Success Fusion */}
</section>

# HEADER
<HeadingImage title="Our" highlight="Programs" />
<p>Skill up, stand out, and soar into success with our expert led programs.</p>


Displays section title: "Our Programs"

Subtext describes what users can expect from the programs

# PROGRAM CARD 1: Udaan 90
🔹 Left (Image + Stats Bar)
<img src={udaanImg} alt="Udaan 90" />


Shows an image representing the Udaan program

<div className="absolute ...">
  <p>2K+ Enrolled</p>
  <img src={Head} />
  <p>1089 hours of Learning</p>
</div>


Floating stats bar over the image

Shows enrollment number and total learning hours

🔹 Right (Program Details)
<SubHeadImg text="Udaan - 90" />
<p>Zero to Job–Ready in 90 Days at just ₹999.</p>
<p>Affordable. Practical. Result-driven.</p>
<ul>
  <li>Live classes + projects</li>
  <li>Resume & interview preparation</li>
  ...
</ul>


Lists features and benefits of the program

Target audience: beginners looking for jobs in 90 days

🔹 "Explore" Button with Modal
<button onClick={() => setShowModal(true)}>Explore</button>
{showModal && (
  <ContactForm onClose={() => setShowModal(false)} />
)}


Clicking "Explore" opens a ContactForm modal

Clicking outside the modal or onClose closes it

# PROGRAM CARD 2: Success Fusion
🔹 Similar structure as Udaan 90, but with content reversed

Order is flipped using Tailwind's order-* classes

Left: Textual content

Right: Image with floating stats bar

Pricing: ₹4999

Duration: 12 months

Key features: Live projects, Internships, Placement Support, 1:1 Mentorship, Upto 20 LPA

# MODAL SHARING

The showModal state is shared between both "Explore" buttons

Clicking either button opens the same modal

A better UX might involve separate modals or passing the program name to the form for context

# DESIGN / RESPONSIVENESS

The layout adjusts based on screen size:

Mobile: Vertical stacking (flex-col)

Desktop: Horizontal split (md:flex-row)

Responsive padding, font sizes, and spacing ensure visual appeal across devices

**************************************************************************************
#  src/components/Home/Partner.jsx
# IMPORTS
import React from "react";
import { motion } from "framer-motion";


React: Base library for components

motion: From framer-motion, used for smooth and configurable animations

import "../../index.css"; // Custom CSS (likely includes .animate-marquee class or resets)

import IILM from "../../assets/Home/Partner/1.webp";
import amity from "../../assets/Home/Partner/2.webp";
...
import delhi from "../../assets/Home/Partner/9.webp";


These are university logo images imported from the local assets

# PARTNER LOGOS ARRAY
const universities = [
  IILM,
  rajdhani,
  amity,
  alliance,
  shardha,
  rkdf,
  miatreyi,
  hanshraj,
  delhi,
  gla,
];


A simple array of images to be used in the scrolling display

Note: alliance and gla both use image 4 (4.webp) — maybe an image duplication error?

# COMPONENT STRUCTURE
<section className="...">
  {/* Heading Section */}
  {/* Marquee Section */}
</section>

# HEADER SECTION
<h1>Built with <span className="text-orange-500">Leading</span> Universities</h1>
<p>We partner with top institutions ...</p>


Displays a title and supporting text with styling

Responsive typography (text-3xl, md:text-[48px], etc.)

# SCROLLING MARQUEE SECTION
<motion.div
  initial={{ x: 0 }}
  animate={{ x: "-100%" }}
  transition={{
    duration: 15,
    ease: "linear",
    repeat: Infinity,
  }}
>
  {/* Render logos */}
</motion.div>


motion.div uses Framer Motion to animate its x position from 0 to -100%, making it scroll left

repeat: Infinity: It loops endlessly

ease: "linear": Smooth and consistent speed

duration: 15: Takes 15 seconds to scroll one full width

Two identical <motion.div> blocks are rendered back-to-back to create a seamless looping effect, meaning as one goes off-screen, the other takes over.

# LOGO RENDERING
<img
  className="h-16 w-36 sm:h-20 sm:w-44 md:h-[100px] md:w-[220px] object-contain"
  src={image}
  alt={`University logo ${index}`}
/>


Responsive sizes for different screens

object-contain: Ensures logos aren't stretched

Alt text dynamically adds the index

# CSS Notes
.animate-marquee {
  animation: marquee 15s linear infinite;
}

.no-scrollbar {
  scrollbar-width: none;
  -ms-overflow-style: none;
}


While not shown directly in the code snippet, custom CSS like animate-marquee and no-scrollbar are likely defined in index.css.

# POTENTIAL CLEANUPS OR IMPROVEMENTS
# Image duplication
..import alliance from "../../assets/Home/Partner/4.webp";import gla from "../../assets/Home/.Partner/4.webp";


.Both alliance and gla use the same image (4.webp). You might want to double-check if this was intentional.

# Dynamic key

You’re using index as the key — which is okay for static arrays, but ideally, use a unique identifier (like a university name) if available.


*****************************************************************************

# src/components/Home/Prestige.jsx

Imports
import React from 'react';
import { motion } from 'framer-motion';
import '../../index.css';


React: For JSX and component logic

motion: From framer-motion library to animate scrolling

index.css: Your custom/global styles (likely includes custom animation styles)

# Image Assets
import Accenture from "../../assets/Home/Prestige/accenture.webp";
...
import learnyst from "../../assets/Home/Prestige/Learnyst.webp";


Imported logos of companies in .webp format, stored locally in the assets/Home/Prestige folder

# network Array
const network = [ Accenture, Cognizant, TCS, Greyt, EY, Mentorsity, languify, learnyst ];


An array of all imported image variables to loop over and render in the UI

# JSX Structure
1. Top-Level Section
<section className="bg-gray-100 py-10 mt-7 ...">


Adds spacing and background styling using Tailwind classes

Font is set to Poppins

2. Header Section
<h1>Our <span className="text-orange-500">Prestige</span> Network</h1>
<p>Alliances with bold startups and global leaders...</p>


Displays a heading and a subtext to explain the context:

“We’re working with top global companies & startups.”

Responsive typography using Tailwind (text-[32px], text-[48px], etc.)

3. Scrolling Logos Section
Container
<div className="w-full overflow-hidden bg-gray-100">
  <div className="container mx-auto">
    <div className="flex">


overflow-hidden: Hides scrollbars

container mx-auto: Centers the inner content

flex: Horizontal alignment of scrolling sections

# Two motion.divs for Seamless Looping
Why Two?

To create a continuous scrolling loop. When one set of logos finishes scrolling, the duplicate follows immediately—giving the illusion of an endless line.

# motion.div (Framer Motion Animation)
<motion.div
  initial={{ x: 0 }}
  animate={{ x: "-100%" }}
  transition={{
    duration: 15,
    ease: "linear",
    repeat: Infinity,
}}


initial: { x: 0 }: Starts at the beginning

animate: { x: "-100%" }: Moves the div completely to the left

repeat: Infinity: Keeps repeating

ease: "linear": Constant speed (no acceleration or deceleration)

duration: 15: One full scroll takes 15 seconds

# Inside the Animated Div
{network.map((image, index) => (
  <div key={index} className="px-4 sm:px-6 md:px-8 py-2 sm:py-3 md:py-4">
    <img
      className="h-8 sm:h-10 md:h-12 w-auto object-contain"
      src={image}
      alt={`Company logo ${index}`}
    />
  </div>
))}


Each logo is:

Padded for spacing

Responsive in height:

h-8 for mobile

h-12 for large screens

w-auto + object-contain: Keeps logo proportions intact

# Alt Tag Note

In the second marquee, you’re appending -copy to the alt tag:

alt={`Company logo ${index}-copy`}


Good for accessibility to avoid identical alt tags.

******************************************************************************************
# src/components/Home/StandOut.jsx
# Imports
import React from "react";
import { FaCheckCircle, FaTimesCircle } from "react-icons/fa";


React: Required for writing React components.

FaCheckCircle / FaTimesCircle: Icons from react-icons representing ✔️ and ❌.

# Data Arrays
const mobileFeatures = [...];  // Short feature names for small screens
const fullFeatures = [...];    // Full-length feature descriptions for larger screens

const others = [true, false, true, ...]; // Boolean values for "Others" column
const us = Array(fullFeatures.length).fill(true); // "Us" supports all features


mobileFeatures: Short names for features (used on small devices)

fullFeatures: Full descriptions (used on medium+ devices via responsive rendering)

others: Array of booleans representing whether competitors offer a feature

us: Always true — your platform offers all the features

# Component Structure
<section className="bg-gray-50 py-8 sm:py-12 px-4 sm:px-6 ...">

🔹 Outer Layout

Adds padding, background, centering, and applies custom font (Poppins)

Responsive padding via Tailwind

# Section Heading
<h2>Here's Why <span className="text-orange-500">Baoiam Stands Out!</span></h2>
<p>Our commitment to quality...</p>


Highlights the key message: Baoiam offers more than competitors

Responsive typography (text-2xl, md:text-5xl, etc.)

# Main Table Grid
<div className="grid grid-cols-10 ...">


Uses Tailwind CSS Grid with 10 columns total:

5 columns → Feature names

2.5 columns → "Others" column (competitors)

2.5 columns → "Us" column (your platform)

# Column Details
# Features Column
<div className="col-span-5 ...">


Header: "Features"

Lists each feature name:

On mobile (md:hidden): uses mobileFeatures

On desktop (md:inline): uses fullFeatures

<span className="md:hidden">{item}</span>
<span className="hidden md:inline">{fullFeatures[idx]}</span>


. Dynamic rendering based on screen size = Responsive-friendly feature names

#  "Others" Column
<div className="col-span-2 ...">


Header: "Others"

Loops through others[]

If true: ✅ Green check (feature available)

If false: ❌ Red cross (not available)

{val ? <FaCheckCircle /> : <FaTimesCircle />}

# "Us" Column
<div className="col-span-3 ...">


Header: "Us"

Since all values are true, always renders ✅ green check

<FaCheckCircle className="text-green-500" />

# Responsive Design

Tailwind utilities like:

text-xs sm:text-sm md:text-xl — responsive text

min-h-[32px], md:h-[60px] — consistent row height

md:hidden and hidden md:inline to swap feature names based on screen size

**********************************************************************************

# src/components/Home/StatsSection.jsx

# Imports
import React from "react";
import { FaStar } from "react-icons/fa";
import img1 from "../../assets/Home/StatsSection/1.webp";
import img2 from "../../assets/Home/StatsSection/2.webp";
import img3 from "../../assets/Home/StatsSection/3.webp";


FaStar: Yellow star icon from react-icons to show ratings

img1, img2, img3: Accreditation images (e.g., MSME, ISO, Startup India)

# JSX Structure
# Outer Container
<section className="..."> ... </section>


Full-width section with padding, white background, and vertical layout

Uses custom font (Poppins) and responsive spacing (px-2 sm:px-4, etc.)

# Top Black Stats Bar
<div className="w-full max-w-[1070px] ... bg-black text-white ... flex flex-row">


Black bar with white text

Contains 3 equal-width stats blocks (flex-1)

Responsive spacing and rounded corners
# 3 Key Stats Inside:
⭐ Ratings
<p>4.8 <FaStar ... /></p>
<p>Ratings from 10k+ students</p>


Uses FaStar icon colored yellow (text-yellow-400)

Highlights user satisfaction

# Hiring Partners
<p>200 +</p>
<p>Hiring Partners</p>


Shows number of companies hiring from you

# Highest Package
<p>50 LPA</p>
<p>Highest Package</p>


Displays the highest salary package offered

# Spacer
<div className="h-8 md:h-12"></div>


Adds vertical space between the stats and accreditation section

3️# Accreditation Section
<h2>We are accredited by</h2>


A large heading centered on the page

# Logos Displayed in Flex Wrap
<div className="flex flex-wrap justify-center items-center gap-6 md:gap-10 lg:gap-[70px]">


Responsive grid of logos, centered and evenly spaced

Uses object-contain to keep images scaled proportionally

Logos shown:

img2: DPIIT / Startup India

img1: MSME

img3: ISO 9001 certified

# Divider Line at the Bottom
<hr className="w-full border-t-[2px] border-gray-100 mt-14" />


Light gray line used to separate the section visually from the next content

# Responsive Design

All elements use Tailwind’s responsive utilities:

Breakpoint	Effect
sm:	Padding/text size increase
md:	Bigger spacing, text, images
lg:	Large logo sizes, font sizes

************************************************************

#  src/components/Home/TeamSection.jsx
1. Imports
import React from "react";
import { motion } from "framer-motion";
import { FaLinkedin } from "react-icons/fa";


Pulls in core tools like React, motion for animation, and icon for LinkedIn.

Imports HeadingImage to show the section title.

 2. Data Structures
# members array

Each team member has:

{
  name: "John Doe",
  position: "CTO",
  linkedin: "https://linkedin.com/in/johndoe",
  image: JohnImage
}


Used to dynamically render member profile cards.

# Styling Arrays
const gradients = [...]; // gradient background classes
const solidColors = [...]; // solid background for image backgrounds


Used to alternate or consistently style card backgrounds.

 3. Card Renderer Function
const renderMemberCard = (member, index) => ( ... );


This function renders each team member’s card with:

Name

Position

LinkedIn icon (only if a URL exists)

Profile picture

Responsive styling

Background (solid + gradient)

The structure is:

<div className="flex flex-col items-center">
  <div className="text info">
    Name, position, LinkedIn
  </div>
  <div className="image wrapper">
    <img src={...} />
  </div>
</div>

# 4. Main JSX Return
# Section Wrapper
<div className="bg-white py-6 ...">


Full white background

Uses Poppins font

Padding added for all screen sizes

# Header
<HeadingImage title="Our" highlight="Team" />
<p>Experts who guide...</p>


Uses a custom component HeadingImage (likely shows a styled heading)

Adds a subheading/description below the title

# Marquee Section
<div className="relative w-full overflow-hidden h-[300px] ...">


Wrapper around two horizontally scrolling rows

Fixed height (responsive with screen size)

Inside this:

<motion.div animate={{ x: "-100%" }} ...>
  {members.map(...)}
</motion.div>


Two duplicate motion divs (used for seamless infinite scrolling)

Each renders the members cards using the renderMemberCard function

This creates the illusion of continuous horizontal scroll

# Animation Details
initial: { x: 0 }
animate: { x: "-100%" }
transition: {
  duration: 35,
  ease: "linear",
  repeat: Infinity
}


Starts at 0, slides to -100% (full width left)

Infinite repeat to scroll forever

35 seconds duration (slow, smooth animation)

# Responsive Design

Card and container widths adjust across screen sizes using Tailwind breakpoints like:

sm:, md:, lg: — for spacing, width, height, font-size

object-cover ensures image fills the round container cleanly

Scales from w-48 to w-64 and so on

******************************************************************************

#  src/components/Home/Testimonial.jsx
1. Imports
import React, { useState, useEffect } from 'react';
import { FaArrowLeft, FaArrowRight } from "react-icons/fa";
import m1 from "../../assets/Home/Testimonial/m1.webp";
import f1 from "../../assets/Home/Testimonial/f1.webp";
import HeadingImage from '../Lines/HeadingImages';


useState, useEffect: Manage current slide and auto-slide behavior.

FaArrowLeft, FaArrowRight: Icons for navigation buttons.

m1, f1: Testimonial user images.

HeadingImage: Custom heading component.

 2. Testimonials Data
const testimonials = [ { id, content, author, role, image }, ... ];


Array of testimonial objects, each with:

content: the quote

author: the name

role: job title and salary

image: profile picture

 3. State Management
const [currentIndex, setCurrentIndex] = useState(0);


Tracks which testimonial is currently displayed.

4. Slide Navigation Functions
const nextSlide = () => {
  setCurrentIndex((prev) => (prev === testimonials.length - 1 ? 0 : prev + 1));
};
const prevSlide = () => {
  setCurrentIndex((prev) => (prev === 0 ? testimonials.length - 1 : prev - 1));
};


nextSlide(): Moves to the next testimonial, loops to start if at the end.

prevSlide(): Moves to the previous testimonial, loops to end if at the beginning.

 5. Auto-Slide with useEffect
useEffect(() => {
  const interval = setInterval(() => {
    nextSlide();
  }, 5000);
  return () => clearInterval(interval);
}, [currentIndex]);


Automatically transitions every 5 seconds.

Clears interval on unmount to prevent memory leaks.

 6. Card Styling Logic: getCardClasses()

Determines how each testimonial appears, depending on its position relative to currentIndex.

const getCardClasses = (index) => {
  // Base styles
  let classes = "absolute transition-all duration-500 ease-in-out p-6 rounded-xl shadow-lg h-full flex flex-col";

  const offset = index - currentIndex;

  if (window.innerWidth < 768) {
    // On mobile: only show current slide
    return offset === 0 ? classes + " bg-pink-100 scale-100 opacity-100 z-20 w-full left-0" : classes + " hidden";
  }

  // On larger screens
  if (offset === 0) {
    classes += " bg-pink-100 scale-100 opacity-100 z-20 w-2/3 left-1/2 -translate-x-1/2";
  } else if (offset === -1 || (offset === testimonials.length - 1 && currentIndex === 0)) {
    classes += " bg-green-100 scale-95 opacity-50 z-10 w-1/2 -left-1/4";
  } else if (offset === 1 || (offset === -(testimonials.length - 1) && currentIndex === testimonials.length - 1)) {
    classes += " bg-green-100 scale-95 opacity-50 z-10 w-1/2 -right-1/4";
  } else {
    classes += " hidden";
  }

  return classes;
};

# Visual Effect:

Center (active): larger, pink, fully opaque.

Side (prev/next): smaller, green, semi-transparent.

Others: hidden.

 7. Rendering the Component
# Section Header
<HeadingImage title="Testimonials" />
<p className="...">Experts who guide, Mentors who matter...</p>


Displays section title and subtitle.

# Carousel Container
<div className="relative h-[320px] sm:h-[280px] md:h-[240px] max-w-4xl mx-auto">
  {testimonials.map((testimonial, index) => (
    <div key={testimonial.id} className={getCardClasses(index)}>
      ...
    </div>
  ))}
</div>


Each testimonial card is positioned absolutely inside the container, so they stack and animate using classes from getCardClasses().

🔷 Testimonial Card Layout

Each card includes:

. User image

. Author's name and role

# Testimonial content

<div className="flex-grow flex flex-col">
  <div className="flex items-center mb-4">
    <img src={testimonial.image} ... />
    <div>
      <p className="font-bold">{testimonial.author}</p>
      <p>{testimonial.role}</p>
    </div>
  </div>
  <div className="flex-grow mt-1">
    <p className="italic">"testimonial content"</p>
  </div>
</div>

# Navigation Buttons
<div className="flex justify-center items-center mt-8 md:mt-10 gap-6">
  <button onClick={prevSlide}> <FaArrowLeft /> </button>
  <button onClick={nextSlide}> <FaArrowRight /> </button>
</div>


Circular buttons styled with Tailwind and custom colors.

Hover effects included.

# Responsiveness

Mobile: Only current testimonial is shown.

Desktop: Centered card and side peeks of previous/next testimonials.

Tailwind handles most breakpoints (sm:, md:, etc.).

# Color/Style Guide
Element	Style
Active Card	Pink background (bg-pink-100)
Side Cards	Green background (bg-green-100)
Buttons	Light orange background, orange icon
Text	Italicized quote, bold names

*********************************************************************
#   (src/components/Home/Webinars.jsx


# Imports
import React, { useState, useRef, useEffect } from "react";
import LandingPages from "../../assets/Home/Webinar/LandingPages.mp4";
import ContactForm from "../../Pages/ContactForm";
import { MdPlayCircle, MdVolumeUp, MdVolumeOff } from "react-icons/md";


useState, useRef, useEffect: React hooks for state, DOM reference, and lifecycle

LandingPages: A local video file

ContactForm: A modal form component

Icons for volume control

# Component State & Refs
const videoRef = useRef(null);
const [isPlaying, setIsPlaying] = useState(true);
const [isMuted, setIsMuted] = useState(true);
const [showModal, setShowModal] = useState(false);


videoRef: Direct reference to the <video> DOM element

isPlaying: Whether the video is playing

isMuted: Whether the video is muted

showModal: Controls modal form visibility

# useEffect() for Autoplay
useEffect(() => {
  const video = videoRef.current;
  if (video) {
    video.muted = true;
    video.play()
      .then(() => setIsPlaying(true))
      .catch(err => {
        console.log("Autoplay failed...", err);
        video.muted = true;
        video.play();
      });
  }
}, []);


Ensures video plays on page load (muted is often required for autoplay).

If autoplay fails, it retries with muted mode enabled.

# Control Functions
const togglePlay = () => {
  if (!videoRef.current) return;
  if (videoRef.current.paused) {
    videoRef.current.play();
    setIsPlaying(true);
  } else {
    videoRef.current.pause();
    setIsPlaying(false);
  }
};

const toggleMute = () => {
  if (!videoRef.current) return;
  videoRef.current.muted = !videoRef.current.muted;
  setIsMuted(videoRef.current.muted);
};

const handleVideoClick = () => {
  toggleMute(); // Clicking the video toggles mute
};


Play/pause and mute/unmute handlers

Tied to buttons and video click

# Top Section (Heading & Buttons)
<div className="bg-white ...">
  <h2>Webinars That Inspire and Impact</h2>
  <p>Join the webinar that makes learning unforgettable.</p>

  <div className="flex ...">
    <button onClick={() => setShowModal(true)}>Register for Webinar</button>
    <button onClick={() => setShowModal(true)}>Talk to our Counsellor</button>
  </div>

  {showModal && (
    <div onClick={() => setShowModal(false)}>
      <div onClick={(e) => e.stopPropagation()}>
        <ContactForm onClose={() => setShowModal(false)} />
      </div>
    </div>
  )}
</div>


Headline and supporting text

Two CTA buttons open the modal (ContactForm)

Clicking outside the form closes it

# Bottom Section (Video Preview)
<div className="bg-[#FF6501B2] h-[105px] md:h-[305px] relative">
  <div className="absolute ...">
    <div className="relative max-w-4xl">
      <video
        ref={videoRef}
        src={LandingPages}
        autoPlay
        muted={isMuted}
        loop
        playsInline
        onClick={handleVideoClick}
      />


Styled video section overlaps top area slightly

Auto-playing video with loop, muted, playsInline for smooth mobile experience

Click on video toggles mute

# Muted Overlay
{isMuted && (
  <button onClick={toggleMute} className="absolute inset-0 ...">
    <MdVolumeOff />
    <span>Click to unmute</span>
  </button>
)}


If video is muted, a semi-transparent overlay appears prompting the user to unmute

# Video Controls (Play/Pause, Mute/Unmute)
<div className="absolute bottom-4 left-4 ...">
  <button onClick={togglePlay}>
    {isPlaying ? "Pause" : "Play"}
  </button>
  <button onClick={toggleMute}>
    {isMuted ? <MdVolumeOff /> : <MdVolumeUp />} Mute/Unmute
  </button>
</div>


Positioned over video (bottom left)

Show dynamic labels/icons based on state

# Design Elements
Feature	Tech / Style
Layout	Tailwind CSS flex, px, py
Video Preview	HTML5 video, styled with Tailwind
Icons	React Icons (Material Design)
Modal	Custom-built modal using Tailwind
CTA Buttons	Tailwind hover and transition
Responsive	sm:, md: Tailwind breakpoints

*************************************************************************

# src/components/Lines/HeadingImages.jsx

# Import
import Group from "../../assets/Home/Lines/Group.webp";


Imports an image (Group.webp) to be used next to the heading.

Likely a line, icon, or decorative graphic.
# Component Definition
const HeadingImage = ({ title, highlight }) => {


This component receives two props:

title: A normal word in the heading (e.g., "Our")

highlight: A highlighted word in orange (e.g., "Team")

# Returned JSX
<div className="flex items-center justify-center w-full">
  <h2 className="text-3xl md:text-5xl font-bold mb-2">
    {title} <span className="text-orange-500">{highlight}</span>
  </h2>
  <img src={Group} alt="" className="w-9 mb-4" />
</div>

# Layout

flex items-center justify-center: Horizontal alignment

w-full: Takes full container width

# Heading
<h2 className="text-3xl md:text-5xl font-bold mb-2">
  {title} <span className="text-orange-500">{highlight}</span>
</h2>


Responsive text size: text-3xl on mobile, text-5xl on medium+ screens

font-bold: Makes it bold

{highlight} gets a bright orange color using text-orange-500

# Image
<img src={Group} alt="" className="w-9 mb-4" />


Image next to the heading

w-9: Small image width

mb-4: Adds space below it for alignment

alt="": No alt text (could be improved for accessibility)

# Example Usage
<HeadingImage title="Our" highlight="Team" />

Output:

"Our Team" → with "Team" in orange and an image beside it.

************************************************************
#  src/components/Lines/SubHeading.jsx
import React from "react";
import VectorImg from "../../assets/Home/Lines/Vector_11.webp";
Imports React and a vector image used for decorative purposes (like an underline or flair).

# Component Declaration
jsx
Copy code
const SubHeadImg = ({ text }) => {
text is a prop used to set the heading content dynamically.

# JSX Structure
jsx
Copy code
<div className="inline-flex flex-col items-center relative mb-2">
inline-flex: Makes the element behave like inline content (sits next to others)

flex-col: Stacks children vertically

items-center: Horizontally center children

relative: Required to position the image absolutely relative to this container

mb-2: Adds space below the block

# Gradient Animated Text
jsx
Copy code
<h3 className="text-2xl md:text-[42px] font-medium bg-clip-text text-transparent bg-gradient-to-r from-[#1D2026] via-[#e45c02] to-[#FF6501] bg-[length:400%_auto] animate-gradient">
  {text}
</h3>
.text-2xl md:text-[42px]: Responsive text size (42px on medium and up)

.font-medium: Medium font weight

.bg-clip-text + text-transparent: Makes text take color from background

.bg-gradient-to-r: Applies a left-to-right gradient

.Colors:

.#1D2026 (dark gray/black)

.#e45c02 (burnt orange)

.#FF6501 (bright orange)

.bg-[length:400%_auto]: Enlarges the background for smoother animation

.animate-gradient: Custom animation class (defined in your CSS or Tailwind config)

. This makes the text look animated and shiny with a smooth gradient motion.

# Decorative Underline Image
jsx
Copy code
<div className="absolute top-full -mt-3" style={{ left: "calc(100% - 100px)" }}>
  <img src={VectorImg} alt="" className="w-[90px] h-[18px]" />
</div>
absolute top-full -mt-3:

Places the image directly below the heading

top-full: Moves it just below the bottom of the parent

-mt-3: Slight negative margin to bring it closer

left: calc(100% - 100px):

Offsets the image to the left slightly to make it appear like an underlining decoration

img element:

Displays the imported vector image with fixed width and height

*******************************************************************************
# src/components/Pride/AboutBonnay.jsx
# Imports
import React from "react";
import img1 to img11 from "../../assets/Pride/OurEvents/";
import Group from "../../assets/Home/Lines/Group.webp";


Importing all images used in the gallery.

Group.webp is a small visual icon used near the heading.

# images Array
const images = [
  { src: img1, w: "200px", h: "200px" },
  { src: img2, w: "530px", h: "200px" },
  ...
];


Each object contains:

src: image source

w: width

h: height

These are applied via inline styles to allow masonry-style scaling.

# Photo Component (Reusable)
const Photo = ({ index, extraClass = "" }) => {
  const { src, w, h } = images[index];
  return (
    <img
      src={src}
      alt={`img${index + 1}`}
      style={{ width: w, height: h }}
      className={`object-cover rounded-xl ${extraClass}`}
    />
  );
};


This component renders a single image.

Takes index to select the image from the array.

Accepts optional extraClass for layout flexibility.

Applies:

object-cover to maintain aspect ratio

rounded-xl to give curved corners

# OurEvent Component
const OurEvent = () => (
  <div className="w-full bg-[#F8F8F8] py-10 font-['Poppins']">


Full-width section with light gray background and padding

Uses Poppins font

# Section Header
<h2 className="text-3xl md:text-[48px] font-semibold mb-2">
  A face of <span className="text-orange-500">hope,</span> a voice of <span className="text-orange-500">equality</span>
</h2>
<img src={Group} alt="" className="w-9 mb-4 hidden sm:block" />


Main heading with highlighted orange words for emphasis

Group image shown only on screens sm and up

<p className="text-center ...">
  Bonya represents resilience, purpose, and the power of inclusion.
</p>

.Supporting paragraph under the heading

# Desktop Image Layout
<div className="hidden md:grid grid-cols-1 md:grid-cols-2 lg:grid-cols-[3fr_1fr] ...">


Only visible on md and larger screens

Uses custom grid layout:

Two columns on medium

Custom 3:1 layout on large screens

🔹 Left Column

Consists of 3 main rows:

Top: img1, img2

Middle: img3, img4 in a column beside img5

Bottom: img6

🔹 Right Column

Contains:

img3 and img7 stacked

🔹 Bottom Row

Spans full width: img8, img9, img10

# Mobile Layout
<div className="md:hidden grid grid-cols-2 gap-3 bg-white p-4 rounded-xl shadow-md">
  <Photo index={0} />
  <Photo index={1} />
  <Photo index={3} />
  <Photo index={4} />
</div>


Visible only below md

Grid of 2 columns

Shows fewer images (first 4-5 only)

Keeps performance and layout clean for small screens
********************************************************************
#  src/components/Pride/AmbassadorAdvice.jsx
1. State & Imports
import React, { useState } from "react";
import Group from "../../assets/Home/Lines/Group.webp";
import ContactForm from "../../Pages/ContactForm";
import { Link } from "react-router-dom";

const [isPlaying, setIsPlaying] = useState(false);
const [showModal, setShowModal] = useState(false);


Group: decorative icon

ContactForm: modal form component

Link: navigates to /DataScience when "Enroll Now" is clicked

isPlaying: controls whether the video is playing

showModal: toggles contact form modal

2. Top Section (White Area)
<div className="bg-white text-center px-4 py-12 mb-16 sm:mb-28">

🔹 Heading
<h2 className="...">
  Breaking <span className="text-orange-500">Barriers,</span> Building <span className="text-orange-500">Futures</span>
</h2>


Stylized heading with orange-highlighted words

🔹 Paragraph
<p>Bonya's journey from resilience to leadership now fuels a movement of inclusion.</p>

🔹 Buttons
<Link to="/DataScience">Enroll Now</Link>
<button onClick={() => setShowModal(true)}>Talk to our Counsellor</button>


"Enroll Now" navigates to another route

"Talk to our Counsellor" opens a modal with the ContactForm

🔹 Modal Logic
{showModal && (
  <div className="fixed inset-0 z-50 flex ...">
    <div onClick={(e) => e.stopPropagation()}>
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}


Clicking outside closes the modal

Clicking inside the form won't close it (event bubbling stopped)

ContactForm receives onClose prop to close modal

 3. Bottom Section (Orange Background)
<div className="bg-[#FF6501B2] h-[105px] md:h-[305px] relative">


This is a design element — an orange strip behind the video container

 4. YouTube Video
<div onClick={handleVideoClick}>
  {!isPlaying && <▶️ overlay>}
  <iframe src={`https://www.youtube.com/embed/...`} />
</div>


Clicking on the video triggers setIsPlaying(true)

This changes the iframe’s autoplay param to 1, making it play

Includes:

loop=1 to repeat the video

playlist param (same as video ID) is required for looping on YouTube embeds

# Bonus: Responsive Iframe Hack
<div className="relative w-full h-0 pb-[56.25%]">


This creates a 16:9 aspect ratio container (56.25% = 9/16)

iframe is absolutely positioned inside it to scale with width

****************************************************************************
# src/components/Pride/AmbassadorAdvice.jsx


1. React Import
import React from "react";


React ko import karte hain taake hum JSX likh sakein aur React components bana sakein.

Although React 17+ mein ye zaroori nahi hota for JSX, lekin purani compatibility ke liye ya kuch setups mein ye common hai.

2. Images Import
import blog1 from "../../assets/Pride/BlogSection/blog1.png";
import blog2 from "../../assets/Pride/BlogSection/blog2.png";
import blog3 from "../../assets/Pride/BlogSection/blog3.png";
import blog4 from "../../assets/Pride/BlogSection/blog4.png";


Ye lines aapke project folder ke andar assets directory se images import kar rahi hain.

blog1, blog2, etc. variables mein ye images ka paths store ho jaate hain, jo phir JSX mein <img src={blog1} /> jese use karte hain.

Is tarah import karne se build tools (jaise Webpack ya Vite) optimize kar sakte hain images ko bundling ke waqt.

3. Group Image Import
import Group from "../../assets/Home/Lines/Group.webp";


Ye bhi ek image import hai, lekin .webp format mein.

Ye image aapne blog heading ke bagal mein display kiya hai (decorative image).

.webp ek modern image format hai jo size mein chhota aur quality mein acha hota hai.

4. React Router Link Import
import { Link } from "react-router-dom";


react-router-dom ek popular React library hai jo client-side routing ke liye use hoti hai.

Link component se hum page reload ke bina URL change kar sakte hain aur different views ya pages dikha sakte hain.

Aapke code mein Link use kiya gaya hai jese:

<Link to="/blogs">
  <button>Read More</button>
</Link>


Ye ensure karta hai ke jab user "Read More" button pe click kare, toh wo /blogs route par bina page reload ke navigate ho jaye.
# 1. Wrapper Section
<section className="max-w-7xl mx-auto px-4 py-12 font-['Poppins']">


Centers the content on the page (mx-auto)

Limits maximum width (max-w-7xl)

Adds padding (px-4 horizontal, py-12 vertical)

Uses the 'Poppins' font family for the whole section

2. Heading Area
<div className="flex flex-col md:flex-row md:items-center md:justify-between mb-6">


On mobile: vertical column layout

On medium screens and above (md:): horizontal layout, centered vertically, spaced between items

Bottom margin of 6 units for spacing below

Inside:
<div>
  <div className="flex w-full md:mb-2">
    <h2 className="text-3xl md:text-[48px] font-semibold mb-2">
      Voices That<span className="text-orange-500"> Matter </span>
    </h2>
    <img src={Group} alt="" className="w-9 mb-4" />
  </div>
  <p className="text-black max-w-2xl text-[18px] md:text-[24px]">
    Exploring the intersections of education, identity, and empathy.
  </p>
</div>


Title: "Voices That Matter" with “Matter” highlighted in orange

Decorative Group image next to the heading

Subtitle paragraph below the heading explaining the section theme

3. Main Grid Layout
<div className="grid grid-cols-1 md:grid-cols-3 gap-6">


Uses CSS Grid with:

1 column on mobile

3 columns on medium and larger screens

Gap of 6 units between grid items

4. Featured Large Blog Card (Left Side, Spanning 2 Columns)
<div className="md:col-span-2 w-full">


On medium+ screens, spans 2 out of 3 columns for prominence

Full width inside its grid cell

Contents:

A “View More” button aligned to the right above the main blog card

Large blog card with:

White background, rounded corners, shadow, and hover effects

Image fills the card with object-cover

Date badge positioned top-left

A semi-transparent white overlay at the bottom with:

Blog title: "Making Room:"

Subtitle describing the blog topic

A short excerpt snippet

A “Read More” button in the bottom-right that links to /blogs

5. Right Side: Two Smaller Blog Cards
<div className="flex flex-col gap-6 w-full">


Stacks cards vertically with gaps in between

Full width inside the grid column

Card 1
<div className="relative rounded-2xl overflow-hidden shadow hover:shadow-lg transition w-full h-[250px] md:h-[300px] lg:w-[350px]">


Rounded corners and shadow with hover effect

Fixed height and responsive width (350px on large screens)

Image with object-right to focus on the right side

Title text overlaid top-left with white color for contrast

Date badge top-right (orange background)

“Read More” button bottom-right with hover style

Card 2
<div className="relative rounded-2xl overflow-hidden bg-white shadow hover:shadow-lg transition w-full h-[250px] md:h-[300px] lg:w-[350px]">


Similar styling to Card 1 but with white background behind the image

Date badge and “Read More” button are placed top-left and top-right respectively

Title and subtitle overlay at the bottom with white text

6. Routing

The “Read More” buttons use regular <button> elements, but only the big card’s “Read More” button is wrapped in a React Router <Link to="/blogs">

This means clicking the big card’s button navigates to the blogs page, but the smaller cards’ buttons currently don’t navigate (you might want to wrap them with <Link> or add onClick handlers).
**************************************************
# src/components/Pride/BlogSection.jsx
Imports:
import React from "react";
import bonnay from "../../assets/Pride/Herosection_P/bonnay.webp";
import { Link } from "react-router-dom";


React: For creating the component.

bonnay: Image asset imported from your project folder.

Link: From react-router-dom for client-side navigation without page reload.

Component structure:
const HeroSection_P = () => {
  return (
    <section className="...">
      ...
    </section>
  );
};


This is a functional React component returning JSX that represents the hero section.

Outer <section> container:
<section className="relative bg-white overflow-hidden pt-10 md:pt-16 lg:pt-10 font-['Poppins']">


relative: positioning context for child elements (used later for absolute positioning).

bg-white: white background.

overflow-hidden: clips overflowing content.

pt-10 md:pt-16 lg:pt-10: padding-top responsive for different screen sizes.

font-['Poppins']: custom font family set to "Poppins".

Inner container with padding and flex layout:
<div className="px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row items-center gap-10 md:gap-8 md:ml-8 lg:ml-16 xl:ml-14">


Horizontal padding adjusts by screen size.

flex flex-col md:flex-row: vertical stack on small screens, horizontal row on medium+ screens.

items-center: center items vertically in the flex container.

gap-10 md:gap-8: space between flex items.

Margins left (ml) increase with screen size for alignment.

Left side: Text content
<div className="flex-1 order-1 md:order-1 text-center md:text-left">


flex-1: takes equal flexible space.

order-1: order of flex items (explicit but same for both screen sizes).

Text alignment: center on small screens, left-aligned on medium+ screens.

Heading (<h1>):
<h1 className="text-[24px] sm:text-[28px] md:text-5xl lg:text-[55px] font-semibold text-black leading-snug mb-4 md:mb-6 max-w-full md:max-w-[630px] mx-auto md:mx-0">
  Living With <span className="text-[#8A38F5]">Pride,</span> Leading
  With <span className="text-[#FF6501]">Purpose.</span>
</h1>


Responsive font sizes from 24px (small) up to 55px (large).

font-semibold: semi-bold text.

leading-snug: line height is snug for better readability.

Margin bottom to separate from paragraph.

Max width limits the heading width on medium+ screens.

mx-auto centers on small screens, no margin on medium+.

The words "Pride" and "Purpose" are colored differently using inline <span> with custom hex colors.

Paragraph (<p>):
<p className="text-[#222222] text-[15px] sm:text-base md:text-[24px] mb-6 md:mt-5 max-w-[95%] sm:max-w-[90%] md:max-w-[650px] mx-auto md:mx-0 text-justify sm:text-center md:text-justify leading-relaxed">
  Unlock your potential with transformative, expert-led courses designed to fuel your ambition, celebrate your identity, and empower your journey.
</p>


Text color set to a dark gray (#222).

Font size scales from 15px up to 24px.

Margins for spacing.

Max widths adjust for different screen sizes.

mx-auto centers on smaller devices.

Text alignment changes between justified and centered depending on screen size.

leading-relaxed: comfortable line height for readability.

Button with link:
<div className="flex justify-center md:justify-start">
  <Link to="/DataScience">
    <button className="bg-[#FF6501] hover:bg-[#FF8434] px-6 py-2 sm:px-8 sm:py-2 text-white font-semibold rounded-md transition duration-300 text-[16px] sm:text-[18px] md:text-[20px]">
      Enroll Now
    </button>
  </Link>
</div>


Button is centered on small screens, left-aligned on medium+.

Link component wraps button to navigate to /DataScience route.

Button has an orange background, white text, smooth hover effect with color change.

Rounded corners and padding for better UI.

Font size adjusts responsively.

Smooth transition on hover (300ms).

Right side: Image with decorative background
<div className="flex-1 order-2 md:order-2 relative flex justify-center w-full">


Flexible space (equal with left side).

Positioned relative for the absolutely positioned orange blob background.

Flex container centers the content horizontally.

Orange blob background (decorative)
<div className="absolute -z-10 w-40 h-40 sm:w-52 sm:h-52 md:w-[350px] md:h-[350px] lg:w-[400px] lg:h-[400px] bg-orange-500 rounded-[35%_65%_65%_35%/45%_45%_55%_55%] opacity-100"></div>


Absolutely positioned behind (-z-10).

Width and height scale with screen size.

Orange background color.

Unique rounded corners creating a "blob" organic shape.

Full opacity.

Main image
<img
  src={bonnay}
  alt="Hero"
  className="relative w-72 sm:w-52 md:w-[370px] lg:w-[460px] rounded-lg object-cover"
/>


The hero image imported earlier.

Relative positioning (above the blob).

Width changes responsively.

Rounded corners (rounded-lg).

object-cover ensures the image fills the container nicely without distortion.

Export
export default HeroSection_P;


Makes the component available for import elsewhere in your app.
*****************************************************************

# src/components/Pride/Herosection_P.jsx
Imports:
import React from "react";
import bonnay from "../../assets/Pride/Herosection_P/bonnay.webp";
import { Link } from "react-router-dom";


React: For creating the component.

bonnay: Image asset imported from your project folder.

Link: From react-router-dom for client-side navigation without page reload.

Component structure:
const HeroSection_P = () => {
  return (
    <section className="...">
      ...
    </section>
  );
};


This is a functional React component returning JSX that represents the hero section.

Outer <section> container:
<section className="relative bg-white overflow-hidden pt-10 md:pt-16 lg:pt-10 font-['Poppins']">


relative: positioning context for child elements (used later for absolute positioning).

bg-white: white background.

overflow-hidden: clips overflowing content.

pt-10 md:pt-16 lg:pt-10: padding-top responsive for different screen sizes.

font-['Poppins']: custom font family set to "Poppins".

Inner container with padding and flex layout:
<div className="px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row items-center gap-10 md:gap-8 md:ml-8 lg:ml-16 xl:ml-14">


Horizontal padding adjusts by screen size.

flex flex-col md:flex-row: vertical stack on small screens, horizontal row on medium+ screens.

items-center: center items vertically in the flex container.

gap-10 md:gap-8: space between flex items.

Margins left (ml) increase with screen size for alignment.

Left side: Text content
<div className="flex-1 order-1 md:order-1 text-center md:text-left">


flex-1: takes equal flexible space.

order-1: order of flex items (explicit but same for both screen sizes).

Text alignment: center on small screens, left-aligned on medium+ screens.

Heading (<h1>):
<h1 className="text-[24px] sm:text-[28px] md:text-5xl lg:text-[55px] font-semibold text-black leading-snug mb-4 md:mb-6 max-w-full md:max-w-[630px] mx-auto md:mx-0">
  Living With <span className="text-[#8A38F5]">Pride,</span> Leading
  With <span className="text-[#FF6501]">Purpose.</span>
</h1>


Responsive font sizes from 24px (small) up to 55px (large).

font-semibold: semi-bold text.

leading-snug: line height is snug for better readability.

Margin bottom to separate from paragraph.

Max width limits the heading width on medium+ screens.

mx-auto centers on small screens, no margin on medium+.

The words "Pride" and "Purpose" are colored differently using inline <span> with custom hex colors.

Paragraph (<p>):
<p className="text-[#222222] text-[15px] sm:text-base md:text-[24px] mb-6 md:mt-5 max-w-[95%] sm:max-w-[90%] md:max-w-[650px] mx-auto md:mx-0 text-justify sm:text-center md:text-justify leading-relaxed">
  Unlock your potential with transformative, expert-led courses designed to fuel your ambition, celebrate your identity, and empower your journey.
</p>


Text color set to a dark gray (#222).

Font size scales from 15px up to 24px.

Margins for spacing.

Max widths adjust for different screen sizes.

mx-auto centers on smaller devices.

Text alignment changes between justified and centered depending on screen size.

leading-relaxed: comfortable line height for readability.

Button with link:
<div className="flex justify-center md:justify-start">
  <Link to="/DataScience">
    <button className="bg-[#FF6501] hover:bg-[#FF8434] px-6 py-2 sm:px-8 sm:py-2 text-white font-semibold rounded-md transition duration-300 text-[16px] sm:text-[18px] md:text-[20px]">
      Enroll Now
    </button>
  </Link>
</div>


Button is centered on small screens, left-aligned on medium+.

Link component wraps button to navigate to /DataScience route.

Button has an orange background, white text, smooth hover effect with color change.

Rounded corners and padding for better UI.

Font size adjusts responsively.

Smooth transition on hover (300ms).

Right side: Image with decorative background
<div className="flex-1 order-2 md:order-2 relative flex justify-center w-full">


Flexible space (equal with left side).

Positioned relative for the absolutely positioned orange blob background.

Flex container centers the content horizontally.

Orange blob background (decorative)
<div className="absolute -z-10 w-40 h-40 sm:w-52 sm:h-52 md:w-[350px] md:h-[350px] lg:w-[400px] lg:h-[400px] bg-orange-500 rounded-[35%_65%_65%_35%/45%_45%_55%_55%] opacity-100"></div>


Absolutely positioned behind (-z-10).

Width and height scale with screen size.

Orange background color.

Unique rounded corners creating a "blob" organic shape.

Full opacity.

Main image
<img
  src={bonnay}
  alt="Hero"
  className="relative w-72 sm:w-52 md:w-[370px] lg:w-[460px] rounded-lg object-cover"
/>


The hero image imported earlier.

Relative positioning (above the blob).

Width changes responsively.

Rounded corners (rounded-lg).

object-cover ensures the image fills the container nicely without distortion.

Export
export default HeroSection_P;


Makes the component available for import elsewhere in your app.

Summary:

Responsive two-column layout with text and image.

Beautifully styled heading with colored keywords.

Informative paragraph.

Call-to-action button lin
******************************************************************************************
# src/components/Pride/OurFeaturedCourses.jsx
# Imports:
import React from "react";
import { FaStar, FaUserGraduate } from "react-icons/fa";
import { FiBarChart } from "react-icons/fi";
import { MdAccessTime } from "react-icons/md";
import { Link } from "react-router-dom";
import img1 from "../../assets/Pride/OurFeaturedCourses/img1.webp";
import img2 from "../../assets/Pride/OurFeaturedCourses/img2.webp";
import Group from "../../assets/Home/Lines/Group.webp";


React is imported to build the component.

Icons imported from react-icons:

FaStar for rating stars,

FaUserGraduate for students enrolled,

FiBarChart for course level,

MdAccessTime for course duration.

Link from react-router-dom is used for navigation.

Three images imported: two course images and a decorative line image (Group).

Data for courses:
const courses = [
  {
    title: "HRMS",
    image: img1,
    description: "Simplify HR processes and empower growth with smart tools.",
    rating: 5.0,
    students: "265.7K",
    duration: "60 hour",
    level: "Beginner",
  },
  {
    title: "Data Science",
    image: img2,
    description:
      "Transform raw data into powerful insights for smarter decisions.",
    rating: 5.0,
    students: "265.7K",
    duration: "60 hour",
    level: "Beginner",
  },
];


An array of course objects containing all the necessary data to display.

Each object has:

Title, image,

Short description,

Rating (number),

Number of students (string),

Duration (string),

Level (string).

Component return structure:
<div className="w-full py-8 sm:py-12 md:py-16 bg-white flex justify-center overflow-hidden font-['Poppins']">
  <div className="w-[90%] max-w-6xl bg-white">
    {/* Heading */}
    ...
    {/* Cards + Button Wrapper */}
    ...
  </div>
</div>


The whole section has white background, vertical padding (py), and uses "Poppins" font.

Flex container centers the content horizontally.

Inner container has 90% width maxing out at 6xl (a Tailwind max-width).

Heading:
<div className="flex  sm:flex-row items-center justify-center w-full mb-3">
  <h2 className="text-[26px] sm:text-3xl md:text-[48px] font-semibold sm:mb-2 text-center sm:text-left">
    Our Featured <span className="text-orange-500">Courses</span>
  </h2>
  <img src={Group} alt="" className="w-7 sm:w-9 mb-2 sm:mb-4" />
</div>


Flex container to hold heading text and a decorative image side by side.

Responsive font sizes (26px → 48px).

Text "Courses" is colored orange.

Text centered on small screens, left-aligned on larger.

Decorative Group image is placed next to the heading.

Subtitle paragraph:
<p className="text-black text-center text-base sm:text-xl md:text-[24px] mb-4 md:mb-8 mx-auto">
  Skill up, stand out, and soar into success with our expert led programs.
</p>


Simple centered paragraph with responsive font sizes and bottom margin.

Encouraging message about the courses.

Cards container:
<div className="bg-white rounded-2xl p-4 md:p-8 w-full max-w-full mt-4 md:mt-6 flex flex-col items-center shadow-lg md:shadow-xl">
  <div className="w-full flex flex-col sm:flex-row justify-center gap-4 sm:gap-6 md:gap-28">
    {/* Map through courses */}
  </div>
  {/* Explore more button */}
</div>


White background, rounded corners, padding, and shadows for the card container.

Inside, another flex container organizes course cards vertically on mobile, horizontally on bigger screens.

Gaps between cards increase with screen size.

Individual Course Card (inside .map):
{courses.map((course, idx) => (
  <div
    key={idx}
    className="bg-white rounded-2xl p-4 flex flex-col flex-shrink-0 w-full sm:w-[45%] md:w-[389px] h-auto md:h-[502px] shadow-md md:shadow-lg hover:shadow-xl transition duration-300"
  >
    {/* Course title + rating */}
    {/* Course image */}
    {/* Course description */}
    {/* Students enrolled */}
    {/* Level and Duration */}
    {/* Start Learning button */}
  </div>
))}


Each card:

Has white background, rounded corners, padding.

Fixed width on larger screens, full width on mobile.

Fixed height on medium+ screens.

Shadow and hover effect for interaction.

Flex column layout to stack content vertically.

Course title and rating:
<div className="flex justify-between items-center mb-2 mt-1 sm:mt-3">
  <h3 className="text-lg sm:text-xl md:text-[24px] font-medium text-black">
    {course.title}
  </h3>
  <div className="flex items-center space-x-1">
    <FaStar className="text-yellow-400 text-[16px] sm:text-[18px]" />
    <span className="text-[16px] sm:text-[18px] font-medium">
      {course.rating.toFixed(1)}
    </span>
  </div>
</div>


Title on the left, rating with star icon on the right.

Responsive font sizes for title and rating.

Star icon colored yellow.

Course image:
<img
  src={course.image}
  alt={course.title}
  className="rounded-xl w-full h-[180px] sm:h-[200px] md:h-[228px] object-cover mb-4 md:mb-6"
/>


Course image fills width, fixed responsive height.

Rounded corners.

object-cover ensures image covers area without distortion.

Bottom margin for spacing.

Description:
<p className="text-black text-sm sm:text-base md:text-[16px] mb-3 flex-grow overflow-hidden">
  {course.description}
</p>


Paragraph with responsive font size.

Grows to fill available vertical space (flex-grow).

Hides overflow to keep layout clean.

Students enrolled:
<div className="flex items-center text-gray-700 text-xs mb-2">
  <FaUserGraduate className="mr-2 text-blue-800" />
  <span>{course.students}</span>
  <span className="ml-1 text-gray-400">students enrolled</span>
</div>


Icon + number + label.

Blue icon, gray text.

Small font size.

Level and duration info:
<div className="flex justify-between items-center text-gray-500 text-xs mb-3">
  <div className="flex items-center space-x-1">
    <FiBarChart className="text-orange-400" />
    <span>{course.level}</span>
  </div>
  <div className="flex items-center space-x-1">
    <MdAccessTime className="text-green-600" />
    <span>{course.duration}</span>
  </div>
</div>


Two info blocks side by side:

Level with orange bar chart icon,

Duration with green clock icon.

Small gray text.

Start Learning button:
<Link to="/DataScience">
  <button
    className="text-white bg-[#FF6501E5] px-4 sm:px-6 py-1 hover:bg-[#FF650133] hover:text-orange-500 transition duration-300 mt-2 text-base sm:text-[18px] mx-auto"
    style={{
      borderRadius: "5px",
      display: "flex",
      alignItems: "center",
      justifyContent: "center",
      gap: "14px",
    }}
  >
    Start Learning
  </button>
</Link>


Orange semi-transparent background with hover effects that lighten background and change text color.

Rounded corners and padding.

Centered horizontally (mx-auto).

Flexbox styles inside style prop for button content alignment (though here there’s only text).

Links to /DataScience route.

Main "Explore more" button below cards:
<div className="mt-6 md:mt-[30px] mb-4 md:mb-[20px]">
  <Link to="/DataScience">
    <button
      className="text-white bg-black hover:bg-[#7B7B7B] transition duration-300 flex items-center justify-center text-base sm:text-[20px] w-[160px] sm:w-[208px]  h-[35px] sm:h-[46px]"
      style={{
        borderRadius: "5px",
        padding: "5px 5px",
        boxShadow: "0px 4px 6px 0px #0000001A",
        gap: "10px",
      }}
    >
      Explore more →
    </button>
  </Link>
</div>


Black button with white text.

Changes to gray on hover.

Fixed width and height responsive to screen size.

Centered contents.

Rounded corners, padding, shadow.

Links to /DataScience.
*************************************************************************************
# src/components/Pride/PrideBanner.jsx
# Imports:
import React, { useState } from "react";
import bannerImage from "../../assets/Pride/PrideBanner/hand.png";
import ContactForm from "../../Pages/ContactForm";
import { Link } from "react-router-dom";


React and useState hook for managing modal visibility.

bannerImage is a hand image used on the right side.

ContactForm is a form component shown inside the modal.

Link from react-router-dom for internal navigation.

Component state:
const [showModal, setShowModal] = useState(false);


showModal boolean controls if the contact modal is visible.

Initially false — modal hidden.

Main container div:
<div
  className="relative flex flex-row items-center justify-between rounded-[10px] sm:rounded-[20px] w-full max-w-[1200px] sm:mx-4 md:mx-8 lg:mx-auto my-4 md:my-10 lg:my-20 px-2 md:px-10 lg:px-[68px] py-1 sm:py-6 md:py-8 lg:py-[25px]"
  style={{
    background: "linear-gradient(180deg, rgba(255, 101, 1, 0.06) 0%, rgba(255, 101, 1, 0.6) 100%)",
  }}
>


Flex container horizontally aligning content with space between.

Responsive margins, padding, and rounded corners.

Background is a vertical orange gradient with partial transparency.

max-w-[1200px] limits width on large screens.

relative positioning for any absolute children.

Left side: Text and buttons
<div className="w-full lg:w-[885px] flex flex-col justify-center gap-[10px] sm:mb-4 lg:mb-0">


Takes full width on small screens, fixed width on large.

Vertically stacks content with spacing (gap-10px).

Margin bottom on smaller screens for spacing.

Headline:
<h2 className="text-[24px] md:text-[32px] lg:text-[40px] leading-[32px] md:leading-[42px] lg:leading-[50px] font-bold text-[#FF6501] text-center lg:text-left">
  Come join us to make your <span className="text-[#4C00B0]">future rise</span> and your <span className="text-[#4C00B0]">identity shine</span>.
</h2>


Bold, large heading with responsive font size and line height.

Orange main text with purple (#4C00B0) highlights on "future rise" and "identity shine".

Text centered on smaller screens, left-aligned on large.

Buttons container:
<div className="flex flex-row gap-2 sm:gap-4 sm:mt-4 items-center justify-center lg:justify-start">


Horizontal flex container for the buttons with spacing.

Vertically centered buttons.

Centered on small screens, left aligned on large.

"Enroll Now" button:
<Link to="/DataScience">
  <button className="bg-black hover:bg-[#7B7B7B] text-white px-2 py-1 sm:px-6 sm:py-2 rounded-md font-semibold text-[13px] sm:text-[18px]">
    Enroll Now
  </button>
</Link>


Black button with white text.

Slightly smaller padding and font on mobile, bigger on larger screens.

Changes background color on hover.

Clicking navigates to /DataScience.

"Talk to our Counsellor" button & Modal logic:
<button
  className="bg-white text-black border border-gray-300 px-1 py-1 sm:px-6 sm:py-2 rounded-md font-semibold text-[13px] sm:text-[18px]"
  onClick={() => setShowModal(true)}
>
  Talk to our Counsellor
</button>


White button with black text and gray border.

Responsive padding and font size.

Clicking sets showModal to true, which opens the modal.

Modal overlay and content:
{showModal && (
  <div
    className="fixed inset-0 z-50 flex items-center justify-center bg-opacity-50"
    onClick={() => setShowModal(false)}
  >
    <div
      className="relative max-w-xl w-full"
      onClick={(e) => e.stopPropagation()}
    >
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}


Modal is conditionally rendered only if showModal is true.

Outer div:

fixed positioning covering entire viewport (inset-0).

z-50 ensures it overlays everything else.

Centered flex container.

Semi-transparent background (bg-opacity-50).

Clicking on this overlay closes the modal (setShowModal(false)).

Inner div:

Contains the actual ContactForm.

stopPropagation prevents clicks inside the form from closing the modal.

The ContactForm receives an onClose callback to allow closing from inside.

Right side: Image
<div className="relative lg:static">
  <img
    src={bannerImage}
    alt="Pride Hand"
    className="w-[130px] md:w-[180px] lg:w-[205px] h-auto lg:h-[290px] object-contain lg:absolute lg:-top-[72px] lg:right-[0px]"
  />
</div>


Container div for image:

relative on small/medium,

static on large screens.

Image:

Responsive widths (130px to 205px).

Maintains aspect ratio (h-auto).

On large screens, positioned absolutely near top-right.

object-contain keeps the entire image visible without cropping.
*********************************************************************************************
# src/components/Pride/PridePage.jsx
# Imports:
import React from "react";
import HeroSection_P from "./Herosection_P";
import StatsSection from "../Home/StatsSection";
import Footer from "../Footer/Footer";
import Contact from "../Footer/Contact";
import BlogSection from "./BlogSection";
import AmbassadorAdvice from "./AmbassadorAdvice";
// import OurEvents from "./";
import AboutBonnay from "./AboutBonnay";
import OurFeaturedCourses from "./OurFeaturedCourses";
import PrideBanner from "./PrideBanner";


Importing various components, most probably sections of the webpage:

HeroSection_P: Top hero/banner section.

StatsSection: Some statistics section (likely from the Home folder).

Footer and Contact: Footer and contact info sections.

BlogSection: Blog posts or news section.

AmbassadorAdvice: Probably testimonials or advice from ambassadors.

AboutBonnay: About section related to Bonnay.

OurFeaturedCourses: Section showcasing courses.

PrideBanner: Banner component with call to action (previously explained).

OurEvents is commented out, meaning it’s planned but not included yet.

Component definition:
const PridePage = () => {
  return (
    <div>
      <HeroSection_P />
      <StatsSection />
      {/* <OurEvents/> */}
      <AboutBonnay/>
      <OurFeaturedCourses/>
      <PrideBanner/>
      <AmbassadorAdvice/>
      <BlogSection/>
      <Contact/>
      <Footer/>
    </div>
  );
};


This is a functional React component that returns JSX.

It simply returns a <div> that wraps all the imported sections in a vertical stack.

The components are rendered in this order, likely reflecting the page layout from top to bottom:

Hero banner

Stats info

(Events section commented out for now)

About Bonnay info

Featured courses list

Pride call-to-action banner

Ambassador advice/testimonials

Blog posts/news

Contact section

Footer section

Export:
export default PridePage;


Exports the component as default so it can be used in routing or other components.

***************************************************************************
#  src/components/SoftwareDevelopment/BoughtTogether.jsx

# import 
import React from "react";
import { FaStar } from "react-icons/fa";
import { MdAccessTime } from "react-icons/md";
import img1 from "../../assets/CoursesLayout/Software/sd1.png";
import img2 from "../../assets/CoursesLayout/Software/sd2.png";
# Explanation of Each Import:
1.  import React from "react";
What it does:
It imports the React library, which is necessary to write JSX and define components.

Why it's used:
Even though in newer React versions (17+), explicit import React is no longer strictly required to use JSX, it’s still commonly included for clarity or compatibility.

2.  import { FaStar } from "react-icons/fa";
What it does:
Imports the star icon from the Font Awesome (fa) icon pack using react-icons.

Why it's used:
This icon is displayed next to the course rating (e.g., ⭐ 4.8).

Library used:
react-icons – a lightweight library for adding icons from different icon sets like Font Awesome, Material Icons, etc.

3.  import { MdAccessTime } from "react-icons/md";
What it does:
Imports the clock/time icon from Material Design (md) icon pack.

Why it's used:
Used to display the duration of the course next to the time (e.g., 🕒 12h 45min).

4.  import img1 from "../../assets/CoursesLayout/Software/sd1.png";
5.  import img2 from "../../assets/CoursesLayout/Software/sd2.png";
What they do:
These import two course-related images from your project directory.

Why they're used:
These are the thumbnails/cover images for each course shown inside the course cards.
* Component Structure Breakdown
# courses array
const courses = [
  {
    id: 1,
    title: "Master JavaScript",
    rating: 4.8,
    lesson: 15,
    description: "Software Developement",
    duration: "15h 25min",
    image: img1,
  },
  {
    id: 2,
    title: "Masters in MongoDB",
    rating: 4.5,
    lesson: 12,
    description: "Software Developement",
    duration: "12h 45min",
    image: img2,
  },
];


This is static data representing two software development courses.

Each course contains:

title, description

rating, lessons, duration

Course image.

# CourseCard component

A reusable component for displaying individual course information.

const CourseCard = ({ course }) => (
  ...
);

What it displays:

Course image, title, and description.

Number of lessons.

Duration using MdAccessTime icon.

Rating using FaStar icon.

Styling features:

tailwindcss utility classes.

Responsive design (hover, rounded, shadow, etc.).

# BoughtTogether component

This is the main exported component that puts everything together.

const BoughtTogether = () => {
  return (
    <div className="...">
      <h2>...</h2>
      <h3>...</h3>

1. Heading Section
<h2>Your <span>Software Development</span> Growth Path</h2>
<h3>Bundle up the best skillsets...</h3>


Text encouraging users to buy a bundle for better ROI.

2. Course Cards Section
<div className="flex flex-col md:flex-row ...">
  {courses.slice(0, 3).map(...)}
</div>


Loops through courses array.

Renders each using CourseCard.

Adds a + sign between cards (only on desktop).

Adds an = sign after the last card (desktop only).

3. Bundle Price Box
<div className="flex flex-col ...">
  <p className="line-through">Rs 30,000</p>
  <p className="text-[#FF6501]">Rs 9,999</p>
  <button>Purchase Now</button>
</div>


Shows the original price (30,000) and discounted price (9,999).

Call-to-action button to "Purchase Now".

4. Divider Line
<hr className="w-full border-t-[2px] border-gray-100 mt-10 md:mt-14" />


Thin line separating this section from the next on the page.

******************************************************************
# src/components/SoftwareDevelopment/FAQ.jsx

# Imports:
import { useState } from "react";
import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";


useState: React hook to manage the open/closed state of FAQs.

FaPlus, FaTimes: Icons for expand/collapse.

FaArrowRight: (Commented out) Used for optional action buttons.

# State Management
const [openIndex, setOpenIndex] = useState(null);


openIndex: Holds the index of the currently expanded FAQ.

setOpenIndex: Updates the expanded item.

If openIndex === index, that question is open. Else, it's closed.

# Toggle Function
const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


If the same question is clicked again, it collapses.

Otherwise, the new question expands.

# FAQ Data (Questions + Answers)
const faqData = [ ... ];


An array of question–answer pairs.

Example:

{
  question: "Is this a certified course?",
  answer: "Yes, after successful completion, you'll receive a certification..."
}

# Splitting the FAQs in Two Columns
const leftFaqs = faqData.slice(0, 3);
const rightFaqs = faqData.slice(3);


First 3 FAQs go in the left column.

Remaining go in the right column.

# renderFAQItem() – Render Each Question
const renderFAQItem = (item, index) => (
  <div className={`...`}>
    <button onClick={() => toggleIndex(index)} className="...">
      <span>{item.question}</span>
      {openIndex === index ? <FaTimes /> : <FaPlus />}
    </button>
    {openIndex === index && (
      <div className="...">
        <p>{item.answer}</p>
      </div>
    )}
  </div>
);


Renders the FAQ card.

Click toggles the answer open/closed.

Icon changes based on state (FaPlus = collapsed, FaTimes = expanded).

Answer is conditionally rendered using {openIndex === index && (...)}

# JSX Layout (Return Block)
<div className="w-full lg:mb-16 p-8 font-['Poppins'] ">
  <div className="max-w-7xl mx-auto">


Main container is centered and responsive.

Text is styled using Tailwind.

# Final Layout
1.  Title & Subtitle
<h2>Frequently Asked Questions</h2>
<p>Still you have any questions? Contact our Team via support@baoiam.com</p>

2.  Two Columns for FAQs
<div className="flex flex-col md:flex-row gap-8">
  <div className="md:w-1/2">{leftFaqs.map(...)} </div>
  <div className="md:w-1/2">{rightFaqs.map(...)} </div>
</div>

3.  Optional Footer Button
<button className="mt-4 px-5 py-2 ...">See All FAQ’s</button>

*************************************************************************
# src/components/SoftwareDevelopment/HeroSection_C.jsx
# Imports
import React from "react";
import { FaStar } from "react-icons/fa";
import { HiOutlineDownload } from "react-icons/hi";
import { MdPlayCircle } from "react-icons/md";
// image imports
import avatar from "../../assets/CoursesLayout/CoursesPage/avatar.png";
import Expert from "../../assets/CoursesLayout/CoursesPage/DS_Expert.png";
import SD from "../../assets/CoursesLayout/CoursesPage/software_dev.png";
import globe from "../../assets/CoursesLayout/CoursesPage/globe.png";
import laptop from "../../assets/CoursesLayout/CoursesPage/laptop.png";
// icons
import { AiFillHome, AiOutlineRight } from "react-icons/ai";
import { BsBookmark } from "react-icons/bs";
import { FiSend } from "react-icons/fi";
import { Link } from "react-router-dom";
import BookmarkButton from "../../Pages/BookmarkButton";


These are a mix of:

Icons for UI

Images (e.g. course preview, expert avatar)

React Router's Link for navigation

A custom BookmarkButton component

# Main Layout
<div className="bg-white font-['Poppins']">


Everything is wrapped inside a white background using the Poppins font.

# Breadcrumb Navigation
<nav className="flex items-center ...">
  <Link to="/">
    <AiFillHome />
  </Link>
  <AiOutlineRight />
  <span>Master Software Development</span>
</nav>


Displays:

Home Icon → /

Arrow icon (>)

Current page name

# Title + Subtitle
<h1>Master Software Development</h1>
<p>Code. Create. Launch Your Career.</p>


Visually catchy and styled for different screen sizes.

# Download Brochure Button
<a href="/Brochure/SD.pdf" download>Download Brochure</a>


When clicked, downloads the PDF of the course brochure.

👨‍🏫#Instructor Info
<img src={Expert} />
<p>Software Development Expert</p>


Also includes:

Supported languages (Hindi, English)

Last updated info (e.g. June 2025)

Each has an icon next to the label.

# Course Stats
<p>2000+ Got Placed</p>
<p>4.5 ⭐ 31782 Reviews</p>
<p>10,000+ Learners</p>


All styled inside a black rounded box using Tailwind.

# What Will You Learn?
[
  "Data Structures & Algorithms",
  "OOP",
  "Git/GitHub",
  "HTML/CSS/JavaScript",
  ...
]


Each is shown as a pill-like button. It's responsive and clean, using .map() for easy additions.

# Prerequisites
<ul>
  <li>Basic programming (any language)</li>
  <li>Logical thinking</li>
  <li>Commitment to learn</li>
  <li>No CS degree required</li>
</ul>


A bullet list of what the learner needs before starting the course.

# Right Sidebar (<aside>)

This is a call-to-action panel — meant to convert users into buyers.

# Banner Text
<p>20,000+ Openings. ₹7 LPA Median. You Could Be Next!</p>


Quick stat-based motivation to join the course.

🎞️ Video Preview Section
<img src={SD} alt="Course Preview" />


Currently just an image preview of the course (no actual video functionality is included here).

# Purchase Summary
<p>Course Fee: ₹4,999 (One-time)</p>
<ul>
  <li>Lifetime access</li>
  <li>Cancel within 2 days</li>
  <li>Projects & mentorship</li>
  <li>Certificate</li>
</ul>


Essential information about the cost and benefits.

# Action Buttons
<button>Buy Now</button>
<button>Add to Cart</button>
<BookmarkButton />
<FiSend />


Buy Now: Opens a Razorpay payment link in a new tab

Add to Cart: Adds course to cart (functionality not shown in this component)

BookmarkButton: A custom component to save the course

FiSend: Icon only; may represent "share" (functionality not included)

# Bottom Divider
<hr />


Visual separator before moving to next section of the course page.

******************************************************************
# src/components/SoftwareDevelopment/LearningJourney.jsx
# Import a named export:
import { useState } from "react";
 1. modules Array
const modules = [
  {
    title: "Module 1: Foundation & Skill Building (Month 1–3)",
    items: [
      "HTML5, CSS3, Responsive Design",
      ...
    ]
  },
  ...
];


An array of module objects.

Each module has:

A title

An items array (topics/skills covered in that module)

This is the core data used to generate the UI dynamically.

 2. State: openIndex
const [openIndex, setOpenIndex] = useState(null);


Tracks which module is currently open/expanded.

Initially null (none expanded).

 3. Toggle Function
const toggleModule = (index) => {
  setOpenIndex(openIndex === index ? -1 : index);
};


If the clicked index is already open → close it (-1)

If it’s not open → open it (set to index)

 4. Main Layout & Heading
<div className="text-center mb-8">
  <h1>Your <span className="text-orange-500">Data Science</span> Growth Path</h1>
  <p>Follow an expertly curated roadmap...</p>
</div>


Top header introducing the learning journey.

Responsive text sizes.

Highlighted "Data Science" with orange.

 5. Module Container
<div className="w-full md:max-w-2xl lg:w-[723px] ... overflow-auto ...">
  {modules.map((module, index) => (
    <div key={index}>
      ...
    </div>
  ))}
</div>


A scrollable box (max height: 790px).

Each module is rendered by mapping over modules.

 6. Module Title Block
<div
  className="w-full h-[64px] px-[15px] ... cursor-pointer rounded"
  onClick={() => toggleModule(index)}
>
  <span>{module.title}</span>
  <svg>...</svg>
</div>


The main clickable bar for each module.

Includes:

The module title

A dropdown icon (rotates when open)

# Icon Logic
className={`... ${openIndex === index ? "rotate-180" : ""}`}


The arrow icon rotates 180° when the module is expanded.

7. Module Items (Expanded List)
{openIndex === index && module.items.length > 0 && (
  <div className="flex flex-col gap-2 ...">
    {module.items.map((item, idx) => (
      <div key={idx} className="...">• {item}</div>
    ))}
  </div>
)}


If the current module is expanded (openIndex === index), render its items.

Each item is styled like a bullet point (•) with hover effects.

 8. Bottom Divider
<hr className="w-full border-t-[2px] border-gray-100 mt-12 mb-6" />


A horizontal line to visually separate this section from the next.
*******************************************************************
#  src/components/SoftwareDevelopment/SD_Page.jsx
 1. Imports

These lines bring in all the necessary components from other files for use in this page:

import React from 'react'
import HeroSection_C from './HeroSection_C'
import Footer from "../Footer/Footer"
import DiscountBanner from '../DataAnalysis/DiscountBanner'
import CertificateSection from '../DataScience/CertificateSection'
import FlexibleCourses from '../DataScience/FlexibleCourses'
import FAQ from './FAQ'
import LearningJourney from './LearningJourney'
import Navbar_C from '../DataAnalysis/Navbar_C'
import Experts from '../DataAnalysis/Experts'
import BoughtTogether from './BoughtTogether'


Each of these files likely contains a reusable React component for different sections of the page.

 2. Component Definition
const SD_Page = () => {
  return (
    <div>
      ...
    </div>
  )
}


This defines a functional React component named SD_Page, which represents the full Software Development course page.

 3. Component Composition (Inside <div>)

Here’s a breakdown of the components used in the page and their likely purpose/order:

Component	Description
<Navbar_C />	Top navigation bar (from Data Analysis section, reused here).
<HeroSection_C />	Hero section with title, description, download button, and course stats.
<LearningJourney />	Step-by-step course roadmap split into modules (12-month journey).
<BoughtTogether />	Bundle recommendation section: "Buy these together" style with pricing.
<Experts />	Section showing the course instructors or mentors.
<CertificateSection />	Info about the certificate you'll get after course completion.
<FlexibleCourses />	Likely highlights how flexible the course is (self-paced, online, etc.).
<FAQ />	Frequently Asked Questions — collapsible Q&A format.
<DiscountBanner />	Banner showing ongoing discount or promotion.
<Footer />	Website footer with contact, links, social media, etc.
 4. Export the Page
export default SD_Page;


This line makes the component available for use elsewhere, like in routing (e.g., "/software-development").
************************************************************************
# src/components/ScrollToTop.jsx

import { useEffect } from 'react';
import { useLocation } from 'react-router-dom';
useEffect: A React hook used to run side effects (like scrolling) after the component renders.

useLocation: A hook from react-router-dom that gives you the current URL path (pathname).

# Component Definition
js
Copy code
export default function ScrollToTop() {
  const { pathname } = useLocation();
Destructures pathname (e.g., /about, /contact, etc.) from the current URL location.

# Scroll Behavior
js
Copy code
  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);
useEffect runs every time pathname changes.

window.scrollTo(0, 0) scrolls the window to the top-left corner.

So whenever you navigate to a new route, the page scrolls to the top automatically.

# Return Value
js
Copy code
  return null;
}
This component doesn’t render anything in the UI, so it returns null.

# Why is this needed?
By default, React Router doesn't scroll to the top when you navigate to a new page. If you're on a long page, and then navigate to a new one, the scroll position stays the same, which creates a bad user experience.

This component fixes that behavior.


*******************************************************************
#  src/components/ScrollToTop.jsx
import { useEffect } from 'react';
import { useLocation } from 'react-router-dom';

export default function ScrollToTop() {
  const { pathname } = useLocation();

  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);

  return null;
}
#Line-by-Line Explanation
1. Importing hooks
js
Copy code
import { useEffect } from 'react';
import { useLocation } from 'react-router-dom';
useEffect: A React hook used to run code after a component renders.

useLocation: A hook provided by react-router-dom that gives you the current URL location (including the pathname).

 2. Getting the current path
js
Copy code
const { pathname } = useLocation();
This extracts the pathname from the current URL.

For example:

If the URL is https://example.com/about, then pathname = "/about".

 3. Scroll when the path changes
js
Copy code
useEffect(() => {
  window.scrollTo(0, 0);
}, [pathname]);
useEffect runs every time pathname changes (i.e., you navigate to a new page).

window.scrollTo(0, 0) scrolls the page to the top-left corner.

 So, when you change routes (pages), this component automatically scrolls to the top of the new page.

4. Return null
js
Copy code
return null;
The component does not render anything visible.

It's only used for its behavior (side effect), not for UI.

*****************************************************************
# src/Config/api.js
// export const API_BASE_URL = "http://127.0.0.1:8000/";
export const API_BASE_URL = "https://api.baoiam.com";
This sets the base URL of your backend API.

The localhost line is commented out (used for local development).

The active base URL is the live production API: https://api.baoiam.com

# API Endpoints Object
js
Copy code
export const API_ENDPOINTS = {
  ...
};
This object stores all your API paths in one place, making them easy to manage and reuse throughout your application.

# Auth Endpoints
js
Copy code
LOGIN: `${API_BASE_URL}/api/login/`,
SIGNUP: `${API_BASE_URL}/api/signup/`,
VERIFY_LOGIN: `${API_BASE_URL}/api/verify_login/`,
VERIFY_SIGNUP: `${API_BASE_URL}/api/verify_signup/`,
GOOGLE_LOGIN: `${API_BASE_URL}/api/google-login/`,
These endpoints handle user authentication:

Key	Purpose
LOGIN	User login with credentials
SIGNUP	Register a new user
VERIFY_LOGIN	Verify OTP or token after login
VERIFY_SIGNUP	Verify OTP or token after signup
GOOGLE_LOGIN	OAuth login using Google

# Contact Endpoint
js
Copy code
CONTACT_SUBMIT: `${API_BASE_URL}/api/contact/submit/`,
Submits a contact form (e.g., "Contact Us" page or inquiry form).

# Courses Content
js
Copy code
CONTENT: `${API_BASE_URL}/api/content/`,
Fetches course content (e.g., syllabus, module data, etc.).

# GCEP Form
js
Copy code
GCEP_CONTACT_SUBMIT: `${API_BASE_URL}/gcep/contact/submit/`,
A special form for GCEP (Graduate Career Enhancement Program or similar).

May relate to a specific track or department.
# Referral System
js
Copy code
REFERRAL_SUBMIT_FORM: `${API_BASE_URL}/referral/api/referrals/submit-form/`,
GENERATE_REFERRAL: `${API_BASE_URL}/referral/api/referrals/share/`,
Used to handle referrals, where users can refer friends and get rewards.

submit-form submits referral info.

share generates a unique referral link.

# Why This Is Useful
Storing all endpoints in one object like API_ENDPOINTS helps with:

# Code reusability: Use API_ENDPOINTS.LOGIN instead of hardcoding the URL everywhere.

# Environment management: Easily switch between local and production APIs.

# Error reduction: Centralizing URLs avoids typos and inconsistencies.

# Scalability: Easy to add or change API routes later.

# How You Might Use It
In an API call:

js
Copy code
import axios from "axios";
import { API_ENDPOINTS } from "./api";

const loginUser = async (credentials) => {
  const response = await axios.post(API_ENDPOINTS.LOGIN, credentials);
  return response.data;
};

*******************************************************************************
#  src/Pages/AboutUs/AboutUSPage.jsx
# import
import React from "react";
Imports React to use JSX syntax and create the component.

Imported Components
jsx
Copy code
import OurJourney from "./OurJourney.jsx";
import Header from "./Header.jsx";
import JourneySection from "./Journey.jsx";
import WhyUsSection from "./Section.jsx";
import ServicesSection from "./Service.jsx";
import EventsSection from "./Events.jsx";
import TeamSection from "../../components/Home/TeamSection.jsx";
import Contact from "../../components/Footer/Contact.jsx";
import Footer from "../../components/Footer/Footer.jsx";
These are smaller, reusable components that make up sections of the About Us page.

They are imported from various relative paths in the project structure.

Examples:

Header — likely the top section or banner.

JourneySection — a part explaining the company's journey.

WhyUsSection — reasons to choose the company.

ServicesSection — details about the services offered.

EventsSection — info about events.

TeamSection — team member profiles.

Contact — contact form or details.

Footer — the footer of the page.

Component Structure
jsx
Copy code
const AboutUSPage = () => {
  return (
    <div>
      {/* <OurJourney/> */}
      <Header />
      <JourneySection />
      <WhyUsSection />
      <ServicesSection />
      <EventsSection />
      <TeamSection/>
      <Contact/>
      <Footer/>
    </div>
  );
};
Returns a JSX tree that renders the page sections inside a root <div>.

The OurJourney component is commented out, so it won't render currently.

The order of components determines the vertical layout on the page.

What it Does on the Webpage
When this component is rendered, it shows the About Us page with:

A header/banner (Header)

A section explaining the company’s journey (JourneySection)

Reasons why users should choose this company (WhyUsSection)

A section describing their services (ServicesSection)

Information about events they are hosting or attending (EventsSection)

The team members (TeamSection)

A contact form or info (Contact)

The footer of the website (Footer)

Export Statement
jsx
Copy code
export default AboutUSPage;
Exports this component as the default export so it can be imported and used in other parts of the app, such as in routing.


******************************************************
# src/Pages/AboutUs/Events.jsx
# cImports:
import img1 from "../../assets/AboutUs/img1.jpg";
import img2 from '../../assets/AboutUs/img2.png';
import img3 from "../../assets/AboutUs/im3.jpg";


Three image files are imported from your assets folder.

These will be used inside the component to visually represent events.

JSX Returned by the Component:
<div className="py-10 px-4 md:px-10 bg-[#FAFAFA] text-center">
  {/* Heading */}
  <h2 className="text-[26px] md:text-[48px] font-bold mb-2">
    Beyond the Screen: <span className="text-orange-500">Our Events</span>
  </h2>
  <p className="text-black text-[24px] mb-8">
    Workshops, expert sessions, and team collaborations that matter.
  </p>

  {/* Image Grid */}
  <div className="flex justify-center items-center w-full py-5">
    <div className="grid grid-cols-4 grid-rows-2 gap-4 p-4 max-w-5xl bg-white border-4 border-[#D7D7D7]  w-full">
      {/* ...images in grid cells... */}
    </div>
  </div>
</div>


The root container (div) has padding (py-10 px-4 md:px-10), a light gray background (bg-[#FAFAFA]), and centers all text (text-center).

The heading (h2) uses responsive font sizes (text-[26px] md:text-[48px]), is bold, and highlights "Our Events" in orange.

A paragraph explains the nature of the events.

Image Grid:

The images are arranged using CSS Grid inside a centered container:

<div className="flex justify-center items-center w-full py-5">
  <div className="grid grid-cols-4 grid-rows-2 gap-4 p-4 max-w-5xl bg-white border-4 border-[#D7D7D7] w-full">
    {/* images */}
  </div>
</div>


The outer div centers the grid horizontally and vertically (flex justify-center items-center).

The grid has 4 columns and 2 rows with gaps between items (gap-4).

Max width is limited to max-w-5xl (~80rem), white background, and a light gray border.

Images Layout in Grid

Each image is placed in a specific grid cell or spans multiple cells:

{/* Left image: spans 2 rows */}
<div className="row-span-2">
  <img src={img1} alt="Event 1" className="w-full h-full object-cover rounded-md" />
</div>

{/* Large middle image: spans 2 columns */}
<div className="col-span-2">
  <img src={img2} alt="Event 2" className="w-full h-full object-cover rounded-md" />
</div>

{/* Bottom middle left */}
<div className="col-start-2 row-start-2">
  <img src={img3} alt="Event 3" className="w-full h-full object-cover rounded-md" />
</div>

{/* Bottom middle right */}
<div className="col-start-3 row-start-2">
  <img src={img2} alt="Event 4" className="w-full h-full object-cover rounded-md" />
</div>

{/* Right image: spans 2 rows */}
<div className="row-span-2 col-start-4 row-start-1">
  <img src={img1} alt="Event 5" className="w-full h-full object-cover rounded-md" />
</div>


img1 is used twice on the left and right edges, spanning two rows each, making these images tall vertical strips.

img2 is used twice: one large image in the middle spanning two columns on the top row, and one smaller image in the bottom right middle.

img3 is placed in the bottom left middle grid cell.

Each image uses w-full h-full object-cover to make sure it fills the grid cell nicely while preserving aspect ratio and cropping overflow.

Images have rounded corners (rounded-md).
********************************************************
# src/Pages/AboutUs/Header.jsx

# Imports & State:
import React, { useState } from 'react';
import Navbar from '../../components/Home/Navbar.jsx';
import AuthModal from "../../components/Auth/AuthModal.jsx";
import ContactForm from "../../Pages/ContactForm";
import img1 from "../../assets/AboutUs/img1.jpg";

const [showModal, setShowModal] = useState(false);
const [isAuthModalOpen, setIsAuthModalOpen] = useState(false);
const [isLoggedIn, setIsLoggedIn] = useState(false);


showModal controls the visibility of the Contact Form modal.

isAuthModalOpen controls the visibility of the Authentication modal.

isLoggedIn tracks if the user is logged in or not.

Authentication Handlers:
const handleAuthSuccess = () => {
  setIsLoggedIn(true);
  setIsAuthModalOpen(false);
};

const handleLogout = () => {
  setIsLoggedIn(false);
};


handleAuthSuccess is called when the user successfully logs in or signs up, it marks them as logged in and closes the Auth modal.

handleLogout logs the user out.

Component Structure:
1. Auth Modal
<AuthModal
  isOpen={isAuthModalOpen}
  onClose={() => setIsAuthModalOpen(false)}
  onAuthSuccess={handleAuthSuccess}
/>


AuthModal shows the login/signup UI.

It's open when isAuthModalOpen is true.

Closes when onClose is called.

Calls onAuthSuccess on successful authentication.

2. Container & Navbar
<div className="w-full h-auto mx-auto shadow-md overflow-hidden">
  <div className="relative h-[80vh]">
    <div className="fixed top-0 left-0 w-full z-30">
      <Navbar 
        onSignUpClick={() => setIsAuthModalOpen(true)}
        isLoggedIn={isLoggedIn}
        onLogout={handleLogout}
      />
    </div>


Outer container sets width, shadow, and overflow hidden.

Inner container has fixed height of 80% viewport height (80vh).

The Navbar component is fixed at the top (fixed top-0 left-0 w-full z-30), stays visible while scrolling.

Navbar receives:

onSignUpClick prop to open the auth modal.

isLoggedIn state to adjust navbar based on auth.

onLogout handler.

3. Hero Section Background
<div className="relative w-full h-full">
  <img
    src={img1}
    alt="Header"
    className="w-full h-full object-cover block"
  />
  <div className="absolute inset-0 bg-[#FF7C27] opacity-50"></div>
  <div className="absolute inset-0 bg-black opacity-30"></div>
</div>


Shows img1 as full-size background with object-cover to fill container and crop overflow.

Two overlays on top of the image:

Orange gradient (bg-[#FF7C27] with 50% opacity)

Black overlay (bg-black with 30% opacity)

The overlays combine for a warm, darkened background effect.

4. Centered Hero Content
<div className="absolute inset-0 z-20 flex flex-col items-center justify-center text-white text-center px-4 mt-12">
  <h1 className="text-2xl sm:text-3xl md:text-5xl font-bold leading-tight">
    Giving Students Opportunities,  <br className="hidden sm:block" />
    Experience and Skills
  </h1>

  <p className="mt-4 sm:mt-6 max-w-md sm:max-w-xl text-sm sm:text-base md:text-lg">
    We emphasize hands-on learning that promotes genuine <br className="hidden sm:block" />
    development and professional success.
  </p>

  <div className="mt-6 sm:mt-8 flex flex-col sm:flex-row gap-4 w-full sm:w-auto px-6 sm:px-0">
    <button className="bg-orange-500 text-white px-6 py-2 rounded-full hover:text-orange-500 hover:bg-amber-100 border-orange-500 transition duration-200 w-full sm:w-auto">
      Apply Now →
    </button>
    <button className="bg-black text-white px-6 py-3 rounded-full hover:bg-gray-600 transition duration-200 w-full sm:w-auto"
      onClick={() => setShowModal(true)}
    >
      Talk to our Counsellor
    </button>


Absolute positioned container centers its content over the background image.

White text with responsive font sizes.

Heading and paragraph with line breaks that show on larger screens.

Two buttons:

Apply Now — styled orange, fills width on small screens.

Talk to our Counsellor — black button that opens contact modal on click.

5. Contact Modal
{showModal && (
  <div
    className="fixed inset-0 z-50 flex items-center justify-center bg-opacity-50"
    onClick={() => setShowModal(false)}
  >
    <div
      className="relative max-w-xl w-full"
      onClick={(e) => e.stopPropagation()}
    >
      <ContactForm onClose={() => setShowModal(false)} />
    </div>
  </div>
)}


If showModal is true, a modal overlay appears:

Covers entire screen (fixed inset-0).

Centers the ContactForm component.

Clicking the overlay (outside the form) closes the modal.

Clicking inside the form prevents closing (event propagation stopped).

ContactForm receives an onClose callback.
*****************************************************
# src/Pages/AboutUs/Journey.jsx
Outer Container
<div className="py-12 px-4 md:px-10 bg-white">


Adds padding vertically (py-12) and horizontally (px-4 on small screens, px-10 on medium+).

Sets background to white.

2. Heading
<h2 className="text-3xl md:text-[48px] font-bold text-center mb-2">
  Our <span className="text-orange-500">Journey</span>
</h2>
<p className="text-center text-black text-base md:text-[24px] mx-auto mb-6 md:mb-10 max-w-2xl">
  What our side of journey looks like to reach you
</p>


Title "Our Journey" with "Journey" in orange.

Subtitle explaining the section.

Responsive font sizes and centered text.

Width is constrained (max-w-2xl) and centered (mx-auto).

3. Grid Layout for Content
<div className="grid grid-cols-1 md:grid-cols-3 max-w-5xl mx-auto">


Uses CSS Grid with 1 column on small screens and 3 columns on medium and larger.

Maximum width is limited (max-w-5xl) and centered horizontally.

4. Left Column (Hidden on Mobile)
<div className="hidden md:flex flex-col -mr-20 items-center font-poppins justify-center space-y-32 h-[467px]">
  <div className="bg-white shadow border-r-4 border-orange-500 p-4 text-justify text-lg md:text-[24px]">
    <p>
      More than 4+ years of practical experience developing
      professionals who are prepared for future.
    </p>
  </div>
</div>


Hidden on mobile (hidden md:flex).

Displays a single text block vertically centered.

Negative right margin (-mr-20) to shift it slightly left.

Text block has:

White background.

Shadow for elevation.

Right border with thick orange line (border-r-4 border-orange-500).

Padding and justified text.

Uses custom font (likely imported as font-poppins).

5. Center Column - The "Road"
<div className="relative hidden md:flex justify-center h-auto md:h-[467px] mb-8 md:mb-0">
  <div className="h-8 md:h-full w-8 bg-gray-400 relative">
    <div className="absolute inset-0 flex md:flex-col justify-between items-center">
      {Array.from({ length: 4 }).map((_, i) => (
        <div key={i} className="w-14 md:w-1 h-1 md:h-14 bg-white"></div>
      ))}
    </div>
  </div>
</div>


Only visible on medium+ screens (hidden md:flex).

Represents a vertical "road" or timeline:

Gray vertical bar (bg-gray-400, width 8).

White stripes on top arranged vertically, acting like dashed lines on a road.

The white stripes are created by rendering 4 divs in a column (md:flex-col), spaced evenly (justify-between).

On mobile, this whole column is hidden to simplify layout.

6. Right Column - The Main Content Boxes
<div className="flex flex-col md:-ml-20 items-center md:justify-between font-poppins space-y-8 md:space-y-32 h-auto md:h-[467px]">
  {/* Mobile: Show left side content first */}
  <div className="md:hidden bg-white shadow border-l-4 border-orange-500 p-4 text-justify text-lg w-full">
    <p>
      Equipped more than 4000+ students with practical experience and
      employable skills.
    </p>
  </div>

  <div className="bg-white shadow border-l-4 md:border-l-4 border-orange-500 p-4 text-justify text-lg md:text-[24px] w-full">
    <p>
      We've been at this for 4+ years, and we still get excited about
      every project.
    </p>
  </div>

  <div className="bg-white shadow border-l-4 md:border-l-4 border-orange-500 p-4 text-justify text-lg md:text-[24px] w-full">
    <p>
      Hundreds of placements were made possible by our focused training
      and mentoring.
    </p>
  </div>
</div>


This column contains multiple text blocks.

Uses vertical flexbox column layout.

Negative left margin (md:-ml-20) to shift it left for overlap effect on desktop.

Each text block:

White background, shadow, orange left border (border-l-4 border-orange-500).

Padding and justified text.

Responsive font size on medium screens.

The first block is only visible on mobile (md:hidden) and repeats content similar to the left side block to ensure mobile users see all content.

Spacing between blocks is responsive (space-y-8 on mobile, space-y-32 on desktop).

On desktop, flex items are justified between to evenly spread vertically (md:justify-between).

************************************************
# src/Pages/AboutUs/OurJourney.jsx

Component Structure & Explanation
1. Outer Container
<div className="bg-white w-full py-16 px-4 md:px-10 lg:px-20">


Full-width container with a white background.

Vertical padding (py-16).

Horizontal padding changes responsively: small (px-4), medium (px-10), large screens (px-20).

2. Heading Section (Centered)
<div className="text-center mb-14">
  <h2 className="text-3xl md:text-[48px] font-bold text-black mb-2">
    Our <span className="text-orange-500">Journey</span>
  </h2>
  <p className="text-gray-700 text-base max-w-xl mx-auto">
    jdu dkjd dhdjhi djdji shjdher jhdf ajhjhduis kjhduif adjhfjhiuf
  </p>
</div>


Centered heading "Our Journey" with "Journey" highlighted in orange.

Below the heading is a paragraph with placeholder text (jdu dkjd...) describing the section.

Paragraph text color is gray.

Max width of paragraph constrained (max-w-xl) and centered horizontally (mx-auto).

Margin bottom to separate from the next section.

3. Content Section - Images Left, Text Right
<div className="flex flex-col lg:flex-row justify-between items-start gap-4 max-w-6xl mx-auto">


Container for the main content.

Uses flexbox:

On small screens: column (flex-col).

On large screens (lg:): row (flex-row).

justify-between pushes items to edges horizontally on large screens.

Aligns items to start vertically.

Adds spacing between children (gap-4).

Width constrained to max 6xl and centered (mx-auto).

4. Left Side: Image Grid
<div className="flex-1">
  <div className="flex flex-col gap-4">
    {/* First row with two images */}
    <div className="flex gap-4">
      <div className="w-[235px] h-[200px] bg-gray-200 rounded-lg">
        <img src={img1} alt="Placeholder" className="w-full h-full object-cover rounded-lg" />
      </div>
      <div className="w-[230px] h-[200px] bg-gray-200 rounded-lg">
        <img src={img2} alt="Placeholder" className="w-full h-full object-cover rounded-lg" />
      </div>
    </div>
    
    {/* Second row with one large image */}
    <div className="w-[480px] h-[200px] bg-gray-200 rounded-lg">
      <img src={img3} alt="Placeholder" className="w-full h-full object-cover rounded-lg" />
    </div>
  </div>
</div>


flex-1 makes this container take up equal space in flex layout.

Images arranged in a vertical column with spacing (gap-4).

First row: two images side-by-side with fixed width & height and rounded corners.

Second row: one wide image below.

Images fill their containers completely (w-full h-full) and use object-cover to maintain aspect ratio.

Background placeholder gray used for loading or fallback.

5. Right Side: Text Content with Alignment Variation
<div className="flex-1 ">
  <div className="space-y-6">
    {/* Left-aligned items */}
    <div className="flex flex-col items-start">
      <div className="bg-white shadow-md rounded-xl p-4 max-w-md text-[24px]">
        • We've been at this for 4+ years, and we still get excited about every project.
      </div>
    </div>

    {/* Right-aligned middle item */}
    <div className="flex flex-col items-end">
      <div className="bg-white shadow-md rounded-xl p-4 max-w-md text-[24px]">
        • Over 4,000 students have interned with us and actually learned something useful.
      </div>
    </div>

    {/* Left-aligned last item */}
    <div className="flex flex-col items-start">
      <div className="bg-white shadow-md rounded-xl p-4 max-w-md text-[24px]">
        • Many of them landed solid jobs after working with us—and that's what matters.
      </div>
    </div>
  </div>
</div>


Also flex-1 to fill the remaining space.

Vertical stack of three text blocks separated by vertical spacing (space-y-6).

Each text block is inside a flex container to control horizontal alignment:

First and last items are left-aligned (items-start).

Middle item is right-aligned (items-end).

Each text box:

White background.

Medium shadow for subtle elevation.

Rounded corners (rounded-xl).

Padding inside (p-4).

Max width (max-w-md) to keep readable line length.

Text size 24px (text-[24px]).

Text content uses bullet points for emphasis.
**********************************************************************
# src/Pages/AboutUs/Section.jsx
1. Outer Container
<div className="bg-gray-50 mt-10 py-8 md:py-12 px-4 md:px-8">


Light gray background (bg-gray-50).

Top margin (mt-10) to separate it from the previous section.

Vertical padding that adjusts for screen size (py-8 small, md:py-12 medium and above).

Horizontal padding (px-4 small, md:px-8 medium and above).

2. Heading Section (Centered)
<div className="text-center mb-8 md:mb-12">
  <h2 className="text-3xl md:text-[48px] font-semibold">
    What Makes Us <span className="text-orange-500">Different</span>
  </h2>
  <p className="mt-2 md:mt-4 text-gray-700 text-base md:text-[24px] mx-auto max-w-2xl md:max-w-4xl">
    The values, support, and care that makes us more than any another learning platform.
  </p>
</div>


Heading with large, bold text.

The word "Different" is highlighted in orange.

A descriptive paragraph below the heading, centered and constrained in width for readability.

Margins provide spacing below the heading.

3. Cards Grid
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 md:gap-8 max-w-6xl mx-auto">


Responsive grid layout:

1 column on very small screens.

2 columns on small (sm) screens.

4 columns on large (lg) screens and above.

Gaps between cards adjust from 6 to 8 at medium screens.

The container’s width is max 6xl and centered.

4. Each Card

All four cards share the same structure with different icons and texts:

<div className="group bg-white rounded-lg md:rounded-xl shadow-sm hover:shadow-md md:hover:shadow-xl p-4 md:p-6 flex flex-col items-center text-center transition duration-300">
  <div className="w-16 h-16 md:w-[100px] md:h-[100px] bg-white-50 p-2 md:p-4 rounded-full border-2 border-orange-500 group-hover:border-transparent mb-4 md:mb-10">
    <IconComponent className="w-8 h-8 md:w-[60px] md:h-[60px] text-color transition-transform duration-300 group-hover:scale-110 md:group-hover:scale-125 ml-2 sm:ml-0" />
  </div>
  <p className="text-gray-800 font-medium text-base md:text-[22px]">Card Text</p>
</div>

Explanation of the card elements:

group: Used to apply hover effects on child elements when the card is hovered.

Background & Borders:

White background with rounded corners (rounded-lg or larger on medium screens).

Subtle shadow (shadow-sm) that intensifies on hover (hover:shadow-md or md:hover:shadow-xl).

Padding: More padding on larger screens.

Layout: Vertical stack with centered items and text (flex flex-col items-center text-center).

Transition: Smooth animation over 300ms when hovered.

5. Icon Container
<div className="w-16 h-16 md:w-[100px] md:h-[100px] bg-white-50 p-2 md:p-4 rounded-full border-2 border-orange-500 group-hover:border-transparent mb-4 md:mb-10">


Circle container for the icon with fixed width and height, increasing on medium screens.

Light white background (assuming bg-white-50 is a custom or Tailwind extended class for light white).

Padding inside the circle.

Rounded full (circle).

Orange border that disappears on hover (group-hover:border-transparent).

Margin below to separate from the text.

6. Icons

Each card uses a different icon from react-icons/fa:

FaGraduationCap: Symbolizes education or student-centric learning.

FaLightbulb: Represents ideas, innovation.

FaHandshake: Symbolizes collaboration and community.

FaStar: Represents excellence or expertise.

Icons have:

Responsive size (w-8 h-8 small, md:w-[60px] md:h-[60px] medium+).

Color: black or yellow depending on the card.

On hover, the icon slightly scales up (group-hover:scale-110, bigger on md screens).

7. Text Description
<p className="text-gray-800 font-medium text-base md:text-[22px]">...</p>


Dark gray text.

Medium font weight for emphasis.

Font size adjusts for different screen sizes.
****************************************************************
# src/Pages/AboutUs/Service.jsx

1. Imports and Data
import React from "react";
import Slider from "react-slick";
import img1 from "../../assets/AboutUs/Service/img1.jpg";
import img2 from "../../assets/AboutUs/Service/img2.jpg";
import img3 from "../../assets/AboutUs/Service/img3.jpg";
import img4 from "../../assets/AboutUs/Service/img4.jpg";
import img5 from "../../assets/AboutUs/im3.jpg";

import "slick-carousel/slick/slick.css";
import "slick-carousel/slick/slick-theme.css";

const services = [
  { title: 'Nexnott Dating App – for people who want real, not random.', image: img2 },
  { title: 'Courses that will worth your time—training and job-ready.', image: img1 },
  { title: 'Live classes where you can learn, and actually interact.', image: img3 },
  { title: 'Real-time projects for your resume & critical thinking skills', image: img4 },
];


You import images to show with each service.

react-slick package provides the carousel functionality.

An array services holds the title and image for each service.

2. Carousel Settings
const settings = {
  dots: true,
  infinite: true,
  speed: 600,
  slidesToShow: 1,
  slidesToScroll: 1,
  arrows: false,
};


Settings for the carousel:

Shows dots for navigation.

Infinite looping.

Slide animation speed 600ms.

Shows 1 slide at a time.

No arrow buttons.

3. Main Container
<div className="py-8 md:py-12 px-4 md:px-10 bg-white text-center">


Padding top and bottom adjusts based on screen size.

Padding left and right similarly responsive.

White background.

Text centered.

4. Heading
<h2 className="text-3xl md:text-[48px] font-semibold mb-2 md:mb-4">
  Our <span className="text-orange-500">Services</span>
</h2>
<p className="text-black text-base md:text-[24px] mb-10 md:mb-20 max-w-2xl mx-auto">
  Designed to Support, Guide, and Inspire Your Growth.
</p>


Large heading with orange highlight on "Services".

Subheading paragraph for context.

Margins to space content nicely.

Max width and centered for readability.

5. Carousel for Mobile and Medium Screens
<div className="block lg:hidden">
  <Slider {...settings}>
    {services.map((service, index) => (
      <div key={index} className="px-8">
        <div className="relative flex flex-col items-center h-full mb-10 ">
          {/* Image Circle */}
          <div className="absolute -top-0 w-[130px] h-[130px] rounded-full border-4 border-orange-500 bg-white p-1 z-10">
            <img src={service.image} alt="Service" className="w-full h-full object-cover rounded-full" />
          </div>

          {/* Card with polygon shape */}
          <div
            className="relative bg-orange-100 text-center px-6 pt-16 pb-16 rounded-lg w-full shadow-xl shadow-gray-500 mt-[60px]"
            style={{ clipPath: "polygon(0 0, 100% 0, 100% 90%, 50% 100%, 0 90%)", minHeight: "220px" }}
          >
            <p className="text-[20px] text-gray-800 mt-8">{service.title}</p>

            {/* Orange triangle under the card */}
            <div className="absolute bottom-6 left-1/2 transform -translate-x-1/2 translate-y-1/2 w-0 h-0 border-l-[70px] border-r-[70px] border-t-[20px] border-l-transparent border-r-transparent border-t-orange-500"></div>
          </div>
        </div>
      </div>
    ))}
  </Slider>
</div>


Only visible on screens smaller than large (lg).

Uses react-slick to slide through each service.

Each slide has:

A circular image at the top with orange border.

A polygon-shaped card with orange background and shadow.

Service title inside the card.

A decorative orange triangle below the card, created with CSS borders.

Layout is vertically stacked and centered.

6. Grid Layout for Large Screens
<div className="hidden lg:grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 md:gap-20 max-w-[1104px] h-auto md:h-[320px] mb-10 md:mb-20 mx-auto">
  {services.map((service, index) => (
    <div key={index} className="relative flex flex-col items-center h-full">
      <div className="absolute -top-10 w-[130px] h-[130px] rounded-full border-4 border-orange-500 bg-white p-1 z-10">
        <img src={service.image} alt="Service" className="w-full h-full object-cover rounded-full" />
      </div>

      <div
        className="relative bg-orange-100 text-center px-6 pt-16 pb-16 rounded-lg w-full shadow-xl shadow-gray-500"
        style={{ clipPath: 'polygon(0 0, 100% 0, 100% 90%, 50% 100%, 0 90%)', height: '100%', minHeight: '220px' }}
      >
        <p className="text-[20px] text-gray-800 mt-16">{service.title}</p>
        <div className="absolute bottom-6 left-1/2 transform -translate-x-1/2 translate-y-1/2 w-0 h-0 border-l-[70px] border-r-[70px] border-t-[20px] border-l-transparent border-r-transparent border-t-orange-500"></div>
      </div>
    </div>
  ))}
</div>


Visible only on large (lg) screens and above.

Uses CSS Grid with up to 4 columns.

Each grid item has:

Circular image floating above the card.

The same polygon-shaped orange card with shadow.

Service title text.

Orange triangle under the card.

7. Call-To-Action (CTA) Banner
<div
  className="mt-8 md:mt-16 relative bg-cover bg-center rounded-lg md:rounded-xl overflow-hidden text-white"
  style={{ backgroundImage: `url(${img5})` }}
>
  <div className="absolute inset-0 z-0 bg-[linear-gradient(0deg,#FF7C27,#FF7C27),linear-gradient(0deg,rgba(0,0,0,0.5),rgba(0,0,0,0.5))] opacity-30"></div>

  <div className="relative z-10 bg-black/60 px-4 py-6 md:px-12 md:py-10 text-center">
    <h3 className="text-xl md:text-3xl font-bold mb-2">Connect With Us</h3>
    <p className="text-sm md:text-base mb-4 md:mb-6">
      From Pune to Delhi to Bengaluru—we've been where students are.
    </p>
    <div className="flex flex-col sm:flex-row justify-center gap-3 md:gap-4">
      <button className="bg-white text-orange-500 text-sm md:text-xl px-4 py-1 md:px-10 md:py-2 rounded-md hover:text-orange-700 hover:opacity-30 hover:bg-orange-200 transition duration-200">
        Apply Now →
      </button>
      <button className="bg-black text-white text-sm md:text-xl font-semibold px-4 py-1 md:px-10 md:py-2 rounded-md shadow hover:bg-gray-500 transition duration-200">
        Talk to our Counsellor
      </button>
    </div>
  </div>
</div>


Full-width banner with a background image (img5).

Uses a semi-transparent black overlay with orange tint gradients to improve text visibility.

Content inside:

Heading: "Connect With Us"

Subtext mentioning major cities.

Two buttons:

Apply Now (white background, orange text)

Talk to our Counsellor (black background, white text)

Buttons have hover effects and responsive sizes.

Rounded corners for a polished look.
***********************************************************
# src/Pages/GCEP/Contact_Gcep.jsx
# Imports & Setup
import React, { useState } from "react";
import { API_ENDPOINTS } from "../../Config/api";


React, useState: You're using React and its useState hook for managing form state.

API_ENDPOINTS: This is likely an object that contains your backend API URLs. You're using API_ENDPOINTS.GCEP_CONTACT_SUBMIT to submit the form.

# State: formData
const [formData, setFormData] = useState({
  first_name: "",
  last_name: "",
  institute: "",
  designation: "",
  email: "",
  phone: "",
  job_title: "",
  message: "",
});


This initializes all form fields to empty strings.

formData holds the current values of the form fields.

setFormData updates them when the user types in the form.

# Function: handleChange
const handleChange = (e) => {
  const { name, value } = e.target;
  setFormData((prev) => ({
    ...prev,
    [name]: value,
  }));
};


Generic input handler for all fields.

It dynamically updates the correct key in the formData object using the name attribute of the input.

# Function: handleSubmit
const handleSubmit = async (e) => {
  e.preventDefault();
  ...
};


This function:

Prevents default form submission.

Logs the form data.

Sends a POST request to the API with formData as JSON.

Handles the response:

If successful: alerts user and resets form.

If error: alerts error message.

Catches fetch errors and logs them.

# Return JSX: Form UI
return (
  <div className="...">
    ...
  </div>
);


It includes:

# Heading
<h1>Connect or <span className="text-orange-500">Contact</span></h1>
<p>Complete the form...</p>

# Form Fields

Each form field is connected to formData via value and updated by onChange.

First Name & Last Name (required)

Institute (required)

Designation (optional)

Email (required)

Phone (optional)

Job Title (optional)

Message (required textarea)

# Submit Button
<button type="submit">Submit</button>


Triggers handleSubmit.

# Styling

Uses Tailwind CSS classes for:

Responsiveness

Spacing

Text styles

Colors

Borders and layout

*******************************************************************************
# src/Pages/GCEP/GcepPage.jsx
Imports
import React from "react";
import Header from "./Header.jsx";
import Contact from "../../components/Footer/Contact.jsx";
import Footer from "../../components/Footer/Footer.jsx";
import Partner from "../../components/Home/Partner";
import WhyJoinGCEP from "./WhyJoinGCEP.jsx";
import JoinGCEP from "./JoinGCEP.jsx";
import Contact_Gcep from "./Contact_Gcep.jsx";


These are React component imports.

Each import corresponds to a specific section or feature of the page.

The relative paths tell you where each component lives.

Component	Likely Role
Header	Top navigation or branding area
Contact	Possibly a general contact section (different from form)
Footer	Website footer with links, info
Partner	Could showcase partners, sponsors, or collaborators
WhyJoinGCEP	Explains the benefits of joining GCEP
JoinGCEP	A CTA section inviting users to join
Contact_Gcep	The contact form (the component you shared earlier)
# Main Component: GcepPage
const GcepPage = () => {
  return (
    <div>
        <Header/>
        <JoinGCEP/>
        <Partner/>
        <WhyJoinGCEP/>
        <Contact_Gcep/>
        <Contact/>
        <Footer/>
    </div>
  );
};

# What this does:

Renders all the components in a vertical layout inside a parent <div>.

Each component corresponds to a section of the page.

# Component Flow:

Header – likely the site's navigation bar.

JoinGCEP – section to encourage users to join or learn more.

Partner – section showing partnerships or collaborations.

WhyJoinGCEP – persuasive content explaining benefits.

Contact_Gcep – the detailed contact form (probably used for reaching out to collaborate or inquire).

Contact – may be a simpler contact section (e.g. address, phone, email).

Footer – bottom of the page with legal info, links, etc.

# Why it's a Good Structure

Modular: Each part of the page is in its own component.

Readable: Easy to understand and maintain.

Reusable: Components like Header, Footer, and Contact can be reused elsewhere.

Scalable: You can easily insert, remove, or reorder sections.

# Final Thoughts

This is a composition pattern: assembling smaller components to build a larger page.

It promotes clean code, separation of concerns, and reusability.

Great for team development and larger apps.
***************************************************************
# src/Pages/GCEP/Header.jsx

# Imports
import React, { useState } from "react";
import Navbar from "../../components/Home/Navbar.jsx";
import AuthModal from "../../components/Auth/AuthModal.jsx";
import img1 from "../../assets/GCEP/img1.jpg";

Import	Purpose
useState	React Hook to manage local state
Navbar	Top navigation component (includes sign-up/login/logout logic)
AuthModal	A modal popup for user authentication (login/signup form)
img1	Background image used in the hero section
# State Management
const [isAuthModalOpen, setIsAuthModalOpen] = useState(false);
const [isLoggedIn, setIsLoggedIn] = useState(false);

State	Purpose
isAuthModalOpen	Controls whether the authentication modal is visible
isLoggedIn	Tracks if the user is currently logged in
# Auth Handling Functions
const handleAuthSuccess = () => {
  setIsLoggedIn(true);
  setIsAuthModalOpen(false);
};

const handleLogout = () => {
  setIsLoggedIn(false);
};


handleAuthSuccess: Called after successful login/signup → closes modal and sets logged-in state.

handleLogout: Logs the user out.

# JSX Structure
# Main Wrapper
<div className="bg-white text-[#333] mb-4 font-['Poppins']">


Sets background color, text color, bottom margin, and font family.

1. # Auth Modal
<AuthModal
  isOpen={isAuthModalOpen}
  onClose={() => setIsAuthModalOpen(false)}
  onAuthSuccess={handleAuthSuccess}
/>


This modal appears when the user clicks "Sign Up" or "Login" from the Navbar.

Controlled via isAuthModalOpen.

2. # Navbar
<Navbar
  onSignUpClick={() => setIsAuthModalOpen(true)}
  isLoggedIn={isLoggedIn}
  onLogout={handleLogout}
/>


Renders the top navbar.

Props:

onSignUpClick: opens the modal

isLoggedIn: tells Navbar if user is logged in (to show either "Logout" or "Sign In")

onLogout: handles logging out

3. # Hero Section
<div className="relative w-full h-[90vh] min-h-[600px] pt-[80px]">


Height: Takes 90% of viewport height, min height 600px.

Padding top: 80px to avoid overlap with fixed navbar.

# Background Image
<img src={img1} ... />


Fills entire section.

object-cover ensures the image scales properly.

# Overlay Layers
<div className="absolute inset-0 bg-black opacity-60 z-20"></div>
<div className="absolute inset-0 bg-orange-400 opacity-10 z-20"></div>


Layered dark overlay for text readability

Slight orange tint overlay for brand styling

✍️ Hero Text Content
<h1 className="...">GCEP</h1>
<p className="...">Global Collabo Educational Partnership</p>
<p className="...">GCEP (Global Collabo Educational Partnership) is an initiative ...</p>


| Element           | Description                                                         |
| ----------------- | ------------------------------------------------------------------- |
| `h1`              | Large, bold "GCEP" title using `font-poltawski Nowy` (if available) |
| `p` (subtitle)    | Highlights the acronym using colored initials                       |
| `p` (description) | A paragraph describing the GCEP initiative                          |
                              |
| ---------------------- | -------------------------------------------------- |
| `fixed top-0`          | Fixes navbar at top of screen                      |
| `absolute inset-0`     | Positions overlay layers to fully cover hero image |
| `z-20`, `z-30`, `z-50` | Controls layer stacking                            |
| `object-cover`         | Ensures image covers the whole area responsively   |
| `translate-y-[-5%]`    | Slight upward shift of text content                |
| `text-[200px]` etc.    | Responsive font sizes for the title                |
| `text-orange-500`      | Brand color for acronym highlights                 |

********************************************************************
# src/Pages/GCEP/JoinGCEP.jsx
# Imports
import React from "react";
import gIcon from "../../assets/GCEP/maillogo.png"; // ❌ Unused in this component
import { number } from "framer-motion"; // ❌ Unused import


⚠️ Note: Both gIcon and number are imported but not used. You can safely remove them to clean up the code.

# Data: Steps
const steps = [
  { number: "1", title: "Submit an Inquiry", ... },
  { number: "2", title: "Review & Discuss", ... },
  { number: "3", title: "Tailored Partnership", ... },
];


This array contains all the information for each step:

number: The step number (displayed in a circle)

title: Step title

desc: Step description

# Layout & Styling
<div className="py-12 md:py-16 px-4 sm:px-6 lg:px-8 bg-white text-center">


Vertical padding on top/bottom (py-12, md:py-16)

Horizontal padding responsive (px-4 to lg:px-8)

White background and centered text

# Heading & Subheading
<h2>How to <span className="text-orange-500">join GCEP ?</span></h2>
<p>Follow these steps to become a partner...</p>


Bold, large heading

Emphasis on “join GCEP?” with orange color

Friendly instructional subtitle

# Steps Loop
{steps.map((step, index) => (
  <div key={index}> ... </div>
))}


Maps through the steps array and renders each step in a styled card.

Responsive layout:

On mobile: vertical stack

On desktop: horizontal row (md:flex-row)

# Connector Lines (Between Steps)
{index < steps.length - 1 && (
  <>
    {/* Mobile connector (curved line) */}
    <div className="md:hidden ...">
      <svg>...</svg>
    </div>

    {/* Desktop connector (curved SVG line) */}
    <div className="hidden md:block ...">
      <svg>...</svg>
    </div>
  </>
)}


Only rendered between steps (not after the last one).

On mobile: vertical curved line under the card.

On desktop: horizontal dashed curved line connecting to the next card.

Uses SVG paths for custom curved designs with orange dashed lines (strokeDasharray="8").

# Step Card
<div className="bg-white rounded-xl shadow-md p-6 ...">
  <div className="...">
    <div className="rounded-full bg-white shadow-md ...">
      <h1 className="text-orange-500 font-bold text-[48px]">{step.number}</h1>
    </div>
  </div>

  <h3>{step.title}</h3>
  <p>{step.desc}</p>
</div>


Each card includes:


| Element                                  | Purpose                           |
| ---------------------------------------- | --------------------------------- |
| `div.rounded-full`                       | Circle containing step number     |
| `h3`                                     | Step title                        |
| `p`                                      | Step description                  |
| `shadow-md`, `rounded-xl`, `text-center` | Tailwind classes for clean design |

# Responsive Design Highlights

Mobile: Vertical stack, with SVG connectors stacked below cards

Desktop: Horizontal row with curved dashed connectors between cards

Responsive font sizes (text-[24px], md:text-[48px], etc.)

***************************************************************************
#  src/Pages/GCEP/WhyJoinGCEP.jsx
# Imports
import React from 'react'
import seminarImage from '../../assets/GCEP/img2.jpg';


React: Required for the functional component

seminarImage: A local image used as the left-side visual

# Scroll Handler
const handleScroll = () => {
  document.getElementById("target-section").scrollIntoView({
    behavior: "smooth",
  });
};


When the "Join Now" button is clicked, the page will smoothly scroll to the element with id="target-section".

This is a client-side scroll interaction to lead users toward a form or another CTA section (likely the Contact_Gcep component).

# JSX Layout
🔹 Outer Container
<div className="relative w-full min-h-screen bg-white flex flex-col lg:flex-row ...">


Responsive Flex Layout:

flex-col on small screens (image on top, content below)

lg:flex-row on large screens (image and content side-by-side)

Min height: Full screen height (min-h-screen)

White background, with padding (px-4, py-10)

# Left Image Block
<div className="z-10 ... lg:absolute ...">
  <div className="bg-white rounded-lg">
    <img src={seminarImage} ... />
  </div>
</div>


Shows a rounded image of a seminar or educational activity

On desktop (lg), this image is absolutely positioned and floats on top-left

Styled with a white-to-orange gradient border, and shadow-like appearance

# Right Gradient Content Block
<div className="w-full lg:w-[calc(100%-350px)] ... bg-gradient-to-r from-black via-[#2b0f00] to-orange-500 ...">


Takes full width on mobile, partial width on larger screens

Uses a horizontal gradient background (black → brown → orange)

Text is white for contrast

# Content inside:
<h2>Why join GCEP ?</h2>
<p>Empower Your Institution ...</p>
<ul>...</ul>
<button onClick={handleScroll}>Join Now</button>


Heading: Large, bold

Subheading: A motivating message

List of Benefits:

Global Exposure

Access to Cutting-Edge Tools

Student-Centric Opportunities

Educator Empowerment

Collaborative Innovation

Recognition & Growth

CTA Button:

"Join Now" scrolls to a section of the page using handleScroll

Has hover effects and smooth transition

# Tailwind CSS Highlights
| Tailwind Class                                            | What It Does                                                 |
| --------------------------------------------------------- | ------------------------------------------------------------ |
| `flex flex-col lg:flex-row`                               | Stacks content vertically on mobile, horizontally on desktop |
| `absolute`, `translate-y-1/2`                             | Positions the image block to float beside the content        |
| `bg-gradient-to-r from-black via-[#2b0f00] to-orange-500` | Creates the right-side background gradient                   |
| `rounded-xl`, `shadow-md`                                 | Gives a polished, card-like appearance                       |
| `text-white`                                              | Ensures text is readable over dark background                |
| `hover:bg-gray-100 transition`                            | Adds subtle hover feedback to the button                     |
***********************************************************************************************
# src/Pages/Instructor/ApplicationProcess.jsx
Code
🔸 Step Data (Array)
const steps = [
  {
    title: "Fill the Application Form",
    desc: "Submit your details and teaching experience...",
    button: "Apply Now",
    align: "right",
  },
  ...
];


An array of steps, each containing:

title: Step title

desc: Short description

button (optional): CTA button label (e.g., "Apply Now")

align: Determines whether the step card appears on the left or right side of the timeline

# Component JSX
🔹 Outer Container
<div className="bg-white py-16 px-4 md:px-10 font-['Poppins']">


Sets the background to white

Adds vertical and horizontal padding

Uses the Poppins font for modern look

🔹 Section Heading
<h2 className="text-3xl md:text-4xl font-bold text-center mb-16">
  Application Process
</h2>


Responsive, bold heading centered above the timeline

🔹 Timeline Container
<div className="relative flex flex-col items-center">


Uses relative so that the vertical dashed line and step indicators can be positioned absolutely inside it

# Dashed Vertical Line
<div className="absolute top-0 left-1/2 transform -translate-x-1/2 h-full border-l-2 border-dashed border-orange-400 z-0"></div>


Positioned vertically down the center of the timeline

Dashed orange line (border-dashed border-orange-400)

Sits behind all step cards (z-0)

# Step Mapping
{steps.map((step, index) => (
  ...
))}


Loops over each step and renders:

A numbered circle

A card with text

A button (optional)

With conditional alignment

# Step Container
<div className={`w-full max-w-3xl flex flex-col md:flex-row items-center mb-16 relative z-10 ${step.align === "right" ? "md:flex-row-reverse" : ""}`}>


On small screens: vertical layout (flex-col)

On medium+ screens:

flex-row or flex-row-reverse based on step.align

max-w-3xl: restricts maximum width of step layout

z-10: keeps steps above the timeline

# Step Circle
<div className="absolute left-1/2 transform -translate-x-1/2 z-10">
  <div className="bg-orange-500 text-white ... rounded-full"> {index + 1} </div>
</div>


Numbered circle (1, 2, 3...) centered on the vertical line

Absolute positioning ensures it overlaps the line

Styled as a bold, colored circle with shadow

# Step Card (Main Content)
<div className={`w-full md:w-[40%] mt-10 md:mt-0 px-4 ${...}`}>
  <div className="bg-white shadow-md rounded-lg p-5 text-left">
    <h4>{step.title}</h4>
    <p>{step.desc}</p>
    {step.button && <button>{step.button}</button>}
  </div>
</div>

Feature	Purpose
| Feature                     | Purpose                                            |
| --------------------------- | -------------------------------------------------- |
| `md:w-[40%]`                | Makes step cards take 40% width on medium+ screens |
| `text-right` or `text-left` | Adjusts text alignment based on step side          |
| `shadow-md`, `rounded-lg`   | Gives a **card-like appearance**                   |
| `step.button && ...`        | Conditionally renders a CTA button if defined      |
****************************************************************************************
# src/Pages/Instructor/HeroSection_P.jsx
# Imports
import React, { useState } from "react";
import Navbar from "../../components/Home/Navbar.jsx";
import AuthModal from "../../components/Auth/AuthModal.jsx";
import img1 from "../../assets/Instructor/instructor.jpg";
import { FaCheck } from "react-icons/fa";


useState: manages modal and login state

Navbar: custom navigation bar

AuthModal: popup for login/signup

img1: background image (a photo of an instructor)

FaCheck: check icon from react-icons used in the benefits list

# Component State
const [isAuthModalOpen, setIsAuthModalOpen] = useState(false);
const [isLoggedIn, setIsLoggedIn] = useState(false);


isAuthModalOpen: controls whether the auth modal is visible

isLoggedIn: tracks if the user is logged in

# Event Handlers
const handleAuthSuccess = () => {
  setIsLoggedIn(true);
  setIsAuthModalOpen(false);
};

const handleLogout = () => {
  setIsLoggedIn(false);
};


These update the auth state when login/logout happens

# UI Structure Overview
<div className="bg-white ...">
  {/* Auth Modal */}
  {/* Outer Container with full-screen image */}
  {/* Fixed Navbar */}
  {/* Image with overlay gradients */}
  {/* Main Centered Text Content */}
</div>

# Auth Modal
<AuthModal 
  isOpen={isAuthModalOpen}
  onClose={() => setIsAuthModalOpen(false)}
  onAuthSuccess={handleAuthSuccess}
/>


Controlled modal that opens when user clicks "Sign Up" in the navbar

# Fixed Navbar
<div className="fixed top-0 left-0 w-full z-30">
  <Navbar 
    onSignUpClick={() => setIsAuthModalOpen(true)}
    isLoggedIn={isLoggedIn}
    onLogout={handleLogout}
  />
</div>


Navbar stays fixed at the top (z-30 ensures it sits above all other elements)

Passes props to handle login state and modal toggle

# Background Image + Overlays
<img src={img1} ... />
<div className="absolute inset-0 bg-[#FF7C27] opacity-20"></div>
<div className="absolute inset-0 bg-black opacity-50"></div>


img1: full-screen instructor image

Two overlapping layers:

Orange gradient (light overlay)

Black overlay (darker overlay to make text stand out)

# Main Centered Content
<div className="absolute inset-0 flex flex-col items-center justify-center ...">
  <h1>Share Your <span className="text-orange-500">Expertise.</span> Inspire <span className="text-orange-500">Learners.</span></h1>
  <p>Join a growing network...</p>
  <a href="https://forms.gle/..."><button>Apply Now</button></a>
  <div className="bg-white bg-opacity-90 ..."> {/* Benefits */} </div>
</div>


Text: Large headline and supporting paragraph

Button: Takes user to a Google Form to apply

Benefits card: Shows advantages of joining as an instructor

# Benefits List
<ul>
  <li><FaCheck /> Flexible teaching schedule</li>
  <li><FaCheck /> Access to a wide learner base</li>
  ...
</ul>


Each list item:

Uses the ✅ check icon (FaCheck)

Highlights reasons to join (e.g., flexible schedule, payouts)

**********************************************************************
# src/Pages/Instructor/Instructor.jsx
 # File Overview
import React from 'react'
import HeroSection_P from './HeroSection_P'
import ApplicationProcess from './ApplicationProcess'
import Footer from '../../components/Footer/Footer'


These imports bring in 3 child components:

Component	Purpose
HeroSection_P	Hero banner for the page (recruitment pitch to instructors)
ApplicationProcess	Visual timeline/steps showing how instructors can apply
Footer	Common site footer with contact info, links, etc.
# Component Structure
const Instructor = () => {
  return (
    <div>
        <HeroSection_P/>
        <ApplicationProcess/>
        <Footer/>
    </div>
  )
}


This Instructor component renders 3 sections in order:

<HeroSection_P />

Displays a large hero section with:

Background image

Catchy heading and CTA: “Apply Now”

A list of benefits for joining as an instructor

Auth modal and navbar

<ApplicationProcess />

A timeline layout that shows the 5 steps for becoming an instructor:

Fill form

Get shortlisted

(Optional) Give demo

Onboard

Start teaching

<Footer />

Common footer with:

Site links

Contact

Social media icons, etc.

# Page Flow Summary
---------------------------
|        Navbar           |
---------------------------
|  HeroSection_P          |
|  - CTA: Apply Now       |
|  - Benefits of joining  |
---------------------------
|  ApplicationProcess     |
|  - 5-step visual guide  |
---------------------------
|        Footer           |
---------------------------

# Final Purpose

This is a landing page for recruiting instructors, aimed at making the application process clear, persuasive, and visually engaging.

It combines marketing + instructional UX to help potential educators understand and trust the process of joining the platform.

************************************************************
# src/Pages/Kickstarcourses/AI-ML/AI_ML_Courses.jsx
# import 
import React, { useEffect, useState } from "react";
import { Star, Clock3, Users, BarChart3 } from "lucide-react";
import { API_ENDPOINTS } from "../../../Config/api";
useEffect: Runs side effects (API call) after component mounts.

useState: Manages local state (courses, loading).

lucide-react: Icon library used for visuals like star rating, duration, students, etc.

API_ENDPOINTS.CONTENT: A URL pointing to the course data.

# useState Setup
js
Copy code
const [courses, setCourses] = useState([]);
const [loading, setLoading] = useState(true);
courses: Holds the fetched array of course objects.

loading: Boolean to track loading state (shows loading text while data is being fetched).

# useEffect: Fetching Course Data
js
Copy code
useEffect(() => {
  fetch(API_ENDPOINTS.CONTENT) 
    .then((res) => res.json())
    .then((data) => {
      setCourses(data.courses_section.courses);
      setLoading(false);
    })
    .catch((err) => {
      console.error("Error fetching courses:", err);
      setLoading(false);
    });
}, []);
Runs once on mount ([] dependency).

Fetches data from the API.

Extracts courses_section.courses from the response.

Sets the courses state and disables loading.

# if (loading) – Show Loading State
jsx
Copy code
if (loading) {
  return <p className="text-center py-10">Loading courses...</p>;
}
Displays a loading message while the API is being fetched.

# JSX Structure Overview
jsx
Copy code
<section>
  <h2>What You'll Learn in AI-ML</h2>
  <p>Each course in this program...</p>

  <div className="cards grid">
    {courses.map((course, index) => (
      <div key={index} className="course-card">
        ...
      </div>
    ))}
  </div>
</section>
# Course Card Structure
Each course is displayed as a card with:

# Title + Rating
jsx
Copy code
<div className="flex justify-between">
  <div>{course.title}</div>
  <div>
    <Star /> {course.rating}
  </div>
</div>
Course title on the left

Star rating icon with number on the right

# Image Section
jsx
Copy code
<img src={course.image} alt={course.title} className="rounded-3xl" />
Renders course thumbnail image

Optimized with loading="lazy" for better performance

# Description & Meta Info
jsx
Copy code
<p>{course.description}</p>
<div>
  <Users /> {course.students} students
  <BarChart3 /> {course.level}
  <Clock3 /> {course.duration}
</div>
Displays:

Short course description

Number of enrolled students

Difficulty level (Beginner, Intermediate, etc.)

Course duration

# Call-to-Action
jsx
Copy code
<button className="Start Learning">Start Learning</button>
Prompts user to begin the course

Currently static — can be connected to a course detail page or login/signup

# TailwindCSS Styling Used
Responsive grid (flex-wrap, w-[30%], etc.)

Padding & margin: py-12, mb-10, px-4, etc.

Colors: bg-[#FF6501], text-yellow-500, etc.

Hover animations: hover:bg-orange-600, hover:shadow-md

# Example Data Structure Expected from API
json
Copy code
{
  "courses_section": {
    "courses": [
      {
        "title": "Intro to AI",
        "image": "https://example.com/image.jpg",
        "description": "Learn the basics of AI.",
        "students": 1200,
        "level": "Beginner",
        "duration": "6 weeks",
        "rating": "4.5"
      },
      ...
    ]
  }
}
**************************************************************************
# src/Pages/Kickstarcourses/AI-ML/AI-ML.jsx
import React from 'react';
import HeroSection from './HeroSection';
import AI_ML_Courses from './AI_ML_Courses'; 
import WhyUsChoose from './WhyUsChoose';
import Footer from '../../../components/Footer/Footer';
Imports:

HeroSection: Likely the top banner/intro for the AI/ML page.

AI_ML_Courses: A component that lists all available AI/ML courses (previously reviewed).

WhyUsChoose: Explains why someone should choose this platform or program.

Footer: The common footer used site-wide.

# Component Structure
jsx
Copy code
const AIML = () => {
  return (
    <>
      <HeroSection/>
      <AI_ML_Courses/>
      <WhyUsChoose/>
      <Footer/>
    </>
  );
};

export default AIML;
Here's what it does step by step:
<HeroSection />

Likely shows a large banner with heading, background image, and call-to-action to grab user attention.

<AI_ML_Courses />

Displays a list of AI/ML courses (probably using the data from an API like in the earlier AIMLCourses component).

Includes title, image, rating, description, and "Start Learning" button.

<WhyUsChoose />

Explains benefits of enrolling or choosing this particular program or institution.

Could include bullet points, features, or testimonials.

<Footer />

Renders the site's footer with links, contact, social media, etc.

**************************************************************
# src/Pages/Kickstarcourses/AI-ML/HeroSection.jsx
# Imports
import React from 'react';
import { useNavigate } from 'react-router-dom';
import img1 from '../../../assets/KickStar/HeroImg.png';


React: Necessary to define the component

useNavigate: React Router hook for programmatic navigation

img1: A local image asset used in the hero section

# Component Definition
const HeroSection = () => {
  const navigate = useNavigate();


navigate allows redirection when buttons are clicked.

# JSX Structure
🔸 Section Wrapper
<section className="relative ... h-[700px] bg-[#FFF4EC] ...">


relative: Needed for absolutely positioning children (like buttons and image)

h-[700px]: Fixed height

bg-[#FFF4EC]: Light peach background

flex: Layout with Flexbox

px-6 md:px-12: Padding for responsiveness

🔸 Inner Flex Container
<div className="w-full mx-auto flex flex-col-reverse md:flex-row ...">


On small screens: column-reverse (image below text)

On medium+ screens: row layout (image beside text)

# Text Section
<div className="text-center ... md:w-1/2">
  <h1 className="text-4xl md:text-[120px] ...">AI & ML</h1>


Large, bold title

Responsive text sizes (text-4xl, md:text-[120px])

font-poltawski Nowy: Custom font likely for branding

<p className="text-[40px] ...">
  Your 90-Day Career Kickstart
  <p> – By Expert Ferrero Rocher </p> 
</p>


Subheading with additional nested <p> — a bit unconventional HTML, ideally should combine both into one paragraph.

# CTA Buttons
<div className="absolute bottom-16 left-20 flex flex-col sm:flex-row gap-4">


Positioned near the bottom-left of the hero

Responsive layout: Stack vertically on small screens, side-by-side on larger ones

<button onClick={() => navigate('/courses')} ...>Explore Courses</button>
<button onClick={() => navigate('/#')} ...>Talk to our Counsellor</button>


navigate('/courses'): Redirects user to the courses page

navigate('/#'): Likely placeholder — should point to contact section or counselor form

# Image Section
<div className="absolute right-5 bottom-0 md:w-[730px]">
  <img src={img1} ... />
</div>


Absolutely positioned to the bottom-right of the section

img1 is the hero image, likely a person, illustration, or tech grap
***************************************************************************
# src/Pages/Kickstarcourses/AI-ML/WhyUsChoose.jsx
Imports
import React from 'react';
import {
  FaFire,
  FaUserGraduate,
  FaBriefcase,
  FaChalkboardTeacher,
  FaCertificate,
} from 'react-icons/fa';


Imports React and five icons from react-icons/fa, representing different features of the program.

🔸 Features Array (Dynamic Content)
const features = [
  {
    icon: <FaFire className="text-[#FF6501] text-[24px]" />,
    text: 'Intensive 90-Day Learning Journey',
  },
  ...
];


An array of objects, each representing one reason to choose AI-ML.

Each object has:

icon: A JSX element (icon component with Tailwind styling)

text: The description of the benefit

🧠 This pattern lets you loop over the data and render each feature dynamically — makes it easier to maintain or extend later.

🔸 JSX Return: Main Section
<section className="text-center py-16 bg-[#f9f9f9] px-4">


Main wrapper section

text-center: Centers all text

py-16, px-4: Padding for spacing

bg-[#f9f9f9]: Light gray background

🔹 Heading & Subtitle
<h2 className="text-[48px] font-bold mb-2">
  Why <span className="text-[#FF6501]">Choose</span> AI-ML?
</h2>
<p className="text-[20px] max-w-3xl mx-auto mb-10">
  Get access to industry-relevant courses...
</p>


Main heading with styled highlight on "Choose" using orange color

Subtitle is centered and constrained to a max-width for readability

🔹 Features List Grid
<div className="flex flex-wrap justify-center gap-6 max-w-5xl mx-auto">


Uses Flexbox with flex-wrap so cards wrap on smaller screens

gap-6: space between cards

max-w-5xl mx-auto: Centers the content and limits its width

🔸 Rendering Each Feature
{features.map((item, index) => (
  <div
    key={index}
    className="w-full sm:w-[45%] md:w-[30%] bg-white px-6 py-4 rounded-xl shadow-sm flex items-start gap-3 text-left"
  >
    {item.icon}
    <span className="text-[20px] font-medium">{item.text}</span>
  </div>
))}


Each card includes:

Width responsive classes:

Full width on mobile

45% width on small screens (2 in a row)

30% on medium+ screens (3 in a row)

Background & styling:

bg-white, shadow-sm, rounded-xl: clean card look

flex items-start gap-3: icon and text aligned horizontally with spacing
Icon and text are placed side by side
************************************************************************
# src/Pages/Kickstarcourses/SuccessFusion/HeroSection.jsx
📦 Imports
import React from 'react';
import { useNavigate } from 'react-router-dom';
import img1 from '../../../assets/KickStar/HeroImg.png';


useNavigate: From React Router, allows navigation between pages programmatically.

img1: An image asset (likely a hero graphic or illustration).

🚀 Main Component
const HeroSection = () => {
  const navigate = useNavigate();


Initializes navigate, which will be used to handle button clicks.

🎨 Hero Section Wrapper
<section className="relative -mt-25 w-full h-[700px] py-0 bg-[#FFF4EC] px-6 md:px-12 lg:px-18 flex items-center justify-between font-['Poppins']">


relative: For absolutely positioning internal elements

-mt-25: Slight overlap with the previous section (though this value isn't a valid Tailwind class — maybe a custom class?)

h-[700px]: Fixed height of the hero section

bg-[#FFF4EC]: Soft cream-colored background

flex items-center justify-between: Aligns children (text + image) horizontally

Uses custom font 'Poppins'

🔡 Content Container
<div className="w-full mx-auto flex flex-col-reverse md:flex-row items-center justify-between gap-16">


flex-col-reverse on small screens: Image shows above text

md:flex-row: On medium screens and up, show text left and image right

gap-16: Spacing between image and text

📝 Text Section
<div className="text-center mb-5 md:text-left md:w-1/2">


Text is centered on small screens, aligned left on medium+

Takes half width on medium screens and up

🏷️ Heading
<h1 className="text-4xl md:text-[120px] font-poltawski Nowy font-bold text-center">
  SUCCESS FUSION 
</h1>


Very large heading: text-4xl on mobile, 120px on desktop

Uses a likely custom serif font (Poltawski Nowy)

💬 Subheading
<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart  
  <p> – By Expert Ferrero Rocher </p> 
</p>


⚠️ Issue here:

You should not nest a <p> tag inside another <p> — that's invalid HTML.

✅ Suggested fix:

<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart  
</p>
<p className="text-[24px] text-black font-normal px-8 mt-2">
  – By Expert Ferrero Rocher
</p>

🧭 CTA Buttons
<div className="absolute bottom-16 left-20 flex flex-col sm:flex-row gap-4">
  <button onClick={() => navigate('/courses')} ...>Explore Courses</button>
  <button onClick={() => navigate('/#')} ...>Talk to our Counsellor</button>
</div>


Positioned absolutely inside the hero area

Two buttons:

"Explore Courses" navigates to /courses

"Talk to our Counsellor" navigates to an anchor (/#) — probably a placeholder

🖼️ Image Section
<div className="absolute right-5 bottom-0 md:w-[730px]">
  <img src={img1} ... />
</div>


Image is positioned absolutely, aligned to the bottom-right

Responsive width (md:w-[730px])

Adds visual interest on the right side of the hero
*****************************************************************
# src/Pages/Kickstarcourses/SuccessFusion/SuccessFusion.jsx
:

📦 Imports
import React from 'react';
import { useNavigate } from 'react-router-dom';
import img1 from '../../../assets/KickStar/HeroImg.png';


useNavigate: A React Router hook that lets you programmatically navigate between routes/pages in your app (e.g., when buttons are clicked).

img1: An image imported from your assets folder, likely used as the hero section’s main graphic.

🚀 Main Component
const HeroSection = () => {
  const navigate = useNavigate();


You define the React functional component.

Initialize navigate by calling useNavigate(), so you can use it inside the component to change pages when a button is clicked.

🎨 Hero Section Wrapper
<section className="relative -mt-25 w-full h-[700px] py-0 bg-[#FFF4EC] px-6 md:px-12 lg:px-18 flex items-center justify-between font-['Poppins']">


relative: Makes this container a reference point for absolutely positioned child elements.

-mt-25: Applies a negative top margin, pulling the section upwards to overlap with the previous section. (Note: -mt-25 is not a default Tailwind class, so it might be a custom utility or typo.)

w-full: Full width of the parent container.

h-[700px]: Fixed height of 700 pixels.

bg-[#FFF4EC]: Background color with a light cream tone.

px-6 md:px-12 lg:px-18: Responsive horizontal padding (6 units on mobile, 12 on medium, 18 on large screens).

flex items-center justify-between: Use Flexbox to align children horizontally, center vertically, and space them apart.

font-['Poppins']: Apply the 'Poppins' font family.

🔡 Content Container
<div className="w-full mx-auto flex flex-col-reverse md:flex-row items-center justify-between gap-16">


w-full mx-auto: Full width with horizontal auto margins (centers container).

flex flex-col-reverse: On small screens, children stack vertically in reverse order (image appears above text).

md:flex-row: On medium and larger screens, children are side-by-side in a row.

items-center justify-between: Vertically center items and place space between them horizontally.

gap-16: Adds space between the children.

📝 Text Section
<div className="text-center mb-5 md:text-left md:w-1/2">


text-center: Text is centered on small screens.

mb-5: Bottom margin for spacing.

md:text-left: On medium screens and larger, text is left-aligned.

md:w-1/2: Text container takes up half the width on medium+ screens.

🏷️ Heading
<h1 className="text-4xl md:text-[120px] font-poltawski Nowy font-bold text-center">
  SUCCESS FUSION 
</h1>


text-4xl: Large text size on small screens.

md:text-[120px]: Very large text (120px) on medium and larger screens.

font-poltawski Nowy: Custom font family likely imported elsewhere.

font-bold: Bold text weight.

text-center: Center text alignment.

💬 Subheading
<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart  
  <p> – By Expert Ferrero Rocher </p> 
</p>


Large 40px text, black color, medium font weight.

Margin-top of 4 units and horizontal padding.

⚠️ Issue: <p> inside another <p> is invalid HTML.

Fix:

<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart  
</p>
<p className="text-[24px] text-black font-normal px-8 mt-2">
  – By Expert Ferrero Rocher
</p>

🧭 CTA Buttons
<div className="absolute bottom-16 left-20 flex flex-col sm:flex-row gap-4">
  <button
    onClick={() => navigate('/courses')}
    className="bg-[#FF6501] text-white text-[20px] px-16 py-3 rounded-md font-semibold"
  >
    Explore Courses
  </button>
  <button
    onClick={() => navigate('/#')}
    className="bg-black text-white text-[20px] px-16 py-3 rounded-md font-semibold"
  >
    Talk to our Counsellor
  </button>
</div>


Positioned absolutely near the bottom-left of the section.

Buttons stack vertically on small screens, horizontally on small+ screens.

First button navigates to the /courses page.

Second button attempts to navigate to an anchor (/#) — likely a placeholder.

🖼️ Image Section
<div className="absolute right-5 bottom-0 md:w-[730px]">
  <img
    src={img1}
    alt="Hero Section"
    className="w-full h-[492px] flex item-end md:mx-0"
  />
</div>


Positioned absolutely at the bottom-right.

Takes fixed width (730px) on medium and larger screens.

Image is responsive and fits the container.

**************************************************************
# src/Pages/Kickstarcourses/SuccessFusion/SuccessFusionCourses.jsx
Imports
import React, { useEffect, useState } from "react";
import { Star, Clock3, Users, BarChart3 } from "lucide-react";
import { API_ENDPOINTS } from "../../../Config/api";


React hooks useState and useEffect for state management and side effects.

Icons from the lucide-react library for visual embellishment (stars, clock, users, bar chart).

API endpoint constant imported from your config for fetching data.

🚀 Component Initialization
const SuccessFusionCourses = () => {
  const [courses, setCourses] = useState([]);
  const [loading, setLoading] = useState(true);


courses holds the list of courses fetched from the API.

loading controls whether the data is still being fetched, for showing a loading state.

🔄 Data Fetching with useEffect
useEffect(() => {
  fetch(API_ENDPOINTS.CONTENT) 
    .then((res) => res.json())
    .then((data) => {
      setCourses(data.courses_section.courses); // extract courses from response
      setLoading(false);
    })
    .catch((err) => {
      console.error("Error fetching courses:", err);
      setLoading(false);
    });
}, []);


Runs once after the component mounts ([] dependency).

Fetches course data from your API endpoint.

On success, updates courses with data.courses_section.courses and turns off loading.

On failure, logs error and disables loading to avoid infinite spinner.

⏳ Loading State
if (loading) {
  return <p className="text-center py-10">Loading courses...</p>;
}


While fetching data, display a simple loading message centered with padding.

📚 Main Render - Courses Section
<section className="text-center px-4 py-12 bg-white">


Section container styled with centered text, padding, and white background.

📢 Title and Subtitle
<h2 className="text-[48px] font-semibold mb-2">
  What You’ll Learn in <span className="text-[#FF6501]">SUCCESS FUSION </span>
</h2>
<p className="text-[24px] max-w-3xl mx-auto mb-10">
  Each course in this program is tailored to maximize your skills within a short span — all under 90 days.
</p>


Large heading with bold font and a highlighted "SUCCESS FUSION".

Subtitle paragraph describing the course program, limited max width and centered.

🃏 Courses Cards Container
<div className="flex flex-wrap justify-center gap-10 px-10">


A flex container to hold the course cards.

flex-wrap allows cards to wrap on smaller screens.

Centers children horizontally with spacing (gap-10).

📝 Mapping through Courses to Render Cards
{courses.map((course, index) => (
  <div key={index} className="w-full sm:w-[45%] md:w-[30%]">
    ...
  </div>
))}


For each course in courses array, render a card.

Responsive widths: full width on mobile, 45% on small screens, 30% on medium+.

🏷️ Course Card Structure
<div className="bg-white rounded-2xl py-2 shadow-md hover:shadow-md transition-all duration-200 w-full max-w-[350px] mx-auto">


Card container with white background, rounded corners, vertical padding.

Box shadow with a hover effect.

Max width 350px, horizontally centered.

Title + Rating
<div className="flex items-center justify-between px-4 text-[24px] font-semibold">
  <div className="text-black">{course.title}</div>
  <div className="flex items-center gap-1 text-yellow-500">
    <Star size={16} fill="#FACC15" stroke="#FACC15" />
    <span className="text-black">{course.rating}</span>
  </div>
</div>


Flex container between course title (left) and rating (right).

Rating uses a yellow star icon and text.

Course Image
<div className="relative">
  <img
    src={course.image}
    alt={course.title}
    className="w-full h-48 object-cover rounded-3xl p-3"
    loading="lazy"
  />
</div>


Displays the course image.

Fixed height 48 (12rem), object-fit cover for cropping.

Rounded corners and padding inside the image container.

Lazy loading for performance.

Description and Meta Data
<div className="p-4">
  <p className="text-justify text-[18px]">{course.description}</p>

  <div className="mt-4 flex flex-col gap-2 text-[#4E5566] p-1">
    <div className="flex items-center gap-2">
      <Users size={14} className="text-[#564FFD]" />
      <span>{course.students} students enrolled</span>
    </div>

    <div className="flex items-center justify-between gap-4 p-1">
      <div className="flex items-center gap-2">
        <BarChart3 size={16} className="text-[#f52d12ff]" />
        <span>{course.level}</span>
      </div>
      <div className="flex items-center gap-2">
        <Clock3 size={16} className="text-[#1cc354ff]" />
        <span>{course.duration}</span>
      </div>
    </div>
  </div>


Course description text, justified with medium size.

Meta info section includes:

Number of students (with user icon).

Course level (with bar chart icon).

Course duration (with clock icon).

Styled with muted text color and spacing.

Call to Action Button
<button className="mt-5 w-1/2 bg-[#FF6501] text-[18px] text-white py-2 rounded-lg font-semibold hover:bg-orange-600 transition-all">
  Start Learning
</button>


Orange button taking half the card’s width.

White text, padding, rounded corners.

On hover, background color darkens for feedback.

No click handler here, so it’s just a styled button for now.

🔚 Export
export default SuccessFusionCourses;


Exports the component for use in other parts of the app.

*****************************************************************
#  src/Pages/Kickstarcourses/SuccessFusion/WhyUsChoose.jsx
:

📦 Imports
import React from 'react';
import {
  FaFire,
  FaUserGraduate,
  FaBriefcase,
  FaChalkboardTeacher,
  FaCertificate,
} from 'react-icons/fa';


React to create the component.

Icon components imported from react-icons/fa (FontAwesome icons) for visually representing each feature.

🔥 Features Data Array
const features = [
  {
    icon: <FaFire className="text-[#FF6501] text-[24px]" />,
    text: 'Intensive 90-Day Learning Journey',
  },
  {
    icon: <FaUserGraduate className="text-[#FF6501] text-[24px]" />,
    text: 'Designed for Absolute Beginners',
  },
  {
    icon: <FaBriefcase className="text-[#FF6501] text-[24px]" />,
    text: 'Interview-Ready Portfolio Projects',
  },
  {
    icon: <FaChalkboardTeacher className="text-[#FF6501] text-[24px]" />,
    text: 'Industry Expert-Led Live Sessions',
  },
  {
    icon: <FaCertificate className="text-[#FF6501] text-[24px]" />,
    text: 'Certification & Career Support',
  },
];


An array of feature objects.

Each object contains:

An icon element with a custom orange color (#FF6501) and size (24px).

A text description summarizing a feature of the program.

🚀 Main Component: WhyChooseSection
const WhyChooseSection = () => {
  return (
    <section className="text-center py-16 bg-[#f9f9f9] px-4">
      ...
    </section>
  );
};


Defines a functional component returning a styled <section>.

Section is centered text, padded vertically (py-16), has a light gray background (#f9f9f9), and horizontal padding.

🎨 Section Content
Heading
<h2 className="text-[48px] font-bold mb-2">
  Why <span className="text-[#FF6501]">Choose</span> SUCCESS FUSION?
</h2>


Large, bold heading (48px) with a margin bottom.

The word "Choose" is highlighted in the brand orange color (#FF6501).

The program name "SUCCESS FUSION" follows.

Subtitle
<p className="text-[20px] max-w-3xl mx-auto mb-10">
  Get access to industry-relevant courses designed to transform your tech skills and launch your career — all in just 90 days.
</p>


Descriptive paragraph in medium-large font (20px).

Max width limits line length to about 48rem (max-w-3xl).

Centered with mx-auto.

Bottom margin for spacing from the features.

🧩 Features List Container
<div className="flex flex-wrap justify-center gap-6 max-w-5xl mx-auto">
  {features.map((item, index) => (
    <div
      key={index}
      className="w-full sm:w-[45%] md:w-[30%] bg-white px-6 py-4 rounded-xl shadow-sm flex items-start gap-3 text-left"
    >
      {item.icon}
      <span className="text-[20px] font-medium">{item.text}</span>
    </div>
  ))}
</div>


Flex container that wraps features responsively.

justify-center horizontally centers the feature cards.

gap-6 adds consistent spacing between cards.

Maximum width limited to max-w-5xl (~80rem) and centered horizontally.

🃏 Individual Feature Cards

Each feature is mapped into a card <div> with these styles:

className="w-full sm:w-[45%] md:w-[30%] bg-white px-6 py-4 rounded-xl shadow-sm flex items-start gap-3 text-left"


Responsive widths:

w-full: full width on small screens.

sm:w-[45%]: about half width on small screens and up.

md:w-[30%]: about one-third width on medium screens and up.

White background with padding on x and y axes.

Rounded corners (rounded-xl) and subtle shadow (shadow-sm) for a card-like look.

Flexbox layout:

Items aligned at the start vertically (items-start).

Horizontal gap of 3 units between icon and text.

Text aligned left.

🖼️ Inside Each Card
{item.icon}
<span className="text-[20px] font-medium">{item.text}</span>


The icon is displayed first.

The text is styled with 20px font size and medium weight.

🔚 Export
export default WhyChooseSection;


Makes the component available to import and use elsewhere.
****************************************************************
#  src/Pages/Kickstarcourses/Udaan-90/HeroSection.jsx
📦 Imports
import React from 'react';
import { useNavigate } from 'react-router-dom';
import img1 from '../../../assets/KickStar/HeroImg.png';


React: To create the component.

useNavigate: A hook from React Router that lets you programmatically navigate between routes/pages.

img1: An imported image asset used in the hero section (likely a banner or illustration).

🚀 Main Component: HeroSection
const HeroSection = () => {
  const navigate = useNavigate();
  ...
};


Defines a functional component.

Initializes the navigate function to allow navigation when buttons are clicked.

🎨 Section Wrapper
<section className="relative -mt-25 w-full h-[700px] py-0 bg-[#FFF4EC] px-6 md:px-12 lg:px-18 flex items-center justify-between font-['Poppins']">


A <section> element wrapping the entire hero area.

Tailwind CSS classes:

relative: Makes this section a reference for any absolutely positioned children.

-mt-25: Negative margin-top (likely a custom class; not a default Tailwind class).

w-full: Full width of the container.

h-[700px]: Fixed height of 700 pixels.

py-0: No vertical padding.

bg-[#FFF4EC]: Sets a soft cream-colored background.

px-6 md:px-12 lg:px-18: Horizontal padding that increases on medium (md) and large (lg) screens.

flex items-center justify-between: Uses flexbox to horizontally align content, centered vertically, and spaced out.

font-['Poppins']: Uses the "Poppins" font family for text.

📐 Content Container
<div className="w-full mx-auto flex flex-col-reverse md:flex-row items-center justify-between gap-16">


A <div> that:

Takes full width.

Centers horizontally (mx-auto).

Uses flexbox layout:

flex-col-reverse on small screens (mobile): stacks content vertically with image first.

md:flex-row on medium and larger screens: arranges content side-by-side (text left, image right).

items-center justify-between: vertically centers items and spaces them apart.

gap-16: Adds spacing between text and image.

📝 Text Content Section
<div className="text-center mb-5 md:text-left md:w-1/2">


Contains the main textual content.

On mobile:

Text is centered.

Margin bottom for spacing.

On medium+ screens:

Text aligns left.

Takes half the container width (md:w-1/2).

Heading
<h1 className="text-4xl md:text-[120px] font-poltawski Nowy font-bold text-black">
  UDAAN 90
</h1>


Displays the main heading.

Font size:

text-4xl on small screens (around 2.25rem).

Very large 120px on medium and larger screens.

Uses custom font classes font-poltawski Nowy (likely a serif or stylized font).

Bold and black text color.

Subheading
<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart  
  <p> – By Expert Ferrero Rocher </p> 
</p>


Large subheading text with:

Font size 40px.

Top margin for spacing.

Black color and medium font weight.

Horizontal padding for spacing on the sides.

⚠️ Issue: You should not nest <p> inside another <p>, as it's invalid HTML.

Fix:

<p className="text-[40px] mt-4 text-black font-medium px-8">
  Your 90-Day Career Kickstart
</p>
<p className="text-[24px] mt-2 text-black font-normal px-8">
  – By Expert Ferrero Rocher
</p>

🧭 Call to Action Buttons
<div className="absolute bottom-16 left-20 flex flex-col sm:flex-row gap-4">
  <button onClick={() => navigate('/courses')} className="bg-[#FF6501] text-white text-[20px] px-16 py-3 rounded-md font-semibold">
    Explore Courses
  </button>
  <button onClick={() => navigate('/#')} className="bg-black text-white text-[20px] px-16 py-3 rounded-md font-semibold">
    Talk to our Counsellor
  </button>
</div>


Positioned absolutely within the section, near the bottom-left corner (bottom-16 left-20).

Flex container that stacks buttons vertically on small screens (flex-col).

Switches to horizontal layout on small and larger screens (sm:flex-row).

Spacing between buttons (gap-4).

Buttons

Explore Courses:

Orange background #FF6501.

White text, medium font size, padding, rounded corners.

On click, navigates to the /courses page.

Talk to our Counsellor:

Black background.

Same styling.

Navigates to a placeholder link (/#)—likely intended to scroll or open a modal in the future.

🖼️ Image Section
<div className="absolute right-5 bottom-0 md:w-[730px]">
  <img
    src={img1}
    alt="Hero Section"
    className="w-full h-[492px] flex item-end md:mx-0"
  />
</div>


The image container is absolutely positioned at the bottom-right of the section (right-5 bottom-0).

On medium+ screens, it has a fixed width of 730px.

Image itself:

Takes full width and fixed height 492px.

Uses object-fit (implied by object-cover or similar) to keep aspect ratio.

Slightly aligned with flex-end vertically inside its container.

🔚 Export
export default HeroSection;


Makes the component available for import and use in other parts of the app.

********************************************************************************
# src/Pages/Kickstarcourses/Udaan-90/Udaan90.jsx
import React from "react";
import HeroSection from "./HeroSection";
import UdaanCourses from "./UdaanCourses";
import WhyChooseSection from "./WhyUsSection";
import Footer from "../../../components/Footer/Footer";
Imports:

React core library.

Several components from local files and a shared Footer component.

HeroSection: Likely the top banner with the program title and call-to-action.

UdaanCourses: Displays the courses offered in the Udaan 90 program.

WhyChooseSection: Section explaining the benefits or unique selling points of the program.

Footer: The website footer with additional links or information.

jsx
Copy code
const Udaan90 = () => {
  return (
    <>
      <HeroSection />
      <UdaanCourses />
      <WhyChooseSection />
      <Footer/>
    </>
  );
};
Defines a functional component named Udaan90.

Returns a React fragment (<> ... </>) which allows grouping multiple JSX elements without adding extra nodes to the DOM.

Inside the fragment, it renders the imported components in order:

HeroSection at the top.

UdaanCourses next, listing the program's courses.

WhyChooseSection to show reasons to pick this program.

Footer at the bottom of the page.

What does it achieve?
This component serves as the complete page for the Udaan 90 program by combining different modular components into a cohesive layout.

It helps keep your code organized and maintainable by separating concerns.

You can update or reuse each section independently.

The structure clearly defines the flow of the page: hero → courses → reasons → footer.

Export
jsx
Copy code
export default Udaan90;
Exports this component to be used in your app’s routing or wherever the Udaan 90 page needs to be displayed.

**********************************************************
# src/Pages/Kickstarcourses/Udaan-90/UdaanCourses.jsx
Imports
import React, { useEffect, useState } from "react";
import { Star, Clock3, Users, BarChart3 } from "lucide-react";
import { API_ENDPOINTS } from "../../../Config/api";


React hooks: useEffect (for side effects like fetching data) and useState (for managing component state).

Icons: Star, Clock3, Users, BarChart3 — used for UI elements.

API_ENDPOINTS: Config object holding your API URLs (specifically, CONTENT endpoint here).

State Initialization
const [courses, setCourses] = useState([]);
const [loading, setLoading] = useState(true);


courses: Array to store the courses fetched from the API.

loading: Boolean to track loading state — initially true.

Fetch Data with useEffect
useEffect(() => {
  fetch(API_ENDPOINTS.CONTENT)
    .then((res) => res.json())
    .then((data) => {
      setCourses(data.courses_section.courses); // Store fetched courses
      setLoading(false);
    })
    .catch((err) => {
      console.error("Error fetching courses:", err);
      setLoading(false);
    });
}, []);


Runs once when the component mounts (empty dependency array []).

Fetches data from the API endpoint.

Parses JSON response.

Extracts courses array from data.courses_section.

Updates courses state and sets loading to false.

Handles errors by logging and stopping loading.

Conditional Loading Display
if (loading) {
  return <p className="text-center py-10">Loading courses...</p>;
}


While data is loading, shows a centered message to the user.

Once loading is done, renders the courses.

Main Render: Courses Section
<section className="text-center px-4 py-12 bg-white">


Section container with padding and white background.

Title & Subtitle
<h2 className="text-[48px] font-semibold mb-2">
  What You’ll Learn in <span className="text-[#FF6501]">SUCCESS FUSION </span>
</h2>
<p className="text-[24px] max-w-3xl mx-auto mb-10">
  Each course in this program is tailored to maximize your skills within a short span — all under 90 days.
</p>


Large heading with highlight on "SUCCESS FUSION".

Subtitle explains the program focus.

Courses Cards Container
<div className="flex flex-wrap justify-center gap-10 px-10">


Uses flexbox to wrap cards responsively.

Centers content with gaps and horizontal padding.

Mapping Courses to Cards
{courses.map((course, index) => (
  <div key={index} className="w-full sm:w-[45%] md:w-[30%]">
    ...
  </div>
))}


Loops over courses array to create a card for each.

Cards are responsive: full width on small screens, 45% on small-medium, 30% on medium+.

Individual Course Card
<div className="bg-white rounded-2xl py-2 shadow-md hover:shadow-md transition-all duration-200 w-full max-w-[350px] mx-auto">


White card with rounded corners, padding, and shadow effect.

Shadow intensifies slightly on hover.

Maximum width to keep cards neat, centered horizontally.

Card Header: Title & Rating
<div className="flex items-center justify-between px-4 text-[24px] font-semibold">
  <div className="text-black">{course.title}</div>
  <div className="flex items-center gap-1 text-yellow-500">
    <Star size={16} fill="#FACC15" stroke="#FACC15" />
    <span className="text-black">{course.rating}</span>
  </div>
</div>


Displays course title on left.

Displays rating on right with a star icon and rating number.

Course Image
<img
  src={course.image}
  alt={course.title}
  className="w-full h-48 object-cover rounded-3xl p-3"
  loading="lazy"
/>


Course image with fixed height, rounded corners, padding.

loading="lazy" defers image loading for performance.

Description & Meta Information
<p className="text-justify text-[18px]">{course.description}</p>


Course description, justified alignment.

<div className="mt-4 flex flex-col gap-2 text-[#4E5566] p-1">
  <div className="flex items-center gap-2">
    <Users size={14} className="text-[#564FFD]" />
    <span>{course.students} students enrolled</span>
  </div>

  <div className="flex items-center justify-between gap-4 p-1">
    <div className="flex items-center gap-2">
      <BarChart3 size={16} className="text-[#f52d12ff]" />
      <span>{course.level}</span>
    </div>
    <div className="flex items-center gap-2">
      <Clock3 size={16} className="text-[#1cc354ff]" />
      <span>{course.duration}</span>
    </div>
  </div>
</div>


Meta info shows:

Number of students enrolled (with Users icon).

Course difficulty level (with BarChart3 icon).

Course duration (with Clock3 icon).

Call-to-Action Button
<button className="mt-5 w-1/2 bg-[#FF6501] text-[18px] text-white py-2 rounded-lg font-semibold hover:bg-orange-600 transition-all">
  Start Learning
</button>


Button styled with orange background, white text.

Half width of card.

Rounded corners, hover effect darkening the button.

No click handler defined yet, but visually encourages user interaction.
****************************************************************************
# src/Pages/Kickstarcourses/Udaan-90/WhyUsSection.jsx
Imports
import React from 'react';
import {
  FaFire,
  FaUserGraduate,
  FaBriefcase,
  FaChalkboardTeacher,
  FaCertificate,
} from 'react-icons/fa';


React library for creating the component.

Several icons imported from react-icons/fa (FontAwesome icons), which provide a visual symbol for each feature.

Features Data Array
const features = [
  {
    icon: <FaFire className="text-[#FF6501] text-[24px]" />,
    text: 'Intensive 90-Day Learning Journey',
  },
  {
    icon: <FaUserGraduate className="text-[#FF6501] text-[24px]" />,
    text: 'Designed for Absolute Beginners',
  },
  {
    icon: <FaBriefcase className="text-[#FF6501] text-[24px]" />,
    text: 'Interview-Ready Portfolio Projects',
  },
  {
    icon: <FaChalkboardTeacher className="text-[#FF6501] text-[24px]" />,
    text: 'Industry Expert-Led Live Sessions',
  },
  {
    icon: <FaCertificate className="text-[#FF6501] text-[24px]" />,
    text: 'Certification & Career Support',
  },
];


An array named features holds objects.

Each object has:

icon: A JSX element rendering a specific icon with custom orange color (#FF6501) and size (24px).

text: A string describing the feature.

This array will be iterated over to render each feature dynamically.

Component JSX
const WhyChooseSection = () => {
  return (
    <section className="text-center py-16 bg-[#f9f9f9] px-4">
      {/* Heading */}
      <h2 className="text-[48px] font-bold mb-2">
        Why <span className="text-[#FF6501]">Choose</span> UDAAN90?
      </h2>

      {/* Subtitle */}
      <p className="text-[20px] max-w-3xl mx-auto mb-10">
        Get access to industry-relevant courses designed to transform your tech skills and launch your career — all in just 90 days.
      </p>

      {/* Features grid */}
      <div className="flex flex-wrap justify-center gap-6 max-w-5xl mx-auto">
        {features.map((item, index) => (
          <div
            key={index}
            className="w-full sm:w-[45%] md:w-[30%] bg-white px-6 py-4 rounded-xl shadow-sm flex items-start gap-3 text-left"
          >
            {item.icon}
            <span className="text-[20px] font-medium">{item.text}</span>
          </div>
        ))}
      </div>
    </section>
  );
};

Explanation

Section container:

Centered text.

Vertical padding py-16 and light gray background color #f9f9f9.

Horizontal padding px-4 for mobile-friendly spacing.

Heading (h2):

Large bold text (48px).

The word "Choose" is styled with the brand orange color #FF6501.

Bottom margin (mb-2) for spacing below.

Subtitle (p):

Medium-sized text (20px).

Max width max-w-3xl centers and restricts the text width for readability.

Bottom margin (mb-10) for spacing before the features grid.

Features grid container (div):

Uses flexbox with flex-wrap to allow items to wrap on smaller screens.

Justifies content to center.

Gap of 6 units between items.

Max width max-w-5xl and centered horizontally using mx-auto.

Feature item cards:

Responsive width:

Full width on very small screens (w-full).

45% width on small screens (sm:w-[45%]).

30% width on medium and larger screens (md:w-[30%]).

White background, padding (px-6 py-4), rounded corners (rounded-xl).

Light shadow for subtle elevation (shadow-sm).

Flex container aligns icon and text horizontally (flex items-start gap-3).

Text aligned to the left.

Inside each feature card:

The icon is rendered with consistent orange color and size.

The feature text is shown with a medium font weight and 20px font size.

Export
export default WhyChooseSection;


The component is exported so it can be imported and used elsewhere.
*******************************************************************
# src/Pages/PAP/CertificateSection .jsx
Imports
import React from "react";
import certificateImage from "../../assets/CoursesLayout/CoursesPage/certificate.jpg";


React is imported for building the component.

An image file (certificate.jpg) is imported to be displayed in the section, showing the certificate visually.

Component JSX
const CertificateSection = () => {
  return (
    <div className="bg-gray-100 py-10 px-4 flex justify-center font-['Poppins'] ">
      <div className="flex flex-col md:flex-row items-center justify-between max-w-6xl w-full gap-10 md:gap-20">
        
        {/* Left Text Section */}
        <div className="flex-1 text-center md:text-left">
          <h2 className="text-xl md:text-[40px] font-semibold leading-snug mb-4">
            Department for Promotion of Industry and Internal Trade 
            Corporation <span className="text-orange-500">(DPIIT)</span>
            <br />
            Accredited Certificate
          </h2>
          <p className="text-black text-sm md:text-[24px] leading-relaxed max-w-lg">
            Learn Now. Get Certified with our top
            accredited government recognised
            certificate . Pay Only After You're Placed
          </p>
        </div>

        {/* Right Certificate Image */}
        <img
          src={certificateImage}
          alt="Certificate"
          className="w-full max-w-lg mx-auto rounded-lg shadow-lg"
        />
      </div>
    </div>
  );
};

Explanation of JSX

Outer container (div):

Background color: light gray (bg-gray-100).

Vertical padding py-10 and horizontal padding px-4.

Uses flexbox with justify-center to center inner content horizontally.

Applies the 'Poppins' font family.

Inner container (div):

Uses flex for layout.

flex-col on small screens (stack content vertically).

Changes to flex-row on medium and larger screens (md:flex-row), placing text and image side-by-side.

items-center vertically centers the items.

justify-between pushes the two children apart.

Limits width with max-w-6xl for max container width.

Full width available with w-full.

Gaps between children: gap-10 on small screens, gap-20 on medium and above.

Left Text Section
<div className="flex-1 text-center md:text-left">
  <h2 className="text-xl md:text-[40px] font-semibold leading-snug mb-4">
    Department for Promotion of Industry and Internal Trade 
    Corporation <span className="text-orange-500">(DPIIT)</span>
    <br />
    Accredited Certificate
  </h2>
  <p className="text-black text-sm md:text-[24px] leading-relaxed max-w-lg">
    Learn Now. Get Certified with our top
    accredited government recognised
    certificate . Pay Only After You're Placed
  </p>
</div>


flex-1 ensures this section takes up available space in the flex container.

Text is centered on small screens, left-aligned on medium and larger (md:text-left).

Heading (h2):

Font size changes from xl (small screens) to 40px on medium+ screens.

Semi-bold font weight.

leading-snug for tighter line height.

Bottom margin for spacing.

Contains a highlighted span with orange text for "(DPIIT)".

Paragraph (p):

Text color black.

Smaller text on mobile (text-sm), larger on medium screens (text-[24px]).

Relaxed line height for readability.

Max width of lg (to keep text nicely constrained).

Right Certificate Image
<img
  src={certificateImage}
  alt="Certificate"
  className="w-full max-w-lg mx-auto rounded-lg shadow-lg"
/>


Displays the imported certificate image.

Width is full of the container (w-full), but constrained to a max width of lg (large).

Horizontally centered with mx-auto.

Rounded corners (rounded-lg) and a shadow (shadow-lg) for a polished look.

***************************************************************************
# src/Pages/PAP/CourseCard.jsx
Imports
import React from "react";
import courseImg from "../../assets/PAP/CourseImg.png"; // Not used in this code, could be removed
import { FaStar, FaRedo, FaUser, FaClock, FaChartBar } from "react-icons/fa";
import { FiBarChart } from "react-icons/fi";
import { Link } from "react-router-dom";

import DS from "../../assets/Home/FeaturedCourses/DS_F.png";
import DA from "../../assets/Home/FeaturedCourses/DA_F.png";
import Head from "../../assets/PAP/head.png";


react-icons/fa and react-icons/fi provide icons used in the UI.

Link from react-router-dom is used for client-side navigation.

Images imported for course cards and a small "head" icon.

courseData Array

This array holds the data for the courses to be displayed:

const courseData = [
  {
    title: "Data Science Course",
    rating: 5.0,
    description:
      "Up skill on the most in demand skills in the market – Python, Excel, Power BI, SQL.",
    brochure: "/Brochure/DS.pdf",
    brochureName: "DataScience_Brochure.pdf",
    link: "/DataScience",
    image: DS,
  },
  {
    title: "Data Analysis Course",
    rating: 5.0,
    description:
      "Up skill on the most in demand skills in the market – Python, Excel, Power BI, SQL.",
    brochure: "/Brochure/DA.pdf",
    brochureName: "DataAnalysis_Brochure.pdf",
    link: "/DataAnalysis",
    image: DA,
  },
];


Each object contains:

Course title, rating, short description.

Path and filename for downloadable brochure PDF.

Link to the course detail page.

Image representing the course.

Component JSX
return (
  <div className="bg-white py-10 px-4 md:px-10 font-['Poppins']">
    {/* Heading */}
    <h2 className="text-[32px] md:text-[36px] font-semibold text-center mb-2">
      Our courses with <span className="text-orange-500 font-bold">Pay after Placement</span> Options
    </h2>
    <p className="text-center text-black mb-10 text-[20px]">
      From learning to earning — payment comes after placement
    </p>

    {/* Cards Container */}
    <div className="grid grid-cols-1 md:grid-cols-2 gap-16 max-w-4xl mx-auto">
      {courseData.map((course, index) => (
        <div
          key={index}
          className="border border-gray-200 rounded-xl shadow-sm p-4 hover:shadow-md transition duration-300"
        >
          {/* Top Section: Title & Rating */}
          <div className="flex items-center justify-between mt-4">
            {/* Left: Head icon + Title */}
            <div className="flex items-center gap-2">
              <img src={Head} alt="Head Icon" className="w-6 h-6 sm:w-6 sm:h-6 object-contain" />
              <h3 className="text-lg font-bold">{course.title}</h3>
            </div>

            {/* Right: Star Rating */}
            <div className="flex items-center gap-1 text-yellow-500">
              <FaStar size={16} />
              <span className="text-sm font-medium">{course.rating}</span>
            </div>
          </div>

          {/* Course Image */}
          <div className="relative rounded-xl overflow-hidden">
            <img src={course.image} alt="Course" className="w-full h-48 object-cover" />
          </div>

          {/* Course Description */}
          <p className="text-sm text-black mt-2">{course.description}</p>

          {/* Course Details */}
          <div className="text-sm text-gray-700 mt-4 space-y-4">
            {/* Eligibility */}
            <div className="flex items-center justify-between gap-6">
              <div className="flex items-center gap-2">
                <FaUser className="text-indigo-500 text-lg" />
                <span className="font-medium text-gray-900">Eligibility</span>
              </div>
              <span className="text-right">
                All degrees and
                <br />
                Backgrounds Eligible
              </span>
            </div>

            {/* Duration */}
            <div className="flex items-center justify-between gap-6">
              <div className="flex items-center gap-2">
                <FaClock className="text-green-500 text-lg" />
                <span className="font-medium text-gray-900">Duration</span>
              </div>
              <span className="text-right">12 Months</span>
            </div>

            {/* Selection Process */}
            <div className="flex items-center justify-between gap-6">
              <div className="flex items-center gap-2">
                <FiBarChart className="text-red-400 text-lg" />
                <span className="font-medium text-gray-900">Selection Process</span>
              </div>
              <span className="text-right">
                All degrees and
                <br />
                Backgrounds Eligible
              </span>
            </div>

            {/* Next Batch */}
            <div className="flex items-center justify-between gap-6">
              <div className="flex items-center gap-2">
                <FaRedo className="text-red-400 text-lg" />
                <span className="font-medium text-gray-900">Next Batch</span>
              </div>
              <span className="text-right">
                All degrees and
                <br />
                Backgrounds Eligible
              </span>
            </div>
          </div>

          {/* Buttons */}
          <div className="flex gap-7 mt-6">
            <a
              href={course.brochure}
              download={course.brochureName}
              className="flex-1 bg-[#FFE8D9E5] text-orange-500 text-center font-medium py-2 rounded-md hover:bg-orange-300"
            >
              Brochure
            </a>

            <Link
              to={course.link}
              className="flex-1 text-center bg-orange-500 text-white font-medium py-2 rounded-md hover:bg-orange-300 hover:text-orange-500"
            >
              Learn More
            </Link>
          </div>
        </div>
      ))}
    </div>
  </div>
);

Explanation
Outer container

White background with vertical padding and horizontal padding on medium screens.

Uses 'Poppins' font.

The entire component is centered and constrained to max width (max-w-4xl for the grid container).

Heading & subtitle

Large heading with emphasis on "Pay after Placement" in orange color.

Subtitle below the heading explaining the payment model.

Course Cards Grid

Uses CSS grid: one column on small screens, two columns on medium and up.

Gap of 16 units between cards.

Each card is styled with a light border, rounded corners, subtle shadow, and a hover effect that increases the shadow.

Inside Each Card

Top Section:

Small "head" icon followed by course title on the left.

Rating stars with the rating value on the right.

Course Image:

Large image showing course theme.

Rounded corners with overflow hidden to keep image nicely clipped.

Description:

Short summary text below the image.

Details Section:

Four rows with icons and text, aligned left and right.

Eligibility: All degrees and backgrounds.

Duration: Fixed 12 months.

Selection Process and Next Batch: Both display similar text (can be customized).

Uses icons from react-icons with appropriate colors.

Buttons:

Left button to download the course brochure PDF.

Right button navigates to the detailed course page via React Router's Link.

***************************************************************

# src/Pages/PAP/FAQ_Pap.jsx
1. Imports & State
import { useState } from "react";
import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";

const [openIndex, setOpenIndex] = useState(null);


useState is used to keep track of which FAQ item is currently open (openIndex).

Icons from react-icons/fa for plus, times (close), and arrow symbols.

2. FAQ Data
const faqData = [
  {
    question: "Will Baoiam help me with interviews?",
    answer: "Yes! We offer resume reviews, interview preparation, mock sessions, and guaranteed interview opportunities. When you enrol in our course, it's our responsibility to make you 100% job ready and place you with the best package."
  },
  // ...more FAQs
];


An array of objects, each with a question string and an answer string.

This is the source data for the FAQ list.

3. State Logic for Toggling FAQ
const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


Clicking on a question toggles its open/closed state.

If the clicked FAQ is already open (openIndex === index), it closes (null).

Otherwise, it opens the clicked FAQ (setOpenIndex(index)).

4. Splitting FAQs into Two Columns
const leftFaqs = faqData.slice(0, 3);
const rightFaqs = faqData.slice(3);


The first 3 FAQs go into the left column.

The rest go into the right column.

5. Rendering Each FAQ Item
const renderFAQItem = (item, index) => (
  <div
    key={index}
    className={`rounded-lg text-[18px] font-med overflow-hidden shadow-sm transition-all duration-300 p-2 mb-4 ${
      openIndex === index ? "bg-white shadow" : "bg-white"
    }`}
    style={{ minHeight: openIndex === index ? "auto" : "80px" }}
  >
    <button
      onClick={() => toggleIndex(index)}
      className="w-full flex justify-between items-center px-5 py-4 text-left text-gray-900 font-medium focus:outline-none transition text-[16px] sm:text-[20px]"
    >
      <span>{item.question}</span>
      {openIndex === index ? (
        <span className="w-[44px] h-[44px] p-[10px] rounded-[6px] bg-[#FFF4E5] flex items-center justify-center">
          <FaTimes className="text-gray-600 sm:text-xl" />
        </span>
      ) : (
        <span className="w-[44px] h-[44px] p-[10px] rounded-[6px] bg-[#FFF4E5] flex items-center justify-center">
          <FaPlus className="text-gray-600 sm:text-xl" />
        </span>
      )}
    </button>

    {openIndex === index && (
      <div className="px-5 pb-4 text-gray-700 text-sm border-t border-gray-300">
        <p className="mb-3 mt-4 sm:text-[18px]">{item.answer}</p>
        {/* Optional button section commented out */}
        {item.button && (
          <a
            href={item.button.link}
            className="inline-flex items-center text-blue-600 hover:underline text-sm font-medium mt-3"
          >
            {item.button.text}
            <span className="ml-2">→</span>
          </a>
        )}
      </div>
    )}
  </div>
);


Each FAQ item is a div containing a button which toggles the answer visibility.

The button shows the question text and an icon (+ or ×) depending on open state.

When open, the answer text is shown below the question.

Uses Tailwind CSS for styling, including transitions and layout.

The minHeight style keeps closed FAQ items visually uniform.

The item.button code is ready for optional buttons in FAQ answers but currently unused.

6. Main Render Structure
return (
  <div className="w-full lg:mb-16 p-8 font-['Poppins'] ">
    <hr className="w-full  border-t-[2px] border-gray-100 mb-6" />
    <div className="max-w-7xl mx-auto">
      <h2 className="text-[24px] md:text-4xl font-bold text-gray-900 mb-3 text-center">
        Frequently Asked Questions
      </h2>
      <p className="text-center mb-8 text-[12px] sm:text-[18px]">
        You still have any questions? Contact our Team via
        <br />
        <a href="mailto:support@baoiam.com" className="text-orange-500">
          support@baoiam.com
        </a>
      </p>

      <div className="flex flex-col md:flex-row gap-8">
        {/* Left Column */}
        <div className="md:w-1/2">
          {leftFaqs.map((item, index) => renderFAQItem(item, index))}
        </div>

        {/* Right Column */}
        <div className="md:w-1/2">
          {rightFaqs.map((item, index) => renderFAQItem(item, index + 3))}
        </div>
      </div>

      <div className="flex justify-center mt-5">
        <button className="mt-4 px-5 py-2 border rounded-md bg-gray-200 border-gray-300 hover:bg-gray-100 transition hover:font-medium">
          See All FAQ’s
        </button>
      </div>
    </div>
  </div>
);


The FAQ section is wrapped in a full-width container with padding.

A horizontal rule (<hr>) separates the FAQ visually.

Centered title and a contact email for support.

The FAQ list is split into two columns on medium screens using flexbox.

The "See All FAQ's" button is shown below the list (currently without any click handler).

Summary

State management: Tracks which FAQ is open to show/hide answers.

Two columns: Splits FAQs into left/right columns for larger screens.

Toggle icons: Show plus or times icons for open/closed states.

Accessible button: Each question is a button for easy keyboard navigation.

Styled with Tailwind CSS: Responsive and visually clean.

Expandable design: Supports optional buttons in FAQ answers (commented out).

Contact link: Provides a support email for further questions.

***********************************************
# src/Pages/PAP/HeroSection.jsx
1. Imports and State
import React, { useState } from "react";
import { FaStar } from "react-icons/fa";
import { FaUser, FaPhone } from "react-icons/fa6"; // Note: FaPhone is imported but not used in code
import avatar from "../../assets/CoursesLayout/CoursesPage/avatar.png";
import Head from "../../assets/PAP/head.png";

const [name, setName] = useState("");
const [phone, setPhone] = useState("");
const [error, setError] = useState("");


Uses useState to manage name, phone, and error states.

Imports icons for visual UI elements.

Imports images for avatar and header icon.

2. Form Submission Handler
const handleApply = () => {
  if (!name.trim() || !phone.trim()) {
    setError("Please fill in both name and phone number.");
    return;
  }
  setError("");
  // Placeholder for submitting form data, e.g., to backend
  console.log("Form submitted:", { name, phone });
};


Validates that both name and phone inputs are filled.

Shows an error message if either is empty.

Clears error and logs form data on successful validation.

You can expand this to integrate with APIs or backend logic.

3. JSX Structure
<div className="w-full bg-white">


Wrapper div for the entire hero section with white background.

4. Top Banner Announcement
<div className="w-full bg-orange-500 text-white text-center py-2 text-[26px] font-medium mt-5">
  Next batch starts on ⌛️ 5th August. Hurry, limited seats left!
</div>


Orange background banner with white centered text.

Announces upcoming batch date with urgency.

5. Main Content Container
<div className="max-w-7xl mx-auto px-4 py-10 flex flex-col md:flex-row justify-between items-center gap-8">


Centers the content with max width.

Uses flexbox for layout: vertical on small screens (flex-col), horizontal on medium+ screens (md:flex-row).

Adds spacing and alignment between child elements.

6. Left Content (Headline + Stats)
<div className="flex-1 md:mt-2 md:max-w-3xl">
  <div>
    <h1 className="text-3xl sm:text-4xl md:text-[52px] font-bold text-black leading-snug">
      Launch your career with our
      <span className="text-orange-500"> Data Science Course </span>
      and <span className="text-orange-500">Pay After Placement</span>
    </h1>
    <p className="text-[#555555] text-[22px] sm:text-base mt-7">
      Curriculum designed and taught by our best mentors to prepare you
      and upskill your resume.
    </p>
  </div>

  {/* Stats */}
  <div className="w-full flex justify-center my-10">
    <div className="w-full max-w-[575px] min-h-[68px] rounded-[20px] bg-black text-white px-2 sm:px-4 py-4 flex flex-row justify-between items-center gap-1">
      {/* Got Placed */}
      <div className="text-center flex-1 min-w-[100px]">
        <p className="text-[13px] sm:text-[18px] font-semibold flex items-center justify-center">
          2000+
        </p>
        <p className="text-[10px] text-white sm:text-[14px]">
          Got Placed
        </p>
      </div>
      {/* Rating */}
      <div className="text-center flex-1 min-w-[100px]">
        <p className="text-[13px] sm:text-[18px] font-semibold flex items-center justify-center">
          4.5
          <FaStar className="ml-1 text-yellow-400 text-sm sm:text-xl" />
        </p>
        <p className="text-[10px] sm:text-[14px] text-white font-medium">
          31782 Reviews
        </p>
      </div>
      {/* Learners */}
      <div className="text-center flex-1 min-w-[100px] pr-2">
        <div className="flex items-center justify-center">
          <p className="text-[13px] sm:text-[18px] font-semibold">
            10,000+
          </p>
          <img
            src={avatar}
            alt="Learners Icon"
            className="hidden sm:block w-[45px] h-[25px] object-cover rounded-full ml-1"
          />
        </div>
        <p className="text-[10px] sm:text-[14px] text-gray-300 font-medium mt-1">
          Learners
        </p>
      </div>
    </div>
  </div>
</div>


Large headline promoting the course with styled keywords in orange.

Paragraph describing the curriculum briefly.

Stats section in a black rounded container, showing:

Number placed (2000+ Got Placed)

Average rating with stars (4.5 and 31782 Reviews)

Number of learners with an avatar image (10,000+ Learners)

7. Right Form Box
<div className="w-full md:w-[500px] md:h-auto bg-white shadow-md rounded-xl p-8 border border-gray-200">
  <div className="max-w-sm mx-auto text-center">
    {/* Heading */}
    <h3 className="flex items-center justify-center gap-2 text-lg sm:text-[32px] font-semibold text-black mb-1">
      <img
        src={Head}
        alt="Head Icon"
        className="w-8 h-8 sm:w-8 sm:h-8 object-contain"
      />
      <span className="text-black">Start learning for </span>
      <span className="text-orange-500 font-bold">FREE</span>
    </h3>

    <h4 className="text-[16px] text-black mb-4">
      Lectures & Assignments curated by Top Tech Professionals
    </h4>

    {/* Name input */}
    <div className="flex items-center rounded-md px-3 mb-4 bg-[#F6F6F6]">
      <FaUser className="text-gray-500 mr-2" />
      <input
        type="text"
        placeholder="Full Name"
        value={name}
        onChange={(e) => setName(e.target.value)}
        className="w-full py-2 text-[16px] bg-transparent font-medium outline-none"
      />
    </div>

    {/* Phone input with country code selector */}
    <div className="flex items-center rounded-md px-3 mb-3 bg-[#F6F6F6]">
      <select
        className="text-sm text-[#555555] font-medium bg-transparent"
        defaultValue="+91"
      >
        <option value="+91">+91</option>
        <option value="+1">+1</option>
        <option value="+44">+44</option>
        <option value="+61">+61</option>
        <option value="+81">+81</option>
        <option value="+971">+971</option>
        <option value="+49">+49</option>
      </select>

      <input
        type="text"
        placeholder="Phone Number"
        value={phone}
        onChange={(e) => setPhone(e.target.value)}
        className="w-full py-2 text-[16px] bg-transparent font-medium outline-none"
      />
    </div>

    {/* Error message */}
    {error && <p className="text-red-500 text-sm mb-2">{error}</p>}

    {/* Apply button */}
    <button
      onClick={handleApply}
      className="w-full bg-orange-500 text-white font-semibold py-2 rounded-md hover:bg-orange-600 transition mt-2"
    >
      Apply
    </button>

    {/* Terms and conditions */}
    <p className="text-[16px] font-medium text-center text-black mt-4">
      By clicking ‘Apply Now For Free’, you agree to our{" "}
      <span className="text-orange-500 cursor-pointer hover:text-orange-700">
        Terms & Conditions
      </span>
    </p>
  </div>
</div>


White form container with shadow and rounded corners.

Heading with an icon image and "Start learning for FREE" message.

Subtitle about lectures and assignments.

Form fields:

Name input with user icon.

Phone input with country code dropdown.

Error message displayed conditionally.

Submit button that triggers handleApply.

Terms and conditions note below the button.
***************************************************************
#  src/Pages/PAP/Pap_Page.jsx
import React from 'react'
import CourseCard from './CourseCard';
import PlacementSection from './PlacementSection';
import Footer from '../../components/Footer/Footer'
import CertificateSection from './CertificateSection ';
import FAQ_Pap from './FAQ_Pap';
import PlacementSupport from './PlacementSupport';
// import Navbar_C from '../../components/DataAnalysis/Navbar_C';
import HeroSection from './HeroSection';
Imports React.

Imports multiple components from the current directory and other parts of the project.

One import is commented out: Navbar_C (likely a navigation bar component).

These components represent different parts of the PAP page:

HeroSection: The top hero/banner section.

CourseCard: Details about the course offerings.

PlacementSection: Information about placements.

CertificateSection: Details about certificates.

PlacementSupport: Additional support info for placements.

FAQ_Pap: Frequently Asked Questions specific to the PAP program.

Footer: The site footer.

jsx
Copy code
const Pap_Page = () => {
  return (
    <div>
        {/* <Navbar_C/> */}
        <HeroSection/>
        <CourseCard/>
        <PlacementSection/>
        <CertificateSection/>
        <PlacementSupport/>
        <FAQ_Pap/>
        <Footer/>
    </div>
  )
}

export default Pap_Page;
Defines a functional component named Pap_Page.

Returns a <div> wrapping the entire page structure.

Inside the wrapper div, it renders the imported components in order, which creates the full page:

HeroSection: likely the first thing users see.

CourseCard: displays course info or offers.

PlacementSection: highlights placement statistics or guarantees.

CertificateSection: shows certification details.

PlacementSupport: extra info or help related to placements.

FAQ_Pap: FAQs for this program.

Footer: bottom of the page.

The commented <Navbar_C/> suggests there might be a navbar for navigation that’s currently disabled or under development.


******************************************************************
#  src/Pages/PAP/PlacementSection.jsx
Imports
import React from "react";
import { motion } from 'framer-motion'; // For animations
import '../../index.css'; 
// Importing company logos as images
import Accenture from "../../assets/Home/Prestige/accenture.webp";
import Cognizant from "../../assets/Home/Prestige/Cognizant.webp";
import Greyt from "../../assets/Home/Prestige/Greiyt.webp";
import TCS from "../../assets/Home/Prestige/Tcs.webp";
import EY from "../../assets/Home/Prestige/Ey.webp";
import Mentorsity from "../../assets/Home/Prestige/Mentosity.webp";
import languify from "../../assets/Home/Prestige/Languify.webp";
import learnyst from "../../assets/Home/Prestige/Learnyst.webp";
import Head from "../../assets/Home/OurProgram/head.webp"; // decorative image


motion is used for creating animations.

Multiple images of company logos are imported, representing placement partners.

A "Head" image is imported, used decoratively in the header.

Component and Network Array
const PlacementSection = () => {
  const network = [
    Accenture, Cognizant, TCS, Greyt, EY, Mentorsity, languify, learnyst
  ];


Defines a constant array network with the imported company logos. These will be rendered in the carousel.

JSX Return Structure
return (
  <div className="bg-white py-10 px-4 flex justify-center font-['Poppins']">


Outer wrapper with padding, white background, centered content, and Poppins font.

Main Colored Container
<div className="bg-[#FF7A24] text-white rounded-xl w-full max-w-6xl shadow-lg text-center relative py-10">


Orange background container, rounded corners, max width set to 6xl (~96rem), with shadow and padding.

Text color set to white and content centered.

Header Row with Decorative Images and Text
<div className="flex justify-between items-center md:px-16">
  <img src={Head} alt="left head" className="h-8 w-8 md:h-20 md:w-20" />
  
  <div className="flex-1 text-center px-2">
    <h2 className="text-xl md:text-2xl font-bold mb-1">
      Placements at Baoiam
    </h2>
    <p className="text-sm md:text-base leading-snug max-w-xl mx-auto">
      Our programs are designed in collaboration with recruiters to ensure you're 100% job-ready.
    </p>
  </div>

  <img src={Head} alt="right head" className="h-8 w-8 md:h-20 md:w-20" />
</div>


Uses Flexbox to layout the header row.

Two small decorative head images on the left and right (responsive sizes).

Centered title and description about Baoiam placements.

Text size adjusts responsively for medium screens (md).

Company Logos Scrolling Section
<div className="w-full overflow-hidden bg-gray-100 mt-6">
  <div className="container mx-auto">
    <div className="flex">
      {/* Motion 1 */}
      <motion.div
        initial={{ x: 0 }}
        animate={{ x: "-100%" }}
        transition={{
          duration: 15,
          ease: "linear",
          repeat: Infinity,
        }}
        className="flex flex-shrink-0 items-center"
      >
        {network.map((image, index) => (
          <div
            key={index}
            className="px-4 sm:px-6 md:px-8 py-2 sm:py-3 md:py-4"
          >
            <img
              className="h-8 sm:h-10 md:h-12 w-auto object-contain"
              src={image}
              alt={`Company logo ${index}`}
            />
          </div>
        ))}
      </motion.div>

      {/* Motion 2 (duplicate) */}
      <motion.div
        initial={{ x: 0 }}
        animate={{ x: "-100%" }}
        transition={{
          duration: 15,
          ease: "linear",
          repeat: Infinity,
        }}
        className="flex flex-shrink-0 items-center"
      >
        {network.map((image, index) => (
          <div
            key={index}
            className="px-4 sm:px-6 md:px-8 py-2 sm:py-3 md:py-4"
          >
            <img
              className="h-8 sm:h-10 md:h-12 w-auto object-contain"
              src={image}
              alt={`Company logo ${index}-copy`}
            />
          </div>
        ))}
      </motion.div>
    </div>
  </div>
</div>


Container with gray background and overflow hidden, to create a "window" for the scrolling effect.

Uses Flexbox to align content horizontally.

Two identical motion.divs are created, each rendering the full set of company logos side by side.

Each motion.div animates from x: 0 to x: "-100%" (moves left 100% of its width).

The animation repeats infinitely with a linear easing for smooth continuous scrolling.

The duplicate motion div ensures the logos repeat seamlessly — when the first finishes moving off-screen, the second continues, creating an infinite loop.

******************************************************
# src/Pages/PAP/PlacementSupport.jsx
Imports
import React from "react";
import { FaBriefcase, FaUserTie, FaFileAlt, FaBrain } from "react-icons/fa";


You import React to create the component.

You import four icons from the react-icons/fa (FontAwesome icons) package to visually represent different features:

FaBriefcase — represents job/companies

FaUserTie — represents expert/mentor sessions

FaFileAlt — represents resume & portfolio building

FaBrain — represents soft skills and interview training

JSX Structure
<div className="bg-white py-10 px-4 flex justify-center font-['Poppins']">


Main container with:

white background

vertical and horizontal padding

Flexbox centered content horizontally

Poppins font family applied

<div className="max-w-5xl w-full flex flex-col items-center text-center">


Inner container limiting max width (max-w-5xl) and full width (w-full)

Arranged vertically (flex-col)

Content centered horizontally (items-center) and text centered (text-center)

Heading
<h2 className="text-2xl md:text-[48px] font-semibold text-black leading-snug mb-10">
  Our Dedicated Placement Team <br className="hidden md:block" />
  is committed to get you a{" "}
  <span className="text-orange-500">Job</span>
</h2>


A headline with responsive font size (2xl on small, 48px on medium screens)

Semi-bold font weight, black color, tight line height

Margin bottom spacing (mb-10)

The line break (<br>) is only visible on medium screens and above (hidden on smaller devices)

The word Job is highlighted in orange (text-orange-500)

Features Grid
<div className="grid grid-cols-1 sm:grid-cols-2 gap-8 text-left">


A grid container that shows:

1 column on small screens and below (grid-cols-1)

2 columns on medium screens and above (sm:grid-cols-2)

Gap between grid items set to 8 (usually 2rem depending on Tailwind config)

Text aligned left inside grid cells

Individual Features

Each feature is a flex container with an icon on the left and a description on the right.

Example for the first feature:

<div className="flex items-center gap-4">
  <div className="bg-orange-100 p-3 rounded-lg">
    <FaBriefcase className="text-orange-500 text-2xl" />
  </div>
  <p className="text-black text-[24px] ">
    Exclusive access to our <br /> partner companies
  </p>
</div>


flex aligns icon and text horizontally

items-center vertically centers them

gap-4 creates spacing between icon and text

The icon is inside a rounded, light orange background with padding

Icon itself is orange and sized to 2xl

Text is black with font size 24px

Line break is used inside the description where needed

Features Explained

Exclusive access to partner companies
Shows the icon FaBriefcase and describes that learners get access to job opportunities through partner companies.

1v1 experts sessions
Shows the icon FaUserTie and highlights personalized mentoring or expert guidance.

Resume, Linkedin, Portfolio building
Uses FaFileAlt and indicates support with professional profile and portfolio creation.

Soft Skills, HR Interview & Aptitude Training
Uses FaBrain and tells about training in communication, interview preparation, and aptitude.
***********************************************************************
# src/Pages/Refer&Earn/FAQ_R.jsx


📦 Imports
import { useState } from "react";
import { FaPlus, FaTimes, FaArrowRight } from "react-icons/fa";


useState is a React hook used to manage the open/close state of each FAQ item.

FaPlus, FaTimes, FaArrowRight are icons from react-icons/fa used for UI indicators:

FaPlus: Show when an item is collapsed

FaTimes: Show when an item is expanded

FaArrowRight: (Commented out) used in a potential CTA card

🧠 State Logic
const [openIndex, setOpenIndex] = useState(null);


openIndex keeps track of which FAQ item is currently open.

If openIndex === index, that item is expanded. Otherwise, it's collapsed.

🔁 Toggle Logic
const toggleIndex = (index) => {
  setOpenIndex(openIndex === index ? null : index);
};


Clicking an FAQ:

If it's already open → close it

If it's closed → open it and close any others

📋 FAQ Data
const faqData = [
  { question: "...", answer: "..." },
  ...
];


An array of objects, each with a question and answer.

Optional code (commented out) includes more FAQs that could be shown later.

✂️ Split FAQ for Layout
const leftFaqs = faqData.slice(0, 3);
const rightFaqs = faqData.slice(3);


The FAQ list is divided into two columns:

First 3 FAQs go in the left column

Remaining FAQs go in the right column

📦 renderFAQItem() Function

This function returns a single accordion-style FAQ item.

const renderFAQItem = (item, index) => (
  <div
    key={index}
    className={`rounded-lg text-[18px] font-med ...`}
    style={{ minHeight: openIndex === index ? "auto" : "80px" }}
  >

🧩 Key Features:

Adds rounded corners, padding, and shadow when expanded

Changes minHeight based on open/closed state

Icon toggles between plus and close

Toggle Button
<button onClick={() => toggleIndex(index)} ... >
  <span>{item.question}</span>
  {openIndex === index ? <FaTimes /> : <FaPlus />}
</button>

Expanded Answer Section
{openIndex === index && (
  <div className="...">
    <p>{item.answer}</p>
    {item.button && (
      <a href={item.button.link}>...</a>
    )}
  </div>
)}


Only shows answer if the item is open

Supports an optional item.button for adding a CTA link (not currently used)

🖼️ Component Render (JSX)
return (
  <div className="w-full lg:mb-16 p-8 font-['Poppins']">

✅ Header Section
<h2 className="text-[24px] md:text-4xl font-bold text-gray-900 text-center">
  Still have of being <span className="text-orange-500">a Doubts?</span>
</h2>




🧱 FAQ Grid
<div className="flex flex-col md:flex-row gap-8">
  <div className="md:w-1/2">
    {leftFaqs.map(...)}
  </div>
  <div className="md:w-1/2">
    {rightFaqs.map(...)}
  </div>
</div>


On mobile: FAQs are stacked vertically

On desktop: FAQs show in 2 columns

📎 CTA Button
<div className="flex justify-center mt-5">
  <button className="...">See All FAQ’s</button>
</div>


A generic call-to-action to view more FAQs (currently doesn't do anything, could be wired up later)
***************************************************************
#  src/Pages/Refer&Earn/HeroSection_R.jsx
🧩 Imports
import React from "react";
import ReferImage from "../../assets/Refer&Earn/Coins.png";
import ReferAvatars from "../../assets/Refer&Earn/avatar.png";


ReferImage: Image showing coins or money (visual cue for earning).

ReferAvatars: Small avatars or icons representing users who’ve referred.

📦 Component Layout
<section className="...">


This is the main container with padding, responsive layout, and the Poppins font.

flex flex-col md:flex-row items-center justify-between


On mobile: layout is stacked vertically.

On desktop (md) and above: layout is horizontal (side-by-side).

🔵 Left Side – Text Content
<div className="w-full md:w-1/2 ...">

🟠 Heading
<h2 className="...">
  Refer To Your <br />
  <span className="text-orange-500">Friends</span> and <span className="text-orange-500">Earn</span>
</h2>


Large, responsive heading

"Friends" and "Earn" are highlighted in orange to grab attention

📝 Paragraph
<p className="...">
  Turn your friends and network into value...
</p>


A simple explanation encouraging users to refer others

Text is responsive and justified for clean appearance

👥 Avatar + CTA Button
<div className="flex flex-row md:flex-col ...">

👤 Avatar Group + Text
<img src={ReferAvatars} ... />
<div className="text-sm">
  <strong>8,000+</strong>
  <h6>Referrer's</h6>
</div>


Shows how many users are already referring (social proof)

🔘 Button
<button className="bg-orange-500 hover:bg-orange-600 ...">
  Refer now
</button>


CTA (Call-To-Action) button

Encourages user to take action

Styled for hover effect and responsiveness

🟣 Right Side – Image
<div className="w-full md:w-1/2 ...">
  <img src={ReferImage} ... />
</div>


Displays the hero image (e.g., coins, rewards)

Responsive sizing depending on screen width

📱 Responsive Behavior

On mobile:

Text is centered

Image appears below the text

On desktop:

Text is left-aligned

Image appears on the right

Avatar & Button are stacked vertically

********************************************************
# src/Pages/Refer&Earn/ReferBenefits.jsx
.

📦 Component Structure
✔️ 1. State Setup
const [formData, setFormData] = useState({ ... });
const [message, setMessage] = useState("");


formData: Holds all the input values (name, email, contact_number, referral_code)

message: Displays feedback (success/failure)

✔️ 2. Navigation
const navigate = useNavigate();


From react-router-dom

Used to redirect user to /referral page after successful submission.

✔️ 3. Input Handler
const handleChange = (e) => {
  setFormData({ ...formData, [e.target.name]: e.target.value });
};


Updates the state when a user types into any form field

✔️ 4. Form Submission Logic
const handleSubmit = async (e) => {
  ...
}


This function does the heavy lifting:

✅ a. Check Login Status
if (!isLoggedIn) {
  alert("Please login/signup first");
  return;
}


Prevents submission if user isn’t logged in (passed as prop)

✅ b. API 1: Submit Referral Form
const response = await fetch(API_ENDPOINTS.REFERRAL_SUBMIT_FORM, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(formData),
});


Submits form data to the backend

If successful, shows success message

✅ c. API 2: Apply Referral Code (Optional)
if (formData.referral_code) {
  const referralResponse = await fetch(API_ENDPOINTS.GENERATE_REFERRAL, {
    ...
    body: JSON.stringify({
      email: formData.email,
      referral_code: formData.referral_code,
    }),
  });
}


Applies referral benefits only if a code is entered

Shows appropriate success/error message

✅ d. Navigation
navigate("/referral");


Redirects to the referral dashboard or confirmation page

🖼️ JSX Structure (Rendered UI)
🟧 Section Wrapper
<section className="...">


Light gray background

Responsive padding

Center-aligned text

Poppins font

🟠 Heading & Subheading
<h2>Benefits of being <span className="text-orange-500">a Referrer</span></h2>
<p>Refer your friends... earn rewards</p>

🔶 Main Box: Two Columns (Flex layout)
<div className="flex flex-col lg:flex-row ...">

✅ Left Column – Referral Form
<div className="bg-orange-500 text-white ...">


Orange background

Rounded box with padding

Form fields:

Full Name

Email

Contact Number

Referral Code (optional)

Submit Button

Message:

{message && <p className="...">{message}</p>}


✅ Form has validation and state-linked fields.

✅ Right Column – Image + Benefit Tags
<div className="relative w-full lg:w-1/2 ...">
  <img src={MoneyImage} />


Image of money/coins

Below image, there are floating tags showing potential rewards:

<div className="absolute top-4 left-4 ...">
  assured discounts on our courses
</div>
<div className="absolute top-[50%] right-0 ...">
  chance to win an android phone
</div>
<div className="absolute bottom-4 left-4 ...">
  chance to win a brand new Laptop
</div>


These messages are positioned absolutely and styled to look like badges.

**********************************************************
#  src/Pages/Refer&Earn/ReferEarnPage.jsx
import React from 'react'
import HeroSection_R from './HeroSection_R'
import FAQ_R from './FAQ_R'
import Footer from '../../components/Footer/Footer'
import ReferSteps from './ReferSteps'
import ReferBenefits from './ReferBenefits'
Imports several subcomponents that together build the full Refer & Earn experience.

The isLoggedIn prop is passed to ReferBenefits to control form access.

🧩 Component Definition
jsx
Copy code
const ReferEarnPage = ({ isLoggedIn }) => {
This is a page-level React component that receives isLoggedIn as a prop.

isLoggedIn is used to determine if the referral form can be submitted or not.

🧱 JSX Return
jsx
Copy code
return (
  <div>
    <HeroSection_R/>
    <hr className="w-full  border-t-[3px] border-gray-200 mt-6" />
    <ReferSteps/>
    <ReferBenefits isLoggedIn={isLoggedIn} />
    <FAQ_R/>
    <Footer/>
  </div>
)
1. ✅ <HeroSection_R />
Displays the hero banner for the page.

Contains:

Title like "Refer Your Friends & Earn"

Description of the referral program

CTA (Call to Action) like “Refer Now”

Image and avatar count

2. ✅ <hr />
Adds a horizontal separator after the hero section for visual clarity.

3. ✅ <ReferSteps />
Likely a section that explains:

How to refer

What steps are involved

How to claim rewards

(Though not shown in your code, it's a typical feature in referral pages.)

4. ✅ <ReferBenefits isLoggedIn={isLoggedIn} />
This is the main form section for submitting referral information.

Displays a form with inputs like:

Full name

Email

Contact number

Referral code

Also displays:

Rewards (laptop, phone, discounts)

Uses isLoggedIn to block form submission for unauthenticated users.

5. ✅ <FAQ_R />
An accordion-style FAQ section.

Answers common questions like:

“How do I refer?”

“What do I get?”

“What if someone forgets to use my code?”

6. ✅ <Footer />
Standard website footer with:

Contact info

Social links

Legal links

Branding


****************************************************************
# src/Pages/Refer&Earn/ReferralPage.jsx
🧩 Imports & Dependencies
import React, { useState } from "react";
import Navbar_C from "../../components/DataAnalysis/Navbar_C";
import Footer from "../../components/Footer/Footer";
import FAQ_R from "./FAQ_R";
import { API_ENDPOINTS } from "../../Config/api";


useState: To manage state

Navbar_C: Top navigation bar

Footer: Bottom site footer

FAQ_R: FAQ section (accordion-style)

API_ENDPOINTS: Contains backend API URLs for reuse

💡 Component Setup
const [referralData, setReferralData] = useState(null);
const [loading, setLoading] = useState(false);


referralData: Stores data returned from the referral API (like code & message)

loading: Indicates loading state while the referral code is being generated

⚙️ Function: handleGenerateReferral
const handleGenerateReferral = async () => {
  ...
}

What it does:

Calls the backend to generate a referral code

Sends a POST request to API_ENDPOINTS.GENERATE_REFERRAL

Includes Authorization header using token from localStorage

Stores the response in referralData or shows an error

📋 Function: handleCopy
navigator.clipboard.writeText(referralData.referral_code);


Copies the referral code to the user's clipboard

Shows an alert to confirm it was copied

📲 Function: handleWhatsAppShare
const message = referralData.message;
const whatsappUrl = `https://wa.me/?text=${encodeURIComponent(message)}`;
window.open(whatsappUrl, "_blank");


Composes a WhatsApp message using the referral message from API

Opens WhatsApp web/mobile in a new tab to allow sharing

🧱 JSX Return Explained
✅ Navbar_C
<Navbar_C />


Top navigation bar (imported from Data Analysis component set)

✅ "Go Back" Button
<button onClick={() => window.history.back()} ...>
  ← Go back
</button>


Navigates the user back to the previous page

✅ Main Content Section (2-column layout)
<div className="w-full max-w-7xl ... grid grid-cols-1 md:grid-cols-2 gap-16">

🧭 Left Side
<h2 className="text-3xl font-bold mb-4">
  Refer in Just <span className="text-orange-500">3 Steps</span>
</h2>


Tells the user how simple the referral process is

Provides a description of the 3-step process

🧮 Right Side – Referral Code Box

If referral code hasn't been generated:

<button onClick={handleGenerateReferral}>
  Generate Referral Code
</button>


Calls the handleGenerateReferral function

If referral code has been generated:

<input value={referralData.referral_code} readOnly />
<button onClick={handleCopy}>Copy</button>
<button onClick={handleWhatsAppShare}>Share via WhatsApp</button>


Shows the referral code in a read-only field

Allows copying or sharing

✅ FAQ Section
<FAQ_R />


Expands/collapses commonly asked questions and answers about referrals

✅ Footer
<Footer />


Website’s footer with links, copyright, etc.

🔐 Security Note
Authorization: `Bearer ${localStorage.getItem("access")}`


Uses the JWT token stored in localStorage to authenticate API requests

Make sure:

Tokens are securely managed

Token expiry is handled

🟠 Example API Flow

When user clicks "Generate Referral Code":

POST request to /generate-referral endpoint

API returns:

{
  "referral_code": "XYZ123",
  "message": "Join this course and use XYZ123 for a discount!"
}


UI updates with referral code, copy and WhatsApp share options
***************************************************************
#  src/Pages/Refer&Earn/ReferSteps.jsx
High-Level Structure
<section> {/* Wrapper */}
  <Heading />
  <Intro Text />
  <Steps with Icons + SVG Lines />
</section>

🧩 Breakdown of the Code
1. Import Icons
import { FaCheck, FaShareAlt, FaHeart } from "react-icons/fa";


These icons visually represent each step:

✅ Sign Up

🔄 Share

❤️ Receive

2. Steps Data Array
const steps = [
  { icon: <FaCheck />, title: "Sign up", desc: "..." },
  { icon: <FaShareAlt />, title: "Share", desc: "..." },
  { icon: <FaHeart />, title: "Receive", desc: "..." },
];


This is a clean way to define UI content – it’s data-driven, so if you want to add/edit/remove steps, you do it here without touching layout logic.

3. Component UI: Wrapper Section
<section className="...">


Applies responsive padding and font

Centers content

4. Heading & Description
<h2>Steps</h2>
<p>Follow these steps to refer...</p>


Main heading

Subtext that explains purpose

5. Steps Rendering with Map
{steps.map((step, idx) => (
  <div key={idx}>...</div>
))}


Iterates over the steps array

For each step, it renders:

A rounded card with:

Icon

Title

Description

<div className="bg-white shadow-md rounded-full w-[160px] h-[160px] md:w-[220px] md:h-[220px] flex flex-col items-center justify-center">
  {step.icon}
  <h3>{step.title}</h3>
  <p>{step.desc}</p>
</div>


The card:

Is a perfect circle

Uses responsive sizing

Contains centered content

6. SVG Wave Lines Between Steps
{idx < steps.length - 1 && (
  <svg>
    <path d="M0 20 C 40 0, 120 40, 160 20" ... />
  </svg>
)}


Rendered only for the 1st and 2nd steps

Draws a dashed orange curve between the steps

Hidden on smaller screens (hidden md:block)

Purpose: Adds a visual "flow" to show progression from Step 1 → 2 → 3.
***************************************************************************
#  src/Pages/BookmarkButton.jsx
1. Imports
import React, { useState } from "react";
import { BsBookmark } from "react-icons/bs";


useState is used to manage the toggle state (bookmarked or not).

BsBookmark is the Bootstrap bookmark icon from react-icons.

2. State Setup
const [active, setActive] = useState(false);


active → true if bookmarked, false if not.

Default: false (not bookmarked).

3. Click Handler
const handleClick = () => {
  setActive(!active); // Toggle the active state
};


When the user clicks the button, the state is flipped:

If it was false, it becomes true (bookmarked).

If it was true, it becomes false (unbookmarked).

4. Button UI
<button onClick={handleClick}>
  <BsBookmark
    className={`w-[20px] h-[20px] transition-colors duration-300 ${
      active ? "text-orange-500" : "text-black"
    }`}
  />
</button>


BsBookmark is the icon being shown.

className uses Tailwind CSS:

w-[20px] h-[20px]: sets size

transition-colors duration-300: smooth color change on toggle

text-orange-500 if active ✅

text-black if inactive ❌
***************************************************************************
#  src/Pages/ContactForm.jsx
1. Imports & State Setup
import React, { useState } from "react";
import { API_ENDPOINTS } from "../Config/api";


useState: For managing form fields and UI state.

API_ENDPOINTS: Contains the backend API URLs (from a central config file).

State Variables
const [fullName, setFullName] = useState("");
const [email, setEmail] = useState("");
const [mobileNumber, setMobileNumber] = useState("");
const [category1, setCategory1] = useState("");
const [category2, setCategory2] = useState("");
const [agreedToTerms, setAgreedToTerms] = useState(false);


These manage:

Basic user info (name, email, phone)

Selected program/category (category1)

Selected sub-topic/track (category2)

Consent agreement checkbox

✉️ 2. Form Submission Logic
onSubmit Handler
const handleSubmit = async (e) => {
  e.preventDefault();
  const formData = {
    full_name: fullName,
    email,
    mobile_number: mobileNumber,
    category: category1,
    sub_category: category2,
    agreed_to_terms: agreedToTerms,
  };


This gathers all input fields into formData.

API Call
const response = await fetch(API_ENDPOINTS.CONTACT_SUBMIT, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(formData),
});


POSTs the data to the API.

Handles success or error using response.ok.

On Success
if (response.ok) {
  alert("Form submitted successfully!");
  // Reset fields
} else {
  console.error("Validation errors:", data.errors);
}

📚 3. Dynamic Dropdown: Category & Subcategory
subCategories Object
const subCategories = {
  "Success Fusion Program": [...],
  "Udaan 90": [...],
  ...
};


Maps main categories (category1) to an array of sub-categories (category2).

Used to populate the second dropdown dynamically based on the first.

🧾 4. JSX Markup: Form UI

The form is wrapped in a styled box with a close (X) button if onClose is provided.

Basic Inputs:
<input type="text" value={fullName} onChange={...} />
<input type="email" value={email} onChange={...} />
<input type="tel" value={mobileNumber} onChange={...} />

Category Dropdown
<select value={category1} onChange={(e) => {
  setCategory1(e.target.value);
  setCategory2(""); // Reset subcategory
}}>

Sub-Category Dropdown (Dynamic)
<select disabled={!subCategories[category1]}>
  {subCategories[category1]?.map((sub) => (
    <option value={sub}>{sub}</option>
  ))}
</select>

Terms Checkbox
<input type="checkbox" checked={agreedToTerms} onChange={...} />

✅ 5. Final Submit Button
<button type="submit">Submit</button>


Tailwind styles are used for design, with hover, focus, and transition effects.

🔐 6. Close Button
{onClose && (
  <button onClick={onClose}>X</button>
)}


Optional onClose prop: lets you show/hide the form in a modal or pop-up.

SVG icon renders a classic "X".

*****************************************************************
#  src/Pages/ContactUs.jsx
📌 1. Imports
import React, { useState } from "react";
import mapImage from "../assets/ContactUS/map.png";
import { MdEmail, MdPhone, MdLocationOn } from "react-icons/md";
import Footer from '../components/Footer/Footer';


useState is used for form input state.

mapImage is a map image showing the physical address.

Icons from react-icons/md are used for UI.

Footer is a reusable component rendered at the bottom.

🧠 2. State Variables
const [fullName, setFullName] = useState("");
const [email, setEmail] = useState("");
const [mobileNumber, setMobileNumber] = useState("");
const [category1, setCategory1] = useState("");
const [category2, setCategory2] = useState("");
const [agreedToTerms, setAgreedToTerms] = useState(false);


These track the input values of the form:

category1 → Education Level

category2 → Stream (sub-category)

agreedToTerms → Checkbox for marketing consent

📤 3. Form Submission
const handleSubmit = (e) => {
  e.preventDefault();
  console.log({
    fullName,
    email,
    mobileNumber,
    category1,
    category2,
    agreedToTerms,
  });
  alert("Form submitted! Check console for data.");
};


Prevents default form reload.

Logs form data in the browser console.

Displays an alert to simulate submission success.

✅ You can replace this logic later with an actual fetch or axios POST request to send the data to a server or backend API.

🧩 4. Sub-Category (Stream) Options
const subCategories = {
  "Xth standard": ["Maths", "Computer science"],
  "XIIth standard": ["Science", "Commerce", "Arts", "Others"],
  "Under-Graduate": ["Bachelor's of Technology", ...],
  "Post-Graduate": ["Masters in Business Administration", ...],
};


This object maps each education level (category1) to a list of relevant streams (category2).

🧱 5. Component Layout
div with two columns:
<div className="flex flex-col sm:flex-row ...">


Uses responsive flexbox:

On small screens: columns stack vertically

On medium and above: side-by-side layout

📞 Left Column – Contact Information
<div className="w-full md:w-1/2 space-y-4">
  <h1>Get In Touch With Us</h1>
  <p>Have any query, feedback, or need assistance?</p>

Contact Info Card:
<div className="bg-white shadow-md ...">
  <MdEmail /> support@baoiam.com
  <MdPhone /> +91 08062181972
  <MdLocationOn /> B Block Noida Sector 15 ...
  <img src={mapImage} />
</div>

✍️ Right Column – Contact Form
<div className="w-full md:w-1/2 flex">
  <form onSubmit={handleSubmit}>
    <input ... /> // Full name
    <input ... /> // Email
    <input ... /> // Mobile number
    <select ... /> // Education level
    <select ... /> // Stream (based on level)
    <input type="checkbox" /> // Agreement
    <button>Submit</button>
  </form>
</div>

🔄 6. Dynamic Dropdown Logic

When the user selects a category (education level):

onChange={(e) => {
  setCategory1(e.target.value);
  setCategory2(""); // reset subcategory
}}


The second dropdown is:

disabled={!subCategories[category1]}


It only activates when a valid category is chosen and shows options dynamically from subCategories.

✅ 7. Terms & Conditions Checkbox
<input
  type="checkbox"
  checked={agreedToTerms}
  onChange={(e) => setAgreedToTerms(e.target.checked)}
/>


Must be checked to allow submission.

You can later enforce this as a required condition if needed.

🔚 8. Footer Component
<Footer />


This is rendered after the contact section, likely with links and branding. It's imported from your project.
************************************************************************************************

# src/Pages/PrivacyPolicy.jsx
✅ 1. Imports
import React from 'react';
import { IoClose } from "react-icons/io5";


React: Required to create a component.

IoClose (Unused): Imported from react-icons/io5 but not used in this file.

🛠️ You can remove IoClose unless you plan to use it for a close button/modal functionality.

🧩 2. Component Declaration
const PrivacyPolicy = ({ onClose }) => {


Accepts an optional onClose prop (e.g., for closing a modal or popup).

But onClose is not currently used. You can either implement a close button or remove this prop.

🧱 3. Layout and Wrapper
<div className="bg-gray-100 py-10 px-4 relative">
  <div className="w-full max-w-[1200px] mx-auto bg-white border border-gray-200 shadow-md rounded-md p-6 relative">


Sets a light gray background for the whole section.

Inner content is centered (mx-auto), padded (p-6), and styled as a card with border, rounded corners, and shadow.

🧾 4. Heading
<h2 className="text-2xl md:text-3xl font-bold text-center mb-10">
  Privacy Policy – Baoiam Innovations Pvt. Ltd.
</h2>


Displays the page title with responsive font size.

text-center keeps it horizontally centered.

mb-10 adds bottom margin to separate it from the content.

📜 5. Main Content (Scrollable Section)
<div className="space-y-6 text-base no-scrollbar pr-4 mx-auto max-w-[1000px] mt-10">


space-y-6: Vertical spacing between sections.

no-scrollbar: Class is likely defined in your Tailwind config to hide scrollbars (not built-in by default).

pr-4: Padding on the right to avoid clipping content.

max-w-[1000px]: Limits line length for better readability.

mt-10: Adds top margin to separate from heading.

📚 6. Individual Sections

Each section represents a part of the privacy policy.

✏️ Introduction
<h3 className="font-bold text-xl">Introduction</h3>
<p>Baoiam respects your privacy...</p>
<ul>
  <li>Visit baoiam.com</li>
  ...
</ul>


Explains the scope of the policy and when it's applicable.

📦 What We Collect

Describes:

Non-personal data like IP, device info

Personal data like name, email, course preferences

Optional fields are optional

📈 How We Use It

List of purposes:

Registration

Support

Analytics

Marketing communication (if opted-in)

🍪 Cookies & Tracking

Mentions:

Use of cookies for personalization and tracking

Note about limited functionality if cookies are disabled

🔄 Data Sharing

Mentions 3rd party tools:

Payment processors (Stripe, Razorpay)

Email & analytics (Mailchimp, GA)

Support/CRM tools

Clearly states: "Data is not sold."

🛡️ Security Measures

Use of SSL, secured databases, etc.

Encourages users to use strong passwords

👤 Your Rights

View, edit, delete data

Opt out of emails/SMS

Contact via:

<a href="mailto:privacy@baoiam.in">privacy@baoiam.in</a>

⚖️ Legal Compliance

Data might be disclosed to comply with laws

Users will be informed of any data transfer during acquisition/merger

🔄 Policy Updates

Policy may change over time

Users will be notified via email or app alerts

📞 Contact Us

Includes:

Email: support@baoiam.com

Address: Noida, India
**************************************************************************
# src/Pages/RefundPolicy.jsx
1. Component Setup
import React from 'react';

const RefundPolicy = () => { ... }


A functional React component named RefundPolicy.

No props are taken.

Exports the component as default for use elsewhere.

2. Outer Wrapper
<div className="bg-gray-100 py-10 px-4 relative">
  <div className="w-full max-w-[1200px] mx-auto bg-white border border-gray-200 shadow-md rounded-md p-6 relative">
    ...
  </div>
</div>


Outer div sets a light gray background with padding (py-10 px-4).

Inner div creates a centered white card container:

Max width 1200px, horizontally centered (mx-auto).

White background, subtle border, shadow, rounded corners.

Padding inside (p-6).

3. Heading
<h2 className="text-3xl font-bold text-center mb-10 text-black">
  Baoiam Payments, Refunds, and Rescheduling Policy
</h2>
<hr />


Main title, large bold font, centered, black text.

Bottom margin (mb-10) separates heading from the content.

A horizontal line (<hr />) below the heading for separation.

4. Scrollable Content Container
<div className="space-y-6 text-base overflow-y-auto no-scrollbar pr-4 mx-auto max-w-[1000px] mt-10">
  ...
</div>


Holds all policy sections.

space-y-6: vertical spacing between child sections.

text-base: base font size.

overflow-y-auto: vertical scrollbar if content overflows vertically.

no-scrollbar: likely a custom class to hide scrollbars visually.

pr-4: right padding to avoid content clipping.

mx-auto max-w-[1000px]: centers and restricts max width for better readability.

mt-10: margin top separating from heading.

5. Policy Sections

The content is divided into multiple <section> blocks, each focused on a specific topic. Let’s break them down:

Introduction
<p className="text-[16px]">
  Baoiam is committed to delivering accessible, affordable, and high-quality online education...
</p>


Explains general commitment and that enrollment implies agreement to these terms.

Course Categories
<ul className="list-disc list-inside text-[16px] pl-2 mt-1">
  <li><strong>Kickstarter Bootcamps</strong> - Short-term programs (1 to 3 months)...</li>
  <li><strong>Professional Certification Programs (Pro Courses)</strong> - Long-term programs (6 to 12 months)...</li>
</ul>


Describes two categories:

Kickstarter Bootcamps: Short courses (1-3 months).

Pro Courses: Long courses (6-12 months).

Payment Terms
<ul className="list-disc list-inside text-[16px] pl-2 mt-1">
  <li>All course fees must be paid in full before access unless EMI/installment is selected.</li>
  <li>Payments processed via authorized gateways.</li>
  <li>Token payments must be completed within 7 days or forfeited.</li>
  <li>GST applies.</li>
  <li>Discounts only if directly from Baoiam.</li>
</ul>


Explains payment requirements, gateway, token rules, taxes, and offer validity.

Refund Policy

Two subsections:

Kickstarter Bootcamps (fees ≤ ₹999):

No refunds.

Token amounts non-refundable.

Rescheduling allowed only before course start or within 3 days of payment.

Pro Courses (6–12 months):

Refund requests must be within 2 calendar days of payment.

No refunds after 2 days regardless of attendance.

Refunds processed in 30–45 working days to original payment method.

Course access revoked after refund.

No refunds for dissatisfaction or non-usage.

Rescheduling & Transfer

Rescheduling allowed before start or if <10% completed.

Course pause allowed up to 1 month for special cases.

Seat transfers allowed to friend/family.

Baoiam not responsible for personal transfer disputes.

Delivery Issues (Pro Courses Only)

Refunds or claims considered only if:

No onboarding or access despite support communication.

Recordings unavailable for 7+ days after escalation.

Persistent platform issues.

Learner non-response does not count as delivery failure.

Dispute Redressal

Refund/reschedule issues: email support@baoiam.com.

If unresolved, escalate to grievance@baoiam.com.

Committee decisions are final.

Additional Clauses

No refunds if fraud/misrepresentation.

EMI timelines continue during pauses.

Unauthorized vendor offers invalid.

Partial payments forfeited if balance unpaid within 7 days.

Support Contact

Support email provided: support@baoiam.com.

Note: Refund and reschedule decisions are case-by-case by Baoiam's committee.

Policy Updates

Baoiam can modify this policy at any time without prior notice.

Users should review periodically.
**********************************************************************
# src/Pages/TermsAndConditions.jsx
1. Imports
import React from "react";
import { IoClose } from "react-icons/io5";


Imports React to create the component.

Imports the IoClose icon from react-icons/io5 (though currently not used in the component).

2. Component Declaration
const TermsAndConditions = ({ onClose }) => { ... }


Functional component named TermsAndConditions.

Accepts an optional onClose prop, presumably to handle closing a modal or popup, but this prop is currently unused.

3. Outer Layout & Styling
<div className="bg-gray-100 py-10 px-4 relative">
  <div className="w-full max-w-[1200px] mx-auto bg-white border border-gray-200 shadow-md rounded-md p-6 relative">
    ...
  </div>
</div>


Outer div sets a light gray background with vertical and horizontal padding (py-10 px-4).

Inner div:

Creates a centered white card container with max width 1200px.

Has a subtle border, drop shadow, rounded corners, and padding (p-6).

The relative class allows for positioning children absolutely if needed.

4. Heading
<h2 className="text-3xl font-bold text-center mb-10 text-black">
  Terms and Conditions – Baoiam Innovations Pvt. Ltd.
</h2>
<hr></hr>


Main title, large and bold, centered.

Bottom margin separates it from content.

A horizontal line <hr> visually separates the header from the body.

5. Scrollable Content Container
<div className="space-y-6 text-base overflow-y-auto no-scrollbar pr-4 mx-auto max-w-[1000px] mt-10">
  {/* Terms sections */}
</div>


Contains all the terms and conditions sections.

space-y-6 adds vertical spacing between child sections.

text-base sets base font size.

overflow-y-auto allows vertical scrolling if content exceeds container height.

no-scrollbar is a likely custom class to hide visible scrollbars.

pr-4 adds right padding to prevent text from being clipped.

mx-auto max-w-[1000px] centers the content and restricts line width for readability.

mt-10 adds margin-top to separate from the heading.

6. Content Sections

Each <section> has a specific topic, with headings and paragraphs or lists to explain terms clearly.

Some notable sections:

Acceptance of Terms
Users agree to terms by accessing services or enrolling.

Eligibility
Users must be 18+ years old.

User Obligations
Includes confidentiality of login, no sharing course material, respecting others, and no misuse.

Enrollment & Fees
Covers payment plans, promotional eligibility, and possible course schedule changes.

Refund Policy
No refunds after 2 days of course start, refunds processed within 7-14 working days.

Intellectual Property
All content/materials are protected by copyright.

Code of Conduct
Users must abide by rules (note: repeated refund points here might be a copy-paste error).

Placement & Career Support
Placement assistance offered but not guaranteed; hiring decisions rest with employers.

Limitation of Liability
Baoiam not liable for indirect damages or technical failures.

Third-party Services
Use of Zoom, payment gateways, etc., subject to their own terms.

Termination
Baoiam may suspend/terminate accounts for breaches.

Changes to Terms
Terms can be updated anytime; continued use means acceptance.

Governing Law
Indian laws apply, courts in Noida have jurisdiction.

Contact Us
Email and address for support provided.

7. Unused Close Button Placeholder
{/* CLOSE BUTTON */}


You imported IoClose but did not implement a close button.

If this component is used in a modal, you might want to add a close icon button here that calls onClose.
**************************************************************
#   src/routes/ProtectedRoute.jsx
Code explanation:
import React from "react";
import { Navigate } from "react-router-dom";


Imports React for creating the component.

Imports Navigate from react-router-dom to programmatically redirect users.

const ProtectedRoute = ({ isLoggedIn, children }) => {


Functional component named ProtectedRoute.

Takes two props:

isLoggedIn: A boolean indicating if the user is authenticated.

children: The React elements/components that should be rendered if the user is allowed access.

if (!isLoggedIn) {
  alert("Please log in to access this page.");
  return <Navigate to="/" replace />;
}


Checks if the user is not logged in.

If not logged in:

Displays a browser alert with a message prompting the user to log in.

Redirects the user to the homepage ("/") using <Navigate>.

The replace prop ensures the navigation replaces the current entry in the browser history instead of adding a new one (so the user can’t go back to the protected page with the back button).

return children;


If the user is logged in, it renders the children components, i.e., the protected content.

How to use:

Wrap your protected route/component inside <ProtectedRoute> and pass the isLoggedIn flag.

Example:

<ProtectedRoute isLoggedIn={userIsLoggedIn}>
  <Dashboard />
</ProtectedRoute>


If userIsLoggedIn is true, <Dashboard /> renders.

If false, user gets alerted and redirected.

****************************************************
# src/App.css

@import "tailwindcss";
This line imports Tailwind CSS into your stylesheet.

It allows you to use Tailwind's utility classes and configurations in your project.

css
Copy code
/* body{overflow-x: hidden} */
This is a commented-out CSS rule.

If uncommented, it would prevent horizontal scrolling by hiding overflow on the x-axis (overflow-x: hidden) for the entire page (body element).

Useful if you want to avoid unwanted horizontal scrollbars caused by wide elements.

css
Copy code
.font-poltawski {
  font-family: 'Poltawski Nowy', serif;
}
This defines a custom CSS class called .font-poltawski.

Applying this class will set the font of an element to "Poltawski Nowy" with a fallback to any generic serif font.

'Poltawski Nowy' is a specific font (likely imported or available via web fonts).

You can apply this class in your HTML/JSX like: <div className="font-poltawski">Text</div> to use that font.


***************************************************************
#  src/App.jsx
Imports

BrowserRouter as Router, Routes, Route, useLocation from "react-router-dom": For client-side routing.

Several React components representing pages and parts of your app (Navbar, HomePage, PridePage, etc).

useEffect, useState for React state management and lifecycle hooks.

ProtectedRoute: A custom component to protect routes for logged-in users only.

ScrollToTop: Utility to scroll page to top on route change.

Component App
States

isSignupOpen: Boolean state to control whether the signup modal is open.

isLoggedIn: Boolean state to track if user is logged in.

useEffect to Show Signup Modal After 5 Minutes

Checks local storage for a flag "signupModalShown" to see if the modal was already shown.

If not, sets a timer of 5 minutes (5 * 60 * 1000 ms) to open the signup modal and mark it as shown in localStorage.

The timer is cleared on cleanup.

Authentication Handlers

handleAuthSuccess: Called when the user successfully signs up/logs in, sets isLoggedIn to true and closes signup modal.

handleLogout: Logs out user by setting isLoggedIn to false and reopens signup modal.

JSX Structure
<Router>
  <ScrollToTop />
  <div>
    <Routes>
      {/* Public routes */}
      <Route path="/blogs" element={<BlogSectionPage/>} />
      <Route path="/referral" element={<ReferralPage />} />

      {/* Protected routes (require login) */}
      <Route
        path="/DataAnalysis"
        element={
          <ProtectedRoute isLoggedIn={isLoggedIn}>
            <DataAnalysisPage />
          </ProtectedRoute>
        }
      />

      <Route
        path="/DigitalMarketing"
        element={
          <ProtectedRoute isLoggedIn={isLoggedIn}>
            <DM_Page />
          </ProtectedRoute>
        }
      />

      <Route
        path="/SoftwareDevelopment"
        element={
          <ProtectedRoute isLoggedIn={isLoggedIn}>
            <SD_Page />
          </ProtectedRoute>
        }
      />

      <Route
        path="/DataScience"
        element={
          <ProtectedRoute isLoggedIn={isLoggedIn}>
            <DataSciencePage />
          </ProtectedRoute>
        }
      />

      {/* Catch-all route for all other paths */}
      <Route
        path="*"
        element={
          <>
            {/* Navbar shown on all fallback pages */}
            <Navbar
              onSignUpClick={() => setIsSignupOpen(true)}
              isLoggedIn={isLoggedIn}
              onLogout={handleLogout}
            />
            {/* Signup modal */}
            <AuthModal
              isOpen={isSignupOpen}
              onClose={() => setIsSignupOpen(false)}
              onAuthSuccess={handleAuthSuccess}
            />

            {/* Nested routes inside fallback for various public pages */}
            <Routes>
              <Route path="/" element={<HomePage />} />
              <Route path="/pride" element={<PridePage />} />
              <Route path="/Udaan90" element={<Udaan90 />} />
              <Route path="/Successfusion" element={<SuccessFusion />} />
              <Route path="/AIML" element={<AIML />} />
              <Route path="/terms&conditions" element={<TermsAndConditions />} />
              <Route path="/Privacy&Policy" element={<PrivacyPolicy />} />
              <Route path="/refundPolicy" element={<RefundPolicy />} />
              <Route path="/contact_us" element={<ContactUs />} />
              <Route path="/GCEP" element={<GcepPage />} />
              <Route path="/aboutUs" element={<AboutUSPage />} />
              <Route path="/instructor" element={<Instructor />} />
              <Route path="/refer&earn" element={<ReferEarnPage isLoggedIn={isLoggedIn} />} />
              <Route path="/PAP" element={<Pap_Page />} />
            </Routes>
          </>
        }
      />
    </Routes>
  </div>
</Router>

Key Points

ProtectedRoute wraps components that should only be accessible if isLoggedIn is true. Otherwise, it redirects users or alerts them.

The app renders the <Navbar> and <AuthModal> components on any unmatched route (path="*"), so the modal and navbar are visible on all pages except protected routes.

Login state (isLoggedIn) is passed down to <Navbar> so it can show login/logout buttons accordingly.

The signup modal opens automatically after 5 minutes if the user hasn't seen it before (tracked with localStorage).

You use nested <Routes> inside the catch-all to define the rest of the public-facing pages.

*****************************************************************************
# src/index.css
@keyframes gradient: Creates an animation that moves the background gradient horizontally from left to right.

.animate-gradient: Applies the gradient animation infinitely with a 3-second linear timing.

@keyframes bounceUpToCenter: Animates an element bouncing up from below the screen to its center position with opacity fade-in.

.animate-bounceUpToCenter: Applies the bounce animation over 0.8 seconds easing out and keeps the final state.

body { overflow-x: hidden }: Prevents horizontal scrolling on the whole page to avoid unwanted side-scrollbars.

*******************************************************
# src/main.jsx
import { StrictMode } from 'react': Imports React's StrictMode component, which helps highlight potential problems in your app during development (like deprecated APIs, side effects, etc.).

import { createRoot } from 'react-dom/client': Imports the modern React 18+ method to create a root for rendering your React app.

import './index.css': Imports your global CSS styles.

import App from './App.jsx': Imports the main App component, which is the root component of your React application.

createRoot(document.getElementById('root')).render(...):

Finds the HTML element with id 'root' (usually a <div id="root"></div> in your index.html).

Creates a React root using createRoot for React 18 concurrent mode.

Renders the <App /> component inside <StrictMode> into that root.
**********************************************************************
# eslint.config.js
Imports:

@eslint/js: ESLint core rules.

globals: Predefined global variables (like window, document).

eslint-plugin-react-hooks: Rules for React hooks best practices.

eslint-plugin-react-refresh: Supports React Fast Refresh in development.

defineConfig, globalIgnores from ESLint config utilities.

Config:

Ignore all files inside dist folder globally.

Apply settings to all .js and .jsx files.

Extend recommended ESLint rules, React hooks rules, and React Refresh rules.

Set ECMAScript version to 2020 with support for JSX and ES modules.

Use browser globals like window.

Custom rule: throw error for unused variables except those starting with uppercase letters or underscore (^[A-Z_]).
*******************************************************
# index.html
Declares the document as HTML5 (<!doctype html>).

Sets the language to English (lang="en").

Specifies character encoding as UTF-8.

Loads two Google Fonts: Poppins and Poltawski Nowy.

Sets the viewport for responsive design.

Sets the page title to "Baoiam".

Includes a root <div> with id="root" where your React app will mount.

Loads the React app’s main JavaScript module (/src/main.jsx).
********************************************************************


 # Simple commands to setup React with Vite
 ## Requirements
- Node.js (latest version recommended) install pahle se install hona chahiye


.Open your terminal and run this command to create a React app with Vite:

.npm create vite@latest my-react-app -- --template react


..Go inside your project folder:

cd my-react-app


.Install all the dependencies:

npm install


.Start the development server:

npm run dev


.Open the link shown in the terminal (usually http://localhost:5173) in your browser to see your React app running!#


*****************************************************
# One by one commands to setup Tailwind CSS with React + Vite:

Create React + Vite app:

npm create vite@latest my-tailwind-app -- --template react


Go to the project folder:

cd my-tailwind-app


Install dependencies including Tailwind CSS and its peer dependencies:

npm install
npm install -D tailwindcss postcss autoprefixer


Initialize Tailwind CSS config files:

npx tailwindcss init -p


Update tailwind.config.cjs (or tailwind.config.js) to enable content scanning:

Open the file and replace content with:

module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx,ts,tsx}"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}


Add Tailwind directives to your main CSS file (src/index.css or src/main.css):

@tailwind base;
@tailwind components;
@tailwind utilities;


Start the dev server:

npm run dev

Super short combined command (except manual config editing):
npm create vite@latest my-tailwind-app -- --template react && cd my-tailwind-app && npm install && npm install -D tailwindcss postcss autoprefixer && npx tailwindcss init -p

Summary for README.md
# Setup React + Vite + Tailwind CSS

1. Create a React + Vite app:
```bash
npm create vite@latest my-tailwind-app -- --template react
cd my-tailwind-app
npm install


Install Tailwind CSS and its dependencies:

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p


Configure tailwind.config.js:

module.exports = {
  content: ["./index.html", "./src/**/*.{js,jsx,ts,tsx}"],
  theme: { extend: {} },
  plugins: [],
};


Add Tailwind to your CSS (src/index.css):

@tailwind base;
@tailwind components;
@tailwind utilities;


Run dev server:

npm run dev
****************************************************
hello