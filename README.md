## Hi there 👋

import React, { useState } from 'react';

const GitHubProfileGenerator = () => {
  const [name, setName] = useState('');
  const [title, setTitle] = useState('');
  const [about, setAbout] = useState('');
  const [skills, setSkills] = useState('');
  const [projects, setProjects] = useState('');
  const [contact, setContact] = useState('');

  const generateMarkdown = () => {
    return `# Hi there! 👋 I'm ${name}

## ${title}

${about}

### 🛠 Skills
${skills.split(',').map(skill => `- ${skill.trim()}`).join('\n')}

### 🚀 Projects
${projects.split(',').map(project => `- ${project.trim()}`).join('\n')}

### 📫 How to reach me
${contact}

---
Thanks for visiting my GitHub profile! Let's connect and build amazing things together. 😊
`;
  };

  return (
    <div className="max-w-2xl mx-auto p-6 bg-gray-100 rounded-lg shadow-md">
      <h1 className="text-2xl font-bold mb-4">GitHub Profile README Generator</h1>
      <div className="space-y-4">
        <input
          className="w-full p-2 border rounded"
          placeholder="Your Name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <input
          className="w-full p-2 border rounded"
          placeholder="Your Title (e.g., Full Stack Developer)"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
        />
        <textarea
          className="w-full p-2 border rounded"
          placeholder="About You"
          value={about}
          onChange={(e) => setAbout(e.target.value)}
          rows={3}
        />
        <input
          className="w-full p-2 border rounded"
          placeholder="Skills (comma-separated)"
          value={skills}
          onChange={(e) => setSkills(e.target.value)}
        />
        <input
          className="w-full p-2 border rounded"
          placeholder="Projects (comma-separated)"
          value={projects}
          onChange={(e) => setProjects(e.target.value)}
        />
        <input
          className="w-full p-2 border rounded"
          placeholder="Contact Information"
          value={contact}
          onChange={(e) => setContact(e.target.value)}
        />
        <div className="bg-white p-4 rounded border">
          <h2 className="text-lg font-semibold mb-2">Generated README:</h2>
          <pre className="whitespace-pre-wrap">{generateMarkdown()}</pre>
        </div>
      </div>
    </div>
  );
};

export default GitHubProfileGenerator;
