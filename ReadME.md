Feasto

A food-ordering UI wrapped around a real-world DevOps pipeline. Write code → push to GitHub → Jenkins builds it → Docker ships it → EC2 serves it.

Docker Jenkins AWS Nginx HTML5


Build Structure:- 

┌─────────────┐     git push      ┌─────────────┐
│  Developer  │ ────────────────▶ │   GitHub    │
│ edits code  │                   │  (source)   │
└─────────────┘                   └──────┬──────┘
                                          │ webhook / poll
                                          ▼
                                   ┌─────────────┐
                                   │   Jenkins   │
                                   │  CI/CD job  │
                                   └──────┬──────┘
                                          │ docker build
                                          ▼
                                   ┌─────────────┐
                                   │ Docker image│
                                   │devops-portfolio
                                   └──────┬──────┘
                                          │ docker run
                                          ▼
                        ┌─────────────────────────────────┐
                        │              AWS EC2             │
                        │   ┌───────────────────────────┐  │
                        │   │   Docker container         │ │
                        │   │   Nginx ── serves Feasto    │ │
                        │   └──────────────┬─────────────┘ │
                        └──────────────────┼────────────────┘
                                           │ :8081
                                           ▼
                                     Your Browser

One push. Zero manual deploys. That's the whole pitch.