# Frontend - Sistema de Gestión de Tareas

## Descripción

Aplicación web desarrollada con React.js y TypeScript para el Sistema de Gestión de Tareas. Proporciona una interfaz moderna, responsive y accesible para gestionar tareas personales con autenticación, categorías y funcionalidades avanzadas.

## Stack Tecnológico

- **React.js** 18+ - Biblioteca de JavaScript para interfaces
- **TypeScript** - JavaScript tipado
- **HTML5** - Estructura semántica y accesible
- **CSS3** - Estilos modernos con Flexbox/Grid
- **React Router** - Navegación entre páginas
- **Axios** - Cliente HTTP para comunicación con API
- **React Hook Form** - Manejo de formularios
- **React Query** - Gestión de estado del servidor
- **Jest/React Testing Library** - Testing
- **ESLint/Prettier** - Linting y formateo

## Características

- ✅ Interfaz moderna y responsive (mobile-first)
- ✅ Autenticación con JWT
- ✅ CRUD completo para tareas y categorías
- ✅ Filtros y búsqueda avanzada
- ✅ Drag & drop para reordenar tareas
- ✅ Modales con backdrop blur
- ✅ Animaciones y transiciones suaves
- ✅ Tema claro/oscuro
- ✅ PWA (Progressive Web App)
- ✅ Accesibilidad (ARIA, navegación por teclado)
- ✅ Testing unitario e integración

## Estructura del Proyecto

```
task-management-frontend/
├── public/                   # Archivos estáticos
│   ├── index.html
│   ├── manifest.json
│   └── icons/               # Iconos PWA
├── src/
│   ├── components/           # Componentes reutilizables
│   │   ├── common/          # Componentes comunes
│   │   │   ├── Button/
│   │   │   ├── Input/
│   │   │   ├── Modal/
│   │   │   ├── Loading/
│   │   │   └── ErrorBoundary/
│   │   ├── forms/           # Formularios
│   │   │   ├── LoginForm/
│   │   │   ├── RegisterForm/
│   │   │   ├── TaskForm/
│   │   │   └── CategoryForm/
│   │   ├── layout/           # Componentes de layout
│   │   │   ├── Header/
│   │   │   ├── Sidebar/
│   │   │   ├── Footer/
│   │   │   └── Navigation/
│   │   └── features/         # Componentes específicos
│   │       ├── TaskList/
│   │       ├── TaskItem/
│   │       ├── CategoryList/
│   │       └── Dashboard/
│   ├── pages/                # Páginas principales
│   │   ├── Login/
│   │   ├── Register/
│   │   ├── Dashboard/
│   │   ├── Tasks/
│   │   ├── Categories/
│   │   └── Profile/
│   ├── hooks/                # Custom hooks
│   │   ├── useAuth.ts
│   │   ├── useTasks.ts
│   │   ├── useCategories.ts
│   │   └── useLocalStorage.ts
│   ├── context/              # Context API
│   │   ├── AuthContext.tsx
│   │   ├── ThemeContext.tsx
│   │   └── TaskContext.tsx
│   ├── services/             # Servicios API
│   │   ├── api.ts
│   │   ├── auth.service.ts
│   │   ├── task.service.ts
│   │   └── category.service.ts
│   ├── utils/                # Utilidades
│   │   ├── constants.ts
│   │   ├── helpers.ts
│   │   ├── validators.ts
│   │   └── formatters.ts
│   ├── types/                # Tipos TypeScript
│   │   ├── auth.types.ts
│   │   ├── task.types.ts
│   │   ├── category.types.ts
│   │   └── common.types.ts
│   ├── styles/               # Estilos globales
│   │   ├── globals.css
│   │   ├── variables.css
│   │   ├── components.css
│   │   └── themes/
│   │       ├── light.css
│   │       └── dark.css
│   ├── assets/               # Recursos estáticos
│   │   ├── images/
│   │   ├── icons/
│   │   └── fonts/
│   ├── App.tsx               # Componente principal
│   ├── index.tsx             # Punto de entrada
│   └── setupTests.ts         # Configuración de tests
├── tests/                    # Tests
│   ├── components/           # Tests de componentes
│   ├── pages/                # Tests de páginas
│   ├── hooks/                # Tests de hooks
│   ├── utils/                # Tests de utilidades
│   └── __mocks__/            # Mocks
├── package.json
├── tsconfig.json
├── .env.example
└── README.md
```

