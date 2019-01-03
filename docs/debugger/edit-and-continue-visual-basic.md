---
title: Modifier & Continuer (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 290216d9baa2692b1cb05741f3b1afc22c74988c
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307659"
---
# <a name="edit-and-continue-visual-basic"></a>Modifier & Continuer (Visual Basic)
La fonctionnalité Modifier & Continuer destinée au débogage de [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] vous permet d’apporter des modifications à votre code pendant qu’il s’exécute en mode Arrêt. Après avoir modifié le code, vous pouvez continuer son exécution avec les nouvelles modifications en place et observer leurs effets.  
  
 Vous pouvez utiliser la fonctionnalité Modifier & Continuer toutes les fois que vous passez en mode Arrêt. En mode arrêt, le pointeur d’instruction, une flèche jaune dans la fenêtre source, pointe sur la ligne contenant une instruction exécutable dans un corps de méthode ou propriété qui sera exécutée ensuite.

 L'option Modifier & Continuer prend en charge la plupart des modifications que vous pouvez souhaiter apporter pendant une session de débogage, avec quelques exceptions. Pour plus d’informations, consultez [pris en charge les modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Lorsque vous procédez à une modification non autorisée, celle-ci est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Vous devez annuler une modification non autorisée si vous souhaitez continuer à utiliser Modifier & Continuer. Certaines modifications non autorisées peuvent être permises si elles sont réalisées en dehors de Modifier & Continuer. Si vous souhaitez conserver le résultat d'une modification non autorisée, vous devez arrêter le débogage et redémarrer votre application.  
  
 Modifier & Continuer ne prend en charge les applications UWP pour Windows 10 et x86 et x64 des applications qui ciblent le .NET Framework 4.6 bureau ou versions ultérieures (.NET Framework est une version de bureau uniquement).

 > [!NOTE]
 > Plateformes et applications non pris en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.
  
 Modifier etContinuer n'est pas pris en charge lorsque vous commencez à déboguer à l'aide d'**Attacher au processus**. Modifier & Continuer n'est pas pris en charge pour le code optimisé ou mixtes code managé et natif. Pour plus d’informations, consultez [pris en charge les modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).
  
 Les rubriques de cette section fournissent des détails supplémentaires sur l’utilisation de cette fonctionnalité et les types de modifications non autorisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Appliquer des modifications en mode arrêt avec Modifier et Continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explique comment appliquer des modifications de code en mode Arrêt.  
  
 [Prise en charge des modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 Décrit les types de modifications qui ne peuvent pas être appliqués à Modifier & Continuer en [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Modifier & Continuer](../debugger/edit-and-continue.md)  
 Fournit une liste de rubriques sur Modifier & Continuer.
