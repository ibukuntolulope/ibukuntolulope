import React, { useState } from 'react';
import { Clipboard } from 'lucide-react';

const GitHubProfileGenerator = () => {
  const [profile, setProfile] = useState({
    name: '',
    tagline: '',
    about: '',
    skills: '',
    learning: '',
    collaborate: '',
    contact: '',
    funFact: '',
    projects: '',
    stats: false,
    streak: false,
    languages: false
  });

  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    setProfile(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));
  };

  const generateMarkdown = () => {
    return `# Hi there! 👋 I'm ${profile.name}

${profile.tagline}

## 👨‍💻 About Me
${profile.about}

## 🛠 Skills
${profile.skills.split(',').map(skill => `- ${skill.trim()}`).join('\n')}

## 🌱 I'm currently learning
${profile.learning}

## 👯 I'm looking to collaborate on
${profile.collaborate}

## 📫 How to reach me
${profile.contact}

## ⚡ Fun fact
${profile.funFact}

## 🚀 Some of my projects
${profile.projects.split(',').map(project => `- ${project.trim()}`).join('\n')}

${profile.stats ? `## 📊 GitHub Stats
![Your GitHub stats](https://github-readme-stats.vercel.app/api?username=YourGitHubUsername&show_icons=true&theme=radical)
` : ''}
${profile.streak ? `## 🔥 Streak Stats
[![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=YourGitHubUsername&theme=dark)](https://git.io/streak-stats)
` : ''}
${profile.languages ? `## 💻 Most Used Languages
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=YourGitHubUsername&layout=compact)
` : ''}

---
Thanks for visiting my GitHub profile! 😊
`;
  };

  const copyToClipboard = () => {
    navigator.clipboard.writeText(generateMarkdown())
      .then(() => alert('README copied to clipboard!'))
      .catch(err => console.error('Failed to copy: ', err));
  };

  return (
    <div className="max-w-4xl mx-auto p-6 bg-gray-100 rounded-lg shadow-md">
      <h1 className="text-3xl font-bold mb-6 text-center">GitHub Profile README Generator</h1>
      <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div className="space-y-4">
          <input
            className="w-full p-2 border rounded"
            placeholder="Your Name"
            name="name"
            value={profile.name}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Tagline (e.g., Full Stack Developer | AI Enthusiast)"
            name="tagline"
            value={profile.tagline}
            onChange={handleChange}
          />
          <textarea
            className="w-full p-2 border rounded"
            placeholder="About You"
            name="about"
            value={profile.about}
            onChange={handleChange}
            rows={3}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Skills (comma-separated)"
            name="skills"
            value={profile.skills}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="What you're learning"
            name="learning"
            value={profile.learning}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Looking to collaborate on"
            name="collaborate"
            value={profile.collaborate}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Contact Information"
            name="contact"
            value={profile.contact}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Fun Fact"
            name="funFact"
            value={profile.funFact}
            onChange={handleChange}
          />
          <input
            className="w-full p-2 border rounded"
            placeholder="Projects (comma-separated)"
            name="projects"
            value={profile.projects}
            onChange={handleChange}
          />
          <div className="flex items-center space-x-2">
            <input
              type="checkbox"
              id="stats"
              name="stats"
              checked={profile.stats}
              onChange={handleChange}
            />
            <label htmlFor="stats">Include GitHub Stats</label>
          </div>
          <div className="flex items-center space-x-2">
            <input
              type="checkbox"
              id="streak"
              name="streak"
              checked={profile.streak}
              onChange={handleChange}
            />
            <label htmlFor="streak">Include Streak Stats</label>
          </div>
          <div className="flex items-center space-x-2">
            <input
              type="checkbox"
              id="languages"
              name="languages"
              checked={profile.languages}
              onChange={handleChange}
            />
            <label htmlFor="languages">Include Most Used Languages</label>
          </div>
        </div>
        <div className="bg-white p-4 rounded border">
          <div className="flex justify-between items-center mb-2">
            <h2 className="text-lg font-semibold">Generated README:</h2>
            <button 
              onClick={copyToClipboard}
              className="p-2 bg-green-500 text-white rounded hover:bg-green-600 flex items-center"
            >
              <Clipboard size={20} className="mr-1" /> Copy
            </button>
          </div>
          <pre className="whitespace-pre-wrap text-sm">{generateMarkdown()}</pre>
        </div>
      </div>
    </div>
  );
};

export default GitHubProfileGenerator;
