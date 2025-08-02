# Nebusis® Combined Full-Stack Application README
## Unified Website & Portal Implementation Specification
### Date: 01 August 2025

---

## 🔹 1. Application Overview

### Platform Description
Nebusis® is a comprehensive business platform that combines a public marketing website with an authenticated portal system. The platform showcases 23 AI-powered business applications, 16 certification programs, 11 sector-specific suites, and 7 digital transformation services.

**Architecture**: React frontend + Go backend + MySQL database + Docker containerization

### User Types & Access Levels

#### 🌐 **Public Visitors (Website)**
- **Access**: Marketing pages, product information, blog content
- **Features**: Browse applications, view certifications, read case studies, submit demo requests
- **Pages**: Home, Applications, Certifications, Sector Suites, About, Contact, Blog

#### 👤 **Registered Users (Portal)**
- **Access**: Customer dashboard, application trials, certification enrollment
- **Features**: Demo management, training courses, progress tracking, billing
- **Pages**: Dashboard, My Applications, Certifications, Billing, Profile

#### 🏢 **Partners (Portal)**
- **Access**: Partner dashboard, lead management, commission tracking
- **Features**: Referral management, training materials, marketing assets
- **Pages**: Partner Dashboard, Leads, Commissions, Resources

#### 👥 **Collaborators (Portal)**
- **Access**: Project assignments, time tracking, resource access
- **Features**: Task management, availability calendar, skill profiles
- **Pages**: Projects, Schedule, Resources, Performance

#### 💼 **Investors (Portal)**
- **Access**: Financial reports, KPI dashboards, strategic updates
- **Features**: ROI tracking, milestone monitoring, document access
- **Pages**: Financial Dashboard, Reports, Documents, Updates

#### ⚙️ **Administrators (Portal)**
- **Access**: Complete system management, content control, user administration
- **Features**: Content management, user roles, analytics, system settings
- **Pages**: Admin Dashboard, Content Management, User Management, Analytics, Settings

### Key Features by User Type

**Public Website Features:**
- Responsive product showcase with filtering and search
- Interactive demo request system with lead qualification
- Blog/news content management with categories
- Newsletter subscription with preference management
- Contact forms with inquiry routing
- Video gallery with categorization
- SEO-optimized content delivery

**Portal Features:**
- Single Sign-On (SSO) authentication across all modules
- Role-based dashboard customization
- Real-time notifications and alerts
- Document management and sharing
- Integrated billing and subscription management
- Analytics and reporting for all user types
- Multi-language support preparation

---

## 🔹 2. Frontend (React)

### Technology Stack
- **Framework**: React 18 with JavaScript (ES6+)
- **Routing**: React Router v6
- **Styling**: Tailwind CSS + shadcn/ui components
- **State Management**: React Query + Zustand
- **Forms**: React Hook Form + Zod validation
- **HTTP Client**: Axios
- **Build Tool**: Vite
- **Icons**: Lucide React + React Icons

### Page Structure & Components

#### **Public Website Pages**
```
/src/pages/website/
├── HomePage.jsx              → Hero carousel, featured content, stats
├── ApplicationsPage.jsx      → Grid/list view with filtering
├── ApplicationDetailPage.jsx → Detailed app info, demo CTA
├── CertificationsPage.jsx    → Certification programs showcase
├── CertificationDetailPage.jsx → Course details, enrollment
├── SectorSuitesPage.jsx      → Industry-specific solutions
├── SectorSuiteDetailPage.jsx → Suite details, case studies
├── DigitalTransformationPage.jsx → Service offerings
├── ServiceDetailPage.jsx     → Service specifications
├── BlogPage.jsx              → Article listing with search
├── BlogPostPage.jsx          → Full article view
├── AboutPage.jsx             → Company info, team, history
├── ContactPage.jsx           → Contact form, office locations
├── DemoPage.jsx              → Demo request form
├── PricingPage.jsx           → Pricing calculator
├── PrivacyPolicyPage.jsx     → Legal content
├── TermsOfUsePage.jsx        → Terms and conditions
└── NotFoundPage.jsx          → 404 error page
```

#### **Portal Pages**
```
/src/pages/portal/
├── LoginPage.jsx             → Authentication form
├── DashboardPage.jsx         → Role-based dashboard
├── customer/
│   ├── CustomerDashboard.jsx → Customer overview
│   ├── MyApplications.jsx    → Subscribed apps
│   ├── MyCertifications.jsx  → Enrolled courses
│   ├── BillingPage.jsx       → Invoices, payments
│   └── ProfilePage.jsx       → Account settings
├── partner/
│   ├── PartnerDashboard.jsx  → Partner metrics
│   ├── LeadsPage.jsx         → Lead management
│   ├── CommissionsPage.jsx   → Revenue tracking
│   └── ResourcesPage.jsx     → Marketing materials
├── collaborator/
│   ├── CollaboratorDashboard.jsx → Task overview
│   ├── ProjectsPage.jsx      → Project assignments
│   ├── SchedulePage.jsx      → Availability calendar
│   └── PerformancePage.jsx   → KPI tracking
├── investor/
│   ├── InvestorDashboard.jsx → Financial overview
│   ├── ReportsPage.jsx       → Detailed analytics
│   ├── DocumentsPage.jsx     → Investment docs
│   └── UpdatesPage.jsx       → Strategic updates
└── admin/
    ├── AdminDashboard.jsx    → System overview
    ├── ContentManagement.jsx → CMS interface
    ├── UserManagement.jsx    → User administration
    ├── AnalyticsPage.jsx     → Platform analytics
    └── SettingsPage.jsx      → System configuration
```

#### **Shared Components**
```
/src/components/
├── layout/
│   ├── Header.jsx            → Navigation, user menu
│   ├── Footer.jsx            → Links, company info
│   ├── Sidebar.jsx           → Portal navigation
│   └── PageLayout.jsx        → Common page wrapper
├── ui/                       → shadcn/ui components
│   ├── Button.jsx
│   ├── Card.jsx
│   ├── Dialog.jsx
│   ├── Form.jsx
│   ├── Input.jsx
│   ├── Select.jsx
│   └── ...
├── business/
│   ├── ApplicationCard.jsx   → Product showcase card
│   ├── CertificationCard.jsx → Course overview card
│   ├── SectorSuiteCard.jsx   → Industry solution card
│   ├── ServiceCard.jsx       → Service offering card
│   ├── BlogPostCard.jsx      → Article preview card
│   ├── VideoCard.jsx         → Video thumbnail card
│   └── PricingCalculator.jsx → Dynamic pricing tool
├── forms/
│   ├── DemoRequestForm.jsx   → Demo scheduling
│   ├── ContactForm.jsx       → General inquiries
│   ├── NewsletterForm.jsx    → Email subscription
│   ├── LoginForm.jsx         → Authentication
│   └── RegistrationForm.jsx  → User signup
├── charts/
│   ├── DashboardChart.jsx    → Analytics visualization
│   ├── RevenueChart.jsx      → Financial metrics
│   └── PerformanceChart.jsx  → KPI tracking
└── shared/
    ├── LoadingSpinner.jsx    → Loading indicator
    ├── ErrorBoundary.jsx     → Error handling
    ├── SEOHead.jsx           → Meta tags management
    ├── SocialShare.jsx       → Social media sharing
    └── BackToTop.jsx         → Scroll to top button
```

