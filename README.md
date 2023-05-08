NUXT2-TAILWIND
This is a Vue.js project that uses Strapi as a backend for authentication. The project contains two components - Signup and Login. The Signup component allows users to create a new account while the Login component allows existing users to log in.

Project Setup
To set up the project, follow these steps:

Clone the repository to your local machine.
Navigate to the project directory.
Run npm install to install the project dependencies.
Create a .env file in the root of the project and add the following environment variables:
VUE_APP_API_URL=http://localhost:1337
Replace http://localhost:1337 with the URL of your Strapi backend.
Run npm run serve to start the development server.
Navigate to http://localhost:8080 in your browser to view the project.
Project Configuration
The project uses Strapi as a backend for authentication. To configure the project to work with your Strapi backend, you'll need to do the following:

Set up a Strapi backend with authentication enabled.
Update the VUE_APP_API_URL environment variable in the .env file with the URL of your Strapi backend.
Update the Content-Type header in the login and signup methods in the Login.vue and Signup.vue components, respectively, to match the content type of your Strapi backend.
Project Usage
The project contains two components - Signup and Login. The Signup component allows users to create a new account while the Login component allows existing users to log in.

Signup
To create a new account:

Click the Sign-Up button in the navbar.
Enter a username, email, and password in the input fields.
Click the Sign Up button to submit the form.
If the form is submitted successfully, you'll be redirected to the home page.
Login
To log in to an existing account:

Click the Log In button in the navbar.
Enter your email and password in the input fields.
Click the Sign In button to submit the form.
If the login is successful, you'll be redirected to the home page.
Navbar and NavbarAuth
The project includes two navbar components - Navbar and NavbarAuth.

The Navbar component is displayed when the user is not logged in. It contains links to the Signup and Login components.

The NavbarAuth component is displayed when the user is logged in. It contains a link to the home page and a Log Out button.

To switch between the Navbar and NavbarAuth components, the Login and Signup components emit a user-logged-in event when the user logs in. The App.vue component listens for this event and updates the navbar accordingly.
