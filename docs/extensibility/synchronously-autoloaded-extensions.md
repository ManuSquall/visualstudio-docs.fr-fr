---
title: Extensions de chargées automatiquement de façon synchrone
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844579"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensions de chargées automatiquement de façon synchrone

Mode synchrone les extensions chargées automatiquement ont un impact négatif sur les performances de Visual Studio et doivent être converties pour utiliser autoload asynchrone à la place. À partir de Visual Studio 2019 Preview 2, les utilisateurs seront informés quand une extension est en cours de façon synchrone chargées automatiquement. L’extension de charge et fonctionner normalement.

![Avertissement de compatibilité d’extension](media/extension-compatibility-warning.png)

1. Les utilisateurs peuvent cliquer sur **en savoir plus** pour accéder à cette page d’informations.

3. Les utilisateurs peuvent cliquer sur **gérer les performances** pour ouvrir le [boîte de dialogue Gestionnaire de performances](#performance-manager-dialog) qui affiche les problèmes de performances avec les extensions et fenêtres Outil.

3. Les utilisateurs peuvent cliquer sur **ne plus afficher ce message** pour faire disparaître la notification. Cette option empêche également toutes les futures notifications à partir de façon synchrone les extensions chargées automatiquement. Les utilisateurs continueront à recevoir des notifications sur les autres fonctionnalités de Visual Studio.

### <a name="performance-manager-dialog"></a>Boîte de dialogue Gestionnaire de performances

  ![boîte de dialogue Gestionnaire des performances](media/performance-manager.png)

Toutes les extensions de façon synchrone chargé tous les packages dans toutes les sessions utilisateur seront affichera dans le **API déconseillées** onglet.

* Les utilisateurs peuvent cliquer sur le **plus d’informations sur ce problème** pour collecter plus d’informations sur les API déconseillées.
* Les utilisateurs peuvent contacter leurs fournisseurs d’extension de la progression de la migration.

Auteurs de l’extension peuvent trouver des instructions sur la migration des packages à autoload asynchrone à [migrer vers AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
