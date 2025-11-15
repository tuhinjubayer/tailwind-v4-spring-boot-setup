# tailwind-v4-spring-boot-setup
A simple, step-by-step guide on how to connect and configure Tailwind CSS v4 with a Java Spring Boot and Thymeleaf project.

How to Connect Tailwind CSS v4 to Spring Boot
# Connect Tailwind CSS v4 to Spring Boot

A complete guide to using the **Tailwind CSS v4 JIT compiler** with Spring Boot.  
Automatically watches your templates and builds optimized CSS.

---

## 📑 Table of Contents
- [Step 1: Initialize Node.js](#step-1-initialize-nodejs)
- [Step 2: Install Tailwind v4](#step-2-install-tailwind-v4)
- [Step 3: Create Source CSS](#step-3-create-source-css)
- [Step 4: Configure npm Scripts](#step-4-configure-npm-scripts)
- [Step 5: Link CSS in HTML](#step-5-link-css-in-html)
- [Step 6: Start Development Workflow](#step-6-start-development-workflow)
- [Video Tutorial](#video-tutorial)

---

## **Step 1: Initialize Node.js**
Run in project root (same folder as `pom.xml`):

```bash
npm init -y
Step 2: Install Tailwind v4

Install required Tailwind packages:

npm install -D tailwindcss @tailwindcss/cli

Step 3: Create Source CSS

Create folder:

src/main/resources/static/css


Create file:

src/main/resources/static/css/input.css


Add:

@import "tailwindcss";

@source "./src/main/resources/templates/**/*.html";

@theme {
  --color-brand: #3b82f6;
  --font-display: "Inter", "sans-serif";
}

@layer base {
  h1 {
    @apply text-2xl font-bold;
  }
}

Step 4: Configure npm Scripts

Replace "scripts" section in package.json:

"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "build-css": "npx @tailwindcss/cli -i ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/style.css --minify",
  "watch-css": "npx @tailwindcss/cli -i ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/style.css --watch"
}

Step 5: Link CSS in HTML

Inside your Thymeleaf template:

<title>My Spring App</title>
<link rel="stylesheet" th:href="@{/css/style.css}">

Step 6: Start Development Workflow
Terminal 1 — Tailwind Watcher
npm run watch-css

Terminal 2 — Spring Boot
./mvnw spring-boot:run


or run from IDE.

### 🎥 Video Tutorial

I have also created a video tutorial for this guide.


https://youtu.be/HPvwzel-LDo

---

# How to Connect Tailwind CSS v4 to Spring Boot

This guide explains how to set up the Tailwind CSS v4 JIT (Just-In-Time) compiler...


