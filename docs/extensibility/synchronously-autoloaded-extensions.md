---
title: Extensions chargées automatiquement de façon synchrone
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3831fb06d23f622f85a55f5efd0a5650ca5e47
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007161"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensions chargées automatiquement de façon synchrone

Mode synchrone les extensions chargées automatiquement ont un impact négatif sur les performances de Visual Studio et doivent être converties pour utiliser autoload asynchrone à la place. À partir de Visual Studio 2019 Preview 2, les utilisateurs sont avertis quand une extension est en cours de façon synchrone chargées automatiquement. L’extension de charge et fonctionner normalement.

![Avertissement de compatibilité d’extension](media/extension-compatibility-warning.png)

Les utilisateurs peuvent :

- Cliquez sur **en savoir plus** pour accéder à cette page d’informations.

- Cliquez sur **gérer les performances** pour ouvrir le [boîte de dialogue Gestionnaire de performances](#performance-manager-dialog) qui affiche les problèmes de performances avec les extensions et fenêtres Outil.

- Cliquez sur **ne plus afficher ce message** pour faire disparaître la notification. Cette option empêche également toutes les futures notifications à partir de façon synchrone les extensions chargées automatiquement. Les utilisateurs continueront à recevoir des notifications sur les autres fonctionnalités de Visual Studio.

### <a name="performance-manager-dialog"></a>Boîte de dialogue Gestionnaire de performances

![boîte de dialogue Gestionnaire des performances](media/performance-manager.png)

Toutes les extensions de façon synchrone chargé tous les packages dans toutes les sessions utilisateur apparaissent dans le **API déconseillées** onglet.

* Les utilisateurs peuvent cliquer sur le **plus d’informations sur ce problème** pour collecter plus d’informations sur les API déconseillées.
* Les utilisateurs peuvent contacter leurs fournisseurs d’extension de la progression de la migration.

Auteurs de l’extension peuvent trouver des instructions sur la migration des packages à autoload asynchrone à [migrer vers AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
