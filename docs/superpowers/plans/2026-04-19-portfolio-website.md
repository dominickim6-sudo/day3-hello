# Portfolio Static Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 다크 테마 기반 개인 포트폴리오 정적 웹사이트를 단일 HTML 파일로 구현한다.

**Architecture:** 고정 사이드바 + 스크롤 가능한 메인 콘텐츠 영역. Tailwind CSS CDN으로 스타일링, Vanilla JS로 네비게이션과 Intersection Observer 구현. 모바일에서는 햄버거 메뉴로 사이드바 토글.

**Tech Stack:** HTML5, Tailwind CSS (CDN), Vanilla JavaScript

---

### Task 1: HTML 골격 + 사이드바

**Files:**
- Modify: `index.html` (전체 교체)

- [ ] **Step 1: HTML 골격과 사이드바 작성**

`index.html` 전체 내용을 아래로 교체:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        bg: '#0d1117',
                        sidebar: '#161b22',
                        surface: '#21262d',
                        border: '#30363d',
                        text: '#e6edf3',
                        muted: '#8b949e',
                        accent: '#e94560',
                        'accent-hover': '#ff6b81',
                    }
                }
            }
        }
    </script>
    <style>
        html { scroll-behavior: smooth; }
        body { background-color: #0d1117; }
        @media (max-width: 768px) {
            #sidebar { transform: translateX(-100%); }
            #sidebar.open { transform: translateX(0); }
            #main-content { margin-left: 0; }
        }
    </style>
</head>
<body class="text-text font-sans">
    <!-- Sidebar -->
    <aside id="sidebar" class="fixed top-0 left-0 h-full w-56 bg-sidebar border-r border-border flex flex-col p-6 z-40 transition-transform duration-300">
        <!-- Profile -->
        <div class="text-center mb-8">
            <div class="w-28 h-28 rounded-full bg-surface mx-auto mb-3 overflow-hidden border-2 border-border">
                <div class="w-full h-full flex items-center justify-center text-muted text-2xl">👤</div>
            </div>
            <h1 class="text-text font-bold text-lg">Your Name</h1>
            <p class="text-muted text-sm">Full-Stack Developer</p>
        </div>

        <!-- Navigation -->
        <nav class="flex flex-col gap-1 flex-1">
            <a href="#about" class="nav-link active flex items-center gap-3 px-4 py-2.5 rounded-lg text-sm transition-colors">
                <span>🏠</span> About
            </a>
            <a href="#projects" class="nav-link flex items-center gap-3 px-4 py-2.5 rounded-lg text-sm text-muted hover:text-text transition-colors">
                <span>💼</span> Projects
            </a>
            <a href="#resume" class="nav-link flex items-center gap-3 px-4 py-2.5 rounded-lg text-sm text-muted hover:text-text transition-colors">
                <span>📄</span> Resume
            </a>
            <a href="#blog" class="nav-link flex items-center gap-3 px-4 py-2.5 rounded-lg text-sm text-muted hover:text-text transition-colors">
                <span>📝</span> Blog
            </a>
            <a href="#contact" class="nav-link flex items-center gap-3 px-4 py-2.5 rounded-lg text-sm text-muted hover:text-text transition-colors">
                <span>📬</span> Contact
            </a>
        </nav>

        <!-- Social -->
        <div class="flex justify-center gap-3 pt-4 border-t border-border">
            <a href="#" class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center text-muted hover:text-accent transition-colors text-xs">GH</a>
            <a href="#" class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center text-muted hover:text-accent transition-colors text-xs">LI</a>
            <a href="#" class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center text-muted hover:text-accent transition-colors text-xs">EM</a>
        </div>
    </aside>

    <!-- Mobile hamburger -->
    <button id="menu-toggle" class="md:hidden fixed top-4 left-4 z-50 w-10 h-10 bg-sidebar border border-border rounded-lg flex items-center justify-center text-text">
        ☰
    </button>

    <!-- Main Content -->
    <main id="main-content" class="md:ml-56 min-h-screen">
        <div class="max-w-4xl mx-auto px-6 md:px-12 py-12">

            <!-- About Section (placeholder) -->
            <section id="about" class="section-content mb-20">
                <p class="text-muted text-sm">About section coming soon</p>
            </section>

            <!-- Projects Section (placeholder) -->
            <section id="projects" class="section-content mb-20">
                <p class="text-muted text-sm">Projects section coming soon</p>
            </section>

            <!-- Resume Section (placeholder) -->
            <section id="resume" class="section-content mb-20">
                <p class="text-muted text-sm">Resume section coming soon</p>
            </section>

            <!-- Blog Section (placeholder) -->
            <section id="blog" class="section-content mb-20">
                <p class="text-muted text-sm">Blog section coming soon</p>
            </section>

            <!-- Contact Section (placeholder) -->
            <section id="contact" class="section-content mb-20">
                <p class="text-muted text-sm">Contact section coming soon</p>
            </section>

        </div>
    </main>
</body>
</html>
```

- [ ] **Step 2: 브라우저에서 사이드바와 모바일 토글 동작 확인**

브라우저에서 `index.html` 열기. 사이드바가 좌측에 고정되어 보이는지, 768px 이하에서는 햄버거 메뉴로 토글되는지 확인.

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add HTML skeleton with sidebar navigation"
```

---

### Task 2: About 섹션

**Files:**
- Modify: `index.html` (about section 교체)

- [ ] **Step 1: About 섹션 구현**

`index.html`에서 `<!-- About Section (placeholder) -->` 부분을 아래로 교체:

```html
            <!-- About Section -->
            <section id="about" class="section-content mb-20">
                <p class="text-accent text-xs uppercase tracking-widest mb-2 font-semibold">About Me</p>
                <h2 class="text-text text-3xl font-bold mb-6">안녕하세요,<br>개발자입니다.</h2>
                <p class="text-muted leading-relaxed mb-8 max-w-lg">
                    웹 개발과 사용자 경험에 열정을 가진 개발자입니다. 최신 기술을 활용하여 효율적이고 아름다운 솔루션을 만듭니다. 새로운 것을 배우고 공유하는 것을 좋아합니다.
                </p>

                <div class="mb-8">
                    <h3 class="text-text font-semibold mb-3">Tech Stack</h3>
                    <div class="flex flex-wrap gap-2">
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">JavaScript</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">TypeScript</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">React</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">Node.js</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">Python</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">HTML/CSS</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">Git</span>
                        <span class="px-3 py-1 bg-surface text-muted text-xs rounded-full border border-border">Docker</span>
                    </div>
                </div>

                <a href="#contact" class="inline-block px-6 py-2.5 bg-accent text-white text-sm rounded-lg hover:bg-accent-hover transition-colors">연락하기</a>
            </section>
```

- [ ] **Step 2: 브라우저에서 About 섹션 렌더링 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add About section with profile and tech stack"
```

---

### Task 3: Projects 섹션

**Files:**
- Modify: `index.html` (projects section 교체)

- [ ] **Step 1: Projects 섹션 구현**

`index.html`에서 `<!-- Projects Section (placeholder) -->` 부분을 아래로 교체:

```html
            <!-- Projects Section -->
            <section id="projects" class="section-content mb-20">
                <p class="text-accent text-xs uppercase tracking-widest mb-2 font-semibold">Projects</p>
                <h2 class="text-text text-3xl font-bold mb-8">주요 프로젝트</h2>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Project Card 1 -->
                    <div class="bg-surface rounded-xl border border-border overflow-hidden hover:-translate-y-1 hover:shadow-lg hover:shadow-accent/5 transition-all duration-200">
                        <div class="h-40 bg-border flex items-center justify-center text-muted text-4xl">🚀</div>
                        <div class="p-5">
                            <h3 class="text-text font-semibold mb-2">프로젝트 A</h3>
                            <p class="text-muted text-sm leading-relaxed mb-3">웹 애플리케이션 개발 프로젝트. 사용자 친화적인 인터페이스와 고성능 백엔드 구현.</p>
                            <div class="flex flex-wrap gap-1.5 mb-4">
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">React</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">Node.js</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">MongoDB</span>
                            </div>
                            <div class="flex gap-3">
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">GitHub →</a>
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">Live Demo →</a>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card 2 -->
                    <div class="bg-surface rounded-xl border border-border overflow-hidden hover:-translate-y-1 hover:shadow-lg hover:shadow-accent/5 transition-all duration-200">
                        <div class="h-40 bg-border flex items-center justify-center text-muted text-4xl">📊</div>
                        <div class="p-5">
                            <h3 class="text-text font-semibold mb-2">프로젝트 B</h3>
                            <p class="text-muted text-sm leading-relaxed mb-3">데이터 시각화 대시보드. 실시간 데이터 처리와 인터랙티브 차트 구현.</p>
                            <div class="flex flex-wrap gap-1.5 mb-4">
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">Python</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">D3.js</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">PostgreSQL</span>
                            </div>
                            <div class="flex gap-3">
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">GitHub →</a>
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">Live Demo →</a>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card 3 -->
                    <div class="bg-surface rounded-xl border border-border overflow-hidden hover:-translate-y-1 hover:shadow-lg hover:shadow-accent/5 transition-all duration-200">
                        <div class="h-40 bg-border flex items-center justify-center text-muted text-4xl">🤖</div>
                        <div class="p-5">
                            <h3 class="text-text font-semibold mb-2">프로젝트 C</h3>
                            <p class="text-muted text-sm leading-relaxed mb-3">AI 기반 챗봇 서비스. 자연어 처리와 머신러닝 모델 통합.</p>
                            <div class="flex flex-wrap gap-1.5 mb-4">
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">TypeScript</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">FastAPI</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">Redis</span>
                            </div>
                            <div class="flex gap-3">
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">GitHub →</a>
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">Live Demo →</a>
                            </div>
                        </div>
                    </div>

                    <!-- Project Card 4 -->
                    <div class="bg-surface rounded-xl border border-border overflow-hidden hover:-translate-y-1 hover:shadow-lg hover:shadow-accent/5 transition-all duration-200">
                        <div class="h-40 bg-border flex items-center justify-center text-muted text-4xl">📱</div>
                        <div class="p-5">
                            <h3 class="text-text font-semibold mb-2">프로젝트 D</h3>
                            <p class="text-muted text-sm leading-relaxed mb-3">모바일 우선 반응형 웹앱. 오프라인 지원과 푸시 알림 기능.</p>
                            <div class="flex flex-wrap gap-1.5 mb-4">
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">React Native</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">Firebase</span>
                                <span class="px-2 py-0.5 bg-bg text-muted text-xs rounded border border-border">PWA</span>
                            </div>
                            <div class="flex gap-3">
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">GitHub →</a>
                                <a href="#" class="text-accent text-xs hover:text-accent-hover transition-colors">Live Demo →</a>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
```

- [ ] **Step 2: 브라우저에서 프로젝트 카드 그리드와 호버 애니메이션 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add Projects section with card grid"
```

---

### Task 4: Resume 섹션

**Files:**
- Modify: `index.html` (resume section 교체)

- [ ] **Step 1: Resume 섹션 구현**

`index.html`에서 `<!-- Resume Section (placeholder) -->` 부분을 아래로 교체:

```html
            <!-- Resume Section -->
            <section id="resume" class="section-content mb-20">
                <p class="text-accent text-xs uppercase tracking-widest mb-2 font-semibold">Resume</p>
                <h2 class="text-text text-3xl font-bold mb-8">경력 및 학력</h2>

                <!-- Experience -->
                <div class="mb-10">
                    <h3 class="text-text font-semibold mb-6">Experience</h3>
                    <div class="relative pl-8 border-l-2 border-border">
                        <!-- Item 1 -->
                        <div class="relative mb-8">
                            <div class="absolute -left-[25px] top-1 w-4 h-4 rounded-full bg-accent border-2 border-bg"></div>
                            <p class="text-muted text-xs mb-1">2023.01 - 현재</p>
                            <h4 class="text-text font-semibold">시니어 개발자</h4>
                            <p class="text-accent text-sm mb-2">ABC Company</p>
                            <p class="text-muted text-sm leading-relaxed">프론트엔드 아키텍처 설계 및 팀 리드. 대규모 웹 애플리케이션 개발.</p>
                        </div>
                        <!-- Item 2 -->
                        <div class="relative mb-8">
                            <div class="absolute -left-[25px] top-1 w-4 h-4 rounded-full bg-surface border-2 border-border"></div>
                            <p class="text-muted text-xs mb-1">2020.06 - 2022.12</p>
                            <h4 class="text-text font-semibold">풀스택 개발자</h4>
                            <p class="text-accent text-sm mb-2">XYZ Corp</p>
                            <p class="text-muted text-sm leading-relaxed">백엔드 API 개발 및 데이터베이스 설계. 마이크로서비스 아키텍처 도입.</p>
                        </div>
                        <!-- Item 3 -->
                        <div class="relative">
                            <div class="absolute -left-[25px] top-1 w-4 h-4 rounded-full bg-surface border-2 border-border"></div>
                            <p class="text-muted text-xs mb-1">2018.03 - 2020.05</p>
                            <h4 class="text-text font-semibold">주니어 개발자</h4>
                            <p class="text-accent text-sm mb-2">DEF Startup</p>
                            <p class="text-muted text-sm leading-relaxed">웹 서비스 초기 개발 멤버. 프론트엔드 및 백엔드 기능 구현.</p>
                        </div>
                    </div>
                </div>

                <!-- Education -->
                <div class="mb-10">
                    <h3 class="text-text font-semibold mb-6">Education</h3>
                    <div class="relative pl-8 border-l-2 border-border">
                        <div class="relative mb-8">
                            <div class="absolute -left-[25px] top-1 w-4 h-4 rounded-full bg-surface border-2 border-border"></div>
                            <p class="text-muted text-xs mb-1">2014.03 - 2018.02</p>
                            <h4 class="text-text font-semibold">컴퓨터공학 학사</h4>
                            <p class="text-accent text-sm">한국대학교</p>
                        </div>
                    </div>
                </div>

                <!-- Skills -->
                <div>
                    <h3 class="text-text font-semibold mb-4">Skills</h3>
                    <div class="space-y-3">
                        <div>
                            <p class="text-muted text-xs mb-1.5">Frontend</p>
                            <div class="flex flex-wrap gap-1.5">
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">React</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">Vue.js</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">TypeScript</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">Tailwind CSS</span>
                            </div>
                        </div>
                        <div>
                            <p class="text-muted text-xs mb-1.5">Backend</p>
                            <div class="flex flex-wrap gap-1.5">
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">Node.js</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">Python</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">PostgreSQL</span>
                                <span class="px-2.5 py-1 bg-surface text-muted text-xs rounded-full border border-border">Docker</span>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
```

- [ ] **Step 2: 브라우저에서 타임라인 레이아웃 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add Resume section with timeline"
```

---

### Task 5: Blog 섹션

**Files:**
- Modify: `index.html` (blog section 교체)

- [ ] **Step 1: Blog 섹션 구현**

`index.html`에서 `<!-- Blog Section (placeholder) -->` 부분을 아래로 교체:

```html
            <!-- Blog Section -->
            <section id="blog" class="section-content mb-20">
                <p class="text-accent text-xs uppercase tracking-widest mb-2 font-semibold">Blog</p>
                <h2 class="text-text text-3xl font-bold mb-8">최근 글</h2>

                <div class="space-y-4">
                    <!-- Blog Post 1 -->
                    <article class="bg-surface rounded-xl border border-border p-6 hover:border-accent/30 transition-colors">
                        <div class="flex items-center gap-3 mb-3">
                            <span class="px-2 py-0.5 bg-accent/10 text-accent text-xs rounded">React</span>
                            <span class="text-muted text-xs">2026.04.15</span>
                        </div>
                        <h3 class="text-text font-semibold mb-2">React 19의 새로운 기능 정리</h3>
                        <p class="text-muted text-sm leading-relaxed">React 19에서 도입된 주요 변경사항과 새로운 훅, 그리고 마이그레이션 가이드를 정리합니다.</p>
                        <a href="#" class="inline-block mt-3 text-accent text-xs hover:text-accent-hover transition-colors">자세히 보기 →</a>
                    </article>

                    <!-- Blog Post 2 -->
                    <article class="bg-surface rounded-xl border border-border p-6 hover:border-accent/30 transition-colors">
                        <div class="flex items-center gap-3 mb-3">
                            <span class="px-2 py-0.5 bg-accent/10 text-accent text-xs rounded">DevOps</span>
                            <span class="text-muted text-xs">2026.04.01</span>
                        </div>
                        <h3 class="text-text font-semibold mb-2">Docker Compose로 로컬 개발 환경 구축하기</h3>
                        <p class="text-muted text-sm leading-relaxed">Docker Compose를 활용하여 개발 환경을 표준화하고 팀원 간 환경 차이로 인한 문제를 해결하는 방법.</p>
                        <a href="#" class="inline-block mt-3 text-accent text-xs hover:text-accent-hover transition-colors">자세히 보기 →</a>
                    </article>

                    <!-- Blog Post 3 -->
                    <article class="bg-surface rounded-xl border border-border p-6 hover:border-accent/30 transition-colors">
                        <div class="flex items-center gap-3 mb-3">
                            <span class="px-2 py-0.5 bg-accent/10 text-accent text-xs rounded">TypeScript</span>
                            <span class="text-muted text-xs">2026.03.20</span>
                        </div>
                        <h3 class="text-text font-semibold mb-2">TypeScript 고급 타입 패턴 5가지</h3>
                        <p class="text-muted text-sm leading-relaxed">실무에서 자주 사용하는 TypeScript 고급 타입 패턴과 활용 예시를 소개합니다.</p>
                        <a href="#" class="inline-block mt-3 text-accent text-xs hover:text-accent-hover transition-colors">자세히 보기 →</a>
                    </article>
                </div>
            </section>
```

- [ ] **Step 2: 브라우저에서 블로그 카드 리스트 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add Blog section with post cards"
```

---

### Task 6: Contact 섹션 (카카오톡 포함)

**Files:**
- Modify: `index.html` (contact section 교체)

- [ ] **Step 1: Contact 섹션 구현**

`index.html`에서 `<!-- Contact Section (placeholder) -->` 부분을 아래로 교체:

```html
            <!-- Contact Section -->
            <section id="contact" class="section-content mb-20">
                <p class="text-accent text-xs uppercase tracking-widest mb-2 font-semibold">Contact</p>
                <h2 class="text-text text-3xl font-bold mb-8">연락처</h2>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <!-- Info -->
                    <div>
                        <p class="text-muted text-sm leading-relaxed mb-6">프로젝트 협업이나 문의사항이 있으시면 편하게 연락해 주세요.</p>

                        <div class="space-y-3 mb-8">
                            <a href="mailto:your@email.com" class="flex items-center gap-3 text-muted hover:text-text transition-colors text-sm">
                                <span class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center border border-border">✉️</span>
                                your@email.com
                            </a>
                            <a href="https://github.com/yourusername" target="_blank" class="flex items-center gap-3 text-muted hover:text-text transition-colors text-sm">
                                <span class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center border border-border">GH</span>
                                github.com/yourusername
                            </a>
                            <a href="https://linkedin.com/in/yourusername" target="_blank" class="flex items-center gap-3 text-muted hover:text-text transition-colors text-sm">
                                <span class="w-8 h-8 bg-surface rounded-lg flex items-center justify-center border border-border">LI</span>
                                linkedin.com/in/yourusername
                            </a>
                        </div>

                        <!-- KakaoTalk Button -->
                        <a href="https://pf.kakao.com/_YOUR_CHANNEL_ID" target="_blank" class="inline-flex items-center gap-2 px-5 py-2.5 bg-[#FEE500] text-[#191919] text-sm font-semibold rounded-lg hover:brightness-110 transition">
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="#191919"><path d="M12 3C6.48 3 2 6.82 2 11.5c0 2.83 1.97 5.33 4.96 6.76l-1.26 3.78c-.11.33.28.6.57.4l4.37-2.94c.44.04.89.07 1.36.07 5.52 0 10-3.82 10-8.5S17.52 3 12 3z"/></svg>
                            카카오톡 상담하기
                        </a>
                    </div>

                    <!-- Contact Form -->
                    <form id="contact-form" class="space-y-4">
                        <div>
                            <label class="text-muted text-xs block mb-1.5">이름</label>
                            <input type="text" name="name" required class="w-full bg-surface border border-border rounded-lg px-4 py-2.5 text-text text-sm focus:outline-none focus:border-accent transition-colors placeholder-muted/50" placeholder="이름을 입력하세요">
                        </div>
                        <div>
                            <label class="text-muted text-xs block mb-1.5">이메일</label>
                            <input type="email" name="email" required class="w-full bg-surface border border-border rounded-lg px-4 py-2.5 text-text text-sm focus:outline-none focus:border-accent transition-colors placeholder-muted/50" placeholder="email@example.com">
                        </div>
                        <div>
                            <label class="text-muted text-xs block mb-1.5">메시지</label>
                            <textarea name="message" rows="4" required class="w-full bg-surface border border-border rounded-lg px-4 py-2.5 text-text text-sm focus:outline-none focus:border-accent transition-colors placeholder-muted/50 resize-none" placeholder="메시지를 입력하세요"></textarea>
                        </div>
                        <button type="submit" class="w-full px-6 py-2.5 bg-accent text-white text-sm rounded-lg hover:bg-accent-hover transition-colors">보내기</button>
                    </form>
                </div>
            </section>
```

- [ ] **Step 2: 브라우저에서 Contact 섹션과 카카오톡 버튼 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add Contact section with KakaoTalk button"
```

---

### Task 7: JavaScript 인터랙션

**Files:**
- Modify: `index.html` (`</body>` 앞에 `<script>` 추가)

- [ ] **Step 1: 네비게이션, Intersection Observer, 폼, 모바일 토글 스크립트 추가**

`index.html`에서 `</body>` 바로 앞에 아래 스크립트 추가:

```html
    <script>
        // Mobile menu toggle
        const menuToggle = document.getElementById('menu-toggle');
        const sidebar = document.getElementById('sidebar');

        menuToggle.addEventListener('click', () => {
            sidebar.classList.toggle('open');
        });

        // Close sidebar on nav click (mobile)
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', () => {
                if (window.innerWidth < 768) {
                    sidebar.classList.remove('open');
                }
            });
        });

        // Close sidebar on outside click (mobile)
        document.addEventListener('click', (e) => {
            if (window.innerWidth < 768 && !sidebar.contains(e.target) && !menuToggle.contains(e.target)) {
                sidebar.classList.remove('open');
            }
        });

        // Active nav link on scroll (Intersection Observer)
        const sections = document.querySelectorAll('.section-content');
        const navLinks = document.querySelectorAll('.nav-link');

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const id = entry.target.getAttribute('id');
                    navLinks.forEach(link => {
                        link.classList.remove('active', 'bg-accent/10', 'text-text');
                        link.classList.add('text-muted');
                    });
                    const activeLink = document.querySelector(`.nav-link[href="#${id}"]`);
                    if (activeLink) {
                        activeLink.classList.add('active', 'bg-accent/10', 'text-text');
                        activeLink.classList.remove('text-muted');
                    }
                }
            });
        }, { threshold: 0.3 });

        sections.forEach(section => observer.observe(section));

        // Contact form → mailto
        document.getElementById('contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const form = e.target;
            const name = form.name.value;
            const email = form.email.value;
            const message = form.message.value;
            const subject = encodeURIComponent(`포트폴리오 문의 - ${name}`);
            const body = encodeURIComponent(`이름: ${name}\n이메일: ${email}\n\n${message}`);
            window.location.href = `mailto:your@email.com?subject=${subject}&body=${body}`;
        });
    </script>
```

- [ ] **Step 2: 사이드바 네비게이션 클릭 시 스크롤, 활성 메뉴 자동 변경, 폼 제출 동작 확인**

- [ ] **Step 3: 커밋**

```bash
git add index.html
git commit -m "feat: add navigation, scroll observer, and form scripts"
```

---

### Task 8: 최종 검증 및 push

**Files:**
- Modify: `index.html`

- [ ] **Step 1: 브라우저에서 전체 기능 확인**

체크리스트:
- 사이드바 네비게이션 클릭 → 해당 섹션으로 스크롤
- 스크롤 시 활성 메뉴 자동 변경
- 프로젝트 카드 호버 애니메이션
- 카카오톡 버튼 링크 동작
- 폼 제출 → mailto 동작
- 모바일 뷰 (768px 이하) 햄버거 메뉴 토글
- 모든 섹션 렌더링 정상

- [ ] **Step 2: 원격 저장소에 push**

```bash
git push origin master
```