## Instalación

### Prerrequisitos

- Node.js 18+
- npm o yarn
- Backend ejecutándose en puerto 3001

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone <repository-url>
cd task-management-frontend
```

2. **Instalar dependencias**
```bash
npm install
# o
yarn install
```

3. **Configurar variables de entorno**
```bash
cp .env.example .env
```

Editar el archivo `.env` con tus configuraciones:
```env
# API
REACT_APP_API_URL=http://localhost:3001/api
REACT_APP_API_TIMEOUT=10000

# Autenticación
REACT_APP_JWT_STORAGE_KEY=task_management_token
REACT_APP_REFRESH_TOKEN_KEY=task_management_refresh_token

# Configuración
REACT_APP_APP_NAME=Task Management
REACT_APP_VERSION=1.0.0
REACT_APP_ENVIRONMENT=development

# PWA
REACT_APP_PWA_ENABLED=true
```

4. **Ejecutar en desarrollo**
```bash
npm start
```

La aplicación se abrirá en `http://localhost:3000`

## Scripts Disponibles

```bash
# Desarrollo
npm start              # Ejecutar en modo desarrollo
npm run build          # Construir para producción
npm run preview        # Previsualizar build de producción

# Testing
npm test               # Ejecutar tests en modo watch
npm run test:ci        # Ejecutar tests una vez
npm run test:coverage  # Tests con cobertura
npm run test:debug     # Tests en modo debug

# Linting y Formateo
npm run lint           # Ejecutar ESLint
npm run lint:fix       # Corregir errores de linting
npm run format         # Formatear código con Prettier
npm run type-check     # Verificar tipos TypeScript

# Análisis
npm run analyze        # Analizar bundle
npm run lighthouse     # Auditoría de performance
```

## Componentes Principales

### Layout Components

#### Header
```typescript
interface HeaderProps {
  user: User | null;
  onLogout: () => void;
  onToggleTheme: () => void;
  isDarkMode: boolean;
}
```

#### Sidebar
```typescript
interface SidebarProps {
  isOpen: boolean;
  onClose: () => void;
  currentPath: string;
}
```

### Feature Components

#### TaskList
```typescript
interface TaskListProps {
  tasks: Task[];
  onTaskToggle: (taskId: number) => void;
  onTaskEdit: (task: Task) => void;
  onTaskDelete: (taskId: number) => void;
  filter: TaskFilter;
  onFilterChange: (filter: TaskFilter) => void;
}
```

#### TaskItem
```typescript
interface TaskItemProps {
  task: Task;
  onToggle: (taskId: number) => void;
  onEdit: (task: Task) => void;
  onDelete: (taskId: number) => void;
  onDragStart: (taskId: number) => void;
  onDragEnd: () => void;
}
```

#### TaskForm
```typescript
interface TaskFormProps {
  task?: Task;
  categories: Category[];
  onSubmit: (taskData: CreateTaskDTO | UpdateTaskDTO) => void;
  onCancel: () => void;
  isLoading: boolean;
}
```

### Common Components

#### Modal
```typescript
interface ModalProps {
  isOpen: boolean;
  onClose: () => void;
  title: string;
  children: React.ReactNode;
  size?: 'sm' | 'md' | 'lg' | 'xl';
  showCloseButton?: boolean;
}
```

#### Button
```typescript
interface ButtonProps {
  variant: 'primary' | 'secondary' | 'danger' | 'ghost';
  size: 'sm' | 'md' | 'lg';
  disabled?: boolean;
  loading?: boolean;
  onClick?: () => void;
  children: React.ReactNode;
  type?: 'button' | 'submit' | 'reset';
}
```

## Hooks Personalizados

### useAuth
```typescript
interface UseAuthReturn {
  user: User | null;
  isAuthenticated: boolean;
  isLoading: boolean;
  login: (credentials: LoginCredentials) => Promise<void>;
  register: (userData: RegisterData) => Promise<void>;
  logout: () => void;
  refreshToken: () => Promise<void>;
}
```

