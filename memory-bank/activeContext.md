# CollabFlow Active Context

*Last Updated: March 20, 2025*

## Current Focus

The current development focus is on enhancing the document management functionality with Dropbox integration:

1. **Document Management with Dropbox**
   - Implementing secure OAuth flow with PKCE
   - Building real file operations with Dropbox API
   - Creating folder and file upload functionality
   - ✅ Fixed authentication and token refresh issues
   - ✅ Migrated from deprecated auth-helpers-nextjs to new @supabase/ssr
   - ✅ UI improvements for better usability and alignment with design system

2. **Authentication Improvements**
   - ✅ Enhanced Supabase client for better cookie handling
   - ✅ Implemented session refresh mechanism
   - ✅ Using Supabase client singleton pattern
   - ✅ Fixed cookies API usage for Next.js 15+
   - ✅ Resolved route conflicts causing authentication errors
   - ✅ Removed development mode bypass for consistent auth behavior

3. **CSS Modernization**
   - ✅ Updated src/app/globals.css to use modern CSS variables and syntax
   - ✅ Replaced all @apply directives with direct CSS properties
   - ✅ Fixed form input styling for better dark mode compatibility
   - ✅ Updated color references to use HSL format with CSS variables
   - ✅ Improved scrollbar styling with modern CSS variables
   - ✅ Enhanced AI component styling for better theme consistency
   - ✅ Fixed task item styling to use CSS variables for colors
   - ✅ Resolved CSS warnings related to unknown @tailwind and @apply directives

## Recent Changes

### UI Style Guardian MCP Server (NEW)

1. **Style Validation System**
   - ✅ Created a custom MCP server for UI style consistency
   - ✅ Implemented component validation against style guidelines
   - ✅ Added style rule recommendations for different component types
   - ✅ Created comprehensive style guide resources
   - ✅ Built system to detect and fix theme inconsistencies

### CSS Modernization

1. **Tailwind CSS Syntax Updates**
   - ✅ Replaced deprecated `@tailwind` directives with modern `@import "tailwindcss"` syntax
   - ✅ Removed all instances of `@apply` in favor of direct CSS properties
   - ✅ Updated all color references to use HSL format with CSS variables
   - ✅ Fixed CSS warnings in VS Code related to unknown directives

2. **Component Styling Improvements**
   - ✅ Updated form input styling for better dark mode compatibility
   - ✅ Enhanced AI component styling for better theme consistency
   - ✅ Improved scrollbar styling with modern CSS variables
   - ✅ Fixed task item styling to use CSS variables for colors
   - ✅ Standardized color usage across all components

3. **Dark Mode Enhancements**
   - ✅ Fixed form input styling in dark mode for better visibility
   - ✅ Updated modal dialog styling for dark mode consistency
   - ✅ Improved contrast for text elements in dark mode
   - ✅ Standardized dark mode color variables across components

### Authentication System Enhancements

1. **Supabase SSR Migration**
   - ✅ Migrated from deprecated @supabase/auth-helpers-nextjs to @supabase/ssr
   - ✅ Updated createClientComponentClient to createBrowserClient
   - ✅ Updated createServerComponentClient to createServerClient
   - ✅ Updated createRouteHandlerClient to createServerClient
   - ✅ Fixed cookie handling with proper await/async patterns
   - ✅ Added explicit cookie management functions

2. **AuthGuard Component**
   - ✅ Created AuthGuard component to protect routes
   - ✅ Implemented redirect to login for unauthenticated users
   - ✅ Added loading state for authentication checks
   - ✅ Removed development mode bypass for consistent behavior

3. **Global Context Updates**
   - ✅ Updated GlobalContext to use Supabase client singleton
   - ✅ Added refreshSession function for manual session refresh
   - ✅ Improved error handling for authentication operations

4. **Supabase Client Singleton**
   - ✅ Implemented singleton pattern for Supabase client
   - ✅ Centralized client creation in clientSingleton.ts
   - ✅ Ensured consistent client usage across the application

5. **Route Conflict Resolution**
   - ✅ Fixed conflicting routes at /app (route.ts vs page.tsx)
   - ✅ Moved route handler to API routes for better separation of concerns
   - ✅ Ensured consistent authentication flow in both development and production

### Document Management Integration

