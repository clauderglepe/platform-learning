# Platform Learning Project

This repository contains the platform learning system, consisting of:

- **Frontend**: Angular application (`platform-frontend/`)
- **Backend**: Spring Boot application (`platform-backend/`)
- **Specifications**: OpenSpec feature proposals (`openspec/changes/`)

## Getting Started

### Frontend
See `platform-frontend/README.md` for Angular development instructions.

### Backend
See `platform-backend/HELP.md` for Spring Boot setup.

### Specifications
Features are managed using OpenSpec. See `openspec/README.md` for details.

## Development

- Use branch `develop` as the integration branch.
- Each sprint works on a branch named `sprint<number>`.
- Pull requests are created from sprint branches to `develop`.
- After a sprint is complete and tested, a pull request from `develop` to `main` may be created for release.

## Conventional Commits

This project follows the [Conventional Commits](https://www.conventionalcommits.org/) specification.

Commit types:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding or correcting tests
- `chore`: Changes to the build process or auxiliary tools

