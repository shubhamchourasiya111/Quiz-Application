# Quiz-Application
A.User-Register
1. It checks if the request method is POST and if it's an AJAX request.
2. If it is, it retrieves the `email` and `password` from the POST data.
3. It then validates the email, and password length, and checks if the email is already registered. If all checks pass, it hashes the password, creates a new `UserInfo` object, assigns a user token, and sets session variables for email and user token. Finally, it returns a JSON response with success as `True`.
If the conditions for registration are not met, it returns a JSON response with success as `False` and an appropriate error message.

B.User-Login

1. It checks if the request method is POST and if it's an AJAX request.
2. If it is, it retrieves the `email` and `password` from the POST data.
3. It then queries the database for a user with the provided email. If a user is found, it checks if the provided password matches the hashed password stored in the database. If the check passes, it generates a user token, sets session variables for user token and user ID, and returns a JSON response with success as `True`. If either the email or password is invalid, it returns a JSON response with success as `False` and an appropriate error message.



c.Home
It checks if there is a user_token stored in the session. If it exists, it means a user is logged in.
If a user is logged in, it retrieves all courses from the database using Course.objects.all().
If there are courses available (all_course is not empty), it prepares a context dictionary with the list of courses and renders the Home.html template with that context. If the user is not logged in or there are no courses available, it redirects the user back to the root URL (/).
In summary, this function renders the Home.html template with a list of courses if a user is logged in, and redirects to the root URL if not.

D. Quiz

It checks if there is a user_token stored in the session, ensuring the user is logged in.
If the request method is POST, it processes the quiz submission. It retrieves user answers, calculates the score, and prepares data for rendering the quiz result in the Quizresult.html template.
If the request method is not POST, it prepares data for rendering the quiz questions in the Quiz.html template, including the questions, time limit, and course name. If the user is not logged in, it redirects to the root URL (/).

E.Contact Form
The @csrf_exempt decorator allows the view to accept POST requests without CSRF protection. This is typically used for views that receive data from external sources.
If the request method is POST, it extracts the email, name, and message from the POST data and creates a new ContactForm object with this information in the database. Then, it redirects to the root URL (/).
If the request method is not POST, it renders the Contact.html template for displaying the contact form.
