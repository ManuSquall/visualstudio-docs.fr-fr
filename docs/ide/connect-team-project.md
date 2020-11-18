---
title: Se connecter aux projets dans Team Explorer
description: Découvrez comment utiliser Team Explorer dans Visual Studio pour travailler avec les membres de l’équipe pour développer et gérer des projets.
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 7d920370013b2d624430acbdbe8e38dcc9aab03d
ms.sourcegitcommit: f78960320798e2c6b33145cee77a2221f031603c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94878255"
---
# <a name="connect-to-projects-in-team-explorer"></a>Se connecter aux projets dans Team Explorer

::: moniker range="vs-2017"

Utilisez la fenêtre d’outil **Team Explorer** pour coordonner vos efforts de codage avec d’autres membres d’équipe afin de développer un projet, et pour gérer le travail assigné à vous-même, à votre équipe ou à vos projets. **Team Explorer** connecte Visual Studio aux dépôts Git et GitHub, aux référentiels Team Foundation Version Control (TFVC) et aux projets hébergés sur [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ou un serveur [Azure DevOps Server](/azure/devops/index-all) sur site (anciennement appelé TFS). Vous pouvez gérer le code source, les éléments de travail et les générations.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser la fenêtre outil **Team Explorer** pour coordonner vos efforts de code avec d’autres membres de l’équipe pour développer un projet et pour gérer le travail qui vous est assigné, votre équipe ou vos projets.

> [!IMPORTANT]
> Avec la dernière version de Visual Studio 2019 [version 16,8](/visualstudio/releases/2019/release-notes/), la nouvelle expérience de contrôle de version git est désormais activée par défaut. Toutefois, si vous préférez continuer à utiliser Team Explorer, accédez à **Outils**  >  **options**  >  **environnement**  >  **Aperçu fonctionnalités** , puis activez la case à cocher **nouvelle expérience utilisateur git** . Pour plus d’informations, consultez la page [interface git dans Visual Studio](git-with-visual-studio.md) .

**Team Explorer** connecte Visual Studio aux dépôts Git et GitHub, aux référentiels Team Foundation Version Control (TFVC) et aux projets hébergés sur [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ou un serveur [Azure DevOps Server](/azure/devops/index-all) sur site (anciennement appelé TFS). Vous pouvez gérer le code source, les éléments de travail et les générations.

::: moniker-end

![Page d’accueil de Team Explorer dans Visual Studio](media/team-explorer/team-explorer.png "La page Team Explorer-page d’hébergement de Visual Studio.")

::: moniker range="vs-2017"

> [!TIP]
> Si vous ouvrez Visual Studio et que **Team Explorer** ne s’affiche pas, ouvrez-le en choisissant **Afficher**  >  les **Team Explorer** dans la barre de menus, ou en appuyant sur **CTRL** + **&#92;**, **CTRL** + **M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Se connecter à un projet ou à un référentiel

Connectez-vous à un projet ou à un référentiel sur la page **Se connecter**.

![Page Se connecter dans Team Explorer](media/team-explorer/connect.png "Page Team Explorer-Connect dans Visual Studio")

Pour se connecter à un projet :

1. Ouvrez la page **Se connecter** en choisissant l’icône **Gérer les connexions**.

   ![Bouton Gérer les connexions dans Team Explorer](media/team-explorer/manage-connections.png "Le bouton Team Explorer-gérer les connexions dans Visual Studio.")

1. Sur la page **Se connecter**, choisissez **Gérer les connexions** > **Se connecter à un projet**.

   ![Se connecter à un projet dans Team Explorer](media/team-explorer/connect-project.png "L’option Team Explorer-se connecter à un projet dans Visual Studio.")

> [!TIP]
> Si vous souhaitez ouvrir un projet à partir d’un référentiel, consultez [ouvrir un projet à partir d’un référentiel](../get-started/tutorial-open-project-from-repo.md). Si vous souhaitez créer un projet ou ajouter des utilisateurs à un projet, consultez [créer un projet (Azure DevOps)](/azure/devops/organizations/projects/create-project) et [Ajouter des utilisateurs à un projet ou une équipe (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Voir aussi

- [Nouvelle expérience git dans Visual Studio](git-with-visual-studio.md)
- [Didacticiel : ouvrir un projet à partir d’un référentiel](../get-started/tutorial-open-project-from-repo.md)
- [Informations de référence sur Team Explorer](reference/team-explorer-reference.md)
- [Se connecter à un projet (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Résoudre les problèmes de connexion à un projet](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
