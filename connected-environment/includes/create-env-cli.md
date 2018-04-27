---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Créer un environnement de développement Kubernetes dans Azure
Avec Connected Environment, vous pouvez créer des environnements Kubernetes entièrement gérées par Azure et optimisés pour le développement. La commande crée un environnement nommé `mydevenvironment` dans `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Emplacements pris en charge : `eastus`, `westeurope`

> [!Note]
> Cette commande prend environ 6 minutes. Vous pouvez passer à la suite de ce guide sans attendre.
