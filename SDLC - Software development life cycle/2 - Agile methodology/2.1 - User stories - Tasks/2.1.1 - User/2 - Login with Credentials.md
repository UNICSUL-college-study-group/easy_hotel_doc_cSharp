 
- **As a user**,  
    I want to log into the platform using my email and password,  
    so that I can access my account and manage my reservations.  
    
    **Acceptance Criteria**:
    - The system should display a login form with fields for email and password.
    - The system should validate the credentials and redirect the user to their profile if valid.
    - If the credentials are invalid, an error message should be displayed.
    
---

### **Tasks for Login with Credentials**

#### **1. Front-End Implementation**

1. **Create Login Form Component**
    
    - Develop a React component for the login form.
    - Include input fields for:
        - Email
        - Password
    - Add a "Login" button for form submission.
2. **Implement Client-Side Validation**
    
    - Validate that the email is in a correct format using a regular expression.
    - Ensure the password field is not empty.
    - Display error messages directly in the form for invalid inputs.
3. **Show Feedback to the User**
    
    - Display a loading spinner or animation while waiting for the server response.
    - Show user-friendly error messages if login fails (e.g., "Invalid email or password").
4. **Handle Successful Login**
    
    - Save the authentication token (e.g., JWT) in localStorage or cookies securely.
    - Redirect the user to their profile or the home page upon successful login.
5. **Handle Logout (Optional)**
    
    - Add functionality to clear the authentication token and redirect to the login page.

---

#### **2. Back-End Implementation**

1. **Create Login API Endpoint**
    
    - Develop a C# endpoint (e.g., `/api/login`) in ASP.NET Core to handle login requests.
    - Accept email and password as input.
2. **Validate User Credentials**
    
    - Query the database to retrieve the user by email.
    - Use a password hashing algorithm (e.g., bcrypt) to compare the provided password with the stored hash.
3. **Generate an Authentication Token**
    
    - Use JWT to generate a token for authenticated users.
    - Include user information in the token payload, such as `UserID` and `Roles`.
    - Set an expiration time for the token (e.g., 24 hours).
4. **Handle Errors**
    
    - Return specific error messages for:
        - Invalid email or password.
        - Inactive or blocked accounts (if applicable).
5. **Implement Secure Authentication Practices**
    
    - Ensure that passwords are never stored or logged in plain text.
    - Use HTTPS for secure communication.

---

#### **3. Integration**

1. **Connect Front-End to Back-End**
    
    - Use Axios or Fetch API to send login data to the `/api/login` endpoint.
    - Handle the server response:
        - On success: Store the JWT token and redirect the user.
        - On failure: Display an error message.
2. **Token Management**
    
    - Store the token in a secure way:
        - Prefer HttpOnly cookies for sensitive applications to prevent XSS attacks.
    - Provide a utility to decode and verify the token on the front-end (e.g., to display user info).
3. **Protect Routes**
    
    - Use React Router guards to restrict access to certain pages based on login status.

---

#### **4. Security Considerations**

1. **Use HTTPS for All Requests**
    
    - Ensure all data exchanged between the client and server is encrypted.
2. **Rate-Limit Login Attempts**
    
    - Implement rate-limiting to prevent brute-force attacks.
3. **Account Lockout (Optional)**
    
    - Lock accounts temporarily after a specified number of failed login attempts.
4. **CSRF Protection**
    
    - Use CSRF tokens if cookies are used for authentication.
5. **Token Expiration**
    
    - Handle token expiration gracefully, prompting users to re-login when their session expires.

---

#### **5. Testing**

1. **Unit Tests (Back-End)**
    
    - Test the login endpoint for:
        - Valid credentials (success).
        - Invalid credentials (failure).
        - Missing email or password.
2. **Integration Tests**
    
    - Test the communication between the front-end and back-end:
        - Verify successful login and token storage.
        - Validate error messages for failed login attempts.
3. **UI Testing**
    
    - Ensure the login form behaves correctly:
        - Displays validation errors for invalid inputs.
        - Shows server-side error messages (e.g., "Invalid email or password").
4. **Load Testing**
    
    - Test the system’s ability to handle multiple concurrent login requests.

---

#### **6. Deployment**

1. **Deploy Login API Endpoint**
    
    - Ensure the `/api/login` endpoint is live and accessible from the front-end.
2. **Update Front-End Build**
    
    - Include the login form and its functionality in the deployed front-end application.
3. **Monitor Login Metrics**
    
    - Track successful and failed login attempts for analytics and security purposes.

---
