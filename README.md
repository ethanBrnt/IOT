# Inception-of-Things (IoT) — Orchestration Kubernetes & GitOps

Projet d'infrastructure de l'**École 42** dédié au déploiement d'environnements **Kubernetes** légers (**K3s** / **K3d**), au provisionnement automatisé via **Vagrant** et à l'intégration continue **GitOps** avec **ArgoCD**.

### Architecture & Étapes réalisées

| Partie | Objectif technique | Composants |
| :--- | :--- | :--- |
| **Partie 1 — Cluster K3s** | Provisionnement de deux VMs sous **Vagrant** : configuration d'un nœud contrôleur (`Server`) et rattachement d'un nœud travailleur (`Agent`). | <kbd>Vagrant</kbd> <kbd>K3s</kbd> <kbd>Linux</kbd> |
| **Partie 2 — Routage Ingress** | Déploiement de trois applications web sur un cluster K3s et routage du trafic HTTP entrant selon le nom d'hôte via **Traefik Ingress**. | <kbd>K3s</kbd> <kbd>Traefik</kbd> <kbd>Ingress</kbd> |
| **Partie 3 — K3d & ArgoCD** | Création d'un cluster **K3d** conteneurisé, séparation des espaces (`argocd` / `dev`) et synchronisation automatique des manifestes depuis un dépôt Git via **ArgoCD**. | <kbd>K3d</kbd> <kbd>ArgoCD</kbd> <kbd>Docker</kbd> <kbd>GitOps</kbd> |

### Flux GitOps (Partie 3)

```text
Dépôt Git (Manifestes Kubernetes)
      │
      ▼  (Surveillance & synchronisation)
┌───────────────────────────┐
│   ArgoCD (namespace)      │
└─────────────┬─────────────┘
              │  Déploiement déclaratif
              ▼
┌───────────────────────────┐
│   Application (dev)       │  (Cluster K3d)
└───────────────────────────┘
```

### Stack
<kbd>Kubernetes (K3s / K3d)</kbd> <kbd>Vagrant</kbd> <kbd>ArgoCD</kbd> <kbd>Traefik</kbd> <kbd>Docker</kbd> <kbd>YAML</kbd>
