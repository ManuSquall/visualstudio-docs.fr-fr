---
title: ID de charge de travail et de composant Visual Studio
titleSuffix: ''
description: Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide d’une ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.custom: seodec18
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.prod: visual-studio-windows
ms.technology: vs-installation
open_to_public_contributors: false
ms.openlocfilehash: c80c9677a52c32f9539858b64e3be0e5cfb5f27f
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276440"
---
# <a name="visual-studio-workload-and-component-ids"></a>ID de charge de travail et de composant Visual Studio

Cliquez sur les noms d’éditions dans le tableau suivant pour voir les ID de composant et de charge de travail disponibles dont vous avez besoin pour installer Visual Studio via une ligne de commandes ou à spécifier en tant que dépendance dans un manifeste VSIX.

::: moniker range="vs-2017"

**Mise à jour pour la [version 15.9](/visualstudio/releasenotes/vs2017-relnotes/)**

| **Édition** | **Id** | **Description** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md?vs-2017) | Microsoft.VisualStudio.Product.Enterprise | Solution Microsoft DevOps axée sur la productivité et la coordination des équipes de toutes tailles |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md?vs-2017) | Microsoft.VisualStudio.Product.Professional | Outils et services de développement professionnels pour les équipes de petite taille |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | Interface IDE gratuite et riche en fonctionnalités pour les étudiants et les développeurs open source et individuels |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2017](workload-component-id-vs-team-explorer.md?vs-2017) | Microsoft.VisualStudio.Product.TeamExplorer | Interagissez avec Team Foundation Server et Azure DevOps Services sans l’ensemble d’outils de développement Visual Studio |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md?vs-2017) | Microsoft.VisualStudio.Product.WDExpress | Générez des applications natives et gérées comme WPF, WinForms et Win32 avec modification du code avec prise en charge de la syntaxe, contrôle de code source et gestion des éléments de travail. Inclut la prise en charge de C#, Visual Basic et Visual C++. |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md?vs-2017) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools vous permet de générer des applications MSBuild natives et managées sans passer par l’IDE Visual Studio. Il existe des options pour installer les compilateurs et bibliothèques Visual C++, ainsi que la prise en charge d’ATL, de MFC et de C++/CLI. |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2017](workload-component-id-vs-test-agent.md?vs-2017)  | Microsoft.VisualStudio.Product.TestAgent | Prend en charge l’exécution de tests automatisés et de tests de charge à distance |
| [Visual&nbsp;Studio&nbsp;Test Controller 2017](workload-component-id-vs-test-controller.md?vs-2017) | Microsoft.VisualStudio.Product.TestController | Distribuer des tests automatisés à plusieurs machines |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md?vs-2017) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md?vs-2017) | Microsoft.VisualStudio.Product.FeedbackClient | Outil de Feedback de Visual Studio 2017 |

Pour plus d’informations sur l’utilisation de ces listes, consultez les pages [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) et [Guide pratique pour migrer des projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2017).

::: moniker-end

::: moniker range="vs-2019"

**Mise à jour pour la [version 16.5](/visualstudio/releases/2019/release-notes/)**

| **Édition** | **Id** | **Description** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2019](workload-component-id-vs-enterprise.md?vs-2019) | Microsoft.VisualStudio.Product.Enterprise | Solution Microsoft DevOps axée sur la productivité et la coordination des équipes de toutes tailles |
| [Visual&nbsp;Studio Professional&nbsp;2019](workload-component-id-vs-professional.md?vs-2019) | Microsoft.VisualStudio.Product.Professional | Outils et services de développement professionnels pour les équipes de petite taille |
| [Visual&nbsp;Studio Community&nbsp;2019](workload-component-id-vs-community.md?vs-2019) | Microsoft.VisualStudio.Product.Community | Interface IDE gratuite et riche en fonctionnalités pour les étudiants et les développeurs open source et individuels |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2019](workload-component-id-vs-team-explorer.md?vs-2019) | Microsoft.VisualStudio.Product.TeamExplorer | Interagissez avec Team Foundation Server et Azure DevOps Services sans l’ensemble d’outils de développement Visual Studio |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2019](workload-component-id-vs-build-tools.md?vs-2019) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools vous permet de générer des applications MSBuild natives et managées sans passer par l’IDE Visual Studio. Il existe des options pour installer les compilateurs et bibliothèques Visual C++, ainsi que la prise en charge d’ATL, de MFC et de C++/CLI. |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2019](workload-component-id-vs-test-agent.md?vs-2019)  | Microsoft.VisualStudio.Product.TestAgent | Prend en charge l’exécution de tests automatisés et de tests de charge à distance |
| [Visual&nbsp;Studio Load&nbsp;Test&nbsp;Controller 2019](workload-component-id-vs-test-controller.md?vs-2019) | Microsoft.VisualStudio.Product.TestController | Distribuer des tests automatisés à plusieurs machines |

Pour plus d’informations sur la façon d’utiliser ces listes, consultez les [paramètres de la ligne de commande Use pour installer](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) la page Visual Studio et les [projets How to: Migrate extensibility vers visual Studio](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2019) page.

> [!NOTE]
> Pour obtenir la liste des ID de charge de travail et de composant de la version précédente, voir [ID de charge de travail et de composant de Visual Studio 2017](workload-and-component-ids.md?view=vs-2017).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Guide de l’administrateur Visual Studio pour Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
