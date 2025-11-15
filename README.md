# Project-portfolio-2
<!DOCTYPE html>
    <html>
    <head>
        <title>Linking JavaScript</title>
    </head>
    <body>
        <h1>My Webpage</h1>
        <button onclick="myFunction()">Click me</button>

        <script src="script.js"></script>
    </body>
    </html>

import { useState, useEffect } from "react";
import { motion, AnimatePresence } from "framer-motion";
import {
  Github,
  Linkedin,
  Mail,
  Moon,
  Sun,
  Download,
  Code,
  Server,
  Zap,
  HardHat,
  MessageSquare,
  Target,
  Clock,
  RefreshCw,
  Users,
  Lightbulb,
  Briefcase,
  Layers,
  Feather,
} from "lucide-react";

// --- SKILLS DATA & COMPONENTS (TECHNICAL) ---

const SKILLS_DATA = [
  {
    category: "Frontend Development",
    icon: Code,
    tools: "HTML5, CSS3, JavaScript (ES6+), React.js, Next.js, Tailwind CSS, Framer Motion, Axios, Git/GitHub.",
    work: [
      "Build responsive and user-friendly interfaces",
      "Create reusable UI components",
      "Add smooth animations",
      "Convert Figma designs into real pages",
      "Connect UI with backend APIs",
      "Optimize performance and loading speed",
    ],
    color: "text-blue-400",
  },
  {
    category: "Backend Development",
    icon: Server,
    tools: "Node.js, Express.js, MongoDB, Mongoose, Firebase, REST API, JWT, Bcrypt, Postman.",
    work: [
      "Build secure REST APIs",
      "Create backend logic and routing",
      "Manage databases and schemas",
      "Implement authentication and authorization",
      "Integrate external APIs",
      "Handle validation and error control",
      "Deploy backend services",
    ],
    color: "text-green-400",
  },
  {
    category: "Full-Stack Capabilities",
    icon: Zap,
    // FIXED: Changed descriptive string into a comma-separated list for proper chip rendering
    tools: "System Architecture, Database Design, Deployment (Vercel/Netlify), CI/CD Principles, Security Practices, Problem Solving.",
    work: [
      "Complete web applications",
      "Dashboards and admin panels",
      "CRUD systems",
      "Authentication-based apps",
      "API-driven projects",
      "Business/portfolio websites",
    ],
    color: "text-pink-400",
  },
];

const ToolChip = ({ children }) => (
  <span className="inline-block bg-pink-600/20 text-pink-100 backdrop-blur-sm rounded-full px-3 py-1 text-xs font-medium border border-pink-500/30 whitespace-nowrap transition duration-300 hover:bg-pink-600/30 hover:shadow-lg">
    {children}
  </span>
);

const SkillCategoryCard = ({ data, index }) => {
  const cardVariants = {
    hidden: { opacity: 0, y: 50 },
    visible: {
      opacity: 1,
      y: 0,
      transition: { duration: 0.7, delay: index * 0.2 },
    },
  };

  const cardTheme = "bg-pink-900/40 border border-pink-800 backdrop-blur-sm";

  return (
    <motion.div
      className={`p-8 rounded-2xl shadow-2xl transition duration-500 hover:shadow-pink-500/30 ${cardTheme}`}
      variants={cardVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, amount: 0.3 }}
    >
      <data.icon className={`w-10 h-10 mb-4 ${data.color}`} strokeWidth={2.5} />

      <h3 className="text-2xl font-bold mb-4 text-pink-200">{data.category}</h3>

      {/* Tools Section */}
      <div className="mb-6">
        <h4 className="text-lg font-semibold mb-3 text-pink-300 flex items-center">
          <HardHat className="w-4 h-4 mr-2 text-pink-500" /> Tools & Technologies
        </h4>
        <div className="flex flex-wrap gap-2">
          {data.tools.split(", ").map((tool, i) => (
            <ToolChip key={i}>{tool}</ToolChip>
          ))}
        </div>
      </div>

      {/* Capabilities Section */}
      <div>
        <h4 className="text-lg font-semibold mb-3 text-pink-300 flex items-center">
          <Code className="w-4 h-4 mr-2 text-pink-500" /> Key Capabilities
        </h4>
        <ul className="space-y-2 text-sm text-pink-100/80">
          {data.work.map((item, i) => (
            <li key={i} className="flex items-start">
              <span className="text-pink-500 mr-2 mt-1">•</span>
              {item}
            </li>
          ))}
        </ul>
      </div>
    </motion.div>
  );
};

