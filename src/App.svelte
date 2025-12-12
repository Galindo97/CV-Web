<script>
  import { onMount } from 'svelte';
  
  let expandedProject = null;
  let isVisible = false;
  let imageViewer = false;

  onMount(() => {
    isVisible = true;
  });

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

<div class="snap-y snap-proximity h-screen overflow-y-scroll scroll-smooth text-gray-100 relative animated-bg">
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
    <div class="absolute inset-0 bg-gradient-to-r from-cyan-600/20 to-blue-600/20 animate-gradient"></div>
    <div class="absolute inset-0 opacity-30">
      <div class="absolute top-10 left-10 md:top-20 md:left-20 w-40 h-40 md:w-72 md:h-72 bg-cyan-500 rounded-full filter blur-3xl animate-float"></div>
      <div class="absolute bottom-10 right-10 md:bottom-20 md:right-20 w-48 h-48 md:w-96 md:h-96 bg-blue-500 rounded-full filter blur-3xl animate-float-delay"></div>
      <div class="absolute top-1/2 left-1/2 w-32 h-32 md:w-64 md:h-64 bg-purple-500 rounded-full filter blur-3xl animate-float-slow"></div>
    </div>
    <div class="relative max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-12">
      <div class="text-center">
        <div class="inline-block mb-3 md:mb-4">
          <button 
            on:click={() => imageViewer = true}
            class="w-32 h-32 md:w-40 md:h-40 rounded-full overflow-hidden border-4 border-cyan-500 shadow-2xl shadow-cyan-500/50 cursor-pointer hover:scale-105 transition-transform duration-300 hover:border-cyan-400"
          >
            <img 
              src="/IMG-PERFIL-PROYECTO.jpeg" 
              alt="Abel Santiago Galindo de la Cruz"
              class="w-full h-full object-cover"
            />
          </button>
        </div>
        <h1 class="text-2xl md:text-4xl lg:text-5xl font-bold mb-2 md:mb-3 text-white leading-tight">
          Abel Santiago Galindo de la Cruz
        </h1>
        <p class="text-base md:text-lg lg:text-xl text-gray-300 mb-4 md:mb-6">
          Desarrollador Full Stack en Formación
        </p>
        <div class="flex flex-col md:flex-row flex-wrap justify-center gap-3 md:gap-4 text-gray-300 text-sm md:text-base">
          <div class="flex items-center gap-2 bg-slate-800/50 px-3 md:px-4 py-2 rounded-lg backdrop-blur-sm hover:bg-slate-700/50 transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            <span>636 124 1070</span>
          </div>
          <div class="flex items-center gap-2 bg-slate-800/50 px-4 py-2 rounded-lg backdrop-blur-sm hover:bg-slate-700/50 transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
            <span>sxantiglndo@gmail.com</span>
          </div>
          <a 
            href="https://github.com/Galindo97" 
            target="_blank" 
            rel="noopener noreferrer"
            class="flex items-center gap-2 bg-slate-800/50 px-4 py-2 rounded-lg backdrop-blur-sm hover:bg-slate-700/50 transition-all duration-300 hover:scale-105"
          >
            <svg class="w-5 h-5 text-cyan-400" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <span>GitHub</span>
          </a>
          <div class="flex items-center gap-2 bg-slate-800/50 px-4 py-2 rounded-lg backdrop-blur-sm hover:bg-slate-700/50 transition-all duration-300 hover:scale-105">
            <svg class="w-5 h-5 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
            </svg>
            <span>Inglés: Básico–Intermedio</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Profile Section -->
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-16">
    <div class="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-6 md:p-8 shadow-2xl border border-slate-700/50 hover:border-cyan-500/50 transition-all duration-300">
      <h2 class="text-2xl md:text-3xl font-bold mb-4 md:mb-6 flex items-center gap-3">
        <svg class="w-6 h-6 md:w-8 md:h-8 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
        </svg>
        Perfil Profesional
      </h2>
      <p class="text-base md:text-lg text-gray-300 leading-relaxed">
        Desarrollador en formación con habilidades en Python, FastAPI, Svelte y Docker. 
        Me gusta crear soluciones eficientes y trabajar con tecnologías modernas. Busco seguir 
        creciendo en el ámbito laboral, como personalmente. Al igual, busco integrarme a un equipo 
        donde pueda aportar valor real mientras continúo desarrollando mis habilidades en software development.
      </p>
    </div>
    </div>
  </section>

  <!-- Skills Section -->
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-16">
      <div class="relative w-full h-[400px] md:h-[500px] flex items-center justify-center">
      {#each skills as skill, index}
        <div 
          class="absolute skill-item skill-item-{index}"
        >
          <div class="group cursor-pointer transform transition-all duration-300 hover:scale-125">
            <div class="flex flex-col items-center gap-1 md:gap-2">
              <div class="w-14 h-14 md:w-20 md:h-20 rounded-full bg-gradient-to-br {skill.color} p-1 shadow-xl hover:shadow-2xl transition-shadow duration-300">
                <div class="w-full h-full rounded-full bg-slate-900 flex items-center justify-center p-3">
                  <img 
                    src={skill.icon} 
                    alt={skill.name}
                    class="w-full h-full object-contain filter drop-shadow-lg"
                  />
                </div>
              </div>
              <span class="font-semibold text-xs md:text-sm text-gray-200 group-hover:text-white transition-colors duration-300 whitespace-nowrap">
                {skill.name}
              </span>
            </div>
          </div>
        </div>
      {/each}
      <!-- Centro con título -->
      <div class="absolute flex flex-col items-center justify-center">
        <div class="absolute w-32 h-32 md:w-40 md:h-40 rounded-full bg-gradient-to-br from-cyan-500/30 to-blue-500/30 blur-3xl animate-pulse"></div>
        <div class="relative flex flex-col items-center gap-2 md:gap-3">
          <svg class="w-8 h-8 md:w-12 md:h-12 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
          </svg>
          <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-center">
            <span class="block text-cyan-400">Habilidades</span>
            <span class="block text-blue-400">Técnicas</span>
          </h2>
        </div>
      </div>
    </div>
    </div>
  </section>

  <!-- Projects Section -->
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-16">
    <h2 class="text-2xl md:text-3xl font-bold mb-6 md:mb-8 flex items-center gap-3">
      <svg class="w-6 h-6 md:w-8 md:h-8 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
      </svg>
      Proyectos Destacados
    </h2>
    <div class="space-y-4 md:space-y-6">
      {#each projects as project}
        <div class="bg-slate-800/50 backdrop-blur-sm rounded-2xl shadow-2xl border border-slate-700/50 hover:border-cyan-500/50 transition-all duration-300 overflow-hidden hover:shadow-cyan-500/20">
          <div class="p-4 md:p-6">
            <div class="flex justify-between items-start">
              <div class="flex-1">
                <div class="flex items-center gap-2 md:gap-3 mb-2">
                  <h3 class="text-xl md:text-2xl font-bold text-cyan-400">{project.title}</h3>
                  <a 
                    href={project.github} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    class="p-1 md:p-1.5 bg-slate-700/50 hover:bg-slate-600 rounded-lg transition-all duration-300 hover:scale-110"
                    title="Ver en GitHub"
                  >
                    <svg class="w-4 h-4 md:w-5 md:h-5 text-white" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                    </svg>
                  </a>
                </div>
                <p class="text-sm md:text-base text-white font-medium mb-1">Tecnologías:</p>
                <p class="text-sm md:text-base text-blue-400 font-medium mb-2 md:mb-3">{project.tech}</p>
              </div>
            </div>
            <div class="mt-3 md:mt-4 pt-3 md:pt-4 border-t border-slate-700">
              <p class="text-sm md:text-base text-gray-300 leading-relaxed mb-3 md:mb-4">{project.description}</p>
              <div class="flex flex-wrap gap-2">
                {#each project.highlights as highlight}
                  <span class="px-2 md:px-3 py-1 bg-slate-700/50 rounded-full text-xs md:text-sm text-cyan-300 border border-cyan-500/30 hover:bg-slate-700 hover:border-cyan-400 transition-all duration-300">
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
  <section class="snap-start">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-8 md:py-16 text-center">
      <div class="bg-gradient-to-r from-cyan-600/20 to-blue-600/20 rounded-2xl p-6 md:p-8 backdrop-blur-sm border border-slate-700/50 hover:border-cyan-500/50 transition-all duration-300">
        <h3 class="text-xl md:text-2xl font-bold mb-3 md:mb-4">¿Interesado en trabajar juntos?</h3>
      <p class="text-sm md:text-base text-gray-300 mb-4 md:mb-6">Estoy disponible para nuevas oportunidades y colaboraciones</p>
      <div class="flex justify-center gap-4">
          <a 
          href="tel:6361241070"
          class="px-5 md:px-6 py-2.5 md:py-3 bg-cyan-600 hover:bg-cyan-700 rounded-lg text-sm md:text-base font-semibold transition-all duration-300 inline-flex items-center gap-2 hover:scale-105 hover:shadow-lg hover:shadow-cyan-500/50"
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
        src="/IMG-PERFIL-PROYECTO.jpeg" 
        alt="Abel Santiago Galindo de la Cruz"
        class="max-w-full max-h-[85vh] object-contain rounded-lg shadow-2xl animate-scaleIn"
      />
      <div class="text-center mt-4">
        <p class="text-white text-lg md:text-xl font-semibold">Abel Santiago Galindo de la Cruz</p>
        <p class="text-gray-400 text-sm md:text-base">Desarrollador Full Stack en Formación</p>
      </div>
    </div>
  </div>
{/if}

<style>
  @keyframes bgAnimation {
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

  .animated-bg {
    background: linear-gradient(
      135deg,
      #0c1445 0%,
      #0f172a 15%,
      #1e3a8a 30%,
      #0f172a 45%,
      #1e1b4b 60%,
      #0f172a 75%,
      #1e3a8a 90%,
      #0c1445 100%
    );
    background-size: 400% 400%;
    animation: bgAnimation 45s ease-in-out infinite;
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
      transform: rotate(0deg) translateX(250px) rotate(0deg);
    }
    to {
      transform: rotate(360deg) translateX(250px) rotate(-360deg);
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

  @media (max-width: 768px) {
    @keyframes orbit {
      from {
        transform: rotate(0deg) translateX(130px) rotate(0deg);
      }
      to {
        transform: rotate(360deg) translateX(130px) rotate(-360deg);
      }
    }
  }
</style>