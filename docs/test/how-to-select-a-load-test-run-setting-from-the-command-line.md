---
title: Définir les paramètres d’exécution des tests de charge à partir de la ligne de commande
description: Un test de charge peut contenir des paramètres d’exécution, autrement dit des propriétés qui influencent la manière dont un test de charge est exécuté. Découvrez comment charger des paramètres d’exécution à partir de la ligne de commande.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 872799a01e13ca94108f9acac655ee6541779c44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971841"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Guide pratique pour sélectionner un paramètre d’exécution des tests de charge à utiliser à partir d’une ligne de commande

Un test de charge peut contenir des *paramètres d’exécution*, autrement dit des propriétés qui influencent la manière dont un test de charge est exécuté. Les paramètres d’exécution sont classés par catégories dans la fenêtre **Propriétés**. Lorsqu'un test de charge est exécuté, il utilise le paramètre d'exécution actuellement actif.

Si votre test de charge contient un seul paramètre d'exécution, c'est toujours le nœud actif. Si votre test de charge contient plusieurs nœuds Paramètres d’exécution, vous pouvez sélectionner celui à utiliser lors de l’exécution d’un test de charge à partir la ligne de commande. Consultez [Comment : ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Pour modifier le paramètre d’exécution depuis la ligne de commande

1. Si vous souhaitez utiliser des paramètres d’exécution différents à partir de la ligne de commande pour tirer parti de la stratégie de paramètre de contexte, utilisez la commande suivante :

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Exécutez le test de charge avec mstest :

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Spécifier les ensembles de compteurs et les règles de seuil des ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Comment : ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Comment : sélectionner le paramètre d’exécution actif d’un test de charge](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
