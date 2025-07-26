# EstateKart - Complete Frontend Structure & Workflow

## 📁 Project Structure

```
src/
├── components/
│   ├── analytics/
│   │   ├── ConversionFunnel.tsx      # Sales funnel visualization
│   │   ├── PropertyViewsChart.tsx    # Views/offers trend chart
│   │   └── StatsCard.tsx             # Reusable stats display card
│   └── common/
│       ├── Header.tsx                # Main navigation with hamburger menu
│       ├── PropertyCard.tsx          # Property display card (grid/list)
│       └── SearchBar.tsx             # Advanced search with filters
├── contexts/
│   ├── AuthContext.tsx               # Authentication state management
│   └── PropertyContext.tsx           # Property data & catalogue management
├── pages/
│   ├── auth/
│   │   ├── Login.tsx                 # User authentication
│   │   └── Register.tsx              # User registration
│   ├── lister/
│   │   ├── AddProperty.tsx           # Property listing form
│   │   ├── Analytics.tsx             # Lister performance metrics
│   │   ├── ClientManagement.tsx      # Query & viewing management
│   │   ├── Dashboard.tsx             # Lister main dashboard
│   │   └── Properties.tsx            # Lister's property management
│   ├── user/
│   │   ├── Catalogue.tsx             # User's saved properties
│   │   ├── Dashboard.tsx             # User main dashboard
│   │   ├── Favourites.tsx            # Legacy favorites (now catalogue)
│   │   ├── Properties.tsx            # Browse all properties
│   │   └── Recommendations.tsx       # AI-powered suggestions
│   ├── Landing.tsx                   # Main landing page
│   └── PropertyDetail.tsx            # Individual property view
├── routes/
│   └── AppRouter.tsx                 # Route configuration
├── services/
│   └── s3Service.ts                  # AWS S3 integration (placeholder)
├── utils/
│   └── imageValidation.ts            # Image upload validation
├── App.tsx                           # Main app component
├── main.tsx                          # App entry point
└── index.css                         # Global styles
```

## 🎨 Design System

### Color Theme
- **Primary**: Orange gradient (#f97316 to #ea580c)
- **Secondary**: Gray scale (#f8fafc to #020617)
- **Success**: Green (#22c55e)
- **Warning**: Yellow (#eab308)
- **Error**: Red (#ef4444)

### Design Features
- **Modern Glassmorphism**: Backdrop blur effects
- **Animated Blobs**: Dynamic background elements
- **Smooth Animations**: Spring-based transitions
- **Responsive Design**: Mobile-first approach
- **Sharp Contrasts**: High readability

## 🔄 User Workflow

### 1. **Public Access (No Authentication)**
```
Landing Page → Browse Properties → Property Details
     ↓
Sign Up/Login Prompt for Advanced Features
```

### 2. **Authenticated User Journey**
```
Login → User Dashboard → Browse/Search Properties
  ↓           ↓              ↓
Catalogue   Recommendations  Schedule Viewings
  ↓           ↓              ↓
Manage      AI Suggestions  Contact Listers
Saved       Based on        View Appointments
Properties  Preferences
```

### 3. **Property Lister Journey**
```
Login → Lister Dashboard → Add Property
  ↓           ↓              ↓
Analytics   Client Mgmt    Property Mgmt
  ↓           ↓              ↓
Performance Queries &      Edit/Delete
Metrics     Viewings       Properties
```

## 🧭 Navigation Structure

### Hamburger Menu (Authenticated Users)
- **Browse Properties** → `/properties`
- **My Dashboard** → `/user-dashboard`
- **My Catalogue** → `/catalogue`
- **Recommendations** → `/recommendations`
- **List Property** → `/add-property`

### Profile Menu
- **Profile Settings** → `/profile`
- **Sign Out** → Logout function

## 📱 Page Functionality

### **Landing Page** (`/`)
- Hero section with search
- Recommended properties
- Recent properties
- Quick actions
- CTA for non-authenticated users

### **User Dashboard** (`/user-dashboard`)
- Personalized welcome
- Search bar
- Stats cards (viewed, catalogue, trends)
- Recommended properties section
- Recent properties section
- Quick action cards

### **Browse Properties** (`/properties`)
- Advanced search & filters
- Grid/List view toggle
- Property cards with catalogue option
- Schedule viewing functionality
- Pagination/load more

### **Property Details** (`/property/:id`)
- Image gallery with navigation
- Property information
- Amenities & features
- Contact lister
- Schedule viewing modal
- Add to catalogue

### **My Catalogue** (`/catalogue`)
- Saved properties grid
- Remove from catalogue
- Direct property access
- Empty state with CTA

### **Recommendations** (`/recommendations`)
- AI-powered suggestions
- Category filters (budget, luxury, location)
- Personalized insights
- AWS ML integration explanation

### **Lister Dashboard** (`/dashboard`)
- Welcome section
- Property overview
- Analytics cards
- Quick actions (Add Property, Client Management, Analytics)
- Recent properties

### **Add Property** (`/add-property`)
- Multi-step form
- Image upload (URL/File)
- Property details
- Amenities selection
- Contact information
- AWS S3 integration ready

### **Client Management** (`/clients`)
- Property overview with counts
- Query management
- Scheduled viewing management
- Contact client modals
- Accept/Reject/Extend viewing options

### **Analytics** (`/analytics`)
- Performance metrics
- Charts & visualizations
- Conversion funnel
- Insights & recommendations

## 🔧 State Management

### **AuthContext**
```typescript
interface AuthContextType {
  user: User | null;
  login: (email: string, password: string) => Promise<void>;
  logout: () => void;
  register: (email: string, password: string, name: string) => Promise<void>;
  loading: boolean;
}
```

### **PropertyContext**
```typescript
interface PropertyContextType {
  properties: Property[];
  catalogueProperties: string[];
  favorites: string[];
  addProperty: (property: Omit<Property, 'id' | 'createdAt' | 'views' | 'offers'>) => void;
  updateProperty: (id: string, updates: Partial<Property>) => void;
  deleteProperty: (id: string) => void;
  toggleCatalogue: (propertyId: string) => void;
  toggleFavorite: (propertyId: string) => void;
  getPropertiesByLister: (listerId: string) => Property[];
  getPropertyAnalytics: (listerId: string) => any;
}
```

## 🎯 Key Features

### **Authentication System**
- JWT-based authentication (mock)
- Protected routes
- Role-based access (user/lister)
- Persistent sessions

### **Property Management**
- CRUD operations
- Image upload system
- Advanced search & filtering
- Catalogue/favorites system

### **Client Interaction**
- Query system
- Viewing scheduling
- Contact management
- Communication tracking

### **Analytics & Insights**
- Performance metrics
- Conversion tracking
- AI recommendations
- Market insights

### **Modern UX/UI**
- Responsive design
- Smooth animations
- Intuitive navigation
- Accessibility features

## 🚀 Technology Stack

- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS
- **Animations**: Framer Motion
- **Charts**: Recharts
- **Routing**: React Router DOM
- **Icons**: Lucide React
- **Build Tool**: Vite

## 🔮 AWS Integration Ready

- **S3**: Image storage
- **Cognito**: Authentication
- **Lambda**: Serverless functions
- **SageMaker**: ML recommendations
- **RDS**: Database storage

This structure provides a complete, scalable real estate platform with modern design and comprehensive functionality for both property seekers and listers.