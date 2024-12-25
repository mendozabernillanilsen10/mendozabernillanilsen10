// Script para generar README.md
const fs = require('fs');

const generateReadme = () => {
  const readme = `
<!-- Header Dinámico -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=venom&height=300&color=gradient&text=Nilsen%20Ray&desc=Full%20Stack%20Mobile%20Developer&animation=twinkling&fontSize=70&descSize=20&fontColor=ffffff&stroke=0000" />
</div>

<!-- Banner Animado -->
<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=25&duration=3000&pause=1000&color=F70000&center=true&vCenter=true&random=false&width=600&height=100&lines=Mobile+Development+Expert+%F0%9F%93%B1;AI+%26+Machine+Learning+Enthusiast+%F0%9F%A4%96;Coffee+Disease+Classifier+%F0%9F%8C%BF;Innovating+Through+Code+%F0%9F%9A%80" />
</div>

<!-- Estadísticas en Tiempo Real -->
<div align="center">
  <img src="https://komarev.com/ghpvc/?username=mendozabernillanilsen10&style=for-the-badge&color=red" />
  <img src="https://img.shields.io/github/followers/mendozabernillanilsen10?style=for-the-badge&color=red" />
  <img src="https://img.shields.io/github/stars/mendozabernillanilsen10?style=for-the-badge&color=red" />
</div>

<!-- Tech Stack Moderno -->
<h2 align="center">
  <img src="https://media.giphy.com/media/HwBlFQZFcAoUcPHZdX/giphy.gif" width="35px"> 
  Technologies & Tools
</h2>

<div align="center">
  <!-- Frontend -->
  <h3>Frontend & Mobile</h3>
  ${generateTechBadges([
    ['React Native', '20232A', 'react', '61DAFB'],
    ['Flutter', '02569B', 'flutter', 'white'],
    ['Kotlin', '0095D5', 'kotlin', 'white'],
    ['Swift', 'FA7343', 'swift', 'white']
  ])}
  
  <!-- Backend -->
  <h3>Backend & Cloud</h3>
  ${generateTechBadges([
    ['Python', '3776AB', 'python', 'white'],
    ['Node.js', '339933', 'nodedotjs', 'white'],
    ['AWS', '232F3E', 'amazon-aws', 'white'],
    ['Firebase', 'FFCA28', 'firebase', 'black']
  ])}
  
  <!-- AI/ML -->
  <h3>AI & ML</h3>
  ${generateTechBadges([
    ['TensorFlow', 'FF6F00', 'tensorflow', 'white'],
    ['PyTorch', 'EE4C2C', 'pytorch', 'white']
  ])}
</div>

<!-- GitHub Stats -->
<div align="center">
  <h2><img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="35px"> GitHub Stats </h2>
  ${generateGitHubStats()}
</div>

<!-- Current Projects -->
<h2 align="center">🚀 Featured Projects</h2>
${generateFeaturedProjects()}

<!-- Weekly Development -->
<div align="center">
  <h2>💻 Weekly Development Breakdown</h2>
  ${generateWeeklyStats()}
</div>

<!-- Social Links -->
<div align="center">
  <h2>🌐 Connect With Me</h2>
  ${generateSocialLinks()}
</div>

<!-- Footer -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=shark&height=150&section=footer&text=Let's%20Create%20Something%20Amazing&fontSize=40&fontColor=fff&animation=fadeIn&color=gradient" />
</div>
`;

  return readme;
};

// Funciones auxiliares
function generateTechBadges(technologies) {
  return technologies.map(([name, color, logo, logoColor]) => 
    `<img src="https://img.shields.io/badge/${name}-${color}?style=for-the-badge&logo=${logo}&logoColor=${logoColor}" />`
  ).join('\n  ');
}

function generateGitHubStats() {
  return `<img src="https://github-stats-alpha.vercel.app/api?username=mendozabernillanilsen10&cc=22272e&tc=37BCF6&ic=fff&bc=0000" width="49%" />
  <img src="http://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=mendozabernillanilsen10&theme=radical&utcOffset=8" width="49%" />`;
}

function generateFeaturedProjects() {
  const projects = [
    {
      name: 'coffee-disease-classifier',
      description: 'AI-powered coffee leaf disease detection'
    },
    {
      name: 'mobile-development-solutions',
      description: 'Collection of mobile development tools'
    }
  ];

  return projects.map(project => 
    `<a href="https://github.com/mendozabernillanilsen10/${project.name}">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=mendozabernillanilsen10&repo=${project.name}&theme=radical" />
    </a>`
  ).join('\n');
}

function generateWeeklyStats() {
  const stats = {
    'Kotlin': 45.25,
    'Python': 30.28,
    'Flutter': 15.12,
    'JavaScript': 9.35
  };

  return `\`\`\`text\n${
    Object.entries(stats)
      .map(([lang, percent]) => 
        `${lang.padEnd(12)} ${'█'.repeat(Math.floor(percent/5))}${'░'.repeat(20-Math.floor(percent/5))} ${percent}%`
      )
      .join('\n')
  }\n\`\`\``;
}

function generateSocialLinks() {
  const socials = [
    ['LinkedIn', '0077B5', 'linkedin', 'nilsen-mendoza-bernilla-233649282'],
    ['Instagram', 'E4405F', 'instagram', 'smith_de_cielos'],
    ['Discord', '7289DA', 'discord', 'nilsenray']
  ];

  return socials.map(([name, color, platform, username]) =>
    `<a href="https://${platform}.com/${username === 'discord' ? 'gg' : 'in'}/${username}">
      <img src="https://img.shields.io/badge/${name}-${color}?style=for-the-badge&logo=${platform}&logoColor=white" />
    </a>`
  ).join('\n  ');
}

// Generar y guardar README
const readmeContent = generateReadme();
fs.writeFileSync('README.md', readmeContent);
console.log('README.md generado exitosamente!');

// Para ejecutar el script:
// node generate-readme.js
