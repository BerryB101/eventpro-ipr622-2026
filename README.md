# EventPro — Online Event Management System

A PHP 8+ / MySQL project built from scratch for the Internet Programming 622 assignment. The interface follows the supplied EventPro screenshots: dark navy background, blue links/buttons, rounded panels, a top navigation bar, event management, profile/search pages and private conversations. It uses plain CSS and JavaScript; no CSS framework or CMS is used.

## Requirements
- PHP 8.0+ with PDO MySQL, Fileinfo, and GD or a compatible image library enabled (GD is not required by the current upload validation).
- MySQL 5.7+ / MariaDB 10.4+.
- XAMPP or WAMP recommended for local testing.

## Install in XAMPP
1. Copy the `EventPro` folder to `C:/xampp\htdocs\EventPro` (WAMP: your `www` folder).
2. Start Apache and MySQL.
3. Open `http://localhost/phpmyadmin`, select **Import**, and import `database.sql`.
4. Open `config.php`. The default local XAMPP settings are host `127.0.0.1`, database `eventpro`, user `root`, blank password. Change these if your MySQL account differs.
5. The included `config.php` is set for a folder named `EventPro` under `htdocs` (`BASE_URL` is `/EventPro`). If hosted at the web root, change it to an empty string.
6. Ensure `uploads/profiles` is writable by the web server.
7. Visit `http://localhost/EventPro/` and register two test users to verify messaging.

## Features
- Registration with unique email, optional profile image, server-side validation and `password_hash()`.
- Secure login/logout, regenerated session ID, session-protected pages and CSRF tokens on POST forms.
- Forgot/reset password with expiring, single-use reset token stored as a hash. For this local demo, the reset link is shown on the page because SMTP/email delivery is not configured. A production deployment must email this link and should not display it in the UI.
- Dashboard showing upcoming events and the signed-in user's events; create, edit and delete with ownership checks, timestamps and chronological ordering.
- Profile view/update and validated profile picture uploads.
- Search for users and events, live search submission, and read-only public profile views.
- One-to-one private messaging with conversation history and access limited to the two participants.
- Prepared PDO statements, output escaping with `htmlspecialchars`, HTML/JS validation, server validation, image MIME/size checks and responsive hand-written CSS.

## Test checklist
1. Register two different email addresses; verify duplicate email is rejected.
2. Log out and log in as each user.
3. Create an event; edit it; delete it. Confirm another user cannot edit/delete it by changing the URL.
4. Update profile name and picture; check preview before submission.
5. Search for the second user and an event; open their view-only profile.
6. Send messages both ways and verify the conversation history.
7. Use Forgot Password, open the local reset link, set a new password, then log in with it. Expired/used tokens should be rejected.
8. Try invalid fields and a non-image file upload; the server should reject them.

## Notes
- The code is a teaching/demo project. Before production use, configure HTTPS, mail delivery, rate limiting, logging, database least-privilege credentials, a stricter Content Security Policy, and a deployment-safe error handler.
- Do not submit the screenshots in the assignment as if they were captured from your own running application. Run the project and capture your own evidence screenshots for the submission.
