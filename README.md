# Book Review Web Project 📚

## 🧩 Description

This project is a simple web application built to display book recommendations along with user reviews and comments.
The entire cloud infrastructure and management are managed through Lovable Cloud AI, allowing for more efficient and automated front-end and back-end development.

---

## ⚙️ The Stack

This project uses modern technologies to support performance and responsiveness, including:

- ⚡ **Vite** — A modern build tool for rapid development.
- ⚛️ **React (TypeScript)** — A JavaScript library for building dynamic user interfaces.
- 🎨 **Tailwind CSS** — A CSS framework for consistent and efficient design.
- 🧱 **shadcn/ui** — Ready-to-use UI components based on Tailwind.
---

## 💻 Local Project

Although this project is maintained by **Lovable Cloud**, development can also be done locally using Node.js.

Make sure Node.js and npm are installed on your system.
If not, we recommend using [nvm (Node Version Manager)](https://github.com/nvm-sh/nvm#installing-and-updating).

Steps to run the project:
1. Clone repository
```
git clone https://github.com/destiaeka/Library-Books-Review.git
```

2. Go to the project directory
```
cd Library-Books-Review
```

3. Install all dependencies
```
npm install
```

4. Run the development server
```
npm run dev
```

## 🐳 Running Using Docker
This project has also been packaged in a Docker image so it can be run directly without manual installation.
1. pull image
```
docker pull destiaeka/booksreview
```

3. Run the Container
```
docker run -d --name booksreview -p 80:80 destiaeka/booksreview
```

5. The application can be accessed at
```
http://localhost
```

## ⚙️ CI/CD Workflow
This project is equipped with an automated workflow that handles the following processes:
- Build a Docker image from source code.
- Push the image to Docker Hub.
- Automatic deployment to a Kubernetes (K3s) cluster.
All of these processes are executed through GitHub Actions, so every code change is automatically pushed through the CI/CD pipeline to ensure application integrity and availability.

## 🧑‍💻 Developer
### Destia Eka
- 📦 Repository: [Library-Books-Review](https://github.com/destiaeka/Library-Books-Review.git)
- 🐋 Docker Hub: [destiaeka/booksreview](https://hub.docker.com/repository/docker/destiaeka/booksreview)
