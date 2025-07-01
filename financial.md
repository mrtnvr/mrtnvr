# FashionAI App Development Prompt for Claude Sonnet 4

## Project Overview

```
Create a complete SwiftUI app called "FashionAI" with the following core functionality:

The app allows users to upload their photos, then leverages OpenAI's APIs to generate new outfit ideas and visualize the user wearing these outfits. The app also provides product links for purchasing the suggested items.

TECHNICAL WORKFLOW:
1. User uploads a full-body photo
2. App sends image to OpenAI API requesting outfit suggestions
3. OpenAI returns JSON with outfit details, product links, and image URLs
4. App sends original image + returned JSON to GPT-image-1
5. GPT-image-1 generates visualization of user wearing the new outfit
6. App displays results with shopping options

ARCHITECTURE:
- MVVM architecture with SwiftUI for all UI components
- Combine framework for reactive programming
- Async/await for API communication
- Core Data for local storage
- CloudKit for user account synchronization
- Modular components for reusability across features
```

## Core Pages & Features

### 1. Onboarding & Authentication

```
Design an onboarding and authentication flow with:

UI COMPONENTS:
- Animated welcome carousel explaining core app functionality
- Email/Apple/Google sign-in options with SwiftUI SignInWithAppleButton and custom buttons
- Quick style quiz using SwiftUI TabView with page indicator style
- Progressive disclosure of permissions (camera, notifications)

FUNCTIONALITY:
- Secure authentication using Firebase Authentication or AWS Amplify
- Style quiz with 5 key questions to establish user preferences:
  • Style preferences (casual, formal, streetwear, etc.)
  • Color preferences (bright, neutral, monochrome, etc.)
  • Brand preferences (luxury, mid-range, budget)
  • Occasion preferences (work, weekend, special events)
  • Body confidence areas (areas they want to highlight/minimize)
- Onboarding data stored in UserDefaults and synced to CloudKit

VISUAL DESIGN:
- Clean, modern interface with ample whitespace
- Subtle animations for transitions between onboarding steps
- Clear progression indicators
- Neutral color palette with accessible contrast ratios
- Minimalist illustration style for onboarding concepts

TECHNICAL REQUIREMENTS:
- Keychain integration for credential storage
- BiometricAuthentication for quick re-entry
- Offline capability to complete onboarding without connectivity
- Analytics tracking for onboarding completion rate
```

### 2. Home Feed

```
Create a home feed screen that serves as the app's central hub:

LAYOUT COMPONENTS:
- Scrolling feed using LazyVStack inside ScrollView
- Section headers with horizontally scrolling content
- Floating action button for new outfit generation
- Pull-to-refresh functionality with custom animation
- Tab bar navigation using TabView

CONTENT SECTIONS:
- Personalized outfit suggestions based on style quiz
- "Trending Now" horizontal carousel of popular styles
- "Recently Generated" section showing user's history
- "Complete Your Look" suggestions based on past preferences
- Quick access to saved outfits

INTERACTION PATTERNS:
- Card-based UI with subtle shadow and corner radius
- Haptic feedback on important actions
- Double-tap to save outfits to collection
- Long-press for quick action menu
- Share button for social media integration

TECHNICAL FEATURES:
- Lazy loading images with progressive rendering
- Prefetching content based on scroll direction
- Caching system for offline viewing
- Background refresh for updated content
- Custom animations with matched geometry effect for transitions

VISUAL DESIGN:
- Dynamic typography respecting system settings
- Balanced image-to-text ratio (60/40)
- Consistent card design with 16pt corner radius
- System-based dark/light mode support
- Custom loading states with skeleton screens
```

### 3. Outfit Generation Flow

```
Design a streamlined outfit generation process with these components:

MULTI-STEP PROCESS:
1. Photo capture/selection screen
2. Processing/analysis screen
3. Results display screen

PHOTO CAPTURE SCREEN:
- Custom camera interface using AVFoundation
- Gallery access using PHPickerViewController
- Composition guides overlay for optimal positioning
- Real-time feedback on photo quality/suitability
- Example images showing ideal poses/lighting

PROCESSING EXPERIENCE:
- Animated progress indicator with percentage completion
- Informative processing stages explanation
- Cancel option with confirmation dialog
- Background processing capability
- Estimated time remaining indicator

RESULTS DISPLAY:
- Before/after image comparison using SwiftUI's ViewModifier
- Horizontal scroll of individual clothing items
- "Try Different Style" option for regeneration
- Save to collection button
- Share results functionality
- Product links with price information

API INTEGRATION:
- OpenAI API request formatting:
  • Image encoding as base64
  • System prompt for outfit generation
  • Temperature and top_p parameters optimized
- JSON parsing with Codable conformance
- Error handling with user-friendly messages
- Retry mechanism for failed requests
- Rate limiting management

TECHNICAL REQUIREMENTS:
- Efficient image resizing before API transmission
- Background thread processing
- Caching of results
- Progress tracking across API calls
- Timeout handling with appropriate user feedback
```

### 4. Product Discovery

```
Create a product discovery interface with these specifications:

LAYOUT STRUCTURE:
- Grid view of products using LazyVGrid
- Filtering system with expandable/collapsible controls
- Sort options (price, relevance, popularity)
- List/grid view toggle
- Search functionality with suggestion chips

PRODUCT CARDS:
- Image with lazy loading and caching
- Price with optional strikethrough for sales
- Brand name and product title
- Rating indicator (if available)
- "Save" button with animation
- Quick-look functionality

FILTERING SYSTEM:
- Price range slider using custom SwiftUI slider
- Category filter chips with multi-select
- Color filter with visual color swatches
- Size filter relevant to apparel type
- Brand filter with search capability
- "Similar style" filter based on AI matching

INTERACTION PATTERNS:
- Tap product card to view details
- Swipe actions for quick save/dismiss
- Pull-to-refresh for new recommendations
- Infinite scrolling with loading indicator
- Haptic feedback on filter application

TECHNICAL FEATURES:
- Efficient API pagination
- Local caching of product data
- Intelligent preloading based on user behavior
- Filter state persistence between sessions
- Deep linking capability to specific products
- Share product functionality
```

### 5. User Profile

