<script>
  import { onMount } from 'svelte';
  import perfilImg from './assets/perfil.jpeg';
  
  let expandedProject = null;
  let isVisible = false;
  let imageViewer = false;
  let currentTheme = 'cyber-oceanic';
  let showThemeSelector = false;

  const themes = {
    'cyber-oceanic': {
      name: 'Cyber Oceanic',
      primary: 'cyan',
      secondary: 'blue',
      gradient: 'from-cyan-600/20 to-blue-600/20',
      orb1: 'bg-cyan-500',
      orb2: 'bg-blue-500',
      orb3: 'bg-purple-500',
      text: 'text-cyan-400',
      textSecondary: 'text-blue-400',
      border: 'border-cyan-500/50',
      hoverBorder: 'hover:border-cyan-500/50',
      cardBg: 'bg-slate-800/50',
      cardBorder: 'border-slate-700/50',
      buttonBg: 'bg-slate-800/80',
      buttonBorder: 'border-slate-700/50',
      hoverButtonBg: 'hover:bg-slate-700/50',
      iconBg: 'bg-slate-900',
      baseBg: 'from-slate-950 via-slate-900 to-slate-950',
      baseText: 'text-gray-100',
      secondaryText: 'text-gray-300',
      tertiaryText: 'text-gray-400'
    },
    'sunset-coder': {
      name: 'Sunset Coder',
      primary: 'orange',
      secondary: 'pink',
      gradient: 'from-orange-600/20 to-pink-600/20',
      orb1: 'bg-orange-500',
      orb2: 'bg-pink-500',
      orb3: 'bg-red-500',
      text: 'text-orange-400',
      textSecondary: 'text-pink-400',
      border: 'border-orange-500/50',
      hoverBorder: 'hover:border-orange-500/50',
      cardBg: 'bg-slate-800/50',
      cardBorder: 'border-slate-700/50',
      buttonBg: 'bg-slate-800/80',
      buttonBorder: 'border-slate-700/50',
      hoverButtonBg: 'hover:bg-slate-700/50',
      iconBg: 'bg-slate-900',
      baseBg: 'from-slate-950 via-slate-900 to-slate-950',
      baseText: 'text-gray-100',
      secondaryText: 'text-gray-300',
      tertiaryText: 'text-gray-400'
    },
    'forest-tech': {
      name: 'Forest Tech',
      primary: 'emerald',
      secondary: 'teal',
      gradient: 'from-emerald-600/20 to-teal-600/20',
      orb1: 'bg-emerald-500',
      orb2: 'bg-teal-500',
      orb3: 'bg-green-500',
      text: 'text-emerald-400',
      textSecondary: 'text-teal-400',
      border: 'border-emerald-500/50',
      hoverBorder: 'hover:border-emerald-500/50',
      cardBg: 'bg-slate-800/50',
      cardBorder: 'border-slate-700/50',
      buttonBg: 'bg-slate-800/80',
      buttonBorder: 'border-slate-700/50',
      hoverButtonBg: 'hover:bg-slate-700/50',
      iconBg: 'bg-slate-900',
      baseBg: 'from-slate-950 via-slate-900 to-slate-950',
      baseText: 'text-gray-100',
      secondaryText: 'text-gray-300',
      tertiaryText: 'text-gray-400'
    },
    'purple-dream': {
      name: 'Purple Dream',
      primary: 'purple',
      secondary: 'indigo',
      gradient: 'from-purple-600/20 to-indigo-600/20',
      orb1: 'bg-purple-500',
      orb2: 'bg-indigo-500',
      orb3: 'bg-violet-500',
      text: 'text-purple-400',
      textSecondary: 'text-indigo-400',
      border: 'border-purple-500/50',
      hoverBorder: 'hover:border-purple-500/50',
      cardBg: 'bg-slate-800/50',
      cardBorder: 'border-slate-700/50',
      buttonBg: 'bg-slate-800/80',
      buttonBorder: 'border-slate-700/50',
      hoverButtonBg: 'hover:bg-slate-700/50',
      iconBg: 'bg-slate-900',
      baseBg: 'from-slate-950 via-slate-900 to-slate-950',
      baseText: 'text-gray-100',
      secondaryText: 'text-gray-300',
      tertiaryText: 'text-gray-400'
    },
    'monochrome': {
      name: 'Monocromático',
      primary: 'gray',
      secondary: 'slate',
      gradient: 'from-gray-600/20 to-slate-600/20',
      orb1: 'bg-gray-500',
      orb2: 'bg-slate-500',
      orb3: 'bg-zinc-500',
      text: 'text-gray-300',
      textSecondary: 'text-slate-400',
      border: 'border-gray-500/50',
      hoverBorder: 'hover:border-gray-500/50',
      cardBg: 'bg-slate-800/50',
      cardBorder: 'border-slate-700/50',
      buttonBg: 'bg-slate-800/80',
      buttonBorder: 'border-slate-700/50',
      hoverButtonBg: 'hover:bg-slate-700/50',
      iconBg: 'bg-slate-900',
      baseBg: 'from-slate-950 via-slate-900 to-slate-950',
      baseText: 'text-gray-100',
      secondaryText: 'text-gray-300',
      tertiaryText: 'text-gray-400'
    },
    'light-mode': {
      name: 'Modo Claro',
      primary: 'slate',
      secondary: 'gray',
      gradient: 'from-blue-50/30 to-slate-50/30',
      orb1: 'bg-blue-200',
      orb2: 'bg-slate-200',
      orb3: 'bg-gray-200',
      text: 'text-blue-600',
      textSecondary: 'text-slate-700',
      border: 'border-slate-200',
      hoverBorder: 'hover:border-blue-400',
      cardBg: 'bg-white',
      cardBorder: 'border-slate-200',
      buttonBg: 'bg-white',
      buttonBorder: 'border-slate-200',
      hoverButtonBg: 'hover:bg-slate-50',
      iconBg: 'bg-slate-100',
      baseBg: 'from-white via-white to-slate-50',
      baseText: 'text-gray-900',
      secondaryText: 'text-gray-700',
      tertiaryText: 'text-gray-600'
    },
    'dark-mode': {
      name: 'Modo Oscuro',
      primary: 'white',
      secondary: 'gray',
      gradient: 'from-black/20 to-gray-900/20',
      orb1: 'bg-white',
      orb2: 'bg-gray-400',
      orb3: 'bg-gray-500',
      text: 'text-white',
      textSecondary: 'text-gray-200',
      border: 'border-white/20',
      hoverBorder: 'hover:border-white/40',
      cardBg: 'bg-black/50',
      cardBorder: 'border-white/10',
      buttonBg: 'bg-black/80',
      buttonBorder: 'border-white/20',
      hoverButtonBg: 'hover:bg-gray-900/50',
      iconBg: 'bg-black',
      baseBg: 'from-black via-black to-gray-950',
      baseText: 'text-white',
      secondaryText: 'text-gray-200',
      tertiaryText: 'text-gray-400'
    }
  };

  $: theme = themes[currentTheme];

  onMount(() => {
    isVisible = true;
    const savedTheme = localStorage.getItem('cv-theme');
    if (savedTheme && themes[savedTheme]) {
      currentTheme = savedTheme;
    }
  });

  function changeTheme(newTheme) {
    currentTheme = newTheme;
    localStorage.setItem('cv-theme', newTheme);
    showThemeSelector = false;
  }

  const skills = [
    { 
      name: 'Python', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg',
      color: 'from-blue-400 to-yellow-400'
    },
    { 
      name: 'FastAPI', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/fastapi/fastapi-original.svg',
      color: 'from-teal-400 to-green-400'
    },
    { 
      name: 'Svelte', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/svelte/svelte-original.svg',
      color: 'from-orange-400 to-red-400'
    },
    { 
      name: 'Docker', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg',
      color: 'from-blue-400 to-cyan-400'
    },
    { 
      name: 'JavaScript', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg',
      color: 'from-yellow-400 to-yellow-500'
    },
    { 
      name: 'HTML & CSS', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg',
      color: 'from-orange-500 to-pink-500'
    },
    { 
      name: 'Git / GitHub', 
      icon: 'data:image/svg+xml,%3Csvg viewBox="0 0 128 128" xmlns="http://www.w3.org/2000/svg"%3E%3Cpath fill="%23FFFFFF" d="M64 5.103c-33.347 0-60.388 27.035-60.388 60.388 0 26.682 17.303 49.317 41.297 57.303 3.017.56 4.125-1.31 4.125-2.905 0-1.44-.056-6.197-.082-11.243-16.8 3.653-20.345-7.125-20.345-7.125-2.747-6.98-6.705-8.836-6.705-8.836-5.48-3.748.413-3.67.413-3.67 6.063.425 9.257 6.223 9.257 6.223 5.386 9.23 14.127 6.562 17.573 5.02.542-3.903 2.107-6.568 3.834-8.076-13.413-1.525-27.514-6.704-27.514-29.843 0-6.593 2.36-11.98 6.223-16.21-.628-1.52-2.695-7.662.584-15.98 0 0 5.07-1.623 16.61 6.19C53.7 35 58.867 34.327 64 34.304c5.13.023 10.3.694 15.127 2.033 11.526-7.813 16.59-6.19 16.59-6.19 3.287 8.317 1.22 14.46.593 15.98 3.872 4.23 6.215 9.617 6.215 16.21 0 23.194-14.127 28.3-27.574 29.796 2.167 1.874 4.097 5.55 4.097 11.183 0 8.08-.07 14.583-.07 16.572 0 1.607 1.088 3.49 4.148 2.897 23.98-7.994 41.263-30.622 41.263-57.294C124.388 32.14 97.35 5.104 64 5.104z"/%3E%3C/svg%3E',
      color: 'from-gray-400 to-gray-600'
    },
    { 
      name: 'Linux', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg',
      color: 'from-yellow-300 to-orange-400'
    },
    { 
      name: 'SQL', 
      icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg',
      color: 'from-blue-300 to-blue-500'
    }
  ];

  const projects = [
    {
      id: 1,
      title: 'Gestor de Proyectos',
      tech: 'Svelte, FastAPI, Docker',
      description: 'Aplicación web para administrar proyectos y tareas. Backend con FastAPI, frontend con Svelte y contenedorización con Docker. Diseñado para ser modular, rápido y fácil de desplegar.',
      highlights: ['Arquitectura modular', 'API RESTful', 'Contenedorización completa'],
      github: 'https://github.com/tu-usuario/gestor-proyectos' // Cambia esto por tu URL real
    },
    {
      id: 2,
      title: 'Skamina',
      tech: 'Svelte, FastAPI, Keycloak, Docker',
      description: 'Sistema escolar en desarrollo con funciones como gestión de alumnos, profesores y tareas. Desarrollado con Svelte y FastAPI, utilizando Keycloak para la gestión de usuarios y autenticación. Se ejecuta mediante Docker para facilitar el trabajo en equipo y el despliegue.',
      highlights: ['Gestión de usuarios con Keycloak', 'Sistema de autenticación', 'Trabajo colaborativo'],
      github: 'https://github.com/tu-usuario/skamina' // Cambia esto por tu URL real
    }
  ];

  function toggleProject(projectId) {
    expandedProject = expandedProject === projectId ? null : projectId;
  }

  function handleKeyPress(event, projectId) {
    if (event.key === 'Enter' || event.key === ' ') {
      event.preventDefault();
      toggleProject(projectId);
    }
  }