### API Integration Points

**Website APIs:**
- `GET /api/applications` → ApplicationsPage, HomePage
- `GET /api/applications/:slug` → ApplicationDetailPage
- `GET /api/certifications` → CertificationsPage, HomePage
- `GET /api/certifications/:slug` → CertificationDetailPage
- `GET /api/sector-suites` → SectorSuitesPage
- `GET /api/digital-transformation` → DigitalTransformationPage
- `GET /api/blog/posts` → BlogPage, HomePage
- `GET /api/blog/posts/:slug` → BlogPostPage
- `GET /api/videos` → VideoGallery component
- `POST /api/demo-requests` → DemoRequestForm
- `POST /api/contact` → ContactForm
- `POST /api/newsletter/subscribe` → NewsletterForm

**Portal APIs:**
- `POST /api/auth/login` → LoginForm
- `POST /api/auth/logout` → Header component
- `GET /api/auth/me` → Authentication context
- `GET /api/dashboard/:role` → Role-based dashboards
- `GET /api/users/:id` → ProfilePage
- `PATCH /api/users/:id` → Profile updates
- `GET /api/subscriptions` → MyApplications, Billing
- `GET /api/enrollments` → MyCertifications
- `GET /api/invoices` → BillingPage
- `GET /api/leads` → Partner LeadsPage
- `GET /api/projects` → Collaborator ProjectsPage
- `GET /api/analytics` → Admin/Investor dashboards

### Required Static Assets

**Location**: `/frontend/public/assets/`

#### **Brand Assets**
```
/logos/
├── nebusis-logo.svg          → Main logo (header)
├── nebusis-logo-white.svg    → White version (footer)
├── nebusis-icon.svg          → Favicon and mobile icon
└── nebusis-wordmark.svg      → Text-only logo

/brand/
├── brand-guidelines.pdf      → Brand usage guide
└── color-palette.json        → Brand colors reference
```

#### **Application Icons**
```
/icons/applications/
├── complianceone.svg         → Nebusis® ComplianceOne
├── cyberwatch.svg            → Nebusis® CyberWatch
├── membercore.svg            → Nebusis® MemberCore
├── peoplecore.svg            → Nebusis® PeopleCore
├── engage.svg                → Nebusis® Engage
├── smartbooks.svg            → Nebusis® SmartBooks
├── performancetracker.svg    → Nebusis® Performance Tracker
├── emisionsflow.svg          → Nebusis® EmissionsFlow
├── selfcertpro.svg           → Nebusis® SelfCertPro
├── knowledgecheck.svg        → Nebusis® KnowledgeCheck
├── interopwiz.svg            → Nebusis® InterOpWiz
├── zappformz.svg             → Nebusis® ZappFormZ
├── bodegamonster.svg         → Nebusis® BodegaMonster
├── multiomics-wizard.svg     → Nebusis® Multiomics Wizard
├── elearning-wizard.svg      → Nebusis® e-Learning Wizard
├── intelex-isotools.svg      → Nebusis® Intelex ISOTools
├── wizspeek.svg              → Nebusis® WizSpeek
├── compliancecore.svg        → Nebusis® ComplianceCore
├── aiomics-engine.svg        → Nebusis® AIOmics Engine
├── manufacturing-suite.svg   → Manufacturing Suite
├── semiconductor-suite.svg   → Semiconductor Suite
├── advanced-manufacturing.svg → Advanced Manufacturing
└── multiomics-engine.svg     → Multiomics Engine
```

#### **Hero & Marketing Images**
```
/images/hero/
├── hero-business-apps.jpg    → Applications hero
├── hero-certifications.jpg   → Education hero
├── hero-sector-suites.jpg    → Industry solutions hero
├── hero-digital-transformation.jpg → Services hero
└── hero-about.jpg            → Company story hero

/images/features/
├── ai-powered-automation.jpg → AI capabilities
├── compliance-management.jpg → Regulatory features
├── real-time-analytics.jpg   → Dashboard preview
├── secure-cloud-platform.jpg → Security features
└── integration-ecosystem.jpg → Integration capabilities

/images/industry/
├── healthcare.jpg            → Healthcare sector
├── manufacturing.jpg         → Manufacturing sector
├── government.jpg            → Government sector
├── finance.jpg               → Financial services
├── education.jpg             → Education sector
├── retail.jpg                → Retail sector
└── technology.jpg            → Technology sector
```

#### **Team & Company**
```
/images/team/
├── celso-white.jpg           → CEO profile
├── leadership-team.jpg       → Leadership group
└── company-culture.jpg       → Office/culture photo

/images/company/
├── company-timeline.svg      → Historical milestones
├── mission-vision.jpg        → Company values
└── office-locations.jpg      → Global presence
```

#### **Certification Assets**
```
/images/certifications/
├── cert-ai-specialist.jpg    → AI certification
├── cert-compliance-expert.jpg → Compliance certification
├── cert-digital-transformation.jpg → DT certification
├── cert-cybersecurity.jpg    → Security certification
├── cert-data-analytics.jpg   → Analytics certification
└── cert-prompt-engineering.jpg → Prompt engineering
```

#### **Documents & Resources**
```
/documents/
├── business-plan-2025.pdf    → Company strategy
├── product-catalog.pdf       → Complete offerings
├── compliance-guide.pdf      → Regulatory guidance
├── integration-guide.pdf     → Technical documentation
├── pricing-guide.pdf         → Pricing information
└── case-studies/
    ├── healthcare-transformation.pdf
    ├── manufacturing-optimization.pdf
    └── government-compliance.pdf
```

#### **UI Assets**
```
/ui/
├── placeholder-avatar.svg    → Default user avatar
├── placeholder-image.svg     → Image loading state
├── error-illustration.svg    → Error page graphic
├── empty-state.svg           → No data illustration
└── success-checkmark.svg     → Success confirmation

/icons/ui/
├── dashboard.svg             → Dashboard icon
├── applications.svg          → Apps menu icon
├── certifications.svg        → Education icon
├── analytics.svg             → Reports icon
├── settings.svg              → Configuration icon
├── notifications.svg         → Alert icon
├── profile.svg               → User profile icon
└── logout.svg                → Sign out icon
```