### useTasks
```typescript
interface UseTasksReturn {
  tasks: Task[];
  isLoading: boolean;
  error: string | null;
  createTask: (taskData: CreateTaskDTO) => Promise<void>;
  updateTask: (taskId: number, taskData: UpdateTaskDTO) => Promise<void>;
  deleteTask: (taskId: number) => Promise<void>;
  toggleTask: (taskId: number) => Promise<void>;
  filterTasks: (filter: TaskFilter) => void;
}
```

### useCategories
```typescript
interface UseCategoriesReturn {
  categories: Category[];
  isLoading: boolean;
  error: string | null;
  createCategory: (categoryData: CreateCategoryDTO) => Promise<void>;
  updateCategory: (categoryId: number, categoryData: UpdateCategoryDTO) => Promise<void>;
  deleteCategory: (categoryId: number) => Promise<void>;
}
```

## Context API

### AuthContext
```typescript
interface AuthContextType {
  user: User | null;
  isAuthenticated: boolean;
  isLoading: boolean;
  login: (credentials: LoginCredentials) => Promise<void>;
  register: (userData: RegisterData) => Promise<void>;
  logout: () => void;
}
```

### ThemeContext
```typescript
interface ThemeContextType {
  theme: 'light' | 'dark';
  toggleTheme: () => void;
  isDarkMode: boolean;
}
```

### TaskContext
```typescript
interface TaskContextType {
  tasks: Task[];
  categories: Category[];
  filter: TaskFilter;
  setFilter: (filter: TaskFilter) => void;
  refreshTasks: () => void;
  refreshCategories: () => void;
}
```

## Servicios API

### AuthService
```typescript
class AuthService {
  static async login(credentials: LoginCredentials): Promise<AuthResponse>;
  static async register(userData: RegisterData): Promise<AuthResponse>;
  static async logout(): Promise<void>;
  static async refreshToken(): Promise<AuthResponse>;
  static async getCurrentUser(): Promise<User>;
}
```

### TaskService
```typescript
class TaskService {
  static async getTasks(filter?: TaskFilter): Promise<Task[]>;
  static async getTask(id: number): Promise<Task>;
  static async createTask(taskData: CreateTaskDTO): Promise<Task>;
  static async updateTask(id: number, taskData: UpdateTaskDTO): Promise<Task>;
  static async deleteTask(id: number): Promise<void>;
  static async toggleTask(id: number): Promise<Task>;
}
```

### CategoryService
```typescript
class CategoryService {
  static async getCategories(): Promise<Category[]>;
  static async getCategory(id: number): Promise<Category>;
  static async createCategory(categoryData: CreateCategoryDTO): Promise<Category>;
  static async updateCategory(id: number, categoryData: UpdateCategoryDTO): Promise<Category>;
  static async deleteCategory(id: number): Promise<void>;
}
```

## Tipos TypeScript

### Auth Types
```typescript
interface User {
  id: number;
  email: string;
  firstName: string;
  lastName: string;
  createdAt: string;
  updatedAt: string;
}

interface LoginCredentials {
  email: string;
  password: string;
}

interface RegisterData {
  email: string;
  password: string;
  firstName: string;
  lastName: string;
}

interface AuthResponse {
  user: User;
  accessToken: string;
  refreshToken: string;
}
```

### Task Types
```typescript
interface Task {
  id: number;
  title: string;
  description?: string;
  completed: boolean;
  priority: 'low' | 'medium' | 'high';
  dueDate?: string;
  createdAt: string;
  updatedAt: string;
  userId: number;
  categoryId?: number;
  category?: Category;
}

interface CreateTaskDTO {
  title: string;
  description?: string;
  priority: 'low' | 'medium' | 'high';
  dueDate?: string;
  categoryId?: number;
}

interface UpdateTaskDTO {
  title?: string;
  description?: string;
  priority?: 'low' | 'medium' | 'high';
  dueDate?: string;
  completed?: boolean;
  categoryId?: number;
}

interface TaskFilter {
  completed?: boolean;
  priority?: 'low' | 'medium' | 'high';
  categoryId?: number;
  search?: string;
  sortBy?: 'createdAt' | 'dueDate' | 'priority' | 'title';
  sortOrder?: 'asc' | 'desc';
}
```

