# CI/CD with DevSecOps for Spring Boot Application Using GitLab

This project demonstrates a comprehensive Continuous Integration/Continuous Delivery (CI/CD) pipeline with integrated DevSecOps practices for a Spring Boot application, leveraging GitLab CI/CD.




## Project Overview

This repository provides a robust example of how to implement a CI/CD pipeline for a Spring Boot application, incorporating essential DevSecOps practices directly within GitLab. The pipeline automates the build, test, and deployment processes, while also integrating security scans at various stages to ensure code quality and identify vulnerabilities early in the development lifecycle.




## Features

*   **Automated Build & Test:** Compiles the Spring Boot application and runs unit tests automatically.
*   **Dependency Scanning:** Utilizes Trivy to scan for vulnerabilities in project dependencies.
*   **Container Scanning:** Scans the Docker image for known vulnerabilities before deployment.
*   **Automated Deployment:** Deploys the Spring Boot application as a Docker container.
*   **Dynamic Application Security Testing (DAST):** Integrates ZAP for dynamic security testing of the running application.
*   **GitLab CI/CD Integration:** Leverages GitLab's native CI/CD capabilities for seamless pipeline execution.
*   **Dockerized Application:** The Spring Boot application is containerized using Docker for consistent environments.




## Project Structure

```
.gitlab-ci.yml        # GitLab CI/CD pipeline definition
Dockerfile            # Dockerfile for containerizing the Spring Boot application
install.sh            # Script for installing Trivy
pom.xml               # Maven project object model file
mvnw                  # Maven wrapper script
mvnw.cmd              # Maven wrapper script for Windows
src/                  # Spring Boot application source code
```




## CI/CD Pipeline

The `.gitlab-ci.yml` file defines the CI/CD pipeline, which consists of the following stages:

### 1. Build

*   **Description:** This stage is responsible for compiling the Spring Boot application and packaging it into a JAR file.
*   **Tool:** Maven
*   **Command:** `mvn clean install -Dmaven.test.skip=true`

### 2. Test

*   **Description:** This stage executes the unit tests for the Spring Boot application.
*   **Tool:** Maven
*   **Command:** `mvn test -DskipCompile`

### 3. Dependency Scanning

*   **Description:** This stage scans the project dependencies for known vulnerabilities.
*   **Tool:** Trivy
*   **Report:** `misc-scan-report.json` (Code Quality Report)

### 4. Container Scanning

*   **Description:** This stage builds the Docker image and then scans it for vulnerabilities.
*   **Tool:** Trivy, Docker
*   **Report:** `container-scan-report.json` (Code Quality Report)

### 5. Deploy

*   **Description:** This stage builds the Docker image, pushes it to a Docker registry (assumed to be configured in GitLab CI/CD variables), and then runs the container.
*   **Tool:** Docker

### 6. DAST (Dynamic Application Security Testing)

*   **Description:** This stage performs dynamic security testing on the running application to identify runtime vulnerabilities.
*   **Tool:** OWASP ZAP
*   **Report:** `Dast-report.html`




## Prerequisites

Before you begin, ensure you have the following installed:

*   Java 17 or higher
*   Maven 3.6 or higher
*   Docker (for local testing or if not using GitLab CI/CD)
*   GitLab Runner (if you plan to run the CI/CD pipeline on your own infrastructure)




## Getting Started

To get a local copy up and running, follow these simple steps.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/ShimaaELsaadi/CI-CD-with-DevSecOps-for-Spring-Boot-Application-Using-GitLab.git
    cd CI-CD-with-DevSecOps-for-Spring-Boot-Application-Using-GitLab
    ```
2.  **Build the project:**
    ```bash
    mvn clean install
    ```
3.  **Run the application (optional, for local testing):**
    ```bash
    mvn spring-boot:run
    ```




### Usage

Once the application is running (either locally or deployed via GitLab CI/CD), it will be accessible on port `8080`. You can interact with the RESTful API endpoints defined within the Spring Boot application.

If deployed via the CI/CD pipeline, the application will be exposed on port `5050` (as configured in the `.gitlab-ci.yml` for the DAST stage).




## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request




## License

Distributed under the MIT License. See `LICENSE` for more information.




## Contact

Project Link: [https://github.com/ShimaaELsaadi/CI-CD-with-DevSecOps-for-Spring-Boot-Application-Using-GitLab](https://github.com/ShimaaELsaadi/CI-CD-with-DevSecOps-for-Spring-Boot-Application-Using-GitLab)



