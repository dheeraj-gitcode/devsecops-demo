# DevSecOps Pipeline Implementation for Tic Tac Toe Game

![Screenshot 2025-03-04 at 7 16 48 PM](https://github.com/user-attachments/assets/7ed79f9c-9144-4870-accd-500085a15592)

![image](https://github.com/user-attachments/assets/5b2813a5-f493-4665-8964-77359b5be93a)

## Features

- 🎮 Fully functional Tic Tac Toe game
- 📊 Score tracking for X, O, and draws
- 📜 Game history with timestamps
- 🏆 Highlights winning combinations
- 🔄 Reset game and statistics
- 📱 Responsive design for all devices

## Technologies Used

- React 18
- TypeScript
- Tailwind CSS
- Lucide React for icons

## Project Structure

```
src/
├── components/
│   ├── Board.tsx       # Game board component
│   ├── Square.tsx      # Individual square component
│   ├── ScoreBoard.tsx  # Score tracking component
│   └── GameHistory.tsx # Game history component
├── utils/
│   └── gameLogic.ts    # Game logic utilities
├── App.tsx             # Main application component
└── main.tsx           # Entry point
```

## Game Logic

The game implements the following rules:

1. X goes first, followed by O
2. The first player to get 3 of their marks in a row (horizontally, vertically, or diagonally) wins
3. If all 9 squares are filled and no player has 3 marks in a row, the game is a draw
4. Winning combinations are highlighted
5. Game statistics are tracked and displayed

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. To Clone the repository:
   ```bash
   git clone https://github.com/yourusername/devsecops-demo.git
   cd devsecops-demo
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn
   ```

3. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. Open your browser and navigate to `http://localhost:5173`

## Building for Production

To create a production build:

```bash
npm run build
# or
yarn build
```

The build artifacts will be stored in the `dist/` directory.

🐳 4. Build and Run Docker Container Locally (Optional)

```bash
docker build -t tictactoe-demo:v1 .
docker run -d -p 9090:80 tictactoe-demo:v1
```

☸️ 5. Create Kubernetes Cluster Using Kind

```bash
kind create cluster --name devsecops-demo
```
To verify:

```bash
kubectl cluster-info --context kind-devsecops-demo
```
📥 6. Deploy Argo CD into Kind Cluster
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
🌐 7. Access Argo CD UI

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Access ArgoCD UI at: https://localhost:8080

🔑 8. Login to Argo CD (Default)

```bash
kubectl get pods -n argocd
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
Username: admin
Password: (from the above command)

📌 9. Deploy the App via Argo CD
Create an Argo CD app pointing to the GitHub repo (k8s manifest path).

Configure imagePullSecrets if you're using GitHub Container Registry (GHCR).

🔁 10. CI/CD Workflow with GitHub Actions
On every push, the following jobs run:

Unit Tests

Linting

Build

Docker Build & Push (to GHCR)

Vulnerability Scan (Trivy)

Auto-update deployment.yaml with image tag

Argo CD syncs updated deployment automatically

🧹 Clean Up
To delete the Kind cluster and all resources:

```bash
kind delete cluster --name devsecops-demo
```

