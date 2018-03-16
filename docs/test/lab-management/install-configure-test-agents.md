---
title: Installer et configurer des agents de test dans Visual Studio | Microsoft Docs
ms.date: 03/02/2018
ms.technology: vs-devops-test
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 16e29676ec67bc3fd22313debe70ba8dbcd7fd76
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="install-and-configure-test-agents"></a>Installer et configurer des agents de test

Pour les scénarios de test qui utilisent Visual Studio et Visual Studio Team Services (VSTS) ou Team Foundation Server (TFS), vous n’avez pas besoin d’un contrôleur de test. Les Agents pour Visual Studio gèrent l’orchestration en communiquant avec VSTS ou TFS. Un scénario peut être que vous exécutez des tests en continu de flux de travail de build et de mise en production dans VSTS ou TFS.

Vous pouvez aussi vous demander s’il ne serait pas plus facile [d’utiliser la gestion de build et de mise en production](use-build-or-rm-instead-of-lab-management.md) à la place de Lab Management.

## <a name="system-requirements"></a>Configuration requise

| Élément | Configuration requise |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Contrôleur** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installer le contrôleur de test et les agents de test

Vous pouvez télécharger des agents pour Visual Studio 2017 à partir de [visualstudio.com](https://www.visualstudio.com/downloads/?q=agents). Recherchez *Agents pour Visual Studio 2017* et sélectionnez *Agent* ou *Contrôleur*. Vous pouvez télécharger des agents pour Visual Studio 2015 et Visual Studio 2013 à partir de la page [Téléchargements plus anciens](https://www.visualstudio.com/vs/older-downloads/).

Ces programmes d’installation sont disponibles sous forme de fichiers ISO pour faciliter l’installation sur les machines virtuelles.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versions compatibles de TFS, de Microsoft Test Manager, du contrôleur de test et de l’agent de test

Vous pouvez combiner des versions différentes de TFS, Microsoft Test Manager (MTM), du contrôleur de test et de l’agent de test, conformément au tableau suivant :

| TFS | MTM avec le Centre lab | Contrôleur | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2017 | 2017 | 2017 |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017 : mise à niveau à partir de 2015 ou nouvelle installation | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015 : mise à niveau à partir de 2013 | 2013 | 2013 |2013 |
| 2015 : nouvelle installation | 2013 | 2013 | 2013 |
| 2015 : mise à niveau à partir de 2013 ou nouvelle installation | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Mettre à niveau à partir des agents de test Visual Studio 2013

Nous vous recommandons d’utiliser les agents pour Visual Studio dans tous les nouveaux scénarios de tests automatisés. Vous pouvez utiliser la tâche *Déployer les agents de test* dans une définition de build pour télécharger et installer les agents de test sur votre ordinateur.

Le tableau suivant présente les scénarios pris en charge par les Agents pour Visual Studio 2013 et les alternatives avec Team Foundation Server (TFS) 2015 et VSTS :

| Scénarios pris en charge par les Agents pour Visual Studio 2013 | Alternative dans TFS et VSTS |
| --- | --- |
| Flux de travail Générer-Déployer-Tester dans Visual Studio | Les utilisateurs peuvent employer une [définition de build](/vsts/build-release/) (pas une build XAML) pour générer, déployer et tester les scénarios dans TFS. |
| Test de charge (test des performances) avec des ordinateurs distants locaux | Utilisez le contrôleur de test et les agents des test de la version 2013 Update 5 pour exécuter les tests de charge localement. Pour plus d’informations, consultez [Utilisation d’un contrôleur de test et d’agents de test dans un test de charge](https://msdn.microsoft.com/library/ff400223.aspx). |
| Exécution à distance de tests automatisés à partir de Microsoft Test Manager à l’aide d’un environnement lab | Actuellement, il n’existe pas d’alternative à ce scénario. Nous vous recommandons d’utiliser la tâche Exécuter les tests fonctionnels dans les définitions de build et de mise en production (pas dans une build XAML) pour exécuter les tests à distance. |
| Développeurs exécutant les tests à distance dans Visual Studio | N'est plus pris en charge. |

## <a name="see-also"></a>Voir aussi

* [Configurer des ordinateurs et collecter des informations de diagnostic](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
