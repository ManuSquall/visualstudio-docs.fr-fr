---
title: Installer et configurer des agents de test | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configure test agents, test lab
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 495f14643245f17a2e7fcef1e21d2fc1fe978a46
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="install-and-configure-test-agents"></a>Installer et configurer des agents de test

Pour les scénarios de test avec Visual Studio et Visual Studio Team Services ou Team Foundation Server (TFS), vous n’avez besoin d’aucun contrôleur de test parce que les Agents pour Microsoft Visual Studio gèrent l’orchestration en communiquant avec Team Services ou TFS. Par exemple, supposons que vous exécutez des tests en continu avec vos flux de travail de build et de mise en production dans Team Services ou TFS.

Si vous avez besoin de votre agent de test ou contrôleur de test pour utiliser TFS 2013, faites appel aux Agents pour Microsoft Visual Studio 2013 Update 5 et configurez le contrôleur de test.

Demandez-vous aussi si cela ne serait pas plus facile d’[utiliser la gestion de build et de mise en production à la place](use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>De quoi ai-je besoin ?

**Où me procurer le contrôleur de test et les agents de test ?**

* Si vous exécutez les tests avec les tâches Build vNext et que vous souhaitez installer les agents à partir d’un répertoire local - 

  * [Téléchargez les Agents pour Microsoft Visual Studio 2015 RTM Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Téléchargez les Agents pour Visual Studio 2017 et Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs) - choisissez **Outils pour Visual Studio 2015** et sélectionnez **Agents pour Visual Studio 2015** dans la barre de navigation de gauche.

* [Téléchargez les Agents pour Microsoft Visual Studio 2013 RTM Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264) si vous voulez exécuter :

  * Des tests de charge sur des ordinateurs distants locaux.

  * Des tests en continu à distance avec Microsoft Test Manager ou MSTest et les paramètres de test pour les environnements lab.

  * Des tests en continu avec TFS 2013.

Ces programmes d’installation sont disponibles sous forme de fichiers ISO (CD virtuel) pour faciliter l’installation sur les machines virtuelles. 

[Puis-je mélanger des versions de TFS, de Microsoft Test Manager, du contrôleur de test et de l’agent de test ?](#MixedVersions)

**Quelle configuration système dois-je avoir pour installer mon contrôleur de test et mes agents de test ?**

| Élément | Configuration requise |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Contrôleur** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Questions et réponses

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Q : Puis-je mélanger des versions de TFS, de Microsoft Test Manager, du contrôleur de test et de l’agent de test ?

R : Oui, voici les combinaisons compatibles prises en charge :

| TFS | Microsoft Test Manager avec centre lab | Contrôleur | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2015 : mise à niveau à partir de 2013 | 2013 | 2013 |2013 |
| 2015 : nouvelle installation | 2013 | 2013 | 2013 |
| 2015 : mise à niveau à partir de 2013 ou nouvelle installation | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>Q : Test Agent 2015 prend-il en charge tous les scénarios pris en charge par le contrôleur de test et l’agent de test de Visual Studio 2013 ?

R : Nous vous recommandons d’utiliser les Agents pour Visual Studio dans tous les nouveaux scénarios de tests automatisés. Vous pouvez utiliser la tâche Déployer les agents de test dans une définition de build pour télécharger et installer les agents de test sur votre ordinateur.
Le tableau suivant présente les scénarios pris en charge par les Agents pour Visual Studio 2013 et les alternatives avec Team Foundation Server (TFS) 2015 et Team Services (TS).

| Scénarios pris en charge par les Agents pour Visual Studio 2013 | Alternative dans TFS et TS |
| --- | --- |
| Flux de travail Générer-Déployer-Tester dans Visual Studio | Les utilisateurs peuvent employer une [définition de build](https://www.visualstudio.com/team-services/continuous-integration/) (pas une build XAML) pour générer, déployer et tester les scénarios dans TFS. |
| Test de charge (test des performances) avec des ordinateurs distants locaux | Utilisez le contrôleur de test/les agents des test de la version 2013 Update 5 pour exécuter les tests de charge localement. [Complément d’information](https://msdn.microsoft.com/en-us/library/ff400223.aspx). |
| Exécution à distance de tests automatisés à partir de Microsoft Test Manager à l’aide d’un environnement lab | Actuellement, il n’existe pas d’alternative à ce scénario. Nous vous recommandons d’utiliser la tâche Exécuter les tests fonctionnels dans les définitions de build et de mise en production (pas dans une build XAML) pour exécuter les tests à distance. |
| Développeurs exécutant les tests à distance dans Visual Studio | N'est plus pris en charge. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Voir aussi

* [Configuration d’ordinateurs et collecte d’informations de diagnostic à l’aide de paramètres de test](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