```
Design a user profile screen with these components:

LAYOUT STRUCTURE:
- Header with user info and profile image
- Statistics section with key metrics
- Segmented control for different content categories
- Settings access point
- Premium status indicator (if applicable)

CONTENT SECTIONS:
- "Saved Outfits" collection using LazyVGrid
- "Generated History" with chronological list
- "Style Preferences" with visual representation
- "Wishlist" of saved products

PERSONALIZATION OPTIONS:
- Edit profile button and flow
- Update style preferences
- Notification preferences
- Privacy controls
- Connected accounts management

INTERACTION PATTERNS:
- Pull-to-refresh for latest data
- Tap outfit to view details/regenerate
- Long-press for quick actions menu
- Swipe actions on history items
- Double-tap to favorite

TECHNICAL REQUIREMENTS:
- CloudKit sync for user data
- Local caching for offline access
- Background refresh capability
- Efficient image caching system
- Data analytics for personalization improvement
```

### 6. Premium Upsell

```
Create a premium subscription page with these features:

LAYOUT STRUCTURE:
- Hero section with key value proposition
- Feature comparison table/cards
- Pricing options with visual hierarchy
- FAQ accordion section
- Testimonials carousel (if applicable)

SUBSCRIPTION TIERS:
- Clear presentation of free vs. paid features
- Monthly/annual toggle with savings calculation
- Family plan option (if applicable)
- Limited-time promotions (if applicable)
- Trial offer prominently displayed

FEATURE PRESENTATION:
- Icon-based feature list with clear explanations
- Feature showcase with before/after examples
- Usage limits visualized (e.g., 5/10 generations used)
- Premium-exclusive styles highlighted
- Higher-quality generation examples

PAYMENT FLOW:
- In-app purchase integration using StoreKit 2
- ApplePay button where applicable
- Secure payment messaging
- Clear subscription terms
- Restore purchases functionality
- Subscription management link

TECHNICAL REQUIREMENTS:
- StoreKit 2 implementation
- Server-side receipt validation
- Graceful degradation if IAP unavailable
- A/B testing framework for pricing optimization
- Analytics for conversion tracking
```

### 7. Settings

```
Design a comprehensive settings screen with these components:

LAYOUT STRUCTURE:
- Grouped table view using SwiftUI List
- Clear section headers with explanatory text
- Toggle switches for binary options
- Disclosure indicators for sub-screens
- Version information in footer

SETTINGS CATEGORIES:
- Account (profile, password, linked accounts)
- Privacy (data usage, sharing preferences)
- Notifications (types, frequency, quiet hours)
- Appearance (theme, text size, reduced motion)
- Storage & Data (cache management, offline mode)
- Help & Support (FAQ, contact, tutorials)
- About (version, terms, privacy policy)

INTERACTION PATTERNS:
- Immediate application of toggle changes
- Confirmation dialogs for important changes
- Form validation for inputs
- Back button with unsaved changes warning
- Deep links to system settings where needed

TECHNICAL IMPLEMENTATION:
- UserDefaults for preference storage
- Combine publishers for settings state
- Environment objects for app-wide settings
- Settings bundle for system settings integration
- Keychain for sensitive information
```

## Technical Implementation

```
CORE TECHNOLOGIES:
- Swift 5.9+ with SwiftUI 4.0+
- Combine framework for reactive programming
- Core Data for local persistence
- CloudKit for synchronization
- StoreKit 2 for in-app purchases
- AVFoundation for camera functionality
- URLSession for networking
- SwiftUI Animations for interactive elements

API INTEGRATION:
- OpenAI API client with proper authentication
- Robust error handling with user-friendly messages
- Request/response models conforming to Codable
- Rate limiting and retry logic
- Background processing for long-running operations
- Caching layer for reduced API calls

ARCHITECTURE PATTERNS:
- MVVM (Model-View-ViewModel) as primary pattern
- Repository pattern for data access
- Coordinator pattern for navigation flow
- Dependency injection for service management
- Protocol-oriented programming for flexibility
- Actor model for concurrency (Swift 5.5+)

DATA MANAGEMENT:
- Core Data stack with persistent history tracking
- CloudKit sync engine with conflict resolution
- Local caching strategy for images and API responses
- Efficient memory management for image processing
- Secure storage for authentication tokens
- Analytics events tracking with privacy considerations

PERFORMANCE CONSIDERATIONS:
- Image optimization before API transmission
- Background task scheduling for intensive operations
- Memory footprint monitoring and optimization
- Battery usage optimization
- Network bandwidth management
- Thermal efficiency for processing tasks
```

## Accessibility & Internationalization

```
ACCESSIBILITY REQUIREMENTS:
- VoiceOver support with meaningful labels
- Dynamic Type compatibility for all text elements
- Sufficient color contrast (WCAG AA minimum)
- Reduced motion option for animations
- Haptic feedback with appropriate intensity
- Keyboard/switch control navigation
- Image descriptions for AI-generated content

INTERNATIONALIZATION:
- Localization-ready string tables
- Adaptable layouts for text expansion/contraction
- Right-to-left layout support
- Date and number formatting for locales
- Culturally neutral imagery and icons
- Currency display adaptation
```

## Quality & Testing

```
TESTING STRATEGY:
- Unit tests for business logic and models
- UI tests for critical user flows
- Integration tests for API communication
- Snapshot tests for UI consistency
- Performance tests for critical operations
- Accessibility audit automation

QUALITY ASSURANCE:
- Error handling for all network operations
- Graceful degradation for offline scenarios
- Input validation with user feedback
- Edge case handling for unusual inputs
- Analytics for crash reporting
- User feedback mechanism
```

This comprehensive prompt provides Claude Sonnet 4 with all necessary information to generate a complete SwiftUI app for the FashionAI concept, with a regionless approach that can be adapted to various markets. The prompt covers all mandatory pages, technical implementation details, and considerations for creating a high-quality user experience.


# Enhanced European Expansion Plan: Detailed Regional Design Specifications

I'll provide a more comprehensive breakdown of design specifications tailored for each region, focusing on UI/UX elements, cultural considerations, and technical requirements.

## I. WESTERN EUROPE (DE/FR/NL/BE)

### Core Design Philosophy: *Eco-conscious precision with understated elegance*

