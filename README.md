import React, { useState } from "react";
import { motion } from "framer-motion";
import {
  SiDocker,
  SiAmazonaws,
  SiKubernetes,
  SiTerraform,
  SiPostgresql,
  SiPython,
  SiGithub,
  SiLinkedin,
  SiInstagram,
} from "react-icons/si";
import { FiChevronDown } from "react-icons/fi";

// ---------------------------
//  Single-file React portfolio
//  - TailwindCSS used for styling
//  - Framer Motion for animations
//  - react-icons for tech & social icons
//  Replace placeholders (NAME, BIO, avatarUrl, social URLs)
//  Drop into a Vite + React project with Tailwind configured.
// ---------------------------

export default function DevOpsPortfolio() {
  const NAME = "Your Name"; // <-- replace
  const BIO = "I build reliable, scalable, and automated cloud infrastructure. DevOps engineer focused on CI/CD, containers, and infrastructure as code.";
  const avatarUrl = "https://images.unsplash.com/photo-1545996124-1b6aefb7a9b7?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.0.3&s=placeholder"; // replace with your photo

  const socials = [
    { id: "github", icon: <SiGithub size={22} />, url: "https://github.com/youruser" },
    { id: "linkedin", icon: <SiLinkedin size={22} />, url: "https://linkedin.com/in/youruser" },
    { id: "instagram", icon: <SiInstagram size={22} />, url: "https://instagram.com/youruser" },
  ];

  const skills = [
    { id: "docker", name: "Docker", Icon: SiDocker, level: "Advanced", desc: "Containerization, multi-stage builds, image optimization" },
    { id: "aws", name: "AWS", Icon: SiAmazonaws, level: "Advanced", desc: "EC2, S3, IAM, ECS/EKS, Lambda, CloudFormation" },
    { id: "k8s", name: "Kubernetes", Icon: SiKubernetes, level: "Intermediate", desc: "Deployments, services, ingress, Helm charts" },
    { id: "tf", name: "Terraform", Icon: SiTerraform, level: "Intermediate", desc: "IaC, state management, modules" },
    { id: "sql", name: "SQL", Icon: SiPostgresql, level: "Advanced", desc: "Design, queries, performance tuning" },
    { id: "python", name: "Python", Icon: SiPython, level: "Advanced", desc: "Scripting, automation, AWS SDK (boto3)" },
  ];

  const [activeSkill, setActiveSkill] = useState(null);

  const containerVariants = {
    hidden: {},
    visible: { transition: { staggerChildren: 0.06 } },
  };

  const cardVariants = {
    hidden: { opacity: 0, y: 20 },
    visible: { opacity: 1, y: 0 },
    hover: { scale: 1.03, y: -6 },
  };

  return (
    <div className="min-h-screen w-full bg-gradient-to-b from-[#071033] via-[#0b1b34] to-[#071033] text-slate-100 antialiased">
      {/* page container with vertical snap */}
      <main className="h-screen snap-y snap-mandatory overflow-y-scroll scroll-smooth">
        {/* HERO / INTRO */}
        <section className="snap-start h-screen flex items-center justify-center">
          <div className="container mx-auto px-6 lg:px-20 flex flex-col-reverse lg:flex-row items-center gap-12">
            {/* left: text */}
            <motion.div
              initial={{ opacity: 0, x: -40 }}
              animate={{ opacity: 1, x: 0 }}
              transition={{ duration: 0.7 }}
              className="flex-1"
            >
              <div className="max-w-xl">
                <h1 className="text-4xl md:text-5xl font-extrabold tracking-tight leading-tight">
                  <span className="bg-clip-text text-transparent bg-gradient-to-r from-indigo-300 via-sky-300 to-rose-300">Hi, I&apos;m {NAME}</span>
                </h1>
                <p className="mt-4 text-slate-300">{BIO}</p>

                <div className="mt-6 flex items-center gap-4">
                  <a
                    href="#skills"
                    className="group inline-flex items-center gap-3 bg-gradient-to-r from-indigo-600 to-rose-500 px-5 py-3 rounded-2xl shadow-lg transform-gpu hover:scale-105 transition"
                  >
                    <span className="font-medium">Explore my skills</span>
                    <motion.span animate={{ x: [0, 6, 0] }} transition={{ repeat: Infinity, duration: 1.8 }}>
                      <FiChevronDown />
                    </motion.span>
                  </a>

                  <div className="flex items-center gap-3">
                    {socials.map((s) => (
                      <motion.a
                        key={s.id}
                        href={s.url}
                        target="_blank"
                        rel="noopener noreferrer"
                        whileHover={{ scale: 1.12, rotate: 10 }}
                        whileTap={{ scale: 0.95 }}
                        className="p-3 rounded-full bg-white/5 backdrop-blur-sm border border-white/6 hover:bg-white/6 transition"
                        title={s.id}
                      >
                        {s.icon}
                      </motion.a>
                    ))}
                  </div>
                </div>
              </div>
            </motion.div>

            {/* right: avatar and animated background */}
            <motion.div
              initial={{ opacity: 0, x: 40 }}
              animate={{ opacity: 1, x: 0 }}
              transition={{ duration: 0.7 }}
              className="flex-1 flex items-center justify-center"
            >
              <div className="relative w-64 h-64 rounded-3xl p-1" aria-hidden>
                {/* fancy animated gradient ring */}
                <div className="absolute inset-0 rounded-3xl blur-2xl opacity-40" style={{ background: "radial-gradient(circle at 10% 20%, rgba(99,102,241,0.18), transparent 10%), radial-gradient(circle at 90% 80%, rgba(236,72,153,0.14), transparent 10%)" }} />

                <div className="relative h-full w-full rounded-3xl bg-gradient-to-br from-white/5 to-white/3 border border-white/6 flex items-center justify-center overflow-hidden">
                  <img src={avatarUrl} alt="avatar" className="w-full h-full object-cover rounded-2xl" />
                  {/* small animated container icons */}
                  <motion.div animate={{ rotate: [0, 15, 0, -10, 0] }} transition={{ duration: 10, repeat: Infinity, ease: "linear" }} className="absolute -bottom-6 right-3 flex gap-2">
                    <div className="p-2 rounded-md bg-white/6 backdrop-blur-md border border-white/6 shadow-sm">
                      <SiDocker size={20} />
                    </div>
                    <div className="p-2 rounded-md bg-white/6 backdrop-blur-md border border-white/6 shadow-sm">
                      <SiAmazonaws size={20} />
                    </div>
                  </motion.div>
                </div>
              </div>
            </motion.div>
          </div>
        </section>

        {/* SKILLS */}
        <section id="skills" className="snap-start h-screen flex items-center justify-center">
          <div className="container mx-auto px-6 lg:px-20 py-12">
            <motion.h2 initial={{ opacity: 0, y: 8 }} animate={{ opacity: 1, y: 0 }} className="text-3xl font-bold text-center mb-8">
              Tech Stack & Expertise
            </motion.h2>

            <motion.div variants={containerVariants} initial="hidden" animate="visible" className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 max-w-5xl mx-auto">
              {skills.map((s) => (
                <motion.div
                  key={s.id}
                  variants={cardVariants}
                  whileHover="hover"
                  onMouseEnter={() => setActiveSkill(s.id)}
                  onMouseLeave={() => setActiveSkill(null)}
                  onClick={() => setActiveSkill(s.id)}
                  className={`relative p-6 rounded-2xl bg-gradient-to-br from-white/3 to-white/5 border border-white/6 shadow-md cursor-pointer transform-gpu`}
                >
                  <div className="flex items-start gap-4">
                    <div className="p-3 rounded-lg bg-white/6">
                      <s.Icon size={28} />
                    </div>
                    <div>
                      <h3 className="font-semibold text-lg">{s.name}</h3>
                      <p className="text-sm text-slate-300 mt-1">{s.level}</p>
                    </div>
                  </div>

                  {/* subtle hover details */}
                  <motion.div
                    animate={{ opacity: activeSkill === s.id ? 1 : 0, y: activeSkill === s.id ? 0 : 8 }}
                    transition={{ duration: 0.22 }}
                    className="mt-4 text-sm text-slate-300"
                  >
                    {s.desc}
                  </motion.div>

                  {/* decorative animated corner */}
                  <motion.div
                    initial={{ opacity: 0 }}
                    animate={{ opacity: activeSkill === s.id ? 1 : 0 }}
                    className="absolute -top-4 -right-6"
                  >
                    <div className="w-16 h-16 rounded-full border border-white/5 bg-gradient-to-tr from-indigo-500/20 to-rose-400/10 blur-sm" />
                  </motion.div>
                </motion.div>
              ))}
            </motion.div>

            {/* expanded skill modal / detail panel */}
            <div className="mt-10 max-w-4xl mx-auto">
              <motion.div initial={{ opacity: 0 }} animate={{ opacity: activeSkill ? 1 : 0 }} transition={{ duration: 0.25 }} className={`${activeSkill ? "block" : "hidden"}`}>
                {activeSkill && (
                  <div className="p-6 rounded-xl bg-gradient-to-br from-white/4 to-white/6 border border-white/6">
                    <div className="flex items-start gap-4">
                      <div className="p-3 rounded-lg bg-white/6">
                        {skills.find((x) => x.id === activeSkill).Icon({ size: 28 })}
                      </div>
                      <div>
                        <h4 className="font-bold text-xl">{skills.find((x) => x.id === activeSkill).name}</h4>
                        <p className="text-slate-300 mt-2">{skills.find((x) => x.id === activeSkill).desc}</p>

                        <div className="mt-4 flex gap-3">
                          <a href="#" className="px-4 py-2 rounded-lg bg-indigo-600/80 hover:scale-105 transition">See projects</a>
                          <a href="#" className="px-4 py-2 rounded-lg bg-white/6">Read notes</a>
                        </div>
                      </div>
                    </div>
                  </div>
                )}
              </motion.div>
            </div>
          </div>
        </section>

        {/* SOCIALS / CONTACT */}
        <section className="snap-start h-screen flex items-center justify-center">
          <div className="container mx-auto px-6 lg:px-20 py-12 text-center">
            <motion.h2 initial={{ opacity: 0, y: 8 }} animate={{ opacity: 1, y: 0 }} className="text-3xl font-bold mb-6">
              Let’s Connect
            </motion.h2>

            <p className="text-slate-300 max-w-2xl mx-auto mb-8">I share projects, notes and bite-sized DevOps tips across my socials. Happy to chat about collaboration or mentoring.</p>

            <motion.div className="flex items-center justify-center gap-6">
              {socials.map((s) => (
                <motion.a
                  key={s.id}
                  href={s.url}
                  target="_blank"
                  rel="noopener noreferrer"
                  whileHover={{ y: -6, scale: 1.08 }}
                  whileTap={{ scale: 0.98 }}
                  className="group relative flex flex-col items-center gap-2 w-20 h-20 rounded-xl p-3 bg-gradient-to-br from-white/4 to-white/6 border border-white/6 shadow-md"
                >
                  <div className="text-2xl">{s.icon}</div>
                  <div className="text-xs opacity-80 group-hover:opacity-100 transition">{s.id}</div>

                  {/* ripple on click visual (CSS) */}
                </motion.a>
              ))}
            </motion.div>

            <div className="mt-12">
              <a href="mailto:youremail@example.com" className="inline-flex items-center gap-3 px-6 py-3 rounded-2xl bg-gradient-to-r from-indigo-600 to-rose-500 shadow-lg">Say hello</a>
            </div>
          </div>
        </section>

        {/* FOOTER small */}
        <footer className="h-28 flex items-center justify-center text-slate-400">
          <div className="text-sm">© {new Date().getFullYear()} {NAME} • Designed with ❤️ for DevOps</div>
        </footer>
      </main>

      {/* small utility styles for snap behavior (Tailwind should handle most) */}
      <style>{`
        /* enable scroll snap with smooth experience */
        main { scroll-snap-type: y mandatory; }
        section { scroll-snap-align: start; }
      `}</style>
    </div>
  );
}
