---
layout: default
title: W3.CSS Workflow for Jekyll GitHub Pages
---

# W3.CSS Workflow for Jekyll GitHub Pages

Here's a step-by-step workflow:

1. Download W3.CSS
First, you need to get the W3.CSS file itself.
You can download w3.css directly from the W3Schools website or its GitHub repository. The most common approach is to get the w3.css file.

2. Add W3.CSS to Your Jekyll Project
In your Jekyll project's root directory, create a css (or assets/css) folder if you don't already have one. Then, place the downloaded w3.css file into this folder.

Your project structure might look something like this:

```text
my-jekyll-blog/
├── _layouts/
├── _posts/
├── css/
│   └── w3.css  <-- W3.CSS file goes here
├── _config.yml
├── index.html
└── ...
```

3. Link W3.CSS in Your Layouts
  To make W3.CSS available across your entire site, you'll want to link it in your main Jekyll layout file (e.g., _layouts/default.html or _layouts/home.html). Open your primary layout file and add the following line within the <head> section:

  **Explanation:**
  
  - {{ "/css/w3.css" | relative_url }}: This Jekyll Liquid filter is crucial.
  
    + "/css/w3.css" specifies the path to your W3.CSS file relative to your Jekyll project's root.
    
    + relative_url ensures that the path is correctly generated for GitHub Pages, taking into account your baseurl if you have one configured in _config.yml. This makes your links work correctly whether you're developing locally or deploying to GitHub Pages.

4. Use W3.CSS Classes in Your Content
Now you can start using W3.CSS classes in your Jekyll posts and pages!

For example, in a _posts/2025-07-04-my-post.md file or an about.md page:

```markdown
---
layout: post
title: My Awesome Post with W3.CSS
---

<div class="w3-container w3-teal">
  <h1>Welcome to My Blog!</h1>
  <p>This is a W3.CSS container with a teal background.</p>
</div>

<button class="w3-button w3-red w3-round-large">Click Me!</button>

<div class="w3-panel w3-yellow w3-card-4">
  <p>This is a W3.CSS panel with a yellow background and a shadow.</p>
</div>
```

5. Local Testing
  Before pushing to GitHub Pages, it's always a good idea to test your changes locally. Navigate to your Jekyll project's root directory in your terminal and run:

```bash
bundle exec jekyll serve
```

This will build your site and serve it on a local server (usually http://localhost:4000). Open your browser to this address and ensure W3.CSS styles are applied correctly.

6. Deploy to GitHub Pages
  Once you're satisfied with your local testing, commit your changes and push them to your GitHub repository. GitHub Pages will automatically build your Jekyll site, and W3.CSS will be included and styled as intended.

  ```bash
  git add .
  git commit -m "Add W3.CSS to Jekyll project"
  git push origin master # or main, depending on your branch name
  ```

**Considerations**

- CDN Option: While the local file approach is generally recommended for Jekyll GitHub Pages for reliability, you could also link directly to the W3.CSS CDN in your layout:

```html
<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
```

  However, relying on a CDN means your site's styling is dependent on the CDN being available. For a self-contained GitHub Pages site, including the file locally is often preferred.
  
  + Customization: If you want to customize W3.CSS (e.g., change colors, fonts), you can modify the w3.css file directly
    or, better yet, create your own CSS file (e.g., main.css) and link it after w3.css in your layout. This way, your custom styles can override W3.CSS defaults.

```html
<link rel="stylesheet" href="{{ "/css/w3.css" | relative_url }}">
<link rel="stylesheet" href="{{ "/css/main.css" | relative_url }}">
```

- Asset Pipeline: For more complex Jekyll setups, you might consider using a more robust asset pipeline (like Jekyll Asset Pipeline or Gulp/Webpack) to manage your CSS, but for simply including W3.CSS, the direct file inclusion is sufficient.

By following these steps, you can effectively integrate W3.CSS into your Jekyll GitHub Pages site to enhance its styling and responsiveness.

