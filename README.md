import zipfile
import os

# Create directory structure
os.makedirs("CAE_INSTITUTE/assets", exist_ok=True)

# index.html content
html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CAE INSTITUTE</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <header>
    <h1>CAE INSTITUTE</h1>
    <nav>
      <a href="#about">About</a>
      <a href="#courses">Courses</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <div class="hero">
    <h2>Empowering the Future through Education</h2>
    <p>Join CAE Institute to shape your career in Engineering, IT, and more</p>
  </div>

  <section id="about">
    <h2 class="section-title">About CAE Institute</h2>
    <p>CAE Institute is a premier educational institution committed to excellence in technical and professional education. Our mission is to foster innovation and build a skilled workforce equipped to meet global challenges.</p>
  </section>

  <section id="courses">
    <h2 class="section-title">Our Courses</h2>
    <div class="courses">
      <div class="course-card">
        <h3>Computer Science</h3>
        <p>Learn programming, software development, and AI fundamentals.</p>
      </div>
      <div class="course-card">
        <h3>Mechanical Engineering</h3>
        <p>Study thermodynamics, CAD, robotics, and design systems.</p>
      </div>
      <div class="course-card">
        <h3>Electronics & Communication</h3>
        <p>Explore embedded systems, signal processing, and circuits.</p>
      </div>
      <div class="course-card">
        <h3>Data Science</h3>
        <p>Hands-on learning with Python, ML models, and real datasets.</p>
      </div>
    </div>
  </section>

  <section id="contact">
    <h2 class="section-title">Contact Us</h2>
    <form class="contact-form">
      <input type="text" name="name" placeholder="Your Full Name" required />
      <input type="email" name="email" placeholder="Your Email Address" required />
      <textarea name="message" rows="5" placeholder="Your Message" required></textarea>
      <button type="submit">Send Message</button>
    </form>
  </section>

  <footer>
    <p>&copy; 2025 CAE INSTITUTE. All rights reserved.</p>
  </footer>

</body>
</html>
"""

# style.css content
css_content = """
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
  color: #333;
}

header {
  background-color: #004080;
  color: white;
  padding: 20px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header h1 {
  margin: 0;
}

nav a {
  color: white;
  margin-left: 20px;
  text-decoration: none;
  font-weight: bold;
}

nav a:hover {
  text-decoration: underline;
}

.hero {
  background: url('https://images.unsplash.com/photo-1581093588401-22c9b55a3c10?fit=crop&w=1500&q=80') center/cover;
  color: white;
  padding: 100px 40px;
  text-align: center;
}

.hero h2 {
  font-size: 48px;
  margin: 0;
}

section {
  padding: 60px 40px;
}

.section-title {
  font-size: 32px;
  margin-bottom: 20px;
  color: #004080;
}

.courses {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.course-card {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

.contact-form input, .contact-form textarea {
  width: 100%;
  padding: 12px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.contact-form button {
  padding: 10px 20px;
  background-color: #004080;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.contact-form button:hover {
  background-color: #003060;
}

footer {
  background-color: #222;
  color: white;
  text-align: center;
  padding: 20px;
}
"""

# README content
readme_content = """
CAE INSTITUTE - Website Template
--------------------------------

This folder contains a basic HTML/CSS website for CAE INSTITUTE.

FILES:
- index.html: Main website structure
- style.css: Stylesheet
- assets/: Folder for images (currently empty)
- README.txt: This file

TO VIEW LOCALLY:
1. Open "index.html" in any browser.
2. You can edit content in a code editor like VSCode or Notepad++.

TO DEPLOY:
- You can host on GitHub Pages, Netlify, or Vercel for free.
"""

# Write files to directory
with open("CAE_INSTITUTE/index.html", "w") as f:
    f.write(html_content)

with open("CAE_INSTITUTE/style.css", "w") as f:
    f.write(css_content)

with open("CAE_INSTITUTE/README.txt", "w") as f:
    f.write(readme_content)

# Create a zip file
zip_filename = "CAE_INSTITUTE_Website.zip"
with zipfile.ZipFile(zip_filename, 'w') as zipf:
    for root, dirs, files in os.walk("CAE_INSTITUTE"):
        for file in files:
            file_path = os.path.join(root, file)
            zipf.write(file_path, os.path.relpath(file_path, "CAE_INSTITUTE"))

zip_filename  # Output the file name to be sent back to the user
