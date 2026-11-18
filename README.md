<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0b6623,50:146b3a,100:b3000c&height=190&section=header&text=Pubudu%20Gunasekara&fontSize=44&fontColor=ffffff&fontAlignY=36&animation=fadeIn&desc=Happy%20holidays%20from%20San%20Jose&descSize=16&descAlignY=58" alt="Pubudu Gunasekara" width="100%" />
</p>

<p align="center"><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Snowflake.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Christmas%20Tree.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Wrapped%20Gift.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/People/Santa%20Claus.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Bell.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Snowman.png" width="30" height="30" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Snowflake.png" width="30" height="30" alt="" /></p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=20&pause=1200&color=E63946&center=true&vCenter=true&width=620&lines=Shipping+features%2C+not+coal;Making+a+list%2C+checking+it+in+code;Backend+%2B+distributed+systems+engineer;Wishing+for+a+Summer+2027+SWE+internship" alt="Typing intro" />
</p>

<p align="center">
  <a href="https://pubudugunasekara.github.io/"><img src="https://img.shields.io/badge/Portfolio-b3000c?style=for-the-badge&logo=githubpages&logoColor=white" alt="Portfolio"></a>
  <a href="https://www.linkedin.com/in/pubudugunasekera/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:pubudupguna@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
</p>

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/People/Santa%20Claus.png" width="34" height="34" alt="" /> Hi, I'm Pubudu

I build backends that stay correct when things go wrong, and AI systems that don't make things up.
Before grad school I was a QA engineer at Virtusa on a British Telecom platform with 1M+ users, so I test first and trust second.

> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Wrapped%20Gift.png" width="22" height="22" alt="" /> **On my wishlist this year:** a **Summer 2027 SWE / AI internship** in the Bay Area. I've been good, and my tests are green.

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Christmas%20Tree.png" width="28" height="28" alt="" /> Gifts under the tree

| Project | What it does | Proof |
|---|---|---|
| **[ResumeMatch](https://github.com/PubuduGunasekara/rag-resumematch)**<br><sub>Python · FastAPI · ChromaDB · Ollama · Next.js</sub> | RAG system that matches a resume against real job postings and checks every "match" claim in code before showing it | 107,528 postings in ~14 s on a laptop · recall@30 0.79 → 0.97 · 353 tests in CI |
| **[Distributed Task Scheduler](https://github.com/PubuduGunasekara/distributed-task-scheduler)**<br><sub>Java · Spring Boot · Kafka · Redis · PostgreSQL</sub> | Job scheduler that runs each task exactly once even when Kafka delivers a message twice | 0 duplicate runs in a 1,000-task load test · ~2,700 tasks/min · 188 tests, 93% coverage |
| **[AI Code Review Assistant](https://github.com/PubuduGunasekara/ai-code-reviewer)**<br><sub>React · Node.js · Redis · PostgreSQL · AWS</sub> | Sign in with GitHub, pick a pull request, get an AI review with severity-tagged findings · [live demo](https://main.d3dm91k4g9mtr9.amplifyapp.com/) | ~8 s per review · ~$0.002 per review |
| **[IoT Smart Farm](https://github.com/PubuduGunasekara/smart-farm-1.1.0)**<br><sub>React Native · Redux · Firebase · Arduino</sub> | Mobile app for real-time water, food, gate and cleaning control on a physical Arduino farm model (team lead) | Top 10 Most Innovative Projects, NSBM Green EXE |

<details>
<summary><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Bell.png" width="20" height="20" alt="" /> <b>Unwrap this one: how the scheduler avoids running a job twice</b></summary>
<br>

```mermaid
flowchart LR
    P[Producer] -->|task| K[(Kafka)]
    K -->|may deliver twice| C1[Consumer 1]
    K -->|may deliver twice| C2[Consumer 2]
    C1 --> L{"Redis lock + state check"}
    C2 --> L
    L -->|first claim wins| DB[(PostgreSQL<br/>optimistic locking)]
    L -.->|duplicate| X[Skipped]
```

Kafka delivers at least once, so duplicates are normal. A database state machine, optimistic locking and a Redis lock turn that into exactly one run per task.
</details>

<details>
<summary><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Wrapped%20Gift.png" width="20" height="20" alt="" /> <b>And this one: how ResumeMatch keeps the model honest</b></summary>
<br>

```mermaid
flowchart LR
    R[Resume] --> S[Search each section<br/>in ChromaDB]
    S --> F[Merge results<br/>with rank fusion]
    F --> M[Local 3B model<br/>proposes matches]
    M --> V{"Code checks each claim<br/>against resume + posting"}
    V -->|supported| OK[Shown in report]
    V -.->|unsupported| NO[Blocked]
```

Early testing showed the model cited the wrong posting for 35 of 48 "matched" requirements, so now the model only proposes and code decides.
</details>

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Hammer%20and%20Wrench.png" width="28" height="28" alt="" /> The workshop

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,py,ts,js,spring,fastapi,nodejs,react,nextjs,kafka,redis,postgres,mongodb,docker,aws,githubactions,linux,grafana&perline=9" alt="Tech stack" />
</p>

<p align="center"><sub>Also: JUnit · Testcontainers · Prometheus · ChromaDB · Ollama · OpenAI API</sub></p>

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Snowman.png" width="28" height="28" alt="" /> Off the keyboard

<table>
  <tr>
    <td align="center" width="33%"><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Volleyball.png" width="56" height="56" alt="" /><br><b>Volleyball</b><br><sub>Find me on the court, any season</sub></td>
    <td align="center" width="33%"><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/World%20Map.png" width="56" height="56" alt="" /><br><b>Travelling</b><br><sub>Always planning the next trip, holidays included</sub></td>
    <td align="center" width="33%"><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Animals/Owl.png" width="56" height="56" alt="" /><br><b>Potterhead</b><br><sub>Christmas at Hogwarts is the best chapter. Ask me my house.</sub></td>
  </tr>
</table>

<details>
<summary><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Scroll.png" width="20" height="20" alt="" /> <b>Dear Santa (click to open)</b></summary>
<br>

```yaml
name:        Pubudu Gunasekara   # "Pubzi" to friends
based_in:    San Jose, CA
studying:    MS Computer Science @ Northeastern (grad Dec 2027)
interests:   [backend systems, distributed systems, RAG and LLM evaluation]
house:       Backend
wand:        Java core, Python handle, Kafka finish
practicing:  NeetCode 150, one problem at a time
wishlist:    [Summer 2027 SWE internship, more volleyball, a Hogwarts letter (still waiting)]
```
</details>

<p align="center"><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Food/Hot%20Beverage.png" width="26" height="26" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Food/Cookie.png" width="26" height="26" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Animals/Deer.png" width="26" height="26" alt="" /> <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Sled.png" width="26" height="26" alt="" /></p>

<p align="center">
  <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/E-Mail.png" width="22" height="22" alt="" /> Happy holidays, and thanks for stopping by! Reach me at <a href="mailto:pubudupguna@gmail.com">pubudupguna@gmail.com</a>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:b3000c,50:146b3a,100:0b6623&height=110&section=footer" alt="" width="100%" />
</p>
