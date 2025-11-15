# tailwind-v4-spring-boot-setup
A simple, step-by-step guide on how to connect and configure Tailwind CSS v4 with a Java Spring Boot and Thymeleaf project.


# How to Connect Tailwind CSS v4 to Spring Boot

This guide explains how to set up the Tailwind CSS v4 JIT (Just-In-Time) compiler to watch your Spring Boot templates and automatically generate an optimized CSS file.




## Features

- Step 1: Initialize Node.js in Your Project
- Step 2: Install Tailwind CSS v4
- Step 3: Create Your Source CSS File
- Step 4: Configure npm Scripts in package.json
- Step 5: Link the Generated CSS in Your HTML
- Step 6: Start the Development Workflow

## Step 1: Initialize Node.js in Your Project

Open a terminal in your project's root folder (the same folder that contains your pom.xml or build.gradle file).
## Bash
- npm init -y
This creates a package.json file to manage your Node.js dependencies.

## Step 2: Install Tailwind CSS v4
Install the necessary Tailwind packages as development dependencies.
## Bash
- npm install -D tailwindcss @tailwindcss/cli
## Step 3: Create Your Source CSS File
This is the most important change. It's best practice to keep your source CSS file separate from your generated static assets.
- Create a new folder: src/main/resources/static/css
- Inside that new folder, create a file named input.css
Note: We are creating this css folder outside the static folder. The static folder should only be for the final, generated style.css file that Spring Boot serves to the browser. input.css is your source code.
- Now, add the following content to src/main/resources/css/input.css. (Note the corrected @source path and @theme syntax).
## CSS

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
## Step 4: Configure npm Scripts in package.json
Open your package.json file and replace the entire "scripts" section with the following. This tells Tailwind where to find your input.css (input) and where to generate the style.css (output).
## JSON




"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  
  "build-css": "npx @tailwindcss/cli -i ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/style.css --minify",


  "watch-css": "npx @tailwindcss/cli -i ./src/main/resources/static/css/input.css -o ./src/main/resources/static/css/style.css --watch"
}




- -i (Input): Points to your source file from Step 3.
- -o (Output): Points to the final file that Spring Boot will serve.


## Step 5: Link the Generated CSS in Your HTML
Now, go to your Thymeleaf template (e.g., src/main/resources/templates/home-page.html) and add the following link inside the <head> tag.
This th:href path works because Spring Boot automatically serves files from the src/main/resources/static/ directory.

## HTML
<head>

    <meta charset="UTF-8">

    <title>My Spring App</title>
    
    <link rel="stylesheet" th:href="@{/css/style.css}">
</head>

## Step 6: Start the Development Workflow 
To work on your project, you will need two terminals running.
- Terminal 1 (Tailwind Watcher): In your project root, run this command. It will watch your input.css and .html files for changes and automatically rebuild style.css every time you save.
## Bash 
- npm run watch-css
 
 
 Terminal 2 (Spring Boot): In a separate terminal (or your IDE), run your Spring Boot application as usual.

That's it! Now, any time you add a Tailwind class (like bg-blue-500) to your .html files and save, the watch-css script will detect it and update your style.css file instantly. Just refresh your browser to see the changes.

## Video Link
URL : https://youtu.be/HPvwzel-LDo?si=m3mtwXOT_eXEh9No 


- Watch this Video for More Understanding 
- Thank you

