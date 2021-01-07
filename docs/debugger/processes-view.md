---
title: Vue processus | Microsoft Docs
description: Vue processus affiche une arborescence de tous les processus actifs sur votre système. En savoir plus sur son contenu et ses utilisations, et suivre les liens vers des informations supplémentaires.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a52da28d01eac4f04081497888fbbfccaf4495e2
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975132"
---
# <a name="processes-view"></a>Vue Processus
La vue processus affiche une arborescence de tous les processus actifs sur votre système. L’ID de processus et le nom du module sont affichés. Utilisez la vue processus si vous souhaitez examiner un processus système particulier, qui correspond généralement à un programme en cours d’exécution. Les processus sont identifiés par des noms de module ou sont des « processus système » désignés.

 Microsoft Windows prend en charge plusieurs processus. Chaque processus peut avoir un ou plusieurs threads, et chaque thread peut avoir une ou plusieurs fenêtres de niveau supérieur associées. Chaque fenêtre de niveau supérieur peut posséder une série de fenêtres. Un symbole + indique qu’un niveau est réduit. La vue réduite se compose d’une ligne par processus. Cliquez sur le signe + pour développer le niveau.

 Utilisez la vue processus si vous souhaitez examiner un processus système particulier, qui correspond généralement à un programme en cours d’exécution. Les processus sont identifiés par des noms de module ou sont des « processus système » désignés. Pour rechercher un processus, réduisez l’arborescence et recherchez la liste.

## <a name="procedures"></a>Procédures

#### <a name="to-open-the-processes-view"></a>Pour ouvrir la vue processus

1. Dans le menu **Espion** , choisissez **processus**.

   ![Vue processus Spy&#43;&#43; ](../debugger/media/spy--_processes.png "_Processes Spy + +") Affichage des processus Spy + +

   La figure ci-dessus montre la vue processus avec les nœuds de processus et de thread développés.

### <a name="in-this-section"></a>Dans cette section
 [Recherche d’un processus dans la vue processus](../debugger/how-to-search-for-a-process-in-processes-view.md) Explique comment rechercher un processus spécifique dans la vue processus.

 [Affichage des propriétés](../debugger/how-to-display-process-properties.md) d’un processus Explique comment afficher plus d’informations sur un message.

### <a name="related-sections"></a>Sections connexes
 [Vues Spy + +](../debugger/spy-increment-views.md) Explique les vues de l’arborescence Spy + + des fenêtres, des messages, des processus et des threads.

 [Utilisation de Spy + +](../debugger/using-spy-increment.md) Présente l’outil Spy + + et explique comment l’utiliser.

 [Boîte de dialogue recherche de processus](../debugger/process-search-dialog-box.md) Utilisé pour rechercher le nœud d’un processus spécifique dans la vue processus.

 [Boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md) Affiche les propriétés d’un processus sélectionné dans la vue processus.

 [Référence Spy + +](../debugger/spy-increment-reference.md) Comprend des sections décrivant chaque menu et boîte de dialogue Spy + +.