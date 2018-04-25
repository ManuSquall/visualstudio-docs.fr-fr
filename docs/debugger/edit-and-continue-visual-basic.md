---
title: Modifier & Continuer (Visual Basic) | Documents Microsoft
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
ms.openlocfilehash: aa3b8c287129c164d8c6984ac52375d6012fbd68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-visual-basic"></a>Modifier & Continuer (Visual Basic)
La fonctionnalité Modifier & Continuer destinée au débogage de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vous permet d'apporter des modifications à votre code pendant qu'il s'exécute en mode Arrêt. Après avoir modifié le code, vous pouvez continuer son exécution avec les nouvelles modifications en place et observer leurs effets.  
  
 Vous pouvez utiliser la fonctionnalité Modifier & Continuer toutes les fois que vous passez en mode Arrêt. En mode arrêt, le pointeur d’instruction, une flèche jaune dans la fenêtre source, pointe sur la ligne contenant une instruction exécutable dans un corps de méthode ou propriété qui sera exécutée suivant.

 L'option Modifier & Continuer prend en charge la plupart des modifications que vous pouvez souhaiter apporter pendant une session de débogage, avec quelques exceptions. Pour plus d’informations, consultez [modifications de Code prises en charge (c# et Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Lorsque vous procédez à une modification non autorisée, celle-ci est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Vous devez annuler une modification non autorisée si vous souhaitez continuer à utiliser Modifier & Continuer. Certaines modifications non autorisées peuvent être permises si elles sont réalisées en dehors de Modifier & Continuer. Si vous souhaitez conserver le résultat d'une modification non autorisée, vous devez arrêter le débogage et redémarrer votre application.  
  
 Modifier & Continuer est prise en charge dans les applications UWP pour Windows 10 et x86 et x64 des applications qui ciblent le .NET Framework 4.6 bureau ou versions ultérieures (.NET Framework est une version de bureau).

 > [!NOTE]
 > Plateformes et des applications non prises en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.
  
 Modifier & Continuer n'est pas pris en charge lorsque vous démarrez le débogage à l’aide de **attacher au processus**. Modifier & Continuer n'est pas prise en charge pour le code optimisé ou mixte du code managé et natif. Pour plus d’informations, consultez [pris en charge les modifications de Code (c# et Visual Basic](../debugger/supported-code-changes-csharp.md).
  
 Les rubriques de cette section fournissent des détails supplémentaires sur l’utilisation de cette fonctionnalité et les types de modifications non autorisés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour appliquer des modifications en mode arrêt à l’aide de la fonctionnalité Modifier & Continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explique comment appliquer des modifications de code en mode Arrêt.  
  
 [Modifications de Code prises en charge (c# et Visual Basic](../debugger/supported-code-changes-csharp.md)   
 Décrit les types de modifications qui ne peuvent pas être appliqués à Modifier & Continuer en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Modifier & Continuer](../debugger/edit-and-continue.md)  
 Fournit une liste de rubriques sur Modifier & Continuer.