### Category Types
```typescript
interface Category {
  id: number;
  name: string;
  color: string;
  createdAt: string;
  updatedAt: string;
  userId: number;
  taskCount?: number;
}

interface CreateCategoryDTO {
  name: string;
  color: string;
}

interface UpdateCategoryDTO {
  name?: string;
  color?: string;
}
```

## Estilos y Temas

### Variables CSS
```css
/* variables.css */
:root {
  /* Colores primarios */
  --primary-50: #eff6ff;
  --primary-500: #3b82f6;
  --primary-900: #1e3a8a;
  
  /* Colores neutros */
  --gray-50: #f9fafb;
  --gray-500: #6b7280;
  --gray-900: #111827;
  
  /* Espaciado */
  --spacing-1: 0.25rem;
  --spacing-4: 1rem;
  --spacing-8: 2rem;
  
  /* Tipografía */
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.125rem;
  
  /* Sombras */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
  
  /* Transiciones */
  --transition-fast: 150ms ease-in-out;
  --transition-normal: 300ms ease-in-out;
}
```

### Tema Claro
```css
/* light.css */
[data-theme="light"] {
  --bg-primary: #ffffff;
  --bg-secondary: #f9fafb;
  --text-primary: #111827;
  --text-secondary: #6b7280;
  --border-color: #e5e7eb;
  --shadow: var(--shadow-sm);
}
```

### Tema Oscuro
```css
/* dark.css */
[data-theme="dark"] {
  --bg-primary: #111827;
  --bg-secondary: #1f2937;
  --text-primary: #f9fafb;
  --text-secondary: #d1d5db;
  --border-color: #374151;
  --shadow: var(--shadow-md);
}
```

## Responsive Design

### Breakpoints
```css
/* Mobile First */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
```

### Grid System
```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.grid {
  display: grid;
  gap: 1rem;
}

.grid-cols-1 { grid-template-columns: repeat(1, 1fr); }
.grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
.grid-cols-3 { grid-template-columns: repeat(3, 1fr); }

@media (min-width: 768px) {
  .md\:grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
  .md\:grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
}
```

## PWA (Progressive Web App)

### Manifest
```json
{
  "name": "Task Management System",
  "short_name": "TaskManager",
  "description": "Sistema de gestión de tareas personal",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#3b82f6",
  "icons": [
    {
      "src": "/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
```

### Service Worker
```typescript
// serviceWorker.ts
export const registerSW = () => {
  if ('serviceWorker' in navigator) {
    window.addEventListener('load', () => {
      navigator.serviceWorker.register('/sw.js')
        .then(registration => {
          console.log('SW registered: ', registration);
        })
        .catch(registrationError => {
          console.log('SW registration failed: ', registrationError);
        });
    });
  }
};
```

## Testing

### Configuración de Tests
```typescript
// setupTests.ts
import '@testing-library/jest-dom';
import { server } from './tests/__mocks__/server';

beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
```

### Tests de Componentes
```typescript
// TaskItem.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { TaskItem } from '../TaskItem';

const mockTask = {
  id: 1,
  title: 'Test Task',
  completed: false,
  priority: 'medium' as const
};

test('renders task item correctly', () => {
  render(<TaskItem task={mockTask} onToggle={jest.fn()} />);
  expect(screen.getByText('Test Task')).toBeInTheDocument();
});

test('calls onToggle when clicked', () => {
  const onToggle = jest.fn();
  render(<TaskItem task={mockTask} onToggle={onToggle} />);
  fireEvent.click(screen.getByRole('checkbox'));
  expect(onToggle).toHaveBeenCalledWith(1);
});
```

### Tests de Hooks
```typescript
// useAuth.test.ts
import { renderHook, act } from '@testing-library/react';
import { useAuth } from '../useAuth';

test('should login user', async () => {
  const { result } = renderHook(() => useAuth());
  
  await act(async () => {
    await result.current.login({
      email: 'test@example.com',
      password: 'password123'
    });
  });
  
  expect(result.current.isAuthenticated).toBe(true);
});
```

