# Dashboard del Equipo de IA — Brief

## Objetivo
Dashboard web moderno para visualizar el estado de todos los agentes de IA del equipo. Debe ser visual, profesional, y fácil de entender.

## Stack
- HTML + CSS + JavaScript vanilla (sin frameworks, un solo archivo index.html)
- Tailwind CSS via CDN
- Chart.js para gráficos
- Diseño dark mode (fondo oscuro, acentos de color)

## Datos
El dashboard lee un archivo `data.json` en la misma carpeta que se actualiza periódicamente. Incluir un data.json de ejemplo con datos mock realistas.

## Secciones del Dashboard

### 1. Header
- Logo/nombre: "MOLTY — AI Team Dashboard"
- Fecha/hora actual (auto-update cada minuto)
- Indicador: "Agentes activos: X/10"

### 2. Tarjetas de Agentes (grid responsivo)
Una tarjeta por agente con:
- Emoji + nombre del agente
- Rol (ej: "Product Research Lead")
- Estado: 🟢 Activo | 🟡 En espera | 🔴 Inactivo | 🔵 Trabajando
- Última tarea completada
- Última actividad (timestamp relativo: "hace 5 min")
- Canal de Discord asignado
- Barra de progreso de tareas semanales (ej: 3/5 completadas)

Agentes:
1. 🔬 HUNTER — Product Research Lead
2. 🎯 NOVA — Media Buyer Lead
3. ✍️ BLADE — Copywriter Elite
4. 📊 CIPHER — Data Analyst
5. 🔍 ORBIT — SEO Specialist
6. 📧 PULSE — Email Marketing
7. 🚀 FORGE — Landing Page Architect
8. 🕵️ SHADOW — Competitive Intelligence
9. 🎬 PIXEL — Creative Strategist
10. ⚙️ GEAR — Automation Engineer

### 3. Métricas Generales (4 cards en una fila)
- Tareas completadas hoy
- Tokens consumidos hoy (con gráfico sparkline)
- Reportes generados esta semana
- Cron jobs activos

### 4. Timeline de Actividad
Un feed cronológico de las últimas 20 actividades:
- "🔬 HUNTER completó reporte de productos ganadores" — 20:22
- "✍️ BLADE entregó copy para Depurel y Linfatic" — 20:24
- etc.

### 5. Gráfico de Tokens
Gráfico de barras/línea mostrando consumo de tokens por día (últimos 7 días)

### 6. Tabla de Cron Jobs
Lista de tareas automáticas programadas:
- Nombre | Frecuencia | Próxima ejecución | Estado

### 7. Equipo Humano (sidebar o sección)
Tarjetas más pequeñas:
- Ramon (CEO) 🔴
- Juan/Pochi (Manager) 🔵
- Tin (Editor) 🟢
- Jairo (Editor) 🟢
- JoseDavid (Editor) 🟢
- Laura (ML & ATC) 🟡

## Diseño
- Dark mode con fondo #0f172a (slate-900)
- Cards con fondo #1e293b (slate-800), bordes sutiles
- Acentos: verde para activo, amarillo para espera, rojo para inactivo, azul para trabajando
- Fuente: Inter (Google Fonts)
- Fully responsive (mobile + desktop)
- Animaciones sutiles en hover
- Los estados de los agentes deben tener un pulso animado (dot pulsing)

## Archivo data.json (ejemplo)
```json
{
  "lastUpdated": "2026-03-05T21:30:00-03:00",
  "agents": [
    {
      "id": "hunter",
      "name": "HUNTER",
      "emoji": "🔬",
      "role": "Product Research Lead",
      "status": "completed",
      "channel": "#research-productos",
      "lastTask": "Reporte TOP 20 productos ganadores",
      "lastActivity": "2026-03-05T20:22:00-03:00",
      "weeklyTasks": {"completed": 3, "total": 5}
    }
  ],
  "metrics": {
    "tasksToday": 12,
    "tokensToday": 185000,
    "reportsThisWeek": 7,
    "cronJobsActive": 4
  },
  "timeline": [
    {"agent": "HUNTER", "emoji": "🔬", "action": "completó reporte de productos ganadores", "time": "20:22"},
    {"agent": "SHADOW", "emoji": "🕵️", "action": "entregó inteligencia competitiva", "time": "20:25"},
    {"agent": "BLADE", "emoji": "✍️", "action": "entregó copy para Depurel y Linfatic", "time": "20:24"},
    {"agent": "NOVA", "emoji": "🎯", "action": "completó estrategia de media buying", "time": "20:22"},
    {"agent": "FORGE", "emoji": "🚀", "action": "entregó blueprint de landing pages", "time": "20:23"},
    {"agent": "PULSE", "emoji": "📧", "action": "completó sistema de email marketing", "time": "20:26"},
    {"agent": "ORBIT", "emoji": "🔍", "action": "completó estrategia SEO", "time": "20:28"}
  ],
  "tokenHistory": [
    {"date": "2026-03-01", "tokens": 45000},
    {"date": "2026-03-02", "tokens": 62000},
    {"date": "2026-03-03", "tokens": 38000},
    {"date": "2026-03-04", "tokens": 71000},
    {"date": "2026-03-05", "tokens": 185000}
  ],
  "cronJobs": [
    {"name": "Daily Standup", "frequency": "Lun-Sáb 12:00", "next": "2026-03-06T12:00:00-03:00", "status": "active"},
    {"name": "Token Usage", "frequency": "Cada 2 horas", "next": "2026-03-05T23:00:00-03:00", "status": "active"},
    {"name": "Intel Competitiva", "frequency": "Lunes 10:00", "next": "2026-03-10T10:00:00-03:00", "status": "active"},
    {"name": "Product Hunting", "frequency": "Miércoles 10:00", "next": "2026-03-12T10:00:00-03:00", "status": "active"}
  ],
  "team": [
    {"name": "Ramon", "role": "CEO", "color": "red"},
    {"name": "Juan (Pochi)", "role": "Manager", "color": "blue"},
    {"name": "Tin", "role": "Editor", "color": "green"},
    {"name": "Jairo", "role": "Editor", "color": "green"},
    {"name": "JoseDavid", "role": "Editor", "color": "green"},
    {"name": "Laura", "role": "ML & ATC", "color": "yellow"}
  ]
}
```

## Notas
- El dashboard se sirve como archivos estáticos
- Debe poder abrirse directamente como archivo HTML en el navegador
- El data.json se actualiza por un cron job desde OpenClaw
- Todo el texto en español