#### Visual Identity
- **Color Palette:**
  - **Germany**: Slate grey (#4A4E4D) primary, accent colors in Prussian blue (#0B3C5D) and forest green (#136F63)
  - **France**: Cream base (#F8F4E3) with navy (#0D3B66) and burgundy (#841C26) accents, gold highlight (#D4AF37) for premium features
  - **Benelux**: Contemporary palette of dutch orange (#FF4F00), midnight blue (#003366), and warm neutrals (#E8DED2)

#### Typography System
- **Germany**: 
  - Primary: FF DIN Pro (precision-oriented geometric sans-serif)
  - Secondary: Roboto Slab for detailed information
  - Line height: 1.5x for optimal readability
  
- **France**: 
  - Primary: Didot for headings (luxury association)
  - Secondary: Avenir for body text (modern elegance)
  - Letter spacing: +5% for French language optimization

#### UI Component Library
- **Button Hierarchy:**
  - Primary: Rounded corners (8px), subtle drop shadow
  - Secondary: Outline style with 1.5px border weight
  - Tertiary: Text-only with animated underline on hover
  
- **Form Elements:**
  - Input fields with floating labels (Material Design influence)
  - Custom GDPR-compliant checkbox designs
  - Progress indicators showing completion percentage

#### Region-Specific Features

##### Germany-Specific
- **Sustainability Dashboard:**
  - Detailed metrics visualization using D3.js charts
  - CO₂ savings counter with comparative references (e.g., "Equivalent to 3 trees planted")
  - Monthly ecological impact report (downloadable as PDF)
  
- **Technical Specification Display:**
  - Detailed fabric composition breakdowns (percentages to 0.1%)
  - Manufacturing process transparency cards
  - Care instruction illustrations with German precision terminology

- **Data Privacy Controls:**
  - Granular permission settings beyond GDPR requirements
  - Data storage location selector (EU servers only)
  - One-click data export in machine-readable format

##### France-Specific
- **Artisanal Showcase:**
  - "Atelier" section highlighting handcrafted elements
  - Parallax scrolling for collection storytelling
  - Cinematic product transitions with subtle motion design

- **Fashion Calendar Integration:**
  - Paris Fashion Week event tie-ins
  - Seasonal color forecasting tools
  - "Heritage" filter showcasing historical influences in modern designs

#### Usability Considerations
- **Device Optimization:**
  - Desktop-first approach (65% of Western European users access via desktop)
  - Responsive breakpoints at 1440px, 1024px, 768px, 375px
  - Touch targets minimum 44x44px for mobile accessibility

- **Performance Metrics:**
  - Page load time target: <1.2s on 4G connections
  - First Contentful Paint: <0.8s
  - Time to Interactive: <2.5s

---

## II. NORDIC REGION (SE/DK/NO/FI)

### Core Design Philosophy: *Functional minimalism with nature-inspired elements*

#### Visual System
- **Color Palette:**
  - Primary: Glacier blue (#A5BBD9) to pine green (#3E5641) gradient
  - Secondary: Slate grey (#707070), birch white (#F2F2F2)
  - Seasonal accents: Northern lights purple (#5E3577) for winter
  
- **Spatial Design:**
  - Generous whitespace (minimum 24px margins)
  - Asymmetric grid layout inspired by Nordic architecture
  - 8px base unit for all spacing measurements

#### Typography System
- **Font Selection:**
  - Primary: GT America (modern Nordic sensibility)
  - Secondary: GT Sectra for headings (sharp serifs echo Nordic furniture design)
  - Supports Finnish diacritical marks (ä/ö) with optimized rendering

- **Text Hierarchy:**
  - H1: 36/42px (desktop/mobile)
  - H2: 24/28px (desktop/mobile)
  - Body: 16/18px (desktop/mobile)
  - Caption: 12/14px (desktop/mobile)

#### Specialized Components

- **Seasonal Adaptation System:**
  - Auto-dark mode algorithm tracking sunrise/sunset times
  - Winter theme (October-March): Darker background (#121212), reduced blue light
  - Summer theme (April-September): Lighter background (#F9F9F9), increased contrast

- **Sustainability Scorecard:**
  - Multi-parameter radar chart showing:
    - Material sustainability (5-point scale)
    - Production ethics (5-point scale)
    - Transportation footprint (5-point scale)
    - End-of-life recyclability (5-point scale)
  - Comparative visualization against industry averages

- **Interactive Elements:**
  - Custom scroll physics: 15% more momentum for smoother experience
  - Microinteractions with subtle natural sound effects (optional)
  - Focus states with 2px borders in contrasting colors for accessibility

#### Cultural Adaptations
- **Sweden-focused:**
  - "Lagom" filter preset (balanced, not excessive styling)
  - Integration with secondhand marketplaces (Tradera/Blocket)
  
- **Denmark-focused:**
  - "Hygge" collection featuring comfort-oriented styling
  - Social sharing templates with Danish design aesthetics
  
- **Finland-focused:**
  - High-contrast mode for dark winter months
  - Sisu-inspired achievement system (perseverance through challenges)

---

## III. BRITISH ISLES (UK/IE)

### Core Design Philosophy: *Heritage-inspired contemporary design with regional identity markers*

#### Visual Language
- **Color System:**
  - **UK Base**: Royal navy (#0A1045), burgundy (#7D1D3F), cream (#F2E8C6)
  - **Ireland Variant**: Emerald (#046307), slate (#58585B), cream (#F2E8C6)
  - **Premium Tier**: Gold accents (#CFB53B) and royal purple (#800080)

- **Pattern Library:**
  - Subtle tartan/plaid background textures (5% opacity)
  - Celtic knot decorative elements for loading states
  - Textile-inspired divider lines (tweed, herringbone patterns)

#### Interactive Elements
- **Navigation System:**
  - Tab bar with classic British understatement (thin lines, subtle transitions)
  - Toast notifications styled as "calling cards"
  - Pull-to-refresh with Union Jack/Irish flag animation (location-based)

- **Onboarding Experience:**
  - "High Street" metaphor for feature walkthrough
  - Heritage building illustrations as progress markers
  - Regional dialect options (Cockney, Scouse, Edinburgh, Dublin)

#### Weather Integration System
- **Dynamic Weather Responses:**
  - Real-time API connection to Met Office/Met Éireann
  - Outfit suggestions triggered by weather conditions:
    - Rain prediction: Waterproof outerwear suggestions
    - Cold snap: Layering recommendations
    - Heatwave: Breathable fabric prioritization
  
- **Seasonal Collections:**
  - Autumn/Winter: "Cozy Cotswolds" and "Highland Retreat" themes
  - Spring/Summer: "Garden Party" and "Coastal Getaway" themes
  - Festival season special collections (Glastonbury, Electric Picnic)

#### Technical Requirements
- **Payment Integration:**
  - Apple Pay/Google Pay primary CTAs
  - Open Banking connections (UK)
  - One-click currency conversion (£/€)
  
- **Accessibility Standards:**
  - WCAG 2.1 AA compliance minimum
  - Voice control optimization for British/Irish accents
  - High-contrast mode toggle in primary navigation

---

## IV. EASTERN EUROPE (PL/CZ/HU/RO)

### Core Design Philosophy: *Dynamic value-driven interfaces with promotional emphasis*

#### Visual Identity System
- **Color Strategy:**
  - **Poland**: Red (#D22730) and white (#FFFFFF) accents on charcoal base (#333333)
  - **Czechia**: Blue (#11457E), red (#D7141A), white (#FFFFFF) tricolor implementation
  - **Hungary**: Vibrant green (#6AB023) accents on neutral background
  - **Romania**: Yellow (#FFCD00), blue (#002B7F), red (#CE1126) color highlights

- **Animation Framework:**
  - Micro-animations for promotional elements (subtle bounce effects)
  - Entrance animations for new deals (sliding reveals)
  - Progress indicators with gamified elements

#### User Journey Optimization
- **Conversion Funnel:**
  - Reduced form fields (40% fewer than Western Europe version)
  - One-page checkout with instant validation
  - Multiple payment method display (side-by-side comparison)
  
- **Value Communication:**
  - Comparative pricing tables with highlighted savings
  - Bundle offers prominently displayed (30% more screen real estate)
  - Social proof indicators with local celebrity endorsements

#### Mobile-First Adaptations
- **Performance Optimization:**
  - Image lazy loading with low-res placeholders
  - Core functionality available offline (cached outfits)
  - Reduced JS bundle size for older Android devices (popular in region)
  
- **Interface Density:**
  - Information density 25% higher than Nordic version
  - Compact navigation (bottom tab bar with text labels)
  - Multi-function buttons to reduce screen clutter

#### Regional Feature Sets
- **Poland-Specific:**
  - BLIK payment integration (prominent placement)
  - "Paczkomat" delivery option integration
  - Flash sale countdown timers with push notifications
  
- **Romania-Specific:**
  - Cash on delivery payment option
  - Size conversion chart (Romanian/European/International)
  - Influencer curation from local fashion creators

---

## V. TÜRKIYE

### Core Design Philosophy: *Bold contemporary design bridging Eastern and Western aesthetics*

#### Visual Framework
- **Color System:**
  - Primary: Turkish red (#E30A17) with navy (#002D62) 
  - Secondary: Turquoise (#00B5CC) - cultural reference to Aegean Sea
  - Neutrals: Warm stone (#D6CFC7) and terracotta (#CD5C5C)
  - Gold accents (#D4AF37) for premium features

- **Imagery Guidelines:**
  - Bosphorus backdrop for onboarding screens
  - Architectural motifs from Ottoman design (subtle background patterns)
  - High-contrast product photography style with warm lighting

#### Typography System
- **Font Selection:**
  - Primary: GT Walsheim Pro (supports Turkish characters)
  - Secondary: Proxima Nova Alt
  - Special considerations for Turkish characters (ğ, ş, ı, İ, ç, ö, ü)
  - Right-to-left (RTL) layout support for Arabic loanwords

- **Text Hierarchy:**
  - Headlines: Bold, 120% letter spacing
  - Body text: Regular weight, 110% letter spacing
  - CTAs: All caps with custom Turkish character adjustments

#### Cultural Adaptation Layer
- **Regional Style Presets:**
  - "Istanbul Modern" filter (contemporary urban looks)
  - "Riviera" filter (Mediterranean coastal style)
  - "Anatolian Heritage" filter (traditional patterns in modern cuts)
  
- **Seasonal Adjustments:**
  - Ramadan collection with modest fashion options
  - Summer resort wear for tourist destinations
  - Winter layering for continental climate regions

#### Technical Implementation
- **Payment Ecosystem:**
  - Papara wallet integration (primary payment method)
  - Paycell SDK implementation
  - BIM cash integration for offline payments
  - QR code payment support
  
- **Performance Optimization:**
  - Proxy servers in Istanbul and Ankara for reduced latency
  - Progressive Web App functionality for intermittent connections
  - Reduced image sizes (30% smaller than Western Europe version)

- **Mobile Adaptation:**
  - Optimized for Android (72% market share in Türkiye)
  - Touch targets increased to 56px minimum (higher than Western Europe)
  - Specialized keyboard layout for Turkish character input

#### Content Strategy
- **Tone and Voice:**
  - Direct and action-oriented copywriting
  - Emphasis on value propositions and exclusivity
  - Use of Turkish idioms and cultural references
  
- **Notification System:**
  - Higher frequency than Nordic regions (2-3x weekly)
  - Dynamic pricing alerts with urgency messaging
  - Local holiday-themed promotional campaigns

---

## VI. CROSS-REGIONAL TECHNICAL FRAMEWORK

### Component Modularity System
- **Atomic Design Implementation:**
  - Core atoms (buttons, inputs, icons) with regional style overrides
  - Molecules (cards, form groups) with layout variations by region
  - Organisms (product displays, checkout flows) with region-specific logic

- **Design Token Architecture:**
  - Base tokens (spacing, typography, colors)
  - Semantic tokens (background, foreground, accent)
  - Component tokens (button-primary, card-background)
  - Regional override tokens (nordic-spacing-base, western-radius-base)

### Performance Benchmarks
| Region | Target Load Time | First Input Delay | Bundle Size |
|--------|------------------|-------------------|------------|
| Western | 1.2s | <100ms | <350KB |
| Nordic | 1.0s | <75ms | <320KB |
| British | 1.3s | <100ms | <360KB |
| Eastern | 1.5s | <150ms | <300KB |
| Türkiye | 1.8s | <200ms | <280KB |

### Localization Engine
- **Content Management:**
  - Region-aware CMS with variant control
  - A/B testing framework with regional segmentation
  - Automatic text expansion/contraction handling (German text typically 20% longer than English)

- **Asset Management:**
  - CDN with regional edge caching
  - Responsive image selection based on market-typical devices
  - Video transcoding optimized for regional network conditions

This detailed design specification provides comprehensive guidelines for implementing regionally-optimized versions of your app across all five European regions, ensuring both cultural relevance and technical efficiency.


# Regional Design Prompts for FashionAI App

Below are detailed design prompts for Claude Sonnet 4 to generate regional variations of each mandatory page in our FashionAI application.

## WESTERN EUROPE (Germany, France, Benelux)

### Onboarding / Login Screen

```
Generate a Western European onboarding/login screen for a fashion AI app with these specifications:

COLOR PALETTE:
- Primary: Prussian blue (#0B3C5D) for Germans, Navy (#0D3B66) for French
- Secondary: Forest green (#136F63) for eco-conscious elements
- Accent: Muted gold (#D4AF37) only for premium indicators
- Background: Light cream (#F8F4E3) with subtle linen texture

TYPOGRAPHY:
- German market: FF DIN Pro (geometric sans-serif)
- French market: Didot for headlines, Avenir for body text
- Font weights: Light for descriptions, Medium for actions, Bold for CTAs

LAYOUT:
- Authentication options arranged in precise vertical hierarchy
- GDPR compliance badge prominently positioned (top right)
- CO₂ savings indicator ("This digital experience saved 2.4g CO₂ vs. printed fashion")
- "Precision Engineering" micro-text below login button

CULTURAL ELEMENTS:
- German copy emphasizes data privacy with "DSGVO-konform" seal
- French version uses "Édition Exclusive" instead of "Premium"
- Social proof designed as "Trusted by X,XXX users in [city]" with dynamic city detection
- Minimalist background pattern derived from regional textile traditions

INTERACTIONS:
- Error messages appear inline (not as pop-ups)
- Form validation occurs in real-time with subtle green checkmarks
- Authentication buttons have understated hover states (1px border expansion)
- Style quiz presented as "precision calibration" for German market, "personal atelier" for French

TECHNICAL NOTES:
- Reduced motion option prominently available
- Font size 14pt minimum for accessibility
- GDPR-compliant data processing disclosure with expandable details
- Form fields with floating labels in Material Design style
```

### Home Feed

```
Create a Western European Home Feed for a fashion AI app with these specifications:

VISUAL STRUCTURE:
- Clean grid layout with 24px gutters
- Card-based outfit recommendations with shadow depth of 4px
- Status bar showing eco-impact metrics (prominently positioned)
- "Generate New Outfit" as floating action button using primary color

COLOR APPLICATION:
- White space utilized strategically (40% of screen area minimum)
- Content cards with 1px borders in #E0E0E0
- Category dividers in muted secondary color
- Trending items tagged with subtle burgundy indicator (French markets)

CONTENT HIERARCHY:
- Personalized recommendations labeled as "Curated Selection" (German) or "Sélection Personnalisée" (French)
- Trending section using social proof markers ("Popular in Berlin/Paris")
- New arrivals section with timestamp precision ("Added 4 hours ago")
- Feed transitions using fade effects rather than animations

REGIONAL ELEMENTS:
- German feed emphasizes technical specifications of fabrics
- French feed highlights designer influence and heritage
- Weather-appropriate suggestions with precise temperature indicators
- Carbon footprint displayed per outfit with comparative metrics

UI COMPONENTS:
- Filter system with precision parameters (fabric type, occasion, price range)
- Save/bookmark icon using outline style (filled on action)
- Sharing functionality with GDPR-compliant data notice
- Subtle loading states with linear progress indicators (no spinners)

INTERACTION DESIGN:
- Precision scrolling physics (reduced momentum)
- Double-tap to save outfit to collection
- Long-press for quick actions menu
- Pull-to-refresh with eco-impact animation ("Saved 0.5g CO₂")

TECHNICAL REQUIREMENTS:
- Image optimization for high-DPI displays (retina and above)
- Graceful loading states for slower connections
- Caching strategy for offline browsing capability
- Reduced motion option respecting system preferences
```

### Outfit Generation Flow

```
Design a Western European Outfit Generation Flow for a fashion AI app with these specifications:

STEP INDICATOR:
- Horizontal progress bar with precise percentage completion
- Step labels in sentence case with numerical indicators
- Current step highlighted with primary color
- Completed steps marked with subtle checkmark icon

PHOTO UPLOAD INTERFACE:
- Camera frame with golden ratio overlay guides
- Privacy notice prominently displayed ("Images processed in EU servers only")
- Gallery selection with recently used photos prioritized
- Clear technical requirements stated (resolution, lighting recommendations)

PROCESSING EXPERIENCE:
- Deterministic progress indicator (not indefinite spinner)
- Educational content about AI processing displayed during wait
- Estimated time remaining shown with second precision
- Subtle background animation suggesting computational processing

RESULTS DISPLAY:
- Split-screen before/after with precision slider
- Technical specifications panel (expandable)
- Product cards with transparent pricing and availability
- Sustainability scores for each suggested item

COLOR APPLICATION:
- Clinical white (#FFFFFF) background for upload area
- Processing screens use subtle gradient from primary to secondary colors
- Results page uses 10% tint of primary color as background
- Call-to-action buttons in full saturation primary color

TYPOGRAPHY:
- Technical information in monospaced font (suggesting precision)
- Step instructions in 16pt minimum size
- Product descriptions in serif font for French market, sans-serif for German
- Hierarchical type scale with 1.2 ratio between levels

REGIONAL ELEMENTS:
- German version includes detailed technical explanation of AI process
- French version emphasizes artistic transformation narrative
- Processing time expectations adjusted by country (Germans expect accuracy over speed)
- CO₂ savings calculation displayed after processing completes

INTERACTION PATTERNS:
- Swipe between outfit variations
- Pinch-to-zoom on generated outfit details
- Haptic feedback on completion (subtle, single vibration)
- Crossfade transitions between steps (no playful animations)
```

## NORDIC REGION (Sweden, Denmark, Norway, Finland)

### Home Feed

```
Create a Nordic region Home Feed for a fashion AI app with these specifications:

COLOR SYSTEM:
- Primary palette: Glacier blue (#A5BBD9) to pine green (#3E5641) gradient
- Background: Near-white (#F9F9F9) for summer, deeper slate (#121212) for winter
- Accent colors derived from Nordic landscapes (birch yellow, lake blue)
- Auto-adaptive lighting based on user's local sunrise/sunset times

LAYOUT PRINCIPLES:
- Generous whitespace (32px minimum margins)
- Asymmetric grid with natural proportions (golden ratio)
- Content density 30% lower than standard interfaces
- Outfit cards designed with shadow-free, flat aesthetic

NORDIC TYPOGRAPHY:
- GT America as primary typeface (supports Nordic characters)
- Text hierarchy with clear 1:1.5:2.5:4 scale
- Headlines aligned left, body text with comfortable 1.6 leading
- Diacritical marks (ä/ö/å) optimized for legibility at all sizes

SUSTAINABILITY FEATURES:
- CO₂ impact score prominently displayed for each outfit (top-right position)
- Material composition with sustainability indicators
- "Conscious Collection" label for eco-friendly options
- Community leaderboard showing carbon savings (anonymized)

VISUAL LANGUAGE:
- Nature-inspired iconography with thin 1.5px strokes
- Subtle texture inspired by Nordic textiles (only 3% opacity)
- Imagery featuring natural lighting conditions
- Micro-animations suggesting gentle wind movement (optional based on reduced motion settings)

FUNCTIONAL ELEMENTS:
- "Generate New Outfit" button using text-icon combination in primary color
- Seasonal recommendations section (dynamically adapts to local season)
- Usage analytics displayed as minimalist line graph
- Clear labeling system for price categories (dots instead of currency symbols)

CULTURAL ADAPTATIONS:
- Swedish content emphasizes "Lagom" (balanced, appropriate) aesthetic
- Danish interface includes "Hygge" filter for cozy, comfortable looks
- Norwegian version highlights outdoor-appropriate clothing
- Finnish adaptation includes high-contrast mode for dark winter months

INTERACTIONS:
- Subdued hover states (slight color shift without dimension change)
- Custom scrolling physics with momentum calibrated for precision
- Save function with subtle checkmark animation (no bounce)
- Nordic-specific sound design option (forest ambient sounds, togglable)
```

### Premium Upsell Page

```
Design a Nordic region Premium Upsell page for a fashion AI app with these specifications:

CORE AESTHETIC:
- Minimalist layout with functional negative space (40% of viewport)
- Content presented as horizontal cards rather than vertical list
- Muted pine green to glacier blue gradient as accent
- No flashy elements or artificial urgency indicators

VALUE COMMUNICATION:
- Focus on quality over quantity messaging
- "Usage optimization" rather than "unlimited access"
- Transparent comparison with actual usage statistics
- Sustainability benefits emphasized over pure features

PRICING STRUCTURE DISPLAY:
- Clean, single-column layout for pricing tiers
- Price points set at psychological thresholds in local currencies:
  • 149 SEK / 129 DKK / 159 NOK / 14.99€ (Finland)
- Annual discount presented as "Resource efficiency saving" rather than deal
- No countdown timers or limited-time offers

SUBSCRIPTION BENEFITS PRESENTATION:
- Benefits shown with simple iconography (1.5px line weight)
- Carbon footprint reduction highlighted as primary benefit
- Community contribution aspect emphasized
- "Digital Minimalism" as a feature (fewer ads, cleaner experience)

CULTURAL ELEMENTS:
- "Sustainable choice" badge for annual subscription
- Carbon offset certificate with each subscription
- Usage analytics comparing to regional average
- Nordic design principles highlighted in feature descriptions

VISUAL HIERARCHY:
- Most sustainable option subtly highlighted (not flashy)
- Benefits receive more visual weight than pricing
- Clear information hierarchy with ample breathing room
- Privacy information given prominent placement

TYPOGRAPHY:
- GT America with increased letter spacing (+5%)
- Headlines in light weight (300)
- Price figures in medium weight (500)
- Feature lists with generous line height (1.6x)

INTERACTION DESIGN:
- Selection mechanism uses subtle color fill rather than dramatic highlighting
- Hover states with minimal feedback (slight background shift)
- Form inputs with inline validation (no error popups)
- Downgrade option presented equally to upgrade options

TECHNICAL ELEMENTS:
- Optimized for screen readers and keyboard navigation
- Automatic currency detection with manual override
- Responsive layout preserving whitespace proportionally
- Reduced motion design for all transitions
```

## BRITISH ISLES (UK/Ireland)

### User Profile

```
Design a British Isles User Profile for a fashion AI app with these specifications:

VISUAL IDENTITY:
- Color palette: Royal navy (#0A1045) base with burgundy (#7D1D3F) accents for UK
- Irish variant: Emerald (#046307) and slate (#58585B) with cream background
- Subtle texture pattern inspired by regional textiles (tweed/herringbone at 4% opacity)
- Union Jack or Irish flag color influence in UI accents (location-based)

LAYOUT STRUCTURE:
- Classic portrait card with subtle drop shadow (8px blur, 30% opacity)
- Traditional grid layout with clear hierarchy and generous padding (24px)
- Weather-adaptive background (subtle rain effect for inclement weather)
- Saved outfits displayed in chronological order with date stamps

TYPOGRAPHY SYSTEM:
- Primary: Gill Sans for UK users, Garamond influences for Irish users
- Section headers in small caps with traditional serif details
- Body text at 16pt minimum with 1.5 line height
- Traditional typographic hierarchy with clear distinction between levels

PROFILE ELEMENTS:
- Style preferences visualized as traditional color swatch cards
- "Heritage" section showing influence of traditional British/Irish fashion
- Weather-appropriate outfit suggestions with local forecast integration
- Afternoon tea/pub time outfit recommendation feature (region specific)

CONTENT ORGANIZATION:
- Past generations organized by British/Irish seasonal calendar
- "Favourites" section with traditional bookmark icon
- Style preferences with proper British/English spelling conventions
- Local terminology for clothing items (jumper vs. sweater, etc.)

INTERACTIVE ELEMENTS:
- Traditional form controls with understated hover states
- Toast notifications styled as calling cards
- Pull-to-refresh with subtle animation inspired by rain/weather
- Preference toggles designed as classic switches rather than iOS-style toggles

CULTURAL ADAPTATIONS:
- UK version includes royal warrant-inspired "Premium Member" badge
- Irish version uses Celtic-inspired decorative elements
- Regional dialect options in settings (Cockney, Scouse, Dublin, etc.)
- Heritage color options reflecting regional identities

TECHNICAL CONSIDERATIONS:
- £/€ currency display based on location
- Optimization for popular British/Irish devices
- Offline functionality for rural areas with limited connectivity
- Integration with popular UK/Irish payment methods
```

### Settings Page

```
Create a British Isles Settings Page for a fashion AI app with these specifications:

PAGE STRUCTURE:
- Traditional settings list with clear categorization
- Section dividers using subtle double-line pattern
- Header with royal/Celtic-inspired decorative element
- Footer with regional customer support contact information

VISUAL ELEMENTS:
- Background in cream (#F2E8C6) with subtle paper texture
- Toggle switches in UK: navy/burgundy, Ireland: emerald/cream
- Icons using traditional line-drawing style (2px weight)
- Section headers with small ornamental flourish

SETTINGS CATEGORIES:
- "Account Details" with proper UK/Irish address formats
- "Notifications" with tea time / pub alerts option
- "Regional Preferences" for UK/Irish English terminology
- "Weather Integration" with Met Office/Met Éireann options
- "Payment Methods" with regional options (including Open Banking)
- "Privacy Controls" with expanded GDPR explanations

TYPOGRAPHY:
- Primary: Gill Sans for headings
- Secondary: Baskerville for descriptive text
- All navigation labels in proper British English
- Footer notes in smaller 12pt italic

COLOR APPLICATION:
- Category headers in primary color (navy or emerald)
- Selected options highlighted with subtle accent color
- Warning/delete options in traditional British racing red
- Success states in heritage green

INTERACTION PATTERNS:
- Traditional dropdown menus (not modern chips)
- Toggles with descriptive text on right side
- Expandable sections with (+/-) indicators
- Confirmation dialogs styled as formal notices

REGIONAL ADAPTATIONS:
- UK version includes Royal Mail delivery preferences
- Irish version includes An Post delivery options
- Northern Ireland shows dual currency options
- Regional weather alert sensitivity controls

ACCESSIBILITY FEATURES:
- High contrast mode with traditional color scheme
- Font size adjustment with heritage-inspired size markers
- Voice control optimized for British/Irish accents
- Keyboard navigation with traditional focus indicators

CONTENT TONE:
- Formal British English with proper honorifics
- Traditional phrasing for confirmations ("Would you like to...?" rather than "Want to...?")
- Proper noun capitalization following UK style guides
- Help text written in conversational but proper English
```

## EASTERN EUROPE (Poland, Czechia, Hungary, Romania)

### Outfit Generation Flow

```
Design an Eastern European Outfit Generation Flow for a fashion AI app with these specifications:

VISUAL STYLE:
- Color system: Dynamic palette with national color influences
  • Poland: Red (#D22730) accents on white (#FFFFFF) and charcoal (#333333)
  • Czechia: Blue (#11457E), red (#D7141A), white (#FFFFFF) as secondary colors
  • Hungary: Vibrant green (#6AB023) as accent color
  • Romania: Yellow (#FFCD00), blue (#002B7F), red (#CE1126) as accent system
- Bold typography with increased contrast ratios
- High color saturation for interactive elements
- Progress visualization with animated national patterns

UPLOAD INTERFACE:
- Camera frame with countdown timer animation
- Gallery selection with larger thumbnails (easier touch targets)
- Quick-access to recent photos (last 48 hours emphasized)
- Flash/lighting recommendations based on time of day
- Permission requests with clear value explanation

PROCESSING EXPERIENCE:
- Gamified waiting experience with outfit trivia
- Progress bar with percentage and time estimate
- Countdowns styled as digital clock displays
- Achievement system for completed generations
- "Boost processing" premium upsell (subtle placement)

RESULTS PRESENTATION:
- Before/after comparison with dramatic transition
- Product cards with prominent price/discount information
- "Similar items at better value" section highlighted
- Local store availability where applicable
- Social sharing templates optimized for regional platforms

LAYOUT STRUCTURE:
- Compact information density (25% higher than Western Europe)
- Multi-function buttons to reduce screen clutter
- Step indicators as numbered circles with bold typography
- Bottom sheet for additional options (swipe up to reveal)

INTERACTION PATTERNS:
- Haptic feedback on important actions (stronger than Western Europe)
- Swipe cards for alternative outfit suggestions
- Double-tap to save generated outfits
- Long-press for quick-actions menu
- Prominent share button optimized for regional platforms

REGIONAL ADAPTATIONS:
- Polish version highlights "Smart Value" indicators on products
- Romanian version includes cash on delivery payment options
- Size conversion charts between EU/local standards
- Local influencer style matching ("Your outfit matches [local celebrity] style")

PERFORMANCE OPTIMIZATIONS:
- Aggressive image compression for faster loading
- Reduced animation complexity for older devices
- Progressive loading of outfit details
- Offline capability for completed generations
```

### Product Discovery

```
Create an Eastern European Product Discovery page for a fashion AI app with these specifications:

LAYOUT STRUCTURE:
- Grid view with compact card design (3 items per row on standard devices)
- List view alternative with detailed specifications
- Filtering system positioned as persistent header
- Sort options prominently displayed (emphasizing price/value)

VISUAL ELEMENTS:
- Product cards with bold 2px borders
- Price tags with high-contrast display
- Discount indicators using bright accent colors (30% more vibrant than Western regions)
- Availability badges with clear visual hierarchy
- Local store indicators with distance information

COLOR SYSTEM:
- Background using light neutral (#F5F5F5) for maximum readability
- Interactive elements in region-appropriate accent colors:
  • Poland: Red (#D22730) CTAs with white text
  • Romania: Blue (#002B7F) and gold (#FFCD00) highlights
  • Hungary: Green (#6AB023) action buttons
- Price reduction highlights in bright red (#FF0000) with yellow backing
- In-stock indicators in vibrant green (#00CC00)

INFORMATION DISPLAY:
- Price displayed in larger font size (120% of Western Europe version)
- "Best value" badges on appropriate items
- Comparison features built into product cards
- Material composition with simplified icons
- Delivery time estimates prominently shown

INTERACTIVE ELEMENTS:
- Quick filter chips with popular local categories
- One-tap "notify when price drops" functionality
- Prominent wishlist/save buttons (25% larger touch targets)
- Comparison toggle to select multiple items
- Share button optimized for regional platforms (Messenger, Viber)

REGIONAL FEATURES:
- Cash on delivery payment badge where relevant
- Local size conversion system with quick reference
- Regional brand highlighting (promoting local manufacturers)
- Installment payment options clearly displayed
- Flash deal countdown timers for limited offers

PERFORMANCE CONSIDERATIONS:
- Image lazy loading with low-res placeholders
- Reduced JavaScript payload for older Android devices
- Offline catalog browsing capability
- Smaller initial page load (under 1MB)

CONTENT STRATEGY:
- Direct value proposition in product descriptions
- Technical specifications given priority over lifestyle descriptions
- Customer reviews prominently featured
- Social proof indicators ("X people bought this item")
- Clear indicators for imported vs. locally produced items
```

## TÜRKIYE

### Onboarding / Login

```
Design a Türkiye-specific Onboarding/Login experience for a fashion AI app with these specifications:

COLOR PALETTE:
- Primary: Turkish red (#E30A17) for key actions and branding
- Secondary: Deep navy (#002D62) for information and text
- Accent: Turquoise (#00B5CC) for highlights and secondary actions
- Background: Warm stone (#D6CFC7) with subtle traditional pattern texture
- Gold accents (#D4AF37) reserved for premium features only

VISUAL ELEMENTS:
- Bosphorus skyline silhouette as subtle footer element
- Geometric patterns inspired by traditional tiles (5% opacity background)
- Welcome animation incorporating east-meets-west visual metaphor
- Brand presentation incorporating both modern and traditional elements

TYPOGRAPHY:
- Primary font: GT Walsheim Pro (optimized for Turkish characters)
- Secondary: Proxima Nova Alt for body text
- Special handling for Turkish characters (ğ, ş, ı, İ, ç, ö, ü)
- Font rendering optimized for mobile devices popular in Turkey
- Text hierarchy with 16pt minimum size for readability

AUTHENTICATION EXPERIENCE:
- Social login options prioritized (Instagram most prominent)
- Mobile number login option with Türkiye country code (+90) pre-selected
- Quick login via SMS verification (primary path)
- QR code login option for returning users
- Turkish e-government integration option (secondary)

STYLE QUIZ PRESENTATION:
- Questions presented as rich visual cards with large touch targets
- Regional style categories included ("Istanbul Modern", "Anatolian Heritage")
- Progress indicator styled as traditional ceramic tile pattern
- Reduced number of steps (5 maximum) for faster completion
- Results displayed with cultural style references

CULTURAL ADAPTATIONS:
- Copy emphasizing both modern trends and traditional influences
- Modest fashion options prominently included in style categories
- Seasonal adjustments for Ramadan and other cultural periods
- Regional size chart incorporated early in onboarding process

INTERACTION PATTERNS:
- Slightly higher animation energy than European versions
- Haptic feedback on quiz completion
- Error states with friendly, conversational messaging
- Direct path to home feed (reduced friction)
- Sound effects toggle (defaulted to off)

TECHNICAL CONSIDERATIONS:
- Optimized for Android devices (72% market share)
- Reduced initial download size for mobile network constraints
- Offline functionality for style quiz
- Data-saving mode option prominently offered
- Turkish keyboard layout support with predictive text
```

### Premium Upsell Page

```
Create a Türkiye-specific Premium Upsell Page for a fashion AI app with these specifications:

PAGE STRUCTURE:
- Hero section with dynamic Istanbul/Ankara background
- Three-tier pricing structure with visual hierarchy
- Feature comparison in condensed table format
- Testimonials from Turkish fashion influencers
- Special offer banner with countdown element

COLOR IMPLEMENTATION:
- Primary: Rich Turkish red (#E30A17) for headline and primary CTA
- Gold (#D4AF37) for premium tier highlighting
- Turquoise (#00B5CC) for comparative advantage indicators
- Deep navy (#002D62) for stable text elements
- Background gradient from warm stone (#D6CFC7) to cream

PRICING DISPLAY:
- TRY (₺) currency with comma as decimal separator
- Monthly price in larger type (32pt minimum)
- Annual option with "2 months free" promotion
- Installment payment options clearly indicated (3/6/12 months)
- "Most Popular" flag on mid-tier option with gold accent

FEATURE PRESENTATION:
- "Exclusive designs" emphasized over "unlimited usage"
- Comparative value callouts ("3x more designs than free")
- Early access to seasonal collections highlighted
- Direct shopping discounts prominently featured
- Local designer collaborations as premium benefit

CULTURAL ELEMENTS:
- "Special occasion" outfit generator for weddings/holidays
- Regional style filters ("Istanbul Modern", "Aegean Coastal")
- Mobile-first experience optimization
- QR code payment option displayed
- Turkish celebrity style matching feature

VISUAL LANGUAGE:
- Traditional patterns as section dividers (subtle application)
- Modern interface with traditional color influences
- Progress animations for subscription activation
- Custom illustrations blending contemporary and traditional elements

TYPOGRAPHY:
- Headlines: Bold GT Walsheim Pro with increased letter spacing
- Feature list: 16pt minimum with generous line height
- Pricing figures: 42pt for emphasis with ₺ symbol at 32pt
- Legal text: 12pt minimum (larger than Western European version)

PROMOTIONAL ELEMENTS:
- Limited-time offer banner with actual countdown
- "First 7 days free" trial prominently displayed
- Referral program incentive (30% discount for friend referrals)
- Papara payment discount callout (where applicable)
- Mobile operator billing option with provider logos

TECHNICAL CONSIDERATIONS:
- Payment system integration with Turkish providers
- Smooth degradation for older Android devices
- Compressed images for faster loading on mobile networks
- Cache strategy for offline viewing of premium features
- Turkish character rendering optimization
```

I've created detailed design prompts for Claude that outline the region-specific design considerations for key pages in the FashionAI app. Each prompt includes detailed specifications for visual elements, cultural adaptations, technical requirements, and interaction patterns tailored to each regional market.


