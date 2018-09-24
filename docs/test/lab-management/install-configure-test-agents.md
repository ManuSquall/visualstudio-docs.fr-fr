---
title: Installer des agents de test et des contrôleurs de test
ms.date: 07/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83a5716d5a548980b85108b6bbc15329a755bc2b
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320629"
---
# <a name="install-test-agents-and-test-controllers"></a>Installer des agents de test et des contrôleurs de test

Pour les scénarios de test qui utilisent Visual Studio et Azure Test Plans ou Team Foundation Server (TFS), vous n’avez pas besoin d’un contrôleur de test. Les Agents pour Visual Studio gèrent l’orchestration en communiquant avec Azure Test Plans ou TFS. On pourrait imaginer un scénario où vous exécutez des tests en continu de flux de travail de build et de mise en production dans Azure Test Plans ou TFS.

Vous pouvez aussi vous demander s’il ne serait pas plus facile [d’utiliser la gestion de build et de mise en production](use-build-or-rm-instead-of-lab-management.md) à la place de Lab Management.

## <a name="system-requirements"></a>Configuration requise

Le tableau suivant présente la configuration système requise pour l’installation de l’agent de test ou du contrôleur de test pour Visual Studio 2017 :

| Élément | Configuration requise |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard et Datacenter<br />Windows Server 2012 R2 |
| **Contrôleur** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard et Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installer le contrôleur de test et les agents de test

Vous pouvez télécharger des agents pour Visual Studio 2017 à partir de [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Faites défiler la page jusqu’en bas, puis recherchez *Agents pour Visual Studio 2017*. Sélectionnez *Agent* ou *Contrôleur*, puis choisissez *Télécharger*. Exécutez l’exécutable téléchargé pour installer l’agent de test ou le contrôleur de test.

Vous pouvez télécharger des agents pour Visual Studio 2015 et Visual Studio 2013 à partir de la page [Téléchargements plus anciens](https://visualstudio.microsoft.com/vs/older-downloads/).

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

Nous vous recommandons d’utiliser les agents pour Visual Studio dans tous les nouveaux scénarios de tests automatisés. Vous pouvez utiliser la tâche *Déployer les agents de test* dans un pipeline de build pour télécharger et installer les agents de test sur votre ordinateur.

Le tableau suivant présente les scénarios pris en charge par les Agents pour Visual Studio 2013 et les alternatives pour Team Foundation Server (TFS) 2015 et Azure Test Plans :

| Scénarios pris en charge par les Agents pour Visual Studio 2013 | Alternative dans TFS et Azure Test Plans |
| --- | --- |
| Flux de travail Générer-Déployer-Tester dans Visual Studio | Les utilisateurs peuvent employer un [pipeline de build](/azure/devops/pipelines/index?view=vsts) (pas une build XAML) pour générer, déployer et tester des scénarios dans TFS. |
| Test de charge (test des performances) avec des ordinateurs distants locaux | Utilisez le contrôleur de test et les agents des test de la version 2013 Update 5 pour exécuter les tests de charge localement. |
| Exécution à distance de tests automatisés à partir de Microsoft Test Manager à l’aide d’un environnement lab | Actuellement, il n’existe pas d’alternative à ce scénario. Nous vous recommandons d’utiliser la tâche Exécuter les tests fonctionnels dans les définitions de build et de mise en production (pas dans une build XAML) pour exécuter les tests à distance. |
| Développeurs exécutant les tests à distance dans Visual Studio | N'est plus pris en charge. |
