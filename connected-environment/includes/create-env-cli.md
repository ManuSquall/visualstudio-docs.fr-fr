## <a name="create-a-kubernetes-development-environment-in-azure"></a>Créer un environnement de développement Kubernetes dans Azure
Avec Connected Environment, vous pouvez créer des environnements Kubernetes entièrement gérées par Azure et optimisés pour le développement. La commande crée un environnement nommé `mydevenvironment` dans `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Emplacements pris en charge : `eastus`, `westeurope`

> [!Note]
> Cette commande prend environ 6 minutes. Vous pouvez passer à la suite de ce guide sans attendre.
