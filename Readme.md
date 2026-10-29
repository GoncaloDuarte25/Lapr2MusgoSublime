# Musgo Sublime — Green Space Management

A team project developed for **LAPR2**, in the second semester of ISEP's Computer Engineering degree. The Java desktop application supports green-space maintenance through staff and team management, vehicle maintenance, and task scheduling. The project also includes graph algorithms and computational data analysis.

**Start with the [User Manual](User_manual.pdf)** for the project overview, user roles, illustrated workflows, FAQs, and troubleshooting. The manual calls the software **EcoSphere** and the green-space organization **MusgoSublime**; the desktop application uses the title **Musgo Sublime**.

## Development across three sprints

The project was developed iteratively through **Sprint A, Sprint B, and Sprint C**. Each sprint continued the previous work, updating existing artifacts and adding new requirements and functionality. All three folders are retained to show that progression.

**[Sprint C](docs/sprintC/) is the final sprint and the primary reference for the latest engineering documentation.** [Sprint A](docs/sprintA/) and [Sprint B](docs/sprintB/) preserve earlier versions. Some original documents retain template inconsistencies; consult the implementation when a requirement and its description disagree.

## Main features

- Register collaborators, jobs, and skills; assign skills and generate team proposals.
- Register vehicles and check-ups, and identify vehicles needing maintenance.
- Register and list green spaces.
- Create to-do entries, schedule work, assign teams and vehicles, and postpone or cancel agenda entries.
- Consult assigned tasks and record completion.
- Explore irrigation networks and evacuation paths through graph algorithms, alongside notebook-based water-consumption, equipment, survey, and regression analysis.

The application includes console and JavaFX interfaces. Detailed feature instructions are in the user manual.

## Technologies and architecture

- **Java, Maven, and JavaFX** for the desktop application and build.
- **JUnit 5 and Mockito** for tests; JaCoCo and PIT are configured for coverage and mutation analysis.
- **AuthLib** for authentication; GraphStream and JFreeChart for graph-related work.
- **Python/Jupyter**, pandas, NumPy, Matplotlib, SciPy, and scikit-learn for computational analysis.
- Separate UI, controller, domain, and repository layers. Operational data is held in memory and saved locally through Java serialization to `appData.ser`.

## Code and documentation map

Application paths below are relative to [`src/main/java/pt/ipp/isep/dei/esoft/project/`](src/main/java/pt/ipp/isep/dei/esoft/project/).

| Location | Contents |
| --- | --- |
| `domain/` | Entities and business rules |
| `application/controller/` and `application/session/` | Use-case coordination and sessions |
| `repository/` | In-memory data repositories |
| `ui/` | Console and JavaFX interfaces, entry points, and sample-data bootstrap |
| [src/main/resources/](src/main/resources/) | Images, styles, and configuration |
| [src/test/java/](src/test/java/) | Domain, repository, and controller tests |
| [Discrete mathematics code](src/main/java/pt/ipp/isep/dei/mdisc/) and [reports](mdisc/) | Irrigation and evacuation graph algorithms, datasets, and reports |
| [src/matcp/](src/matcp/) | Computational methods notebooks and CSV datasets |
| [docs/Readme.md](docs/Readme.md) | Team and recorded task distribution |
| [Sprint C requirements](docs/sprintC/global-artifacts/01.requirements-engineering/) | Glossary, use cases, and supplementary specification |
| [Sprint C analysis](docs/sprintC/global-artifacts/02.analysis/analysis.md) and [design](docs/sprintC/global-artifacts/03.design/) | Domain model, class diagrams, and sequence diagrams |

Individual user stories are documented under `docs/sprintC/usXXX/`, with requirements, analysis, design, and tests/implementation notes. Executable tests are under `src/test/java/`. Diagrams are provided as PlantUML sources and, where available, SVG exports.

## Run the application

1. Open the project in IntelliJ IDEA, use **JDK 21**, and load the Maven dependencies from [pom.xml](pom.xml).
2. Navigate to `src/main/java/pt/ipp/isep/dei/esoft/project/ui/`.
3. Run the `main` method in the entry point for the interface you want:

| Entry point | Interface |
| --- | --- |
| [MainGUI.java](src/main/java/pt/ipp/isep/dei/esoft/project/ui/MainGUI.java) | JavaFX graphical interface |
| [Main.java](src/main/java/pt/ipp/isep/dei/esoft/project/ui/Main.java) | Console interface |

Set the run configuration's working directory to the repository root so the application can find its resources and saved data.

For the console, sign in with `admin@this.app` / `admin`. JavaFX also has role-specific sample accounts: `hrm@this.app` / `hrm`, `vfm@this.app` / `vfm`, `grm@this.app` / `grm`, and `employee@this.app` / `pwd`. See the [User Manual](User_manual.pdf) for feature workflows.

The application loads `appData.ser` from its working directory, or creates sample data if it is absent. Exit normally to save.

**Validation:** 413 tests across 34 test classes passed, and the console application was exercised successfully with JDK 21. JavaFX execution and the Python notebooks were not verified.

## Team and attribution

Developed by **Ricardo Morim, Afonso Marques, Ana Filipa Alves, Gonçalo Fernandes, and Marisa Afonso**. The course provided the starter template and some authentication/UI scaffolding.

The following summarizes the [recorded task allocation](docs/Readme.md), which is marked as pending verification. Assignments describe user stories rather than exclusive authorship of every related class.

| Team member | Recorded user stories | Feature areas |
| --- | --- | --- |
| Afonso Marques | US001, US002, US028, US029 | Skills, jobs, assigned-task consultation and completion* |
| Ana Filipa Alves | US003, US021, US027 | Collaborators, to-do entries, green-space listings |
| Ricardo Morim | US004, US005, US022, US023 | Collaborator skills, team proposals, scheduling and team assignment |
| Gonçalo Fernandes | US006, US020, US026 | Vehicle registration, green-space registration, vehicle assignment to agenda entries |
| Marisa Afonso | US007, US008, US024, US025 | Check-ups, maintenance listings, postponement and cancellation |