1. **Dropbox Authentication**
   - Implemented OAuth flow for Dropbox authentication with PKCE
   - Fixed cookie handling in Supabase client
   - Enhanced token storage and refresh mechanism
   - Created API routes for token exchange and revocation
   - Added robust error handling and state validation

2. **Document UI**
   - Developed DocumentsUi component for browsing documents
   - Added file upload dialog with Dropbox integration
   - Added folder creation functionality
   - Implemented real Dropbox API integration
   - Removed mock implementation for production use
   - ✅ Improved UI layout with centralized search bar
   - ✅ Added three-dot menu for additional actions (Projects filter, Favorites, Refresh, Disconnect)
   - ✅ Cleaned up redundant UI elements for better usability
   - ✅ Aligned "Documents" heading with "Overview" for consistent design
   - ✅ Removed unnecessary descriptive text to optimize space

3. **Database Schema**
   - Created tables for documents, versions, and project associations
   - Implemented RLS policies for security
   - Added functions for document queries

## Active Decisions

### Authentication Strategy

We've decided to use a centralized authentication approach with the following components:

1. **GlobalContext**
   - Manages authentication state
   - Provides user information throughout the application
   - Handles session refresh

2. **AuthGuard**
   - Protects routes from unauthenticated access
   - Redirects to login page when needed
   - Shows loading state during authentication checks
   - Maintains consistent behavior between development and production environments

3. **Supabase Client Singleton**
   - Ensures single instance of Supabase client
   - Provides consistent authentication state
   - Simplifies client usage across components
   - Uses new @supabase/ssr package for Next.js 15+ compatibility

4. **Next.js Middleware**
   - Handles server-side session validation
   - Redirects unauthenticated users from protected routes
   - Ensures session cookies are properly managed
   - Maintains consistent authentication rules across all environments

### CSS and Styling Approach

For CSS and styling, we've chosen the following approach:

1. **Modern CSS Variables**
   - Use CSS variables for colors, spacing, and other design tokens
   - Implement HSL color format for better theme switching
   - Maintain consistent variable naming across components

2. **Direct CSS Properties**
   - Use direct CSS properties instead of Tailwind's @apply directive
   - Maintain clear, readable CSS with proper organization
   - Group related styles together for better maintainability

3. **Theme Consistency**
   - Ensure consistent styling between light and dark themes
   - Use CSS variables for theme-specific values
   - Test all components in both themes for visual consistency

4. **Component-Specific Styling**
   - Keep component styles close to component definitions
   - Use consistent class naming conventions
   - Avoid global styles that might cause conflicts

### Document Management Approach

For document management, we've chosen the following approach:

1. **Dropbox Integration**
   - Use Dropbox API for document storage
   - Implement OAuth for authentication
   - Store tokens securely in Supabase

2. **Local Metadata**
   - Store document metadata in Supabase
   - Track versions and associations
   - Implement RLS for security

3. **Synchronization Strategy**
   - Two-way sync between local metadata and Dropbox
   - Version tracking for conflict resolution
   - Background sync for seamless experience

4. **User Interface Design**
   - Clean, minimal interface focused on content
   - Consistent alignment with other components
   - Efficient use of space with contextual controls
   - Three-dot menu pattern for secondary actions
   - Search functionality prominently accessible

## Current Challenges

### CSS and Styling Challenges (RESOLVED)

1. **Tailwind CSS Compatibility**
   - ✅ Resolving warnings for unknown @tailwind directives
   - ✅ Updating deprecated @apply usage
   - ✅ Ensuring proper CSS variable usage

2. **Dark Mode Consistency**
   - ✅ Ensuring consistent styling in dark mode
   - ✅ Fixing form input visibility in dark mode
   - ✅ Maintaining proper contrast ratios

3. **Component Styling Consistency**
   - ✅ Standardizing styling approach across components
   - ✅ Ensuring consistent spacing and alignment
   - ✅ Maintaining visual hierarchy in different themes

### Authentication Challenges (RESOLVED)

1. **Session Management**
   - ✅ Ensuring consistent session state across components
   - ✅ Handling session expiration gracefully
   - ✅ Refreshing tokens without disrupting user experience

2. **Route Protection**
   - ✅ Protecting nested routes efficiently
   - ✅ Handling redirects after authentication
   - ✅ Preserving state during authentication flow