// --- SOFT SKILLS DATA & COMPONENTS (SOFT) ---

const SOFT_SKILLS_DATA = [
  {
    title: "Creative Problem-Solving",
    description: "Ability to generate fresh ideas and deliver smart solutions.",
    icon: Lightbulb,
  },
  {
    title: "Effective Communication",
    description: "Clearly expressing concepts to clients and team members.",
    icon: MessageSquare,
  },
  {
    title: "Attention to Detail",
    description: "Ensuring precision and quality in every part of the work.",
    icon: Target,
  },
  {
    title: "Time Management",
    description: "Delivering high-quality results within deadlines.",
    icon: Clock,
  },
  {
    title: "Adaptability",
    description: "Quickly adjusting to new tools, trends, and project requirements.",
    icon: RefreshCw,
  },
  {
    title: "Collaboration",
    description: "Working smoothly with others and valuing diverse ideas.",
    icon: Users,
  },
  {
    title: "Creativity & Innovation",
    description: "Bringing unique and original concepts to each project.",
    icon: Zap,
  },
  {
    title: "Professional Work Ethic",
    description: "Commitment, responsibility, and consistency in every task.",
    icon: Briefcase,
  },
];

const SoftSkillCard = ({ skill, index, darkMode }) => {
  const Icon = skill.icon;

  const cardLight = "bg-white/70 border border-pink-100 hover:shadow-lg hover:shadow-pink-200/50";
  const cardDark = "bg-pink-900/40 border border-pink-800 hover:shadow-xl hover:shadow-pink-800/50";
  const iconColor = darkMode ? "text-pink-400" : "text-pink-600";
  const descriptionColor = darkMode ? "text-pink-200/80" : "text-pink-800/90";

  const cardVariants = {
    hidden: { opacity: 0, scale: 0.8, y: 20 },
    visible: {
      opacity: 1,
      scale: 1,
      y: 0,
      transition: { duration: 0.5, delay: index * 0.1 },
    },
  };

  return (
    <motion.div
      className={`p-6 rounded-2xl transition duration-500 ease-out ${darkMode ? cardDark : cardLight}`}
      variants={cardVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, amount: 0.3 }}
      whileHover={{ y: -3, scale: 1.01 }}
    >
      <Icon className={`w-8 h-8 mb-3 ${iconColor}`} />
      <h4 className="text-xl font-semibold mb-2">{skill.title}</h4>
      <p className={`text-sm ${descriptionColor}`}>{skill.description}</p>
    </motion.div>
  );
};

// --- PROJECT DATA & COMPONENTS ---

const projects = [
  {
    title: "Creative Portfolio Website",
    description: "A responsive personal portfolio built with React & Tailwind.",
    img: "https://placehold.co/600x400/8B5CF6/FFFFFF?text=Project+1",
  },
  {
    title: "UI Landing Page",
    description: "A modern landing page with smooth animations and minimal design.",
    img: "https://placehold.co/600x400/EC4899/FFFFFF?text=Project+2",
  },
  {
    title: "Brand Identity Design",
    description: "A full branding kit including logo, palette, typography.",
    img: "https://placehold.co/600x400/10B981/FFFFFF?text=Project+3",
  },
  {
    title: "Photography Showcase",
    description: "Gallery-style photography portfolio site.",
    img: "https://placehold.co/600x400/F59E0B/FFFFFF?text=Project+4",
  },
  {
    title: "Minimalist Blog Website",
    description: "Blog platform with markdown support.",
    img: "https://placehold.co/600x400/6366F1/FFFFFF?text=Project+5",
  },
  {
    title: "E-commerce UI Concept",
    description: "Product listing & cart UI with soft-pink aesthetics.",
    img: "https://placehold.co/600x400/D946EF/FFFFFF?text=Project+6",
  },
];