### Dependencies (package.json)
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.8.0",
    "axios": "^1.3.0",
    "@tanstack/react-query": "^4.24.0",
    "zustand": "^4.3.0",
    "react-hook-form": "^7.43.0",
    "zod": "^3.20.0",
    "@hookform/resolvers": "^2.9.0",
    "tailwindcss": "^3.2.0",
    "lucide-react": "^0.312.0",
    "react-icons": "^4.7.0",
    "framer-motion": "^9.0.0",
    "recharts": "^2.5.0",
    "date-fns": "^2.29.0",
    "js-cookie": "^3.0.0",
    "react-helmet-async": "^1.3.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^3.1.0",
    "vite": "^4.1.0",
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0",
    "eslint": "^8.34.0",
    "@types/js-cookie": "^3.0.0"
  }
}
```

---

## 🔹 3. Backend (Go)

### Technology Stack
- **Framework**: Gin (HTTP web framework)
- **ORM**: GORM (Object-Relational Mapping)
- **Database Driver**: MySQL driver for GORM
- **Authentication**: JWT tokens + bcrypt
- **Validation**: go-playground/validator
- **Configuration**: Viper (config management)
- **Logging**: Logrus (structured logging)
- **CORS**: gin-contrib/cors
- **Rate Limiting**: golang.org/x/time/rate

### API Endpoints by Feature

#### **🔐 Authentication & Authorization**
```go
// Group: /api/auth
POST   /api/auth/register        → Register new user
POST   /api/auth/login           → User authentication
POST   /api/auth/logout          → Session termination
POST   /api/auth/refresh         → Token refresh
GET    /api/auth/me              → Current user info
POST   /api/auth/forgot-password → Password reset request
POST   /api/auth/reset-password  → Password reset confirmation
POST   /api/auth/verify-email    → Email verification
```

**Example Request/Response:**
```go
// POST /api/auth/login
type LoginRequest struct {
    Email    string `json:"email" validate:"required,email"`
    Password string `json:"password" validate:"required,min=8"`
}

type LoginResponse struct {
    Success bool   `json:"success"`
    Token   string `json:"token"`
    User    User   `json:"user"`
    ExpiresAt int64 `json:"expires_at"`
}
```

#### **👤 User Management**
```go
// Group: /api/users
GET    /api/users                → List users (admin only)
GET    /api/users/:id            → Get user details
PATCH  /api/users/:id            → Update user profile
DELETE /api/users/:id            → Delete user (admin only)
POST   /api/users/:id/role       → Change user role (admin only)
GET    /api/users/:id/activity   → User activity log
POST   /api/users/invite         → Invite new user
```

#### **📱 Applications Management**
```go
// Group: /api/applications
GET    /api/applications         → List all applications
GET    /api/applications/:slug   → Get application details
POST   /api/applications         → Create application (admin only)
PATCH  /api/applications/:id     → Update application (admin only)
DELETE /api/applications/:id     → Delete application (admin only)
GET    /api/applications/categories → Get all categories
GET    /api/applications/search  → Search applications
```

**Example Request/Response:**
```go
// GET /api/applications
type ApplicationsResponse struct {
    Success      bool          `json:"success"`
    Applications []Application `json:"applications"`
    Total        int           `json:"total"`
    Categories   []string      `json:"categories"`
    Meta         Meta          `json:"meta"`
}

type Application struct {
    ID               uint     `json:"id"`
    ProductID        string   `json:"product_id"`
    Name             string   `json:"name"`
    Slug             string   `json:"slug"`
    Description      string   `json:"description"`
    ShortDescription string   `json:"short_description"`
    Icon             string   `json:"icon"`
    Status           string   `json:"status"` // live, beta, coming_soon
    Category         string   `json:"category"`
    Features         []string `json:"features"`
    TargetIndustries []string `json:"target_industries"`
    PricingTiers     []PricingTier `json:"pricing_tiers"`
    ThumbnailURL     string   `json:"thumbnail_url"`
    DemoURL          string   `json:"demo_url"`
    IsFeatured       bool     `json:"is_featured"`
    IsPublic         bool     `json:"is_public"`
    CreatedAt        string   `json:"created_at"`
    UpdatedAt        string   `json:"updated_at"`
}
```

#### **🎓 Certifications Management**
```go
// Group: /api/certifications
GET    /api/certifications       → List all certifications
GET    /api/certifications/:slug → Get certification details
POST   /api/certifications       → Create certification (admin only)
PATCH  /api/certifications/:id   → Update certification (admin only)
DELETE /api/certifications/:id   → Delete certification (admin only)
POST   /api/certifications/:id/enroll → Enroll in certification
GET    /api/certifications/categories → Get all categories
```

#### **🏢 Sector Suites Management**
```go
// Group: /api/sector-suites
GET    /api/sector-suites         → List all sector suites
GET    /api/sector-suites/:slug   → Get suite details
POST   /api/sector-suites         → Create suite (admin only)
PATCH  /api/sector-suites/:id     → Update suite (admin only)
DELETE /api/sector-suites/:id     → Delete suite (admin only)
GET    /api/sector-suites/industries → Get all industries
```

#### **🔄 Digital Transformation Services**
```go
// Group: /api/digital-transformation
GET    /api/digital-transformation → List all services
GET    /api/digital-transformation/:slug → Get service details
POST   /api/digital-transformation → Create service (admin only)
PATCH  /api/digital-transformation/:id → Update service (admin only)
DELETE /api/digital-transformation/:id → Delete service (admin only)
```

#### **📝 Demo Requests**
```go
// Group: /api/demo-requests
POST   /api/demo-requests         → Submit demo request
GET    /api/demo-requests         → List demo requests (admin only)
GET    /api/demo-requests/:id     → Get demo request details
PATCH  /api/demo-requests/:id     → Update demo status (admin only)
DELETE /api/demo-requests/:id     → Delete demo request (admin only)
```

**Example Request/Response:**
```go
// POST /api/demo-requests
type DemoRequestPayload struct {
    FirstName            string   `json:"first_name" validate:"required,min=2,max=50"`
    LastName             string   `json:"last_name" validate:"required,min=2,max=50"`
    Email                string   `json:"email" validate:"required,email"`
    Phone                string   `json:"phone,omitempty"`
    Company              string   `json:"company" validate:"required,min=2,max=200"`
    JobTitle             string   `json:"job_title,omitempty"`
    Industry             string   `json:"industry,omitempty"`
    CompanySize          string   `json:"company_size,omitempty"`
    Country              string   `json:"country,omitempty"`
    InterestedProducts   []string `json:"interested_products" validate:"required,min=1"`
    SpecificRequirements string   `json:"specific_requirements,omitempty"`
    PreferredDemoDate    string   `json:"preferred_demo_date,omitempty"`
    PreferredTimeSlot    string   `json:"preferred_time_slot,omitempty"`
    DemoType             string   `json:"demo_type,omitempty"` // online, onsite
    LeadSource           string   `json:"lead_source,omitempty"`
}