3. **Cookie API Compatibility**
   - ✅ Updated to use async cookies() API in Next.js 15+
   - ✅ Implemented proper cookie functions for get, set, remove
   - ✅ Fixed cookie handling across server and client components

4. **Route Conflicts**
   - ✅ Resolved conflict between route handler and page component at /app
   - ✅ Moved route handler to API routes for better separation of concerns
   - ✅ Ensured consistent authentication flow in both development and production

### Document Management Challenges

1. **OAuth Complexity**
   - ✅ Managing OAuth flow securely
   - ✅ Handling token refresh and revocation
   - Dealing with API rate limits

2. **Synchronization**
   - Resolving conflicts between local and remote changes
   - Handling large file uploads and downloads
   - Maintaining performance during sync operations

3. **UI Consistency**
   - ✅ Ensuring consistent design across various views
   - ✅ Making efficient use of screen space
   - ✅ Providing intuitive access to common actions

## Next Steps

### Short-term Tasks

1. **CSS and Styling**
   - ✅ Fix CSS warnings in globals.css
   - ✅ Update component styling to use modern CSS variables
   - ✅ Improve dark mode compatibility
   - Audit remaining components for styling consistency
   - Document CSS variables and styling conventions

2. **Authentication**
   - ✅ Migrate from deprecated auth-helpers to @supabase/ssr
   - ✅ Fix cookie handling in Next.js 15+
   - ✅ Resolve route conflicts causing authentication errors
   - ✅ Ensure consistent authentication behavior across environments
   - Test AuthGuard with various routes
   - Implement remember me functionality
   - Add session timeout handling

3. **Document Management**
   - ✅ Complete file operations (upload/download)
   - ✅ Implement version history viewer
   - ✅ Add project filtering for documents
   - ✅ Improve UI layout and functionality
   - Add document metadata editing

### Medium-term Tasks

1. **Project Component**
   - Implement project archiving
   - Add advanced filtering options
   - Create project statistics dashboard

2. **Document Management**
   - Develop real-time sync worker
   - Implement permission mapping
   - Add document preview functionality

### Long-term Tasks

1. **Email Integration**
   - Research OAuth for email providers
   - Design unified email interface
   - Implement project-email associations

2. **AI Enhancements**
   - Develop specialized AI assistants
   - Implement document analysis features
   - Create context-aware recommendations

## Implementation Considerations

### CSS Implementation

The CSS modernization follows this pattern:

```css
/* Modern CSS variables approach */
:root {
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;
  --card: 0 0% 100%;
  --card-foreground: 222.2 84% 4.9%;
  /* Other variables */
}

.dark-theme {
  --background: 10 10% 5%;
  --foreground: 210 40% 98%;
  /* Dark theme variables */
}

/* Component styling with direct CSS properties */
.component {
  background-color: hsl(var(--background));
  color: hsl(var(--foreground));
  border-radius: 0.5rem;
  /* Other properties */
}

/* Theme-specific styling */
.component:hover {
  background-color: hsl(var(--accent));
}
```

### Authentication Implementation

The authentication system now uses the following pattern:

```typescript
// middleware.ts (with consistent behavior between environments)
export async function middleware(request: NextRequest) {
  return await updateSession(request);
}

// updateSession (in lib/supabase/middleware.ts)
export async function updateSession(request: NextRequest) {
  const response = NextResponse.next();
  const supabase = createServerClient(/* config */);
  
  try {
    const { data: { session } } = await supabase.auth.getSession();
    
    if (!session && request.nextUrl.pathname.startsWith('/app')) {
      const url = request.nextUrl.clone();
      url.pathname = '/auth/login';
      return NextResponse.redirect(url);
    }
  } catch (error) {
    console.error('Auth validation failed:', error);
    
    if (request.nextUrl.pathname.startsWith('/app')) {
      const url = request.nextUrl.clone();
      url.pathname = '/auth/login';
      return NextResponse.redirect(url);
    }
  }
  
  return response;
}

// AuthGuard.tsx (consistent behavior across environments)
export function AuthGuard({ children }: AuthGuardProps) {
  const { user, loading, refreshSession } = useGlobal();
  const router = useRouter();
  const pathname = usePathname();

  useEffect(() => {
    let isRedirecting = false;
    
    const checkAuth = async () => {
      if (isRedirecting || pathname.startsWith('/auth/')) {
        return;
      }
      
      if (!loading && !user) {
        try {
          isRedirecting = true;
          const success = await refreshSession();
          
          if (!success) {
            sessionStorage.setItem("redirectAfterLogin", pathname);
            router.push("/auth/login");
          } else {
            isRedirecting = false;
          }
        } catch (error) {
          console.error("Auth check error:", error);
          isRedirecting = false;
        }
      }
    };

    checkAuth();
    
    return () => {
      isRedirecting = false;
    };
  }, [user, loading, refreshSession, router, pathname]);

  if (loading || (!user && !loading)) {
    return <LoadingSpinner />;
  }

  return <>{children}</>;
}
```

