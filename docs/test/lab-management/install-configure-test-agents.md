---
title: Installer des agents de test et des contrôleurs de test
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb10246437bff9bef0a6f76ffde95bc12855944
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653081"
---
# <a name="install-test-agents-and-test-controllers"></a>Installer des agents de test et des contrôleurs de test

Pour les scénarios de test qui utilisent Visual Studio et Azure Test Plans ou Team Foundation Server (TFS), vous n’avez pas besoin d’un contrôleur de test. Les Agents pour Visual Studio gèrent l’orchestration en communiquant avec Azure Test Plans ou TFS. On pourrait imaginer un scénario où vous exécutez des tests en continu de flux de travail de build et de mise en production dans Azure Test Plans ou TFS.

Vous pouvez aussi vous demander s’il ne serait pas plus facile [d’utiliser la gestion de build et de mise en production](use-build-or-rm-instead-of-lab-management.md) à la place de Lab Management.

## <a name="system-requirements"></a>Configuration requise

Le tableau suivant présente la configuration système requise pour l’installation de l’agent de test ou du contrôleur de test pour Visual Studio :

| Élément | spécifications |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard et Datacenter<br />Windows Server 2012 R2 |
| **Contrôleur** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard et Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installer le contrôleur de test et les agents de test

Vous pouvez télécharger des agents pour Visual Studio à partir de [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Recherchez *Agents pour Visual Studio 2019*, sélectionnez *Agent* ou *Contrôleur*, puis choisissez *Télécharger*. Exécutez l’exécutable téléchargé pour installer l’agent de test ou le contrôleur de test.

Vous pouvez télécharger des agents pour Visual Studio 2017, Visual Studio 2015 et Visual Studio 2013 à partir de la page des [téléchargements plus anciens](https://visualstudio.microsoft.com/vs/older-downloads/).

Ces programmes d’installation sont disponibles sous forme de fichiers ISO pour faciliter l’installation sur les machines virtuelles.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versions compatibles de TFS, de Microsoft Test Manager, du contrôleur de test et de l’agent de test

Vous pouvez combiner des versions différentes de TFS, Microsoft Test Manager, du contrôleur de test et de l’agent de test, conformément au tableau suivant :

| TFS | Microsoft Test Manager avec centre lab | Contrôleur | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2017 | 2017 | 2017 |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015 : mise à niveau à partir de 2013 | 2013 | 2013 |2013 |
| 2015 : nouvelle installation | 2013 | 2013 | 2013 |
| 2015 : mise à niveau à partir de 2013 ou nouvelle installation | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Les scénarios Lab Management dans TFS 2018 et Azure DevOps Services sont déconseillés. Pour plus d’informations, consultez [Notes de publication de TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Mettre à niveau à partir des agents de test Visual Studio 2013

Nous vous recommandons d’utiliser les agents pour Visual Studio dans tous les nouveaux scénarios de tests automatisés. Vous pouvez utiliser la tâche *Déployer les agents de test* dans un pipeline de build pour télécharger et installer les agents de test sur votre ordinateur.

Le tableau suivant présente les scénarios pris en charge par les Agents pour Visual Studio 2013 et les alternatives pour Team Foundation Server (TFS) 2015 et Azure Test Plans :

| Scénarios pris en charge par les Agents pour Visual Studio 2013 | Alternative dans TFS et Azure Test Plans |
| - | - |
| Flux de travail Générer-Déployer-Tester dans Visual Studio | Les utilisateurs peuvent employer un [pipeline de build](/azure/devops/pipelines/index?view=vsts) (pas une build XAML) pour générer, déployer et tester des scénarios dans TFS. |
| Test de charge (test des performances) avec des ordinateurs distants locaux | Utilisez le contrôleur de test et les agents des test de la version 2013 Update 5 pour exécuter les tests de charge localement. |
| Exécution à distance de tests automatisés à partir de Microsoft Test Manager à l’aide d’un environnement lab | Actuellement, il n’existe pas d’alternative à ce scénario. Nous vous recommandons d’utiliser la tâche Exécuter les tests fonctionnels dans les définitions de build et de mise en production (pas dans une build XAML) pour exécuter les tests à distance. |
| Développeurs exécutant les tests à distance dans Visual Studio | N'est plus pris en charge. |