type DemoRequestResponse struct {
    Success              bool   `json:"success"`
    RequestID            string `json:"request_id"`
    Status               string `json:"status"`
    Message              string `json:"message"`
    EstimatedResponseTime string `json:"estimated_response_time"`
}
```

#### **📞 Contact Messages**
```go
// Group: /api/contact
POST   /api/contact               → Submit contact message
GET    /api/contact               → List contact messages (admin only)
GET    /api/contact/:id           → Get contact message details
PATCH  /api/contact/:id           → Update message status (admin only)
DELETE /api/contact/:id           → Delete contact message (admin only)
```

#### **📰 Blog & Content**
```go
// Group: /api/blog
GET    /api/blog/posts            → List blog posts
GET    /api/blog/posts/:slug      → Get blog post details
POST   /api/blog/posts            → Create blog post (admin only)
PATCH  /api/blog/posts/:id        → Update blog post (admin only)
DELETE /api/blog/posts/:id        → Delete blog post (admin only)
GET    /api/blog/categories       → Get all categories
GET    /api/blog/tags             → Get all tags
```

#### **🎥 Video Gallery**
```go
// Group: /api/videos
GET    /api/videos                → List videos
GET    /api/videos/:id            → Get video details
POST   /api/videos                → Create video (admin only)
PATCH  /api/videos/:id            → Update video (admin only)
DELETE /api/videos/:id            → Delete video (admin only)
```

#### **📧 Newsletter Management**
```go
// Group: /api/newsletter
POST   /api/newsletter/subscribe  → Subscribe to newsletter
GET    /api/newsletter/verify/:token → Verify email subscription
POST   /api/newsletter/unsubscribe → Unsubscribe from newsletter
GET    /api/newsletter/subscribers → List subscribers (admin only)
```

#### **📊 Dashboard & Analytics**
```go
// Group: /api/dashboard
GET    /api/dashboard/customer/:id → Customer dashboard data
GET    /api/dashboard/partner/:id  → Partner dashboard data
GET    /api/dashboard/collaborator/:id → Collaborator dashboard data
GET    /api/dashboard/investor/:id → Investor dashboard data
GET    /api/dashboard/admin        → Admin dashboard data

// Group: /api/analytics
GET    /api/analytics/overview     → Platform overview metrics
GET    /api/analytics/users        → User engagement metrics
GET    /api/analytics/applications → Application usage metrics
GET    /api/analytics/revenue      → Revenue analytics
GET    /api/analytics/performance  → Performance metrics
```

#### **💳 Billing & Subscriptions**
```go
// Group: /api/billing
GET    /api/billing/subscriptions → User subscriptions
GET    /api/billing/invoices      → User invoices
POST   /api/billing/subscribe     → Subscribe to application
PATCH  /api/billing/subscription/:id → Update subscription
DELETE /api/billing/subscription/:id → Cancel subscription
GET    /api/billing/payment-methods → User payment methods
POST   /api/billing/payment-methods → Add payment method
```

#### **🔧 System & Configuration**
```go
// Group: /api/system
GET    /api/system/health         → System health check
GET    /api/system/health/detailed → Detailed health status
GET    /api/system/settings       → System settings (admin only)
PATCH  /api/system/settings       → Update settings (admin only)
GET    /api/system/logs           → System logs (admin only)
```

### Business Logic Implementation

#### **Authentication Flow**
```go
// JWT token generation and validation
func GenerateJWT(userID uint, role string) (string, error) {
    claims := jwt.MapClaims{
        "user_id": userID,
        "role":    role,
        "exp":     time.Now().Add(time.Hour * 24).Unix(),
        "iat":     time.Now().Unix(),
    }
    
    token := jwt.NewWithClaims(jwt.SigningMethodHS256, claims)
    return token.SignedString([]byte(os.Getenv("JWT_SECRET")))
}

// Middleware for authentication
func AuthMiddleware() gin.HandlerFunc {
    return func(c *gin.Context) {
        authHeader := c.GetHeader("Authorization")
        if authHeader == "" {
            c.JSON(401, gin.H{"error": "Authorization header required"})
            c.Abort()
            return
        }
        
        tokenString := strings.Replace(authHeader, "Bearer ", "", 1)
        // Token validation logic...
    }
}
```

#### **Role-Based Access Control**
```go
// Role definitions
const (
    RoleCustomer     = "customer"
    RolePartner      = "partner" 
    RoleCollaborator = "collaborator"
    RoleInvestor     = "investor"
    RoleAdmin        = "admin"
)

// Permission middleware
func RequireRole(roles ...string) gin.HandlerFunc {
    return func(c *gin.Context) {
        userRole := c.GetString("user_role")
        for _, role := range roles {
            if userRole == role {
                c.Next()
                return
            }
        }
        c.JSON(403, gin.H{"error": "Insufficient permissions"})
        c.Abort()
    }
}
```

#### **Data Validation & Sanitization**
```go
// Input validation using validator
type ValidationError struct {
    Field   string `json:"field"`
    Tag     string `json:"tag"`
    Message string `json:"message"`
}

func ValidateStruct(s interface{}) []ValidationError {
    var errors []ValidationError
    validate := validator.New()
    
    err := validate.Struct(s)
    if err != nil {
        for _, err := range err.(validator.ValidationErrors) {
            errors = append(errors, ValidationError{
                Field:   err.Field(),
                Tag:     err.Tag(),
                Message: getErrorMessage(err),
            })
        }
    }
    return errors
}
```

### Required Go Packages
```go
// go.mod
module nebusis-backend

go 1.21

require (
    github.com/gin-gonic/gin v1.9.1
    github.com/gin-contrib/cors v1.4.0
    gorm.io/gorm v1.25.4
    gorm.io/driver/mysql v1.5.1
    github.com/golang-jwt/jwt/v5 v5.0.0
    golang.org/x/crypto v0.12.0
    github.com/go-playground/validator/v10 v10.15.3
    github.com/spf13/viper v1.16.0
    github.com/sirupsen/logrus v1.9.3
    golang.org/x/time v0.3.0
    github.com/google/uuid v1.3.0
    github.com/joho/godotenv v1.4.0
)
```

---

## 🔹 4. Database (MySQL)

### Database Schema

**File Location**: `/db/init.sql`

#### **Users & Authentication**
```sql
-- Users table with role-based access
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    role ENUM('customer', 'partner', 'collaborator', 'investor', 'admin') NOT NULL DEFAULT 'customer',
    phone VARCHAR(50),
    company VARCHAR(200),
    job_title VARCHAR(150),
    industry VARCHAR(100),
    country VARCHAR(100),
    avatar_url VARCHAR(500),
    email_verified_at TIMESTAMP NULL,
    email_verification_token VARCHAR(100),
    password_reset_token VARCHAR(100),
    password_reset_expires_at TIMESTAMP NULL,
    last_login_at TIMESTAMP NULL,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_users_email (email),
    INDEX idx_users_role (role),
    INDEX idx_users_active (is_active),
    INDEX idx_users_company (company)
);

-- User sessions for tracking active sessions
CREATE TABLE user_sessions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    token_hash VARCHAR(255) NOT NULL,
    ip_address VARCHAR(45),
    user_agent TEXT,
    expires_at TIMESTAMP NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    INDEX idx_sessions_user (user_id),
    INDEX idx_sessions_token (token_hash),
    INDEX idx_sessions_expires (expires_at)
);
```

#### **Applications & Products**
```sql
-- Business applications catalog
CREATE TABLE applications (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id VARCHAR(50) NOT NULL UNIQUE,
    name VARCHAR(200) NOT NULL,
    slug VARCHAR(100) NOT NULL UNIQUE,
    description TEXT NOT NULL,
    short_description VARCHAR(500),
    icon VARCHAR(100) NOT NULL,
    status ENUM('live', 'beta', 'coming_soon') NOT NULL DEFAULT 'coming_soon',
    category VARCHAR(100) NOT NULL,
    features JSON NOT NULL,
    target_industries JSON NOT NULL,
    requirements JSON,
    benefits JSON,
    use_cases JSON,
    integrations JSON,
    demo_url VARCHAR(500),
    documentation_url VARCHAR(500),
    thumbnail_url VARCHAR(500),
    gallery_images JSON,
    pricing_model VARCHAR(100) DEFAULT 'subscription',
    base_price DECIMAL(10,2),
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    display_order INT DEFAULT 0,
    is_featured BOOLEAN DEFAULT FALSE,
    is_public BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_applications_status (status),
    INDEX idx_applications_category (category),
    INDEX idx_applications_featured (is_featured),
    INDEX idx_applications_public (is_public),
    INDEX idx_applications_display (display_order),
    FULLTEXT KEY idx_applications_search (name, description)
);