### Document Management Implementation

The document management system uses the following pattern:

```typescript
// useDropboxAuth.ts
export function useDropboxAuth() {
  const supabase = getSupabaseClient();
  const { user: globalUser } = useGlobal();
  
  // Authentication state
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [tokens, setTokens] = useState<DropboxToken | null>(null);
  
  // Check authentication status
  const checkAuth = useCallback(async () => {
    // Check if user is authenticated with Dropbox
    // ...
  }, [supabase, globalUser]);
  
  // Connect to Dropbox
  const getAuthUrl = useCallback(() => {
    // Generate OAuth URL
    // ...
  }, []);
  
  // Handle OAuth callback
  const handleCallback = useCallback(async (code: string, state: string) => {
    // Exchange code for tokens
    // ...
  }, [supabase, globalUser]);
  
  // List files
  const listFiles = useCallback(async (path: string = "") => {
    // List files from Dropbox
    // ...
  }, [tokens]);
  
  // ... other methods
  
  return {
    isAuthenticated,
    getAuthUrl,
    handleCallback,
    listFiles,
    // ... other values
  };
}

// useDocuments.ts
export function useDocuments({ projectId, searchQuery }: UseDocumentsParams = {}) {
  const supabase = getSupabaseClient();
  const { user, loading: authLoading, refreshSession } = useGlobal();
  
  // Fetch documents
  const fetchDocuments = useCallback(async () => {
    // Fetch documents from Supabase
    // ...
  }, [supabase, projectId, searchQuery, user, refreshSession]);
  
  // Create document
  const createDocument = useCallback(async (document: DocumentInsert, projectIds?: string[]) => {
    // Create document in Supabase
    // ...
  }, [supabase, fetchDocuments]);
  
  // ... other methods
  
  return {
    documents,
    isLoading: query.isLoading || isLoading || authLoading,
    createDocument,
    // ... other values
  };
}
```

### Document UI Improvements

The Document UI component has been improved with the following pattern:

```tsx
// DocumentsUi.tsx
return (
  <div className="space-y-6">
    <div className="flex flex-col space-y-4 mb-4">
      <div className="flex justify-between items-center">
        <h2 className="text-xl font-semibold">Documents</h2>
        
        {/* Search Bar - centered and resized */}
        <div className="relative w-80 mx-auto">
          <input
            type="text"
            placeholder="Search"
            className="w-full px-4 py-2 border rounded-md"
            value={searchTerm}
            onChange={handleSearchChange}
          />
          {/* Search Results Dropdown */}
          {showSearchResults && <SearchResultsList results={searchResults} />}
        </div>
        
        {/* Toolbar buttons */}
        <div className="flex items-center gap-2">
          {/* View Toggle */}
          <ViewToggle viewMode={viewMode} setViewMode={setViewMode} />
          
          {/* Upload Button */}
          <UploadButton uploadFile={uploadFile} createFolder={createFolder} />
          
          {/* Three-dot Menu */}
          <ThreeDotsMenu 
            activeProjectFilter={activeProjectFilter}
            setActiveProjectFilter={setActiveProjectFilter}
            showFavoritesOnly={showFavoritesOnly}
            setShowFavoritesOnly={setShowFavoritesOnly}
            fetchDropboxFiles={fetchDropboxFiles}
            disconnectDropbox={disconnectDropbox}
          />
        </div>
      </div>
    </div>
    
    {/* Documents Display Section */}
    {viewMode === "grid" ? (
      <GridView documents={documents} />
    ) : (
      <ListView documents={documents} />
    )}
  </div>
);