## Accesibilidad

### ARIA Labels
```typescript
<button
  aria-label="Marcar tarea como completada"
  aria-pressed={task.completed}
  onClick={() => onToggle(task.id)}
>
  <CheckIcon />
</button>
```

### Navegación por Teclado
```typescript
const handleKeyDown = (event: KeyboardEvent) => {
  if (event.key === 'Enter' || event.key === ' ') {
    event.preventDefault();
    onToggle(task.id);
  }
};
```

### Focus Management
```typescript
useEffect(() => {
  if (isOpen && modalRef.current) {
    modalRef.current.focus();
  }
}, [isOpen]);
```

## Performance

### Lazy Loading
```typescript
const Dashboard = lazy(() => import('../pages/Dashboard'));
const Tasks = lazy(() => import('../pages/Tasks'));

const App = () => (
  <Suspense fallback={<Loading />}>
    <Routes>
      <Route path="/dashboard" element={<Dashboard />} />
      <Route path="/tasks" element={<Tasks />} />
    </Routes>
  </Suspense>
);
```

### Memoización
```typescript
const TaskItem = memo(({ task, onToggle, onEdit, onDelete }) => {
  const handleToggle = useCallback(() => {
    onToggle(task.id);
  }, [task.id, onToggle]);
  
  return (
    <div onClick={handleToggle}>
      {task.title}
    </div>
  );
});
```

### Virtual Scrolling
```typescript
import { FixedSizeList as List } from 'react-window';

const TaskList = ({ tasks }) => (
  <List
    height={600}
    itemCount={tasks.length}
    itemSize={80}
    itemData={tasks}
  >
    {TaskItem}
  </List>
);
```

## Deployment

### Build de Producción
```bash
npm run build
```

### Variables de Entorno de Producción
```env
REACT_APP_API_URL=https://api.taskmanagement.com/api
REACT_APP_ENVIRONMENT=production
REACT_APP_PWA_ENABLED=true
```

### Docker
```dockerfile
FROM node:18-alpine as builder

WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Nginx Configuration
```nginx
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location /static/ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

## Monitoreo y Analytics

### Error Tracking
```typescript
import * as Sentry from '@sentry/react';

Sentry.init({
  dsn: process.env.REACT_APP_SENTRY_DSN,
  environment: process.env.REACT_APP_ENVIRONMENT,
});
```

### Performance Monitoring
```typescript
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals';

getCLS(console.log);
getFID(console.log);
getFCP(console.log);
getLCP(console.log);
getTTFB(console.log);
```

## Troubleshooting

### Problemas Comunes

#### Error de CORS
```bash
# Verificar que el backend tenga CORS configurado
# Verificar REACT_APP_API_URL en .env
```

#### Error de Build
```bash
# Limpiar cache
npm run clean
rm -rf node_modules package-lock.json
npm install
```

#### Error de TypeScript
```bash
# Verificar tipos
npm run type-check
# Reinstalar @types
npm install --save-dev @types/react @types/react-dom
```

### Debug Mode
```bash
# Habilitar logs detallados
REACT_APP_DEBUG=true npm start
```

## Contribución

### Flujo de Trabajo
1. Fork del repositorio
2. Crear branch: `git checkout -b feature/nueva-funcionalidad`
3. Hacer commit: `git commit -m 'Add nueva funcionalidad'`
4. Push: `git push origin feature/nueva-funcionalidad`
5. Crear Pull Request

### Estándares de Código
- Seguir convenciones de React y TypeScript
- Escribir tests para nuevos componentes
- Documentar props con JSDoc
- Usar conventional commits

## Recursos de Aprendizaje

### React
- [React Official Docs](https://reactjs.org/docs/getting-started.html)
- [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)

### CSS y Styling
- [CSS Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Flexbox Froggy](https://flexboxfroggy.com/)
- [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

### PWA
- [PWA Builder](https://www.pwabuilder.com/)
- [Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
- [Web App Manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest)

---

Para más información, consulta la documentación completa del proyecto en la carpeta `docs/`.