-- Application pricing tiers
CREATE TABLE application_pricing_tiers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    application_id INT NOT NULL,
    tier_name VARCHAR(100) NOT NULL,
    tier_slug VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    billing_period ENUM('monthly', 'yearly', 'one_time') NOT NULL DEFAULT 'monthly',
    features JSON NOT NULL,
    user_limit INT,
    storage_limit_gb INT,
    api_calls_limit INT,
    support_level VARCHAR(100),
    is_popular BOOLEAN DEFAULT FALSE,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (application_id) REFERENCES applications(id) ON DELETE CASCADE,
    INDEX idx_pricing_application (application_id),
    INDEX idx_pricing_active (is_active),
    UNIQUE KEY unique_app_tier (application_id, tier_slug)
);
```

#### **Certifications & Education**
```sql
-- Certification programs
CREATE TABLE certifications (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id VARCHAR(50) NOT NULL UNIQUE,
    title VARCHAR(200) NOT NULL,
    slug VARCHAR(100) NOT NULL UNIQUE,
    description TEXT NOT NULL,
    short_description VARCHAR(500),
    price DECIMAL(10,2) NOT NULL DEFAULT 299.00,
    duration_hours INT NOT NULL,
    level ENUM('beginner', 'intermediate', 'advanced') NOT NULL,
    category VARCHAR(100) NOT NULL,
    prerequisites JSON,
    learning_outcomes JSON,
    competency_areas JSON,
    exam_format VARCHAR(100),
    exam_duration_minutes INT DEFAULT 120,
    passing_score INT DEFAULT 70,
    certificate_validity_years INT DEFAULT 3,
    recertification_required BOOLEAN DEFAULT TRUE,
    thumbnail_url VARCHAR(500),
    curriculum JSON,
    target_audience JSON,
    career_benefits JSON,
    industry_recognition JSON,
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    display_order INT DEFAULT 0,
    is_featured BOOLEAN DEFAULT FALSE,
    is_public BOOLEAN DEFAULT TRUE,
    enrollment_status ENUM('open', 'closed', 'waitlist') DEFAULT 'open',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_certifications_level (level),
    INDEX idx_certifications_category (category),
    INDEX idx_certifications_status (enrollment_status),
    INDEX idx_certifications_featured (is_featured),
    FULLTEXT KEY idx_certifications_search (title, description)
);

-- Certification enrollments
CREATE TABLE certification_enrollments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    certification_id INT NOT NULL,
    enrollment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    start_date TIMESTAMP NULL,
    completion_date TIMESTAMP NULL,
    exam_date TIMESTAMP NULL,
    score INT NULL,
    status ENUM('enrolled', 'in_progress', 'completed', 'failed', 'expired') DEFAULT 'enrolled',
    certificate_url VARCHAR(500),
    payment_status ENUM('pending', 'paid', 'failed', 'refunded') DEFAULT 'pending',
    notes TEXT,
    
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    FOREIGN KEY (certification_id) REFERENCES certifications(id) ON DELETE CASCADE,
    INDEX idx_enrollments_user (user_id),
    INDEX idx_enrollments_certification (certification_id),
    INDEX idx_enrollments_status (status),
    UNIQUE KEY unique_user_certification (user_id, certification_id)
);
```

#### **Sector Suites & Services**
```sql
-- Industry-specific solution suites
CREATE TABLE sector_suites (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id VARCHAR(50) NOT NULL UNIQUE,
    name VARCHAR(200) NOT NULL,
    slug VARCHAR(100) NOT NULL UNIQUE,
    description TEXT NOT NULL,
    short_description VARCHAR(500),
    industry VARCHAR(100) NOT NULL,
    target_market JSON,
    included_applications JSON,
    key_features JSON,
    benefits JSON,
    use_cases JSON,
    implementation_timeline VARCHAR(200),
    support_level VARCHAR(100),
    customization_options JSON,
    compliance_standards JSON,
    integration_capabilities JSON,
    thumbnail_url VARCHAR(500),
    gallery_images JSON,
    case_studies JSON,
    testimonials JSON,
    pricing_model VARCHAR(100) DEFAULT 'custom',
    base_price DECIMAL(10,2),
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    display_order INT DEFAULT 0,
    is_featured BOOLEAN DEFAULT FALSE,
    is_public BOOLEAN DEFAULT TRUE,
    availability_status ENUM('available', 'coming_soon', 'limited') DEFAULT 'available',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_sector_suites_industry (industry),
    INDEX idx_sector_suites_status (availability_status),
    INDEX idx_sector_suites_featured (is_featured),
    FULLTEXT KEY idx_sector_suites_search (name, description)
);