const ProjectCard = ({ project, index }) => {
  const cardVariants = {
    hidden: { opacity: 0, y: 20 },
    visible: {
      opacity: 1,
      y: 0,
      transition: { duration: 0.6, delay: index * 0.15 },
    },
  };
  const cardTheme = "bg-white/60 border border-pink-200 shadow-xl dark:bg-pink-900/40 dark:border-pink-800 dark:shadow-pink-950/50";

  return (
    <motion.div
      className={`rounded-2xl overflow-hidden transition duration-500 hover:scale-[1.02] cursor-pointer ${cardTheme}`}
      variants={cardVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, amount: 0.2 }}
    >
      <img
        src={project.img}
        alt={project.title}
        className="w-full h-48 object-cover object-center"
        onError={(e) => {
          e.target.onerror = null;
          e.target.src = "https://placehold.co/600x400/9CA3AF/FFFFFF?text=Image+Unavailable";
        }}
      />
      <div className="p-5">
        <h4 className="text-xl font-bold mb-2 dark:text-pink-100 text-pink-900">{project.title}</h4>
        <p className="text-sm opacity-80 dark:text-pink-200 text-pink-700">{project.description}</p>
      </div>
    </motion.div>
  );
};

// --- MAIN PORTFOLIO APP COMPONENT ---

