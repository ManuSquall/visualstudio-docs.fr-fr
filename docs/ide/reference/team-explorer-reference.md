---
title: Informations de référence sur Team Explorer
description: En savoir plus sur les différentes fonctions de Team Explorer pour gérer le travail et coordonner avec d’autres membres de l’équipe pour développer un projet.
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: a7089defb41c3ba8379d1020cbf1225d6333b912
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560991"
---
# <a name="team-explorer-reference"></a>Informations de référence sur Team Explorer

Cet article fournit des liens vers des articles Azure DevOps sur les diverses fonctions proposées dans **Team Explorer**.

Utilisez la fenêtre d’outil **Team Explorer** pour coordonner vos efforts de codage avec d’autres membres d’équipe afin de développer un projet, et pour gérer le travail assigné à vous-même, à votre équipe ou à vos projets. **Team Explorer** connecte Visual Studio aux dépôts Git et GitHub, aux référentiels Team Foundation Version Control (TFVC) et aux projets hébergés sur [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ou un serveur [Azure DevOps Server](/azure/devops/index-all) sur site (anciennement appelé TFS). Vous pouvez gérer le code source, les éléments de travail et les générations.

## <a name="home-page"></a>page d'accueil

Une fois que vous vous êtes [connecté à un projet](../connect-team-project.md) dans **Team Explorer**, les liens suivants sont disponibles dans la section **Projet** :

- [Cloner le référentiel](/azure/devops/repos/git/clone)
- [Portail Web](/azure/devops/project/navigation/index)
- [Tableau de tâches](/azure/devops/boards/sprints/task-board)

La page d’**accueil** propose des fonctions différentes selon que vous êtes connecté à un dépôt [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true) ou à un référentiel [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview).

> [!TIP]
> Pour une comparaison des deux systèmes de contrôle de version, consultez [Choisir le contrôle de version approprié pour votre projet (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| Page d’**accueil** avec Git | Page d’**accueil** avec TFVC |
| - | - |
| ![Page d’accueil de Team Explorer avec Git dans Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Page d’accueil de Team Explorer avec TFVC dans Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Page Modifications (Git)

Consultez [Enregistrer le travail avec des validations](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Page Branches (Git)

Consultez [Créer un travail dans les branches](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Page Demandes de tirage (Git)

Consultez [Réviser le code avec des demandes de tirage](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Page Sync (Git)

Consultez [Mettre à jour du code avec Fetch et Pull](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Page Étiquettes (Git)

Consultez [Utiliser les étiquettes Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Page Mon travail (TFVC)

Consultez [Suspendre/reprendre un travail](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) et [Revue de code](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Page Modifications en attente (TFVC)

Consultez [Gérer des modifications en attente](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Rechercher des jeux de réservations](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) et [Résoudre les conflits](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Page Explorateur du contrôle de code source (TFVC)

Consultez [Ajouter/afficher les fichiers et dossiers](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Page Éléments de travail

La page **Éléments de travail** vous permet de voir les requêtes d’[élément de travail](/azure/devops/boards/work-items/about-work-items). Consultez l'article :

- [Ajouter des éléments de travail](/azure/devops/boards/backlogs/add-work-items)
- [Utiliser l’éditeur de requêtes pour lister et gérer les requêtes](/azure/devops/boards/queries/using-queries)
- [Organiser les dossiers de requête et définir les autorisations de requête](/azure/devops/boards/queries/set-query-permissions)
- [Ouvrir la requête dans Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Ouvrir la requête dans Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Envoyer par courrier électronique la liste des résultats de la requête dans Outlook](/azure/devops/boards/queries/share-plans)
- [Créer des rapports à partir de la requête dans Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (TFS uniquement)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019 propose une nouvelle [expérience en matière d’éléments de travail](/azure/devops/boards/work-items/set-work-item-experience-vs). Pour obtenir des informations sur l’affichage des éléments de travail dans Visual Studio 2019, consultez [Afficher et ajouter des éléments de travail](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Page Builds

La page **Builds** vous permet de voir les définitions de build pour le projet.

Consultez l'article :

- [Créer des pipelines de build](/azure/devops/pipelines/tasks/index)
- [Afficher et gérer les builds](/azure/devops/pipelines/overview)
- [Gérer la file d’attente des builds](/azure/devops/pipelines/agents/pools-queues)
- [Installer les outils de livraison continue (CD) pour Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Configurer et exécuter la livraison continue (CD) pour votre application](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Page Paramètres

La page **Paramètres** vous permet de configurer les fonctionnalités d’administration pour un projet ou une collection de projets. Voir les articles suivants :

| Project | Collection de projets | Autre |
| - | - | - |
| [Sécurité, appartenance au groupe](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Sécurité, contrôle de code source (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Zones d’éléments de travail](/azure/devops/organizations/settings/set-area-paths)<br/>[Itérations d’éléments de travail](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Paramètres du portail](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alertes de projet](/azure/devops/notifications/howto-manage-team-notifications) | [Sécurité, appartenance au groupe](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Contrôle de code source (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Gestionnaire de modèles de processus](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Paramètres globaux Git](/azure/devops/repos/git/git-config)<br/>[Paramètres de dépôt Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Voir aussi

- [Se connecter aux projets dans Team Explorer](../../ide/connect-team-project.md)