-- Digital transformation services
CREATE TABLE digital_transformation_services (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id VARCHAR(50) NOT NULL UNIQUE,
    name VARCHAR(200) NOT NULL,
    slug VARCHAR(100) NOT NULL UNIQUE,
    description TEXT NOT NULL,
    short_description VARCHAR(500),
    service_type VARCHAR(100) NOT NULL,
    methodology JSON,
    deliverables JSON,
    timeline JSON,
    pricing_model VARCHAR(100) DEFAULT 'project_based',
    base_price DECIMAL(10,2),
    pricing_factors JSON,
    target_industries JSON,
    technology_stack JSON,
    team_composition JSON,
    success_metrics JSON,
    case_studies JSON,
    prerequisites JSON,
    risk_factors JSON,
    mitigation_strategies JSON,
    thumbnail_url VARCHAR(500),
    gallery_images JSON,
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    display_order INT DEFAULT 0,
    is_featured BOOLEAN DEFAULT FALSE,
    is_public BOOLEAN DEFAULT TRUE,
    availability_status ENUM('available', 'coming_soon', 'limited') DEFAULT 'available',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_dt_services_type (service_type),
    INDEX idx_dt_services_status (availability_status),
    INDEX idx_dt_services_featured (is_featured),
    FULLTEXT KEY idx_dt_services_search (name, description)
);
```

#### **Lead Management & Communications**
```sql
-- Demo requests and lead tracking
CREATE TABLE demo_requests (
    id INT AUTO_INCREMENT PRIMARY KEY,
    request_id VARCHAR(50) NOT NULL UNIQUE,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL,
    phone VARCHAR(50),
    company VARCHAR(200) NOT NULL,
    job_title VARCHAR(150),
    industry VARCHAR(100),
    company_size ENUM('1-10', '11-50', '51-200', '201-1000', '1000+'),
    country VARCHAR(100),
    interested_products JSON NOT NULL,
    specific_requirements TEXT,
    preferred_demo_date DATE,
    preferred_time_slot ENUM('morning', 'afternoon', 'evening'),
    timezone VARCHAR(100),
    demo_type ENUM('online', 'onsite') DEFAULT 'online',
    priority_level ENUM('low', 'medium', 'high', 'urgent') DEFAULT 'medium',
    lead_source VARCHAR(100),
    utm_campaign VARCHAR(200),
    utm_source VARCHAR(200),
    utm_medium VARCHAR(200),
    status ENUM('new', 'contacted', 'scheduled', 'completed', 'lost', 'converted') DEFAULT 'new',
    assigned_to INT,
    notes TEXT,
    follow_up_date DATE,
    demo_scheduled_at TIMESTAMP NULL,
    demo_completed_at TIMESTAMP NULL,
    outcome VARCHAR(100),
    next_steps TEXT,
    conversion_value DECIMAL(10,2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (assigned_to) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_demo_requests_status (status),
    INDEX idx_demo_requests_assigned (assigned_to),
    INDEX idx_demo_requests_date (created_at),
    INDEX idx_demo_requests_company (company),
    INDEX idx_demo_requests_source (lead_source)
);

-- Contact messages and general inquiries
CREATE TABLE contact_messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message_id VARCHAR(50) NOT NULL UNIQUE,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL,
    phone VARCHAR(50),
    company VARCHAR(200),
    subject VARCHAR(300) NOT NULL,
    message TEXT NOT NULL,
    inquiry_type ENUM('general', 'sales', 'support', 'partnership', 'media', 'careers'),
    priority_level ENUM('low', 'medium', 'high', 'urgent') DEFAULT 'medium',
    status ENUM('new', 'in_progress', 'resolved', 'closed') DEFAULT 'new',
    assigned_to INT,
    response_sent BOOLEAN DEFAULT FALSE,
    response_content TEXT,
    response_sent_at TIMESTAMP NULL,
    lead_source VARCHAR(100),
    utm_campaign VARCHAR(200),
    utm_source VARCHAR(200),
    utm_medium VARCHAR(200),
    ip_address VARCHAR(45),
    user_agent TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (assigned_to) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_contact_messages_status (status),
    INDEX idx_contact_messages_type (inquiry_type),
    INDEX idx_contact_messages_assigned (assigned_to),
    INDEX idx_contact_messages_date (created_at)
);

-- Newsletter subscriptions
CREATE TABLE newsletter_subscriptions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    company VARCHAR(200),
    job_title VARCHAR(150),
    industry VARCHAR(100),
    interests JSON,
    subscription_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('pending', 'active', 'unsubscribed', 'bounced') DEFAULT 'pending',
    email_verified BOOLEAN DEFAULT FALSE,
    verification_token VARCHAR(100),
    verification_sent_at TIMESTAMP NULL,
    verified_at TIMESTAMP NULL,
    unsubscribed_at TIMESTAMP NULL,
    unsubscribe_reason VARCHAR(200),
    lead_source VARCHAR(100),
    utm_campaign VARCHAR(200),
    utm_source VARCHAR(200),
    utm_medium VARCHAR(200),
    last_engagement TIMESTAMP,
    engagement_score INT DEFAULT 0,
    
    INDEX idx_newsletter_status (status),
    INDEX idx_newsletter_verified (email_verified),
    INDEX idx_newsletter_date (subscription_date)
);
```

#### **Content Management**
```sql
-- Blog posts and articles
CREATE TABLE blog_posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(300) NOT NULL,
    slug VARCHAR(200) NOT NULL UNIQUE,
    excerpt VARCHAR(500),
    content LONGTEXT NOT NULL,
    featured_image VARCHAR(500),
    gallery_images JSON,
    author_id INT NOT NULL,
    category VARCHAR(100) NOT NULL,
    tags JSON,
    status ENUM('draft', 'published', 'archived') DEFAULT 'draft',
    featured BOOLEAN DEFAULT FALSE,
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    reading_time_minutes INT,
    view_count INT DEFAULT 0,
    share_count INT DEFAULT 0,
    published_at TIMESTAMP NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (author_id) REFERENCES users(id),
    INDEX idx_blog_posts_status (status),
    INDEX idx_blog_posts_category (category),
    INDEX idx_blog_posts_featured (featured),
    INDEX idx_blog_posts_published (published_at),
    FULLTEXT KEY idx_blog_posts_search (title, excerpt, content)
);

-- Video gallery
CREATE TABLE videos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(300) NOT NULL,
    slug VARCHAR(200) NOT NULL UNIQUE,
    description TEXT,
    video_url VARCHAR(500) NOT NULL,
    thumbnail_url VARCHAR(500),
    duration_seconds INT,
    category VARCHAR(100) NOT NULL,
    tags JSON,
    transcript TEXT,
    captions_url VARCHAR(500),
    quality_options JSON,
    view_count INT DEFAULT 0,
    like_count INT DEFAULT 0,
    share_count INT DEFAULT 0,
    featured BOOLEAN DEFAULT FALSE,
    status ENUM('draft', 'published', 'archived') DEFAULT 'draft',
    seo_title VARCHAR(200),
    seo_description VARCHAR(500),
    seo_keywords JSON,
    published_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_videos_category (category),
    INDEX idx_videos_status (status),
    INDEX idx_videos_featured (featured),
    INDEX idx_videos_published (published_at)
);
```

#### **User Subscriptions & Billing**
```sql
-- User application subscriptions
CREATE TABLE user_subscriptions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    application_id INT NOT NULL,
    pricing_tier_id INT NOT NULL,
    subscription_status ENUM('active', 'cancelled', 'expired', 'suspended') DEFAULT 'active',
    start_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    end_date TIMESTAMP NULL,
    next_billing_date TIMESTAMP NULL,
    auto_renew BOOLEAN DEFAULT TRUE,
    trial_end_date TIMESTAMP NULL,
    is_trial BOOLEAN DEFAULT FALSE,
    payment_method_id VARCHAR(100),
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    FOREIGN KEY (application_id) REFERENCES applications(id) ON DELETE CASCADE,
    FOREIGN KEY (pricing_tier_id) REFERENCES application_pricing_tiers(id),
    INDEX idx_subscriptions_user (user_id),
    INDEX idx_subscriptions_app (application_id),
    INDEX idx_subscriptions_status (subscription_status),
    INDEX idx_subscriptions_billing (next_billing_date),
    UNIQUE KEY unique_user_app_subscription (user_id, application_id)
);

