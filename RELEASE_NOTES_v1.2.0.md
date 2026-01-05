# Release v1.2.0

## 🎉 New Features & Major Improvements

This release includes significant improvements to IRR calculation, judge tuning, binary scale support, and automatic database migrations.

## 📦 What's Included

This release includes the complete project with pre-built client (`client/build/`) in `project-with-build.zip`. Simply extract and run!

## ✨ New Features

### 1. **IRR Recalculation Fixes**
- Fixed duplicate toast notifications during IRR recalculation
- Improved error handling and user feedback
- Automatic refresh of IRR data when navigating between pages

### 2. **Judge Tuning Improvements**
- **Fixed annotation refresh issue**: Judge tuning now automatically picks up new annotations when you add more traces
- Annotations refresh automatically when you navigate back to Judge Tuning page
- Annotations refresh before evaluation/alignment to ensure latest data is used
- Switched from manual state management to React Query hooks for automatic updates

### 3. **Binary Scale Support**
- Full support for binary (Pass/Fail) evaluation scales
- Binary SIMBA optimizer for judge alignment
- Custom binary labels support
- Freeform text responses for binary evaluations

### 4. **Automatic Database Migrations**
- Database migrations now run automatically on application startup
- No manual migration steps needed for deployment
- Handles both new databases and existing databases gracefully
- Supports SQLite and can be configured for PostgreSQL

## 🔧 Improvements

### Database & Backend
- **Alembic migrations**: Added to production dependencies (was only in dev)
- **Automatic migration on startup**: `server/app.py` now runs migrations in the lifespan function
- **Database initialization**: Creates database automatically if it doesn't exist
- **Legacy database support**: Automatically stamps existing databases to baseline

### Frontend
- **IRR Results Page**: Fixed toast notification handling with `toast.promise()`
- **Judge Tuning Page**: Now uses React Query hooks for automatic annotation refresh
- **Better state management**: Replaced manual state with React Query for real-time updates

### Developer Experience
- **Release workflow**: Fixed to properly create `project-with-build.zip`
- **Better error messages**: Improved error handling throughout the application

## 🐛 Bug Fixes

1. **IRR Recalculation**: Fixed duplicate toast notifications showing "Recalculating IRR..." and "Failed to recalculate IRR" simultaneously
2. **Judge Tuning**: Fixed issue where new annotations weren't recognized after adding more traces
3. **Database Migrations**: Fixed Alembic not being available in production deployments

## 📋 Changes Since v1.1.0

### Commits Included
- `7a70eef` - Merge vivian branch: IRR recalculation fixes and judge tuning improvements
- `10a551f` - Fixed IRR recalculation and judge tuning adding more traces
- `cefc182` - Updated judge tuning with binary scale
- `90326ec` - Updated judge tuning with binary scale
- `df777f8` - Updated judge tuning with binary scale
- `cfde44f` - Added binary SIMBA optimizer for alignment
- `579f7dd` - Added binary scale, freeform text
- `e23a6c0` - Added binary scale, freeform text

## 🚀 Quick Start

1. **Download the release:**
   - Download `project-with-build.zip` from the [Releases page](https://github.com/databricks-solutions/project-0xfffff/releases)
   - Extract the zip file

2. **Set up Python environment:**
   ```bash
   uv venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   uv pip install -r requirements.txt
   ```

3. **Run the server:**
   ```bash
   uv run uvicorn server.app:app --reload --port 8000
   ```
   
   The database will be created automatically on first run!

4. **Open your browser:**
   ```
   http://localhost:8000
   ```

## 📋 Requirements

- Python 3.11+
- uv (Python package installer)
- Modern web browser

## 🔧 Configuration

### Database
The application uses SQLite by default (`workshop.db`). To use a different database:

```bash
export DATABASE_URL=postgresql://user:password@host:port/dbname
```

### Databricks Apps Deployment
When deploying to Databricks Apps, migrations run automatically on startup. No manual steps required!

## 📚 Documentation

- [DB_MIGRATIONS.md](doc/DB_MIGRATIONS.md) - Database migration guide
- [BUILD_GUIDE.md](doc/BUILD_GUIDE.md) - Client build instructions
- [README.md](README.md) - Full project documentation

## 🐛 Known Issues

None at this time. Please report issues on GitHub.

## 📝 License

See [LICENSE.md](LICENSE.md) for details.

