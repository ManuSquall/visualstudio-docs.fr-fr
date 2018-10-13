---
title: Modifier & Continuer (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61ce8f61092bdcc612ea535debfcface976ebff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265099"
---
# <a name="edit-and-continue-visual-basic"></a>Modifier & Continuer (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fonctionnalité Modifier & Continuer destinée au débogage de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] vous permet d’apporter des modifications à votre code pendant qu’il s’exécute en mode Arrêt. Après avoir modifié le code, vous pouvez continuer son exécution avec les nouvelles modifications en place et observer leurs effets.  
  
 Vous pouvez utiliser la fonctionnalité Modifier & Continuer toutes les fois que vous passez en mode Arrêt. En mode Arrêt, le pointeur d'instruction, la flèche jaune dans la fenêtre source, pointe sur la ligne qui doit être exécutée ensuite et se trouve sur une instruction exécutable dans le corps d'une méthode ou d'une propriété. Vous pouvez apporter tout type de modification ou presque aux instructions exécutables en mode Arrêt et cette modification sera incorporée dans le projet sous-jacent. Toutefois, en mode Arrêt, vous n'êtes généralement pas autorisé à modifier des instructions de déclaration, telles que des méthodes publiques, des champs publics ou des déclarations de classe.  
  
 Lorsque vous procédez à une modification non autorisée, celle-ci est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Vous devez annuler une modification non autorisée si vous souhaitez continuer à utiliser Modifier & Continuer. Certaines modifications non autorisées peuvent être permises si elles sont réalisées en dehors de Modifier & Continuer. Si vous souhaitez conserver le résultat d'une modification non autorisée, vous devez arrêter le débogage et redémarrer votre application.  
  
 L'option Modifier & Continuer est prise en charge pour les projets 64 bits qui ciblent .NET Framework 4.5.1.  
  
 Modifier & Continuer n'est pas pris en charge lorsque vous démarrez le débogage à l’aide de **attacher au processus**. Modifier & Continuer n'est pas pris en charge pour le code optimisé, le code managé/natif mixte ou les projets Compact Framework (appareil de type Smart Device).  
  
 Les rubriques de cette section fournissent des détails supplémentaires sur l’utilisation de cette fonctionnalité et les types de modifications non autorisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour appliquer des modifications en mode arrêt à l’aide de la fonctionnalité Modifier & Continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explique comment appliquer des modifications de code en mode Arrêt.  
  
 [Modifications non prises en charge dans Modifier & Continuer (Visual Basic)](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Décrit les types de modifications qui ne peuvent pas être appliqués à Modifier & Continuer en [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Modifier & Continuer](../debugger/edit-and-continue.md)  
 Fournit une liste de rubriques sur Modifier & Continuer.