-- Invoices and billing records
CREATE TABLE invoices (
    id INT AUTO_INCREMENT PRIMARY KEY,
    invoice_number VARCHAR(50) NOT NULL UNIQUE,
    user_id INT NOT NULL,
    subscription_id INT,
    amount DECIMAL(10,2) NOT NULL,
    tax_amount DECIMAL(10,2) DEFAULT 0,
    total_amount DECIMAL(10,2) NOT NULL,
    currency VARCHAR(3) DEFAULT 'USD',
    status ENUM('draft', 'sent', 'paid', 'overdue', 'cancelled') DEFAULT 'draft',
    due_date DATE NOT NULL,
    paid_date TIMESTAMP NULL,
    payment_method VARCHAR(100),
    payment_reference VARCHAR(200),
    line_items JSON NOT NULL,
    billing_address JSON,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    FOREIGN KEY (subscription_id) REFERENCES user_subscriptions(id) ON DELETE SET NULL,
    INDEX idx_invoices_user (user_id),
    INDEX idx_invoices_status (status),
    INDEX idx_invoices_due_date (due_date),
    INDEX idx_invoices_subscription (subscription_id)
);
```

#### **System Configuration**
```sql
-- System settings and configuration
CREATE TABLE system_settings (
    id INT AUTO_INCREMENT PRIMARY KEY,
    setting_key VARCHAR(100) NOT NULL UNIQUE,
    setting_value LONGTEXT,
    setting_type ENUM('string', 'number', 'boolean', 'json') DEFAULT 'string',
    category VARCHAR(100),
    description TEXT,
    is_public BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
    INDEX idx_settings_category (category),
    INDEX idx_settings_public (is_public)
);

-- Activity logs for audit trail
CREATE TABLE activity_logs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    action VARCHAR(100) NOT NULL,
    entity_type VARCHAR(100),
    entity_id INT,
    details JSON,
    ip_address VARCHAR(45),
    user_agent TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE SET NULL,
    INDEX idx_activity_logs_user (user_id),
    INDEX idx_activity_logs_action (action),
    INDEX idx_activity_logs_entity (entity_type, entity_id),
    INDEX idx_activity_logs_date (created_at)
);
```

### Database Relationships

#### **Primary Relationships:**
- **users** ↔ **user_subscriptions** (1:many)
- **users** ↔ **certification_enrollments** (1:many)
- **users** ↔ **demo_requests** (1:many via assigned_to)
- **applications** ↔ **application_pricing_tiers** (1:many)
- **applications** ↔ **user_subscriptions** (1:many)
- **certifications** ↔ **certification_enrollments** (1:many)
- **user_subscriptions** ↔ **invoices** (1:many)
- **users** ↔ **blog_posts** (1:many via author_id)

#### **Data Integrity Constraints:**
- Foreign key constraints with appropriate CASCADE/SET NULL actions
- Unique constraints on business-critical fields (email, slugs, product_ids)
- Check constraints on enum values and date ranges
- JSON validation on structured data fields

---

## 🔹 5. Folder & File Structure

```
nebusis-platform/
├── frontend/                      # React application
│   ├── public/
│   │   ├── assets/                # Static assets (as detailed above)
│   │   │   ├── logos/
│   │   │   ├── icons/
│   │   │   ├── images/
│   │   │   └── documents/
│   │   ├── favicon.ico
│   │   └── index.html
│   ├── src/
│   │   ├── components/            # Reusable components
│   │   │   ├── layout/
│   │   │   ├── ui/
│   │   │   ├── business/
│   │   │   ├── forms/
│   │   │   ├── charts/
│   │   │   └── shared/
│   │   ├── pages/                 # Page components
│   │   │   ├── website/
│   │   │   └── portal/
│   │   ├── hooks/                 # Custom React hooks
│   │   ├── lib/                   # Utility libraries
│   │   ├── store/                 # State management
│   │   ├── styles/                # CSS and styling
│   │   ├── types/                 # TypeScript definitions
│   │   ├── App.jsx                # Main app component
│   │   └── main.jsx               # Entry point
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── README.md
├── backend/                       # Go API server
│   ├── cmd/
│   │   └── server/
│   │       └── main.go            # Application entry point
│   ├── internal/
│   │   ├── config/                # Configuration management
│   │   │   └── config.go
│   │   ├── controllers/           # HTTP handlers
│   │   │   ├── auth.go
│   │   │   ├── users.go
│   │   │   ├── applications.go
│   │   │   ├── certifications.go
│   │   │   ├── demo_requests.go
│   │   │   ├── contact.go
│   │   │   ├── blog.go
│   │   │   ├── dashboard.go
│   │   │   └── system.go
│   │   ├── middleware/            # HTTP middleware
│   │   │   ├── auth.go
│   │   │   ├── cors.go
│   │   │   ├── logging.go
│   │   │   ├── ratelimit.go
│   │   │   └── validation.go
│   │   ├── models/                # Database models
│   │   │   ├── user.go
│   │   │   ├── application.go
│   │   │   ├── certification.go
│   │   │   ├── demo_request.go
│   │   │   ├── contact_message.go
│   │   │   ├── blog_post.go
│   │   │   ├── subscription.go
│   │   │   └── base.go
│   │   ├── routes/                # Route definitions
│   │   │   ├── auth.go
│   │   │   ├── api.go
│   │   │   ├── public.go
│   │   │   └── admin.go
│   │   ├── services/              # Business logic
│   │   │   ├── auth_service.go
│   │   │   ├── user_service.go
│   │   │   ├── email_service.go
│   │   │   ├── notification_service.go
│   │   │   └── analytics_service.go
│   │   ├── database/              # Database connection
│   │   │   ├── connection.go
│   │   │   └── migrations.go
│   │   └── utils/                 # Utility functions
│   │       ├── jwt.go
│   │       ├── hash.go
│   │       ├── validation.go
│   │       └── response.go
│   ├── pkg/                       # Public packages
│   │   └── logger/
│   │       └── logger.go
│   ├── uploads/                   # File uploads directory
│   ├── logs/                      # Application logs
│   ├── go.mod
│   ├── go.sum
│   └── README.md
├── db/                            # Database files
│   ├── init.sql                   # Database schema
│   ├── seeds.sql                  # Sample data
│   └── migrations/                # Database migrations
│       ├── 001_initial_schema.sql
│       ├── 002_add_indexes.sql
│       └── ...
├── docker-compose.yml             # Local development setup
├── docker-compose.prod.yml        # Production setup
├── .env.example                   # Environment variables template
├── .gitignore
└── README.md                      # This file
```

---

## 🔹 6. Setup Instructions

### Prerequisites
- **Docker** (version 20.10+)
- **Docker Compose** (version 2.0+)
- **Node.js** (version 18+) - for frontend development
- **Go** (version 1.21+) - for backend development
- **Make** (optional, for convenience commands)

### Local Development Setup

#### 1. Clone Repository
```bash
git clone <repository-url>
cd nebusis-platform
```

#### 2. Environment Configuration
```bash
# Copy environment template
cp .env.example .env

# Edit environment variables
nano .env
```

#### 3. Environment Variables (.env)
```bash
# Application
APP_ENV=development
APP_NAME="Nebusis Platform"
APP_URL=http://localhost:3000
API_URL=http://localhost:8080

# Database
DB_HOST=mysql
DB_PORT=3306
DB_NAME=nebusis_platform
DB_USER=nebusis_user
DB_PASSWORD=secure_password_here
DATABASE_URL=mysql://${DB_USER}:${DB_PASSWORD}@${DB_HOST}:${DB_PORT}/${DB_NAME}

# JWT Authentication
JWT_SECRET=your-super-secure-jwt-secret-change-this
JWT_EXPIRES_IN=24h

# Email Configuration
SMTP_HOST=smtp.sendgrid.net
SMTP_PORT=587
SMTP_USER=apikey
SMTP_PASSWORD=your-sendgrid-api-key
FROM_EMAIL=noreply@nebusis.com

