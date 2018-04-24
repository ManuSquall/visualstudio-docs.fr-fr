---
title: Définir les paramètres d’exécution d’un test de charge Visual Studio à partir de la ligne de commande | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: f5a45733da51f98618b4af36a0be0ea9120837ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Comment : sélectionner un paramètre d'exécution des tests de charge à utiliser à partir d'une ligne de commande

Un test de charge peut contenir un ou plusieurs *paramètres d’exécution*, un ensemble de propriétés qui influencent la manière dont un test de charge est exécuté. Les paramètres d'exécution sont classés par catégories dans la fenêtre Propriétés. Lorsqu'un test de charge est exécuté, il utilise le paramètre d'exécution actuellement actif.

 Si votre test de charge contient un seul paramètre d'exécution, c'est toujours le nœud actif. Si votre test de charge contient plusieurs nœuds Paramètres d'exécution, vous pouvez sélectionner celui à utiliser lors de l'exécution d'un test de charge à partir la ligne de commande. Consultez [Guide pratique pour ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md).

## <a name="to-change-the-run-setting-from-the-command-line"></a>Pour annuler le paramètre d'exécution depuis la ligne de commande

1.  Si vous souhaitez utiliser des paramètres d’exécution différents à partir de la ligne de commande pour tirer parti de la stratégie de paramètre de contexte, utilisez la commande suivante :

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  Exécutez le test de charge avec mstest :

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Guide pratique pour ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Guide pratique pour sélectionner le paramètre d’exécution active d’un test de charge](../test/how-to-select-the-active-run-setting-for-a-load-test.md)