</script>

<div class="snap-y snap-proximity h-screen overflow-y-scroll scroll-smooth {theme.baseText} relative bg-gradient-to-br {theme.baseBg} bg-animated-{theme.primary}">
  <!-- Theme Selector Button -->
  <button
    on:click={() => showThemeSelector = !showThemeSelector}
    class="fixed top-4 right-4 z-50 p-3 {theme.buttonBg} backdrop-blur-sm rounded-full border {theme.buttonBorder} hover:border-{theme.primary}-500/50 transition-all duration-300 hover:scale-110 shadow-lg"
    title="Cambiar tema"
  >
    <svg class="w-6 h-6 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01" />
    </svg>
  </button>

  <!-- Theme Selector Panel -->
  {#if showThemeSelector}
    <button
      type="button"
      class="fixed inset-0 z-40 bg-transparent"
      aria-label="Cerrar selector de tema"
      on:click={() => showThemeSelector = false}
      on:keydown={(e) => (e.key === 'Enter' || e.key === ' ') && (showThemeSelector = false)}
      tabIndex="0"
      style="all:unset;position:fixed;inset:0;z-index:40;cursor:pointer;"
    ></button>
    <div
      class="fixed top-20 right-4 z-50 {theme.buttonBg} backdrop-blur-sm rounded-xl border {theme.buttonBorder} p-4 shadow-2xl animate-fadeIn"
    >
      <h3 class="text-lg font-bold {theme.baseText} mb-3">Elegir Tema</h3>
      <div class="flex flex-col gap-2">
        {#each Object.entries(themes) as [key, themeOption]}
          <button
            class="flex items-center gap-2 px-3 py-2 rounded-lg border {themeOption.border} hover:{themeOption.hoverBorder} transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-{themeOption.primary}-400"
            on:click={() => changeTheme(key)}
          >
            <span class="w-4 h-4 rounded-full block {themeOption.orb1} border-2 {themeOption.border}"></span>
            <span class="{themeOption.text} font-medium">{themeOption.name}</span>
          </button>
        {/each}
      </div>
    </div>
  {/if}

  <!-- Animated Background Particles -->
  <div class="fixed inset-0 pointer-events-none overflow-hidden">
    <div class="particle particle-1"></div>
    <div class="particle particle-2"></div>
    <div class="particle particle-3"></div>
    <div class="particle particle-4"></div>
    <div class="particle particle-5"></div>
  </div>
  
  <!-- Hero Section -->
  <section class="snap-start relative overflow-hidden">
    <div class="absolute inset-0 bg-gradient-to-r {theme.gradient} animate-gradient"></div>
    <div class="absolute inset-0 opacity-30">
      <div class="absolute top-10 left-10 md:top-20 md:left-20 w-40 h-40 md:w-72 md:h-72 {theme.orb1} rounded-full filter blur-3xl animate-float"></div>
      <div class="absolute bottom-10 right-10 md:bottom-20 md:right-20 w-48 h-48 md:w-96 md:h-96 {theme.orb2} rounded-full filter blur-3xl animate-float-delay"></div>
      <div class="absolute top-1/2 left-1/2 w-32 h-32 md:w-64 md:h-64 {theme.orb3} rounded-full filter blur-3xl animate-float-slow"></div>
    </div>
    <div class="relative max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-12">
      <div class="text-center">
        <div class="inline-block mb-3 md:mb-4">
          <button 
            on:click={() => imageViewer = true}
            class="w-32 h-32 md:w-40 md:h-40 rounded-full overflow-hidden border-4 border-{theme.primary}-500 shadow-2xl shadow-{theme.primary}-500/50 cursor-pointer hover:scale-105 transition-transform duration-300 hover:border-{theme.primary}-400"
          >
            <img 
              src={perfilImg} 
              alt="Abel Santiago Galindo de la Cruz"
              class="w-full h-full object-cover"
            />
          </button>
        </div>
        <h1 class="text-2xl md:text-4xl lg:text-5xl font-bold mb-2 md:mb-3 {theme.baseText} leading-tight">
          Abel Santiago Galindo de la Cruz
        </h1>
        <p class="text-base md:text-lg lg:text-xl {theme.secondaryText} mb-4 md:mb-6">
          Desarrollador Full Stack
        </p>
        <div class="flex flex-col md:flex-row flex-wrap justify-center gap-3 md:gap-4 {theme.secondaryText} text-sm md:text-base">
          <div class="flex items-center gap-2 {theme.cardBg} px-3 md:px-4 py-2 rounded-lg backdrop-blur-sm {theme.hoverButtonBg} transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            <span>636 124 1070</span>
          </div>
          <div class="flex items-center gap-2 {theme.cardBg} px-4 py-2 rounded-lg backdrop-blur-sm {theme.hoverButtonBg} transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
            <span>sxantiglndo@gmail.com</span>
          </div>
          <a 
            href="https://github.com/Galindo97" 
            target="_blank" 
            rel="noopener noreferrer"
            class="flex items-center gap-2 {theme.cardBg} px-4 py-2 rounded-lg backdrop-blur-sm {theme.hoverButtonBg} transition-all duration-300 hover:scale-105"
          >
            <svg class="w-5 h-5 {theme.text}" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <span>GitHub</span>
          </a>
          <div class="flex items-center gap-2 {theme.cardBg} px-4 py-2 rounded-lg backdrop-blur-sm {theme.hoverButtonBg} transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
            </svg>
            <span>Inglés: Básico–Intermedio</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Profile & Skills Section -->
  <section class="snap-start overflow-hidden">
    <div class="max-w-7xl mx-auto px-4 md:px-6 py-6 md:py-12">
      <!-- Mobile/Tablet: Stack vertically -->
      <div class="flex flex-col lg:hidden gap-6">
        <!-- Profile -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-2xl p-6 md:p-8 shadow-2xl border {theme.cardBorder} {theme.hoverBorder} transition-all duration-300">
          <h2 class="text-2xl md:text-3xl font-bold mb-4 md:mb-6 flex items-center gap-3">
            <svg class="w-6 h-6 md:w-8 md:h-8 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
            </svg>
            Perfil Profesional
          </h2>
          <p class="text-base md:text-lg {theme.secondaryText} leading-relaxed">
            Desarrollador con habilidades en <span class="text-cyan-400 font-semibold">Python</span>, <span class="text-cyan-400 font-semibold">FastAPI</span>, <span class="text-cyan-400 font-semibold">Svelte</span> y <span class="text-cyan-400 font-semibold">Docker</span>. 
            Me gusta crear <span class="text-blue-300 font-medium">soluciones eficientes</span> y trabajar con <span class="text-blue-300 font-medium">tecnologías modernas</span>. Busco seguir 
            creciendo en el ámbito laboral, como personalmente. Al igual, busco integrarme a un equipo 
            donde pueda aportar valor real mientras continúo desarrollando mis habilidades en <span class="text-cyan-400 font-semibold">software development</span>.
          </p>
        </div>
        
        <!-- Skills Mobile -->
        <div class="relative w-full h-[500px] sm:h-[580px] md:h-[650px] flex items-center justify-center overflow-hidden">
          {#each skills as skill, index}
            <div class="absolute skill-item skill-item-{index}">
              <div class="group cursor-pointer transform transition-all duration-300 hover:scale-125">
                <div class="flex flex-col items-center gap-1 md:gap-2">
                  <div class="w-12 h-12 sm:w-14 sm:h-14 md:w-16 md:h-16 rounded-full bg-gradient-to-br {skill.color} p-1 shadow-xl hover:shadow-2xl transition-shadow duration-300">
                    <div class="w-full h-full rounded-full {theme.iconBg} flex items-center justify-center p-3">
                      <img 
                        src={skill.icon} 
                        alt={skill.name}
                        class="w-full h-full object-contain filter drop-shadow-lg"
                      />
                    </div>
                  </div>
                  <span class="font-semibold text-xs md:text-sm {theme.secondaryText} group-hover:{theme.baseText} transition-colors duration-300 whitespace-nowrap">
                    {skill.name}
                  </span>
                </div>
              </div>
            </div>
          {/each}
          <div class="absolute flex flex-col items-center justify-center">
            <div class="absolute w-32 h-32 md:w-40 md:h-40 rounded-full bg-gradient-to-br from-cyan-500/30 to-blue-500/30 blur-3xl animate-pulse"></div>
            <div class="relative flex flex-col items-center gap-2 md:gap-3">
              <svg class="w-8 h-8 md:w-12 md:h-12 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
              </svg>
              <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-center">
                <span class="block {theme.text}">Habilidades</span>
                <span class="block {theme.textSecondary}">Técnicas</span>
              </h2>
            </div>
          </div>
        </div>
      </div>

      <!-- Desktop: Side by side -->
      <div class="hidden lg:flex gap-8 xl:gap-16 2xl:gap-24">
        <!-- Profile Left -->
        <div class="w-[42%] xl:w-[45%] {theme.cardBg} backdrop-blur-sm rounded-2xl p-6 xl:p-8 shadow-2xl border {theme.cardBorder} {theme.hoverBorder} transition-all duration-300 flex flex-col justify-center">
          <h2 class="text-3xl font-bold mb-6 flex items-center gap-3">
            <svg class="w-8 h-8 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
            </svg>
            Perfil Profesional
          </h2>
          <p class="text-lg {theme.secondaryText} leading-relaxed">
            Desarrollador con habilidades en <span class="{theme.text} font-semibold">Python</span>, <span class="{theme.text} font-semibold">FastAPI</span>, <span class="{theme.text} font-semibold">Svelte</span> y <span class="{theme.text} font-semibold">Docker</span>. 
            Me gusta crear <span class="text-{theme.primary}-300 font-medium">soluciones eficientes</span> y trabajar con <span class="text-{theme.primary}-300 font-medium">tecnologías modernas</span>. Busco seguir 
            creciendo en el ámbito laboral, como personalmente. Al igual, busco integrarme a un equipo 
            donde pueda aportar valor real mientras continúo desarrollando mis habilidades en <span class="{theme.text} font-semibold">software development</span>.
          </p>
        </div>

        <!-- Skills Right -->
        <div class="w-[58%] xl:w-[55%] relative h-[600px] xl:h-[650px] flex items-center justify-center overflow-visible">
          {#each skills as skill, index}
            <div class="absolute skill-item skill-item-{index}">
              <div class="group cursor-pointer transform transition-all duration-300 hover:scale-125">
                <div class="flex flex-col items-center gap-2">
                  <div class="w-16 h-16 xl:w-20 xl:h-20 rounded-full bg-gradient-to-br {skill.color} p-1 shadow-xl hover:shadow-2xl transition-shadow duration-300">
                    <div class="w-full h-full rounded-full {theme.iconBg} flex items-center justify-center p-3">
                      <img 
                        src={skill.icon} 
                        alt={skill.name}
                        class="w-full h-full object-contain filter drop-shadow-lg"
                      />
                    </div>
                  </div>
                  <span class="font-semibold text-sm {theme.secondaryText} group-hover:{theme.baseText} transition-colors duration-300 whitespace-nowrap">
                    {skill.name}
                  </span>
                </div>
              </div>
            </div>
          {/each}
          <div class="absolute flex flex-col items-center justify-center">
            <div class="absolute w-40 h-40 rounded-full bg-gradient-to-br from-cyan-500/30 to-blue-500/30 blur-3xl animate-pulse"></div>
            <div class="relative flex flex-col items-center gap-3">
              <svg class="w-12 h-12 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
              </svg>
              <h2 class="text-3xl font-bold text-center">
                <span class="block {theme.text}">Habilidades</span>
                <span class="block {theme.textSecondary}">Técnicas</span>
              </h2>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Soft Skills Section -->
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-6 md:py-12">
      <h2 class="text-2xl md:text-3xl font-bold mb-6 md:mb-8 flex items-center gap-3">
        <svg class="w-6 h-6 md:w-8 md:h-8 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
        </svg>
        Habilidades Interpersonales
      </h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
        <!-- Comunicación -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} {theme.hoverBorder} transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-{theme.primary}-500/20 to-{theme.secondary}-500/20 rounded-lg group-hover:from-{theme.primary}-500/30 group-hover:to-{theme.secondary}-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Comunicación Efectiva</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Capacidad para expresar ideas claramente y escuchar activamente</p>
            </div>
          </div>
        </div>

        <!-- Trabajo en Equipo -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} hover:border-blue-500/50 transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-blue-500/20 to-purple-500/20 rounded-lg group-hover:from-blue-500/30 group-hover:to-purple-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Trabajo en Equipo</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Colaboración efectiva y adaptabilidad en entornos de equipo</p>
            </div>
          </div>
        </div>

        <!-- Resolución de Problemas -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} hover:border-purple-500/50 transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-purple-500/20 to-pink-500/20 rounded-lg group-hover:from-purple-500/30 group-hover:to-pink-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Resolución de Problemas</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Pensamiento analítico y búsqueda de soluciones creativas</p>
            </div>
          </div>
        </div>

        <!-- Aprendizaje Continuo -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} hover:border-green-500/50 transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-green-500/20 to-emerald-500/20 rounded-lg group-hover:from-green-500/30 group-hover:to-emerald-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Aprendizaje Continuo</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Actitud proactiva para adquirir nuevos conocimientos</p>
            </div>
          </div>
        </div>

        <!-- Adaptabilidad -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} hover:border-yellow-500/50 transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-yellow-500/20 to-orange-500/20 rounded-lg group-hover:from-yellow-500/30 group-hover:to-orange-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 text-yellow-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Adaptabilidad</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Flexibilidad ante cambios y nuevos desafíos</p>
            </div>
          </div>
        </div>

        <!-- Organización -->
        <div class="{theme.cardBg} backdrop-blur-sm rounded-xl p-4 md:p-6 shadow-xl border {theme.cardBorder} hover:border-indigo-500/50 transition-all duration-300 hover:scale-105 group">
          <div class="flex items-start gap-3 md:gap-4">
            <div class="p-2 md:p-3 bg-gradient-to-br from-indigo-500/20 to-blue-500/20 rounded-lg group-hover:from-indigo-500/30 group-hover:to-blue-500/30 transition-all duration-300">
              <svg class="w-6 h-6 md:w-8 md:h-8 text-indigo-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01" />
              </svg>
            </div>
            <div class="flex-1">
              <h3 class="text-lg md:text-xl font-bold {theme.baseText} mb-2">Organización</h3>
              <p class="text-sm md:text-base {theme.tertiaryText}">Gestión eficiente del tiempo y priorización de tareas</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Projects Section -->
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-6 md:py-12">
    <h2 class="text-2xl md:text-3xl font-bold mb-4 md:mb-6 flex items-center gap-3">
      <svg class="w-6 h-6 md:w-8 md:h-8 {theme.text}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
      </svg>
      Proyectos Destacados
    </h2>
    <div class="space-y-4 md:space-y-6">
      {#each projects as project}
        <div class="{theme.cardBg} backdrop-blur-sm rounded-2xl shadow-2xl border {theme.cardBorder} {theme.hoverBorder} transition-all duration-300 overflow-hidden hover:shadow-{theme.primary}-500/20">
          <div class="p-4 md:p-6">
            <div class="flex justify-between items-start">
              <div class="flex-1">
                <div class="flex items-center gap-2 md:gap-3 mb-2">
                  <h3 class="text-xl md:text-2xl font-bold {theme.text}">{project.title}</h3>
                  <a 
                    href={project.github} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    class="p-1 md:p-1.5 bg-slate-700/50 hover:bg-slate-600 rounded-lg transition-all duration-300 hover:scale-110"
                    title="Ver en GitHub"
                  >
                    <svg class="w-4 h-4 md:w-5 md:h-5 {theme.baseText}" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                    </svg>
                  </a>
                </div>
                <p class="text-sm md:text-base {theme.baseText} font-medium mb-1">Tecnologías:</p>
                <p class="text-sm md:text-base {theme.textSecondary} font-medium mb-2 md:mb-3">{project.tech}</p>
              </div>
            </div>
            <div class="mt-3 md:mt-4 pt-3 md:pt-4 border-t border-slate-700">
              <p class="text-sm md:text-base {theme.secondaryText} leading-relaxed mb-3 md:mb-4">{project.description}</p>
              <div class="flex flex-wrap gap-2">
                {#each project.highlights as highlight}
                  <span class="px-2 md:px-3 py-1 bg-slate-700/50 rounded-full text-xs md:text-sm text-{theme.primary}-300 border border-{theme.primary}-500/30 hover:bg-slate-700 hover:border-{theme.primary}-400 transition-all duration-300">
                    {highlight}
                  </span>
                {/each}
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>
    </div>
  </section>

  <!-- Footer -->
  <section class="snap-start pb-safe">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-16 pb-20 md:pb-16 text-center">
      <div class="bg-gradient-to-r {theme.gradient} rounded-2xl p-6 md:p-8 mb-8 backdrop-blur-sm border border-slate-700/50 {theme.hoverBorder} transition-all duration-300">
        <h3 class="text-xl md:text-2xl font-bold mb-3 md:mb-4">¿Interesado en trabajar juntos?</h3>
      <p class="text-sm md:text-base {theme.secondaryText} mb-4 md:mb-6">Estoy disponible para nuevas oportunidades y colaboraciones</p>
      <div class="flex justify-center gap-4">
          <a 
          href="tel:6361241070"
          class="px-5 md:px-6 py-2.5 md:py-3 bg-{theme.primary}-600 hover:bg-{theme.primary}-700 rounded-lg text-sm md:text-base font-semibold transition-all duration-300 inline-flex items-center gap-2 hover:scale-105 hover:shadow-lg hover:shadow-{theme.primary}-500/50"
        >
          <svg class="w-4 h-4 md:w-5 md:h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
          </svg>
          Contactar
        </a>
      </div>
    </div>
    </div>
  </section>
</div>

<!-- Instagram-style Image Viewer -->
{#if imageViewer}
  <div 
    class="fixed inset-0 z-50 flex items-center justify-center bg-black/95 backdrop-blur-sm animate-fadeIn"
    on:click={() => imageViewer = false}
    on:keydown={(e) => e.key === 'Escape' && (imageViewer = false)}
    role="button"
    tabindex="0"
  >
    <button 
      class="absolute top-4 right-4 text-white hover:text-cyan-400 transition-colors duration-300 z-10"
      on:click={() => imageViewer = false}
      aria-label="Cerrar"
    >
      <svg class="w-8 h-8 md:w-10 md:h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>
    <div 
      class="relative max-w-4xl max-h-[90vh] p-4"
      on:click|stopPropagation
      on:keydown|stopPropagation
      role="button"
      tabindex="0"
    >
      <img 
        src={perfilImg} 
        alt="Abel Santiago Galindo de la Cruz"
        class="max-w-full max-h-[85vh] object-contain rounded-lg shadow-2xl animate-scaleIn"
      />
      <div class="text-center mt-4">
        <p class="text-white text-lg md:text-xl font-semibold">Abel Santiago Galindo de la Cruz</p>
        <p class="{theme.tertiaryText} text-sm md:text-base">Desarrollador Full Stack</p>
      </div>
    </div>
  </div>
{/if}

<style>
  /* Safe area para navegadores móviles */
  .pb-safe {
    padding-bottom: env(safe-area-inset-bottom, 1rem);
  }

  @supports (padding: max(0px)) {
    .pb-safe {
      padding-bottom: max(env(safe-area-inset-bottom), 1rem);
    }
  }

  /* Fondos animados por tema */
  .bg-animated-cyan {
    background: linear-gradient(
      135deg,
      #0c1445 0%,
      #0f172a 15%,
      #155e75 30%,
      #0f172a 45%,
      #164e63 60%,
      #0f172a 75%,
      #155e75 90%,
      #0c1445 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-orange {
    background: linear-gradient(
      135deg,
      #451a03 0%,
      #0f172a 15%,
      #7c2d12 30%,
      #0f172a 45%,
      #831843 60%,
      #0f172a 75%,
      #7c2d12 90%,
      #451a03 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-emerald {
    background: linear-gradient(
      135deg,
      #052e16 0%,
      #0f172a 15%,
      #065f46 30%,
      #0f172a 45%,
      #115e59 60%,
      #0f172a 75%,
      #065f46 90%,
      #052e16 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-purple {
    background: linear-gradient(
      135deg,
      #2e1065 0%,
      #0f172a 15%,
      #6b21a8 30%,
      #0f172a 45%,
      #4c1d95 60%,
      #0f172a 75%,
      #6b21a8 90%,
      #2e1065 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-gray {
    background: linear-gradient(
      135deg,
      #18181b 0%,
      #0f172a 15%,
      #374151 30%,
      #0f172a 45%,
      #475569 60%,
      #0f172a 75%,
      #374151 90%,
      #18181b 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-slate {
    background: linear-gradient(
      135deg,
      #ffffff 0%,
      #f8fafc 15%,
      #f1f5f9 30%,
      #f8fafc 45%,
      #ffffff 60%,
      #f8fafc 75%,
      #f1f5f9 90%,
      #ffffff 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  .bg-animated-white {
    background: linear-gradient(
      135deg,
      #000000 0%,
      #0a0a0a 15%,
      #1a1a1a 30%,
      #0a0a0a 45%,
      #0f0f0f 60%,
      #0a0a0a 75%,
      #1a1a1a 90%,
      #000000 100%
    );
    background-size: 400% 400%;
    animation: bgShift 45s ease-in-out infinite;
  }

  @keyframes bgShift {
    0% {
      background-position: 0% 50%;
    }
    25% {
      background-position: 50% 75%;
    }
    50% {
      background-position: 100% 50%;
    }
    75% {
      background-position: 50% 25%;
    }
    100% {
      background-position: 0% 50%;
    }
  }

  @keyframes float {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-10px); }
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  @keyframes scaleIn {
    from { 
      opacity: 0;
      transform: scale(0.9);
    }
    to { 
      opacity: 1;
      transform: scale(1);
    }
  }

  .animate-fadeIn {
    animation: fadeIn 0.2s ease-out;
  }

  .animate-scaleIn {
    animation: scaleIn 0.3s ease-out;
  }

  @keyframes gradient {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  @keyframes floatOrb {
    0%, 100% { 
      transform: translate(0, 0) scale(1);
    }
    33% { 
      transform: translate(30px, -30px) scale(1.1);
    }
    66% { 
      transform: translate(-20px, 20px) scale(0.9);
    }
  }

  @keyframes particle {
    0% {
      transform: translateY(0) translateX(0) scale(0);
      opacity: 0;
    }
    10% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      transform: translateY(-100vh) translateX(50px) scale(1);
      opacity: 0;
    }
  }

  .animate-gradient {
    background-size: 200% 200%;
    animation: gradient 15s ease infinite;
  }

  .animate-float {
    animation: floatOrb 8s ease-in-out infinite;
  }

  .animate-float-delay {
    animation: floatOrb 10s ease-in-out infinite;
    animation-delay: -3s;
  }

  .animate-float-slow {
    animation: floatOrb 12s ease-in-out infinite;
    animation-delay: -6s;
  }

  .particle {
    position: absolute;
    width: 4px;
    height: 4px;
    background: rgba(6, 182, 212, 0.6);
    border-radius: 50%;
    box-shadow: 0 0 10px rgba(6, 182, 212, 0.8);
  }

  .particle-1 {
    left: 10%;
    animation: particle 15s linear infinite;
  }

  .particle-2 {
    left: 30%;
    animation: particle 18s linear infinite;
    animation-delay: -5s;
    background: rgba(59, 130, 246, 0.6);
    box-shadow: 0 0 10px rgba(59, 130, 246, 0.8);
  }

  .particle-3 {
    left: 50%;
    animation: particle 20s linear infinite;
    animation-delay: -10s;
  }

  .particle-4 {
    left: 70%;
    animation: particle 16s linear infinite;
    animation-delay: -7s;
    background: rgba(168, 85, 247, 0.6);
    box-shadow: 0 0 10px rgba(168, 85, 247, 0.8);
  }

  .particle-5 {
    left: 90%;
    animation: particle 22s linear infinite;
    animation-delay: -12s;
    background: rgba(6, 182, 212, 0.6);
    box-shadow: 0 0 10px rgba(6, 182, 212, 0.8);
  }

  .pulse-delay {
    animation-delay: 1s;
  }

  .skill-item {
    animation: orbit 20s linear infinite;
  }

  @keyframes orbit {
    from {
      transform: rotate(0deg) translateX(180px) rotate(0deg);
    }
    to {
      transform: rotate(360deg) translateX(180px) rotate(-360deg);
    }
  }

  @media (min-width: 1280px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(210px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(210px) rotate(-360deg);
      }
    }
  }

  @media (min-width: 1536px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(240px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(240px) rotate(-360deg);
      }
    }
  }

  .skill-item-0 { animation-delay: 0s; }
  .skill-item-1 { animation-delay: -2.2s; }
  .skill-item-2 { animation-delay: -4.4s; }
  .skill-item-3 { animation-delay: -6.6s; }
  .skill-item-4 { animation-delay: -8.8s; }
  .skill-item-5 { animation-delay: -11s; }
  .skill-item-6 { animation-delay: -13.2s; }
  .skill-item-7 { animation-delay: -15.4s; }
  .skill-item-8 { animation-delay: -17.6s; }

  /* Ocultar scrollbar pero mantener funcionalidad */
  .snap-y {
    scrollbar-width: thin; /* Firefox */
  }

  .snap-y::-webkit-scrollbar {
    width: 6px;
  }

  .snap-y::-webkit-scrollbar-track {
    background: rgba(15, 23, 42, 0.5);
  }

  .snap-y::-webkit-scrollbar-thumb {
    background: rgba(6, 182, 212, 0.3);
    border-radius: 3px;
  }

  .snap-y::-webkit-scrollbar-thumb:hover {
    background: rgba(6, 182, 212, 0.5);
  }

  @media (max-width: 640px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(140px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(140px) rotate(-360deg);
      }
    }
  }

  @media (min-width: 641px) and (max-width: 768px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(160px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(160px) rotate(-360deg);
      }
    }
  }

  @media (min-width: 769px) and (max-width: 1023px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(180px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(180px) rotate(-360deg);
      }
    }
  }
</style>