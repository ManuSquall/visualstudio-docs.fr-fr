---
title: Démarrer et terminer la collecte des données de performances | Microsoft Docs
description: Découvrez comment vous pouvez ajouter le fichier binaire cible que vous souhaitez profiler à la session de performance avant de commencer le profilage.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0db420bbc6da16460e599ff8912569f97b506f22
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721721"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Guide pratique pour démarrer et terminer la collecte des données de performances
Vous devez ajouter le fichier binaire cible à profiler à la session de performance avant de démarrer le profilage. Pour ajouter une cible, cliquez avec le bouton droit sur **Cibles** dans l’**Explorateur de performances**, puis cliquez sur **Ajouter un fichier binaire cible**. Dans la boîte de dialogue **Ajouter un fichier binaire cible**, sélectionnez le nom du fichier, puis cliquez sur **Ouvrir**. Un nouveau fichier binaire est ajouté.

### <a name="to-start-profiling"></a>Pour démarrer le profilage

1. Cliquez avec le bouton droit sur le nom de la session de performance dans la fenêtre **Explorateur de performances**, puis choisissez l’une des options suivantes :

    - **Démarrer avec le profilage** : démarre l’application et commence immédiatement le profilage.

    - **Démarrer avec le profilage suspendu** : démarre l’application sans commencer le profilage. Pour commencer le profilage, sélectionnez **Reprendre la collecte** dans la fenêtre **Contrôle de collecte de données**. Pour plus d’informations, consultez [Guide pratique pour suspendre et reprendre la collecte de données de performances](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Pour terminer le profilage

- Pour terminer une session de profilage, il est recommandé de quitter l’application. Pour arrêter immédiatement le profilage, dans la barre d’outils de l’**Explorateur de performances**, cliquez sur **Arrêter**.

## <a name="see-also"></a>Voir aussi
- [Contrôler la collecte des données](../profiling/controlling-data-collection.md)
- [Guide pratique pour suspendre et reprendre la collecte de données de performances](../profiling/how-to-pause-and-resume-performance-data-collection.md)
