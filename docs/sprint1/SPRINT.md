# Sprint 1: Student Identification (add-identificacion-alumno)

## Goal
Implement the student identification feature to allow instructors to manually add students to a course, generate a unique access code for each student, enable students to access their individual space using that code (without password), and automatically invalidate access when the course ends. Personal data of students is used only to adapt their in‑class experience.

## Tasks

### Backend
- [ ] Create Alumno entity (fields: id, nombre, apellido, email?, codigoAcceso (hashed), cursoId, fechaCreacion, fechaUltimoAcceso)
- [ ] Create Curso entity (id, nombre, fechaInicio, fechaFin, estado) – reuse if exists, otherwise create minimal
- [ ] Create repositories for Alumno and Curso (Spring Data JPA)
- [ ] Implement service layer for Alumno:
      - generate unique access code (random string, store hashed)
      - validate access code (compare hash)
      - find alumno by valid code
      - list alumnos by curso
      - manually add alumno to curso (instructor action)
- [ ] Create REST controller for Alumno:
      - POST /api/alumnos (instructor adds alumno)
      - GET /api/alumnos/curso/{cursoId} (list alumnos for a course)
      - POST /api/alumnos/access (validate code and return alumno session token or data)
      - (Optional) DELETE /api/alumnos/{id} (remove alumno)
- [ ] Implement automatic invalidation of access codes when curso.fechaFin is reached (could be a scheduled job or checked on access attempt)
- [ ] Ensure personal data is only used for experience adaptation (e.g., expose only needed fields to frontend)
- [ ] Add unit tests for service and controller
- [ ] Add integration tests for key flows (add alumno, validate code, access denied after course end)

### Frontend
- [ ] Create instructor view to add a new alumno to a course (form with personal fields)
- [ ] Display generated access code after creation (show to instructor to share with student)
- [ ] Create student login page: field for access code, submit to validate and redirect to student space
- [ ] Create student space placeholder (to be expanded in later sprints)
- [ ] Handle invalid/expired code with appropriate error message
- [ ] Use Angular services to call backend endpoints
- [ ] Add basic form validation

### Database
- [ ] Ensure PostgreSQL schema is updated via Flyway (or Hibernate auto‑ddl for dev) to include new tables/columns
- [ ] Add indexes on codigoAcceso (hashed) and cursoId for performance

### Documentation
- [ ] Update API documentation (SpringDoc) with new endpoints
- [ ] Add notes in README.md about student access flow

## Definition of Done
- All backend tasks are completed and pass unit/integration tests.
- Frontend tasks are implemented and manually verified.
- Code follows style guides (Google Java for backend, Prettier/ESLint for frontend).
- No linting errors.
- The feature is demonstrable: instructor can add a student, student can log in with the code and view their space, and access is denied after course end (simulated by setting a past end date).
- Documentation is updated.

## Notes
- This sprint focuses on the core identification flow. Advanced features like password‑based auth, role‑based access control, or course management will be handled in later sprints.
- The access code should be a cryptographically random string (e.g., 20‑character alphanumeric) and stored as a hash (BCrypt or SHA‑256 with salt).
- For simplicity, we can assume a single active course per sprint; later sprints will handle multiple courses and course lifecycle.