# File Storage
UPLOAD_PATH=./uploads
MAX_FILE_SIZE=10485760  # 10MB

# Redis (for sessions/caching)
REDIS_HOST=redis
REDIS_PORT=6379
REDIS_PASSWORD=""

# External APIs
GOOGLE_ANALYTICS_ID=G-XXXXXXXXXX
RECAPTCHA_SITE_KEY=your-recaptcha-site-key
RECAPTCHA_SECRET_KEY=your-recaptcha-secret-key

# Security
CORS_ORIGINS=http://localhost:3000,http://localhost:5173
RATE_LIMIT_REQUESTS=100
RATE_LIMIT_WINDOW=900  # 15 minutes

# Portal Integration
PORTAL_URL=http://localhost:3000/portal
WEBSITE_URL=http://localhost:3000

# Logging
LOG_LEVEL=debug
LOG_FORMAT=json
```

#### 4. Start Development Environment
```bash
# Build and start all services
docker-compose up --build

# Or start in background
docker-compose up -d --build

# View logs
docker-compose logs -f
```

#### 5. Database Initialization
```bash
# Database will be automatically initialized with schema and sample data
# To manually run migrations:
docker-compose exec backend go run cmd/migrate/main.go

# To seed sample data:
docker-compose exec mysql mysql -u nebusis_user -p nebusis_platform < /docker-entrypoint-initdb.d/seeds.sql
```

#### 6. Frontend Development (Optional)
```bash
# For hot reloading during development
cd frontend
npm install
npm run dev
```

#### 7. Backend Development (Optional)
```bash
# For Go development with hot reloading
cd backend
go mod download
go install github.com/cosmtrek/air@latest
air
```

### Service URLs
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8080
- **Database**: localhost:3306
- **Redis**: localhost:6379

### Development Commands
```bash
# Start services
docker-compose up

# Stop services
docker-compose down

# Rebuild services
docker-compose up --build

# View logs
docker-compose logs -f [service-name]

# Execute commands in containers
docker-compose exec backend bash
docker-compose exec frontend sh
docker-compose exec mysql mysql -u root -p

# Database backup
docker-compose exec mysql mysqldump -u nebusis_user -p nebusis_platform > backup.sql

# Database restore
docker-compose exec -T mysql mysql -u nebusis_user -p nebusis_platform < backup.sql
```

---

## 🔹 7. Deployment Notes

### AWS Deployment Architecture

#### **Infrastructure Components**
- **Frontend**: S3 + CloudFront for static asset delivery
- **Backend**: ECS Fargate for containerized Go API
- **Database**: RDS MySQL for persistent data storage
- **File Storage**: S3 for user uploads and media
- **Caching**: ElastiCache Redis for session storage
- **Load Balancer**: Application Load Balancer (ALB)
- **CDN**: CloudFront for global content delivery
- **Monitoring**: CloudWatch + X-Ray for observability

#### **Deployment Strategy**
```yaml
# Production docker-compose.prod.yml example
version: '3.8'

services:
  backend:
    image: nebusis/backend:latest
    environment:
      - APP_ENV=production
      - DATABASE_URL=${RDS_DATABASE_URL}
      - REDIS_URL=${ELASTICACHE_REDIS_URL}
      - S3_BUCKET=${S3_BUCKET_NAME}
      - AWS_REGION=${AWS_REGION}
    deploy:
      replicas: 3
      resources:
        limits:
          memory: 512M
          cpus: '0.5'
        reservations:
          memory: 256M
          cpus: '0.25'
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/api/system/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

#### **Environment Configuration**
```bash
# Production environment variables
APP_ENV=production
DATABASE_URL=mysql://user:pass@rds-endpoint:3306/nebusis
REDIS_URL=redis://elasticache-endpoint:6379
S3_BUCKET=nebusis-production-assets
CDN_URL=https://cdn.nebusis.com
API_DOMAIN=api.nebusis.com
FRONTEND_DOMAIN=nebusis.com
```

#### **CI/CD Pipeline**
```yaml
# .github/workflows/deploy.yml
name: Deploy to AWS

on:
  push:
    branches: [main]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Build Frontend
        run: |
          cd frontend
          npm ci
          npm run build
          
      - name: Deploy Frontend to S3
        run: |
          aws s3 sync frontend/dist s3://${{ secrets.S3_BUCKET }}
          aws cloudfront create-invalidation --distribution-id ${{ secrets.CLOUDFRONT_ID }}
          
      - name: Build Backend Docker Image
        run: |
          docker build -t nebusis/backend:${{ github.sha }} backend/
          
      - name: Deploy Backend to ECS
        run: |
          aws ecs update-service \
            --cluster nebusis-cluster \
            --service nebusis-backend \
            --force-new-deployment
```

#### **Monitoring & Alerting**
- **Health Checks**: Automated health monitoring for all services
- **Metrics**: Custom CloudWatch metrics for business KPIs
- **Alerts**: SNS notifications for critical system events
- **Logging**: Centralized logging with CloudWatch Logs
- **Performance**: X-Ray tracing for request performance analysis

#### **Security Considerations**
- **VPC**: Private subnets for database and backend services
- **Security Groups**: Restrictive firewall rules
- **IAM**: Principle of least privilege for service roles
- **Secrets Manager**: Secure storage of sensitive configuration
- **WAF**: Web Application Firewall for DDoS protection
- **SSL/TLS**: End-to-end encryption with ACM certificates

#### **Backup & Disaster Recovery**
- **Database**: Automated RDS backups with point-in-time recovery
- **Files**: S3 cross-region replication for uploaded content
- **Configuration**: Infrastructure as Code with Terraform/CloudFormation
- **Monitoring**: Multi-region health checks and failover procedures

### Performance Optimization
- **CDN**: Global content delivery through CloudFront
- **Caching**: Redis for session data and frequent queries
- **Database**: Read replicas for improved query performance
- **Auto Scaling**: Automatic scaling based on traffic patterns
- **Compression**: Gzip compression for API responses and static assets

---

## 🔹 8. API Documentation & Testing

### API Documentation
- **Swagger/OpenAPI**: Auto-generated API documentation at `/api/docs`
- **Postman Collection**: Complete API collection for testing
- **Examples**: Request/response examples for all endpoints
- **Authentication**: JWT token examples and flow documentation

### Testing Strategy
```bash
# Backend testing
cd backend
go test ./...

# Frontend testing
cd frontend
npm run test

# Integration testing
docker-compose -f docker-compose.test.yml up --abort-on-container-exit

# Load testing
docker run --rm -i grafana/k6 run --vus 10 --duration 30s - < load-test.js
```

### Quality Assurance
- **Code Coverage**: Minimum 80% test coverage
- **Linting**: ESLint for frontend, golangci-lint for backend
- **Security Scanning**: Automated security vulnerability scanning
- **Performance Testing**: Regular performance benchmarking

---

This comprehensive README provides the complete blueprint for implementing the Nebusis® platform with a clean separation between React frontend, Go backend, and MySQL database, while supporting both public website functionality and authenticated portal features for all user types.

The architecture is designed for scalability, security, and maintainability, with clear separation of concerns and modern development practices throughout the stack.