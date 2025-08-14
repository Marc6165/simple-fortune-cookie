# DockerHub Integration Setup

This guide explains how to set up DockerHub integration for the GitHub Actions workflow.

## Prerequisites

1. A DockerHub account
2. Access to your GitHub repository settings

## Step 1: Create DockerHub Access Token

1. Log in to [DockerHub](https://hub.docker.com/)
2. Go to Account Settings → Security
3. Click "New Access Token"
4. Give it a name (e.g., "GitHub Actions")
5. Copy the generated token (you won't see it again!)

## Step 2: Add GitHub Secrets

1. Go to your GitHub repository
2. Click Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Add these two secrets:

   **Secret Name:** `DOCKERHUB_USERNAME`
   **Secret Value:** Your DockerHub username

   **Secret Name:** `DOCKERHUB_TOKEN`
   **Secret Value:** The access token you created in Step 1

## Step 3: Verify Setup

1. Push to the `main` branch
2. Check the Actions tab to see the workflow running
3. Verify images are pushed to DockerHub under your account

## How It Works

The workflow will:
1. Test both frontend and backend
2. Build Docker images for both services
3. Push images to DockerHub with tags based on:
   - Git SHA
   - Branch name
   - Semantic version tags (if you use them)
4. Deploy by pulling the latest images from DockerHub

## Image Naming Convention

Images will be pushed as:
- `yourusername/simple-fortune-cookie-backend:sha-abc123`
- `yourusername/simple-fortune-cookie-frontend:sha-abc123`

## Troubleshooting

- **Authentication failed**: Check your DockerHub username and token
- **Permission denied**: Ensure your DockerHub account has permission to create repositories
- **Build failed**: Check the Actions logs for specific error messages
