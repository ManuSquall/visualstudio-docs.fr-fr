---
title: 'Comment : rechercher un Thread dans la vue Threads | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 665633047a37a9f219306e2baaa874a37c9344ea
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689562"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Comment : rechercher un thread dans la vue Threads
Vous pouvez rechercher un thread spécifique dans la vue Threads à l’aide de sa chaîne de module ou d’ID de thread comme critère de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs dans la boîte de dialogue affiche les attributs du thread sélectionné dans l’arborescence des threads.

### <a name="to-search-for-a-thread-in-threads-view"></a>Pour rechercher un thread dans la vue Threads

1. Réorganisez vos fenêtres donc que Spy ++ et qu’une [vue Threads](../debugger/threads-view.md) fenêtre sont visibles.

2. À partir de la **recherche** menu, choisissez **rechercher le Thread**.

    Le [boîte de dialogue de recherche de Thread](../debugger/thread-search-dialog-box.md) s’ouvre.

3. Tapez l’ID de thread ou une chaîne de module comme critère de recherche.

4. Effacer tous les champs pour lesquels vous ne souhaitez pas spécifier des valeurs.

   > [!TIP]
   >  Pour rechercher tous les threads détenus par un module, désactivez le **Thread** nom de zone de texte et le type du module dans le **Module** boîte. Utilisez ensuite **suivant** pour poursuivre la recherche pour les threads.

5. Choisissez **des** ou **vers le bas** pour la direction de la recherche initiale.

6. Cliquez sur **OK**.

   Si un thread correspondant est trouvé, il est mis en surbrillance dans la fenêtre de la vue Threads.