export default function App() {
  const [darkMode, setDarkMode] = useState(true); // Default to Dark Mode as per last skill section
  const [loading, setLoading] = useState(true);
  const [typedText, setTypedText] = useState("");

  const theme = darkMode ? "bg-pink-950 text-pink-100" : "bg-pink-50 text-pink-900";
  const primaryColor = darkMode ? "text-pink-400" : "text-pink-600";

  const typewriterWords = ["Designer", "Developer", "Creator", "Dreamer", "Farah ✨"];

  // Typewriter Effect
  useEffect(() => {
    let index = 0;
    let wordIndex = 0;

    const typing = setInterval(() => {
      setTypedText(typewriterWords[wordIndex].slice(0, index));
      index++;
      if (index > typewriterWords[wordIndex].length) {
        index = 0;
        wordIndex = (wordIndex + 1) % typewriterWords.length;
      }
    }, 180);

    return () => clearInterval(typing);
  }, []);

  // Preloader timeout
  useEffect(() => {
    setTimeout(() => setLoading(false), 1800);
  }, []);

  // Cursor Glow effect
  useEffect(() => {
    const glow = document.getElementById("cursor-glow");
    const handleMouseMove = (e) => {
      glow.style.left = `${e.clientX - glow.clientWidth / 2}px`;
      glow.style.top = `${e.clientY - glow.clientHeight / 2}px`;
    };

    window.addEventListener("mousemove", handleMouseMove);
    return () => window.removeEventListener("mousemove", handleMouseMove);
  }, []);

  return (
    <>
      {/* CURSOR GLOW FIXED */}
      <div
        id="cursor-glow"
        className="pointer-events-none fixed top-0 left-0 w-20 h-20 rounded-full bg-pink-300 opacity-40 blur-2xl z-[99999] transition-colors duration-500"
        style={{ backgroundColor: darkMode ? '#D946EF66' : '#EC489966' }}
      ></div>

      {/* Preloader */}
      <AnimatePresence>
        {loading && (
          <motion.div
            className="fixed inset-0 flex items-center justify-center bg-pink-100 dark:bg-pink-950 z-[9999]"
            initial={{ opacity: 1 }}
            exit={{ opacity: 0 }}
            transition={{ duration: 0.8 }}
          >
            <motion.div
              animate={{ rotate: 360 }}
              transition={{ repeat: Infinity, duration: 1, ease: "linear" }}
              className="w-20 h-20 border-4 border-pink-400 border-t-transparent rounded-full"
            />
          </motion.div>
        )}
      </AnimatePresence>

      {!loading && (
        <motion.div
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ duration: 1 }}
          className={`font-sans min-h-screen snap-y snap-mandatory overflow-y-scroll transition-colors duration-700 ${theme}`}
        >
          {/* Floating Particles */}
          <div className="fixed inset-0 pointer-events-none overflow-hidden">
            {[...Array(18)].map((_, i) => (
              <motion.span
                key={i}
                className="absolute w-3 h-3 bg-pink-300/40 rounded-full"
                initial={{ opacity: 0, y: 0, x: 0 }}
                animate={{
                  opacity: [0.4, 1, 0.4],
                  y: [0, -200, 0],
                  x: [0, i % 2 === 0 ? 60 : -60, 0],
                }}
                transition={{ duration: 6 + i, repeat: Infinity }}
                style={{ left: `${Math.random() * 100}%`, top: `${Math.random() * 100}%` }}
              />
            ))}
          </div>

          {/* Header */}
          <header className="p-6 sticky top-0 z-50 bg-opacity-20 backdrop-blur-xl flex justify-between items-center transition-colors duration-700">
            <h1 className="text-2xl font-bold tracking-wide">Farah</h1>

            <div className="flex items-center space-x-6">
              <nav className="space-x-6 text-lg font-medium hidden sm:block">
                <a href="#about" className="hover:opacity-60 transition">
                  About
                </a>
                <a href="#projects" className="hover:opacity-60 transition">
                  Projects
                </a>
                <a href="#skills-tools" className="hover:opacity-60 transition">
                  Skills
                </a>
                <a href="#contact" className="hover:opacity-60 transition">
                  Contact
                </a>
              </nav>

              <button
                onClick={() => setDarkMode(!darkMode)}
                className="p-2 rounded-full bg-white/40 backdrop-blur hover:scale-110 transition dark:bg-pink-800/40"
              >
                {darkMode ? <Sun className="text-pink-300" /> : <Moon className="text-pink-800" />}
              </button>
            </div>
          </header>

          {/* Hero */}
          <section className="max-w-6xl mx-auto px-6 py-20 text-center min-h-screen flex flex-col justify-center snap-center">
            <motion.h2
              initial={{ opacity: 0, y: 30 }}
              whileInView={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.7 }}
              className="text-4xl md:text-6xl font-extrabold mb-4 tracking-tight"
            >
              Hi, I'm Farah
            </motion.h2>

            <p className={`text-2xl md:text-4xl font-semibold h-10 mb-4 opacity-90 ${primaryColor}`}>{typedText}|</p>

            <motion.p
              initial={{ opacity: 0 }}
              whileInView={{ opacity: 1 }}
              transition={{ delay: 0.3, duration: 0.6 }}
              className="text-lg max-w-3xl mx-auto opacity-80 leading-relaxed"
            >
              I create soft, aesthetic, and minimalist digital experiences with elegance and emotion.
            </motion.p>

            <a
              href="/resume.pdf"
              download
              className="mt-8 inline-flex items-center space-x-2 mx-auto px-6 py-3 rounded-xl bg-pink-600 text-white shadow-xl hover:bg-pink-700 transition magnetic-btn"
            >
              <Download /> <span>Download Resume</span>
            </a>
          </section>

          {/* About Section */}
          <section id="about" className="max-w-6xl mx-auto px-6 py-20 snap-center min-h-screen flex flex-col justify-center">
            <motion.h3
              className={`text-4xl font-bold mb-10 text-center ${primaryColor}`}
              initial={{ opacity: 0, y: -20 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ duration: 0.7 }}
            >
              About My Journey
            </motion.h3>

            <div className="grid md:grid-cols-2 gap-10">
              <motion.div
                initial={{ opacity: 0, x: -50 }}
                whileInView={{ opacity: 1, x: 0 }}
                transition={{ duration: 0.8 }}
              >
                <h4 className="text-2xl font-semibold mb-4 flex items-center">
                  <Feather className={`w-6 h-6 mr-2 ${primaryColor}`} /> Passion & Self-Driven Growth
                </h4>
                <p className="text-lg opacity-80 leading-relaxed">
                  I am deeply enthusiastic about design, fueled by a genuine passion that drives me to learn and create constantly. My skills are largely self-taught, reflecting a relentless curiosity and commitment to mastering modern design and development tools. I don't just complete tasks; I approach them with the drive of someone who genuinely loves the craft.
                </p>
              </motion.div>

              <motion.div
                initial={{ opacity: 0, x: 50 }}
                whileInView={{ opacity: 1, x: 0 }}
                transition={{ duration: 0.8 }}
              >
                <h4 className="text-2xl font-semibold mb-4 flex items-center">
                  <Layers className={`w-6 h-6 mr-2 ${primaryColor}`} /> Academic Excellence
                </h4>
                <p className="text-lg opacity-80 leading-relaxed">
                  Currently pursuing Honours, my academic background provides a strong theoretical and critical foundation for my practical skills. This dual focus ensures my design work is not only aesthetically pleasing but also strategically informed, well-researched, and structured to solve complex problems effectively.
                </p>
              </motion.div>
            </div>
          </section>

          {/* Technical Skills Section */}
          <section id="skills-tools" className="py-20 px-6 relative z-10 snap-center">
            <div className="max-w-7xl mx-auto">
              <motion.h2
                className={`text-4xl md:text-5xl font-extrabold mb-16 text-center ${primaryColor}`}
                initial={{ opacity: 0, y: -20 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.7 }}
              >
                Developer Skills & Expertise
              </motion.h2>

              <div className="grid grid-cols-1 lg:grid-cols-3 gap-10">
                {SKILLS_DATA.map((skill, index) => (
                  <SkillCategoryCard key={index} data={skill} index={index} />
                ))}
              </div>
            </div>
          </section>
          
          {/* Soft Skills Section */}
          <section id="soft-skills" className="py-20 px-6 relative z-10 snap-center">
            <div className="max-w-7xl mx-auto">
              <motion.h2
                className={`text-4xl md:text-5xl font-extrabold mb-16 text-center ${primaryColor}`}
                initial={{ opacity: 0, y: -20 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.7 }}
              >
                Essential Soft Skills
              </motion.h2>

              <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                {SOFT_SKILLS_DATA.map((skill, index) => (
                  <SoftSkillCard key={index} skill={skill} index={index} darkMode={darkMode} />
                ))}
              </div>
            </div>
          </section>

          {/* Projects Section */}
          <section id="projects" className="max-w-7xl mx-auto px-6 py-20 snap-center">
            <motion.h3
              className={`text-4xl font-bold mb-12 text-center ${primaryColor}`}
              initial={{ opacity: 0, y: -20 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ duration: 0.7 }}
            >
              Selected Projects
            </motion.h3>
            <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
              {projects.map((project, index) => (
                <ProjectCard key={index} project={project} index={index} />
              ))}
            </div>
          </section>

          {/* Contact Section */}
          <section id="contact" className="max-w-4xl mx-auto px-6 py-20 text-center snap-center">
            <motion.h3
              className={`text-4xl font-bold mb-6 ${primaryColor}`}
              initial={{ opacity: 0, y: -20 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ duration: 0.7 }}
            >
              Let's Connect
            </motion.h3>
            <motion.p
              className="text-lg opacity-80 mb-10"
              initial={{ opacity: 0 }}
              whileInView={{ opacity: 1 }}
              transition={{ delay: 0.3, duration: 0.6 }}
            >
              Whether you have a project idea or just want to chat about design, feel free to reach out. I'm always open to new opportunities.
            </motion.p>

            <div className="flex justify-center space-x-8">
              <motion.a
                href={`mailto:asrafi.farah@gmail.com`}
                className={`p-4 rounded-full transition hover:scale-110 ${primaryColor}`}
                whileHover={{ scale: 1.1 }}
                whileTap={{ scale: 0.95 }}
              >
                <Mail className="w-8 h-8" />
              </motion.a>
              <motion.a
                href="[ YOUR GITHUB URL ]"
                target="_blank"
                className={`p-4 rounded-full transition hover:scale-110 ${primaryColor}`}
                whileHover={{ scale: 1.1 }}
                whileTap={{ scale: 0.95 }}
              >
                <Github className="w-8 h-8" />
              </motion.a>
              <motion.a
                href="[ YOUR LINKEDIN URL ]"
                target="_blank"
                className={`p-4 rounded-full transition hover:scale-110 ${primaryColor}`}
                whileHover={{ scale: 1.1 }}
                whileTap={{ scale: 0.95 }}
              >
                <Linkedin className="w-8 h-8" />
              </motion.a>
            </div>
          </section>

          {/* Footer */}
          <footer className="py-6 text-center border-t border-pink-900/50 text-sm opacity-60">
            <p>&copy; {new Date().getFullYear()} Farah | Designed & Developed with Passion.</p>
          </footer>
        </motion.div>
      )}
    </>
  );
}
