# Mergington High School Activities API

FastAPI-based web application for managing high school extracurricular activities with a simple HTML/CSS/JavaScript frontend.

**Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

## Working Effectively

### Bootstrap, Build, and Run the Application
- Install Python dependencies:
  ```bash
  pip3 install -r requirements.txt
  ```
  - Takes ~10 seconds. NEVER CANCEL - set timeout to 30+ seconds.

- Start the FastAPI server:
  ```bash
  cd src && uvicorn app:app --host 0.0.0.0 --port 8000
  ```
  - Starts in ~3 seconds. NEVER CANCEL - set timeout to 30+ seconds.
  - Server runs on http://localhost:8000
  - Automatically serves static files and API endpoints

### Code Quality and Linting
- Install and run linting tools:
  ```bash
  pip3 install flake8 black
  cd src && flake8 app.py
  cd src && black --check app.py
  ```
  - Takes ~5 seconds to install, ~1 second to run each tool.
  - Current code has minor style issues (long lines) but runs correctly.
  - Always run these before committing changes.

## Validation

### Manual Testing Requirements
- **ALWAYS run through complete end-to-end scenarios after making changes.**
- **CRITICAL**: Test both API endpoints and web interface functionality.

### Required Validation Scenarios
1. **API Testing**:
   ```bash
   # Test activities endpoint
   curl http://localhost:8000/activities
   
   # Test signup endpoint
   curl -X POST "http://localhost:8000/activities/Chess%20Club/signup?email=test@mergington.edu"
   ```

2. **Web Interface Testing**:
   - Navigate to http://localhost:8000/
   - Verify all activities display correctly with participant counts
   - Test signup form with valid email (e.g., testuser@mergington.edu)
   - Select an activity and submit form
   - Verify success message appears
   - Refresh page to confirm participant count updated

3. **API Documentation**:
   - Visit http://localhost:8000/docs to test interactive API documentation
   - Visit http://localhost:8000/redoc for alternative documentation

### Data Model Validation
- **Activities** use activity name as identifier (e.g., "Chess Club", "Programming Class", "Gym Class")
- **Students** use email as identifier
- All data is stored in-memory and resets when server restarts
- Always test with realistic email addresses ending in @mergington.edu

## Application Architecture

### Key Files and Locations
```
src/
├── app.py              # Main FastAPI application
├── static/
│   ├── index.html      # Main web interface
│   ├── app.js          # Frontend JavaScript logic
│   └── styles.css      # Styling
└── README.md           # Application documentation

requirements.txt        # Python dependencies (fastapi, uvicorn)
```

### API Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Redirects to `/static/index.html` |
| GET | `/activities` | Get all activities with participant counts |
| POST | `/activities/{activity_name}/signup?email={email}` | Sign up student for activity |
| GET | `/docs` | Interactive API documentation |
| GET | `/redoc` | Alternative API documentation |

### Frontend Functionality
- Displays all available activities with schedules and availability
- Provides signup form with email validation
- Shows success/error messages for signup attempts
- Auto-refreshes activity data after successful signup

## Common Development Tasks

### Making Changes to the Application
1. Always start the server first to establish baseline functionality
2. Make your code changes
3. Test changes using both curl and web interface
4. Run linting tools before finishing
5. Verify all validation scenarios still pass

### Adding New Activities
- Modify the `activities` dictionary in `src/app.py`
- Follow existing format with description, schedule, max_participants, and participants list
- Always test new activities appear in both API and web interface

### Modifying the Frontend
- Static files are served automatically from `src/static/`
- Changes to HTML, CSS, or JavaScript take effect immediately (no build required)
- Always test in browser after changes

## Troubleshooting

### Common Issues
- **Server won't start**: Ensure you're in the `src` directory when running uvicorn
- **Dependencies missing**: Run `pip3 install -r requirements.txt` from repository root
- **Changes not visible**: For frontend changes, hard refresh browser (Ctrl+F5)
- **API not responding**: Verify server is running on http://localhost:8000

### Expected Behaviors
- Data resets when server restarts (this is normal, not a bug)
- Participant count updates immediately after signup
- Web interface automatically refreshes activity data
- API returns JSON responses for all endpoints

## Performance Expectations
- **Dependency installation**: ~10 seconds
- **Server startup**: ~3 seconds  
- **API response time**: < 1 second
- **Web page load**: < 2 seconds

**NEVER CANCEL commands that take less than 30 seconds. Always wait for completion.**