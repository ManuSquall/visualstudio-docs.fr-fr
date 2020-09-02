---
title: Modifier & Continuer (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24782fee98cff09513ff2b4d1606f2be0bd9fbd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428553"
---
# <a name="edit-and-continue-visual-basic"></a>Modifier & Continuer (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fonctionnalité Modifier &amp; Continuer destinée au débogage de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] vous permet d’apporter des modifications à votre code pendant qu’il s’exécute en mode Arrêt. Après avoir modifié le code, vous pouvez continuer son exécution avec les nouvelles modifications en place et observer leurs effets.  
  
 Vous pouvez utiliser la fonctionnalité Modifier &amp; Continuer toutes les fois que vous passez en mode Arrêt. En mode Arrêt, le pointeur d'instruction, la flèche jaune dans la fenêtre source, pointe sur la ligne qui doit être exécutée ensuite et se trouve sur une instruction exécutable dans le corps d'une méthode ou d'une propriété. Vous pouvez apporter tout type de modification ou presque aux instructions exécutables en mode Arrêt et cette modification sera incorporée dans le projet sous-jacent. Toutefois, en mode Arrêt, vous n'êtes généralement pas autorisé à modifier des instructions de déclaration, telles que des méthodes publiques, des champs publics ou des déclarations de classe.  
  
 Lorsque vous procédez à une modification non autorisée, celle-ci est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Vous devez annuler une modification non autorisée si vous souhaitez continuer à utiliser Modifier &amp; Continuer. Certaines modifications non autorisées peuvent être permises si elles sont réalisées en dehors de Modifier &amp; Continuer. Si vous souhaitez conserver le résultat d'une modification non autorisée, vous devez arrêter le débogage et redémarrer votre application.  
  
 L'option Modifier &amp; Continuer est prise en charge pour les projets 64 bits qui ciblent .NET Framework 4.5.1.  
  
 Modifier etContinuer n'est pas pris en charge lorsque vous commencez à déboguer à l'aide d'**Attacher au processus**. Modifier &amp; Continuer n'est pas pris en charge pour le code optimisé, le code managé/natif mixte ou les projets Compact Framework (appareil de type Smart Device).  
  
 Les rubriques de cette section fournissent des détails supplémentaires sur l’utilisation de cette fonctionnalité et les types de modifications non autorisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : appliquer des modifications en mode arrêt avec modifier & continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explique comment appliquer des modifications de code en mode Arrêt.  
  
 [Modifications non prises en charge dans Modifier &amp;amp; Continuer (Visual Basic)](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Décrit les types de modifications qui ne peuvent pas être appliqués à Modifier &amp; Continuer en [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
## <a name="related-sections"></a>Sections connexes  
 [Modifier &amp; Continuer](../debugger/edit-and-continue.md)  
 Fournit une liste de rubriques sur Modifier &amp; Continuer.
