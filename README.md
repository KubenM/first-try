// Project structure:
// job-portal-app/
// ├── public/
// │   └── index.html
// ├── src/
// │   ├── components/
// │   │   ├── Button.jsx
// │   │   ├── Input.jsx
// │   │   ├── Card.jsx
// │   │   └── Label.jsx
// │   ├── App.jsx
// │   └── index.jsx
// ├── craco.config.js
// ├── tailwind.config.js
// ├── postcss.config.js
// ├── package.json
// └── README.md

// ---------------------
// craco.config.js
module.exports = {
  style: {
    postcss: {
      plugins: [require("tailwindcss"), require("autoprefixer")],
    },
  },
};

// ---------------------
// package.json
{
  "name": "job-portal-app",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0",
    "react-scripts": "5.0.1",
    "@craco/craco": "^7.0.0",
    "tailwindcss": "^3.0.0",
    "postcss": "^8.0.0",
    "autoprefixer": "^10.0.0"
  },
  "scripts": {
    "start": "craco start",
    "build": "craco build",
    "test": "craco test",
    "eject": "react-scripts eject"
  }
}

// ---------------------
// src/index.jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import "./index.css";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// ---------------------
// src/App.jsx
import React from "react";
import { Card } from "./components/Card";
import { Button } from "./components/Button";
import { Input } from "./components/Input";
import { Label } from "./components/Label";

export default function App() {
  return (
    <div className="p-6 max-w-4xl mx-auto">
      <h1 className="text-3xl font-bold mb-6">Job Portal Sample</h1>

      {/* Job Search Section */}
      <Card>
        <h2 className="text-xl font-semibold mb-4">Search Jobs</h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
          <Input placeholder="Job title or keyword" />
          <Input placeholder="Location" />
          <Button>Search</Button>
        </div>
      </Card>

      {/* Job Posting Section */}
      <Card>
        <h2 className="text-xl font-semibold mb-4">Post a Job</h2>
        <div className="grid gap-4">
          <div>
            <Label>Job Title</Label>
            <Input placeholder="e.g., Software Engineer" />
          </div>
          <div>
            <Label>Location</Label>
            <Input placeholder="e.g., Johannesburg" />
          </div>
          <div>
            <Label>Job Description</Label>
            <Input placeholder="Brief job overview..." />
          </div>
          <Button>Post Job</Button>
        </div>
      </Card>

      {/* Job Listings Section */}
      <Card>
        <h2 className="text-xl font-semibold mb-4">Latest Jobs</h2>
        <ul className="space-y-4">
          <li className="border p-4 rounded-lg">
            <h3 className="font-bold">Frontend Developer</h3>
            <p>Location: Cape Town</p>
            <Button className="mt-2">Apply</Button>
          </li>
          <li className="border p-4 rounded-lg">
            <h3 className="font-bold">Project Manager</h3>
            <p>Location: Durban</p>
            <Button className="mt-2">Apply</Button>
          </li>
        </ul>
      </Card>
    </div>
  );
}

// ---------------------
// src/components/Button.jsx
export function Button({ children, className = "", ...props }) {
  return (
    <button
      className={`px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 ${className}`}
      {...props}
    >
      {children}
    </button>
  );
}

// ---------------------
// src/components/Input.jsx
export function Input({ ...props }) {
  return (
    <input
      className="border p-2 rounded w-full"
      {...props}
    />
  );
}

// ---------------------
// src/components/Card.jsx
export function Card({ children }) {
  return (
    <div className="border rounded-xl shadow p-6 mb-6 bg-white">
      {children}
    </div>
  );
}

// ---------------------
// src/components/Label.jsx
export function Label({ children }) {
  return <label className="block font-semibold mb-1">{children}</label>;
}

// ---------------------
// src/index.css
@tailwind base;
@tailwind components;
@tailwind utilities;

// ---------------------
// tailwind.config.js
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
    "./public/index.html"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};

// ---------------------
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};

// ---------------------
// public/index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Job Portal App</title>
  </head>
  <body class="bg-gray-50">
    <div id="root"></div>
  </body>
</html>
