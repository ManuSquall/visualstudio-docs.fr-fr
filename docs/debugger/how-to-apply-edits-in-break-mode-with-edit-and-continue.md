---
title: Appliquer des modifications en mode arrêt avec Modifier & Continuer | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f43582b9511aa8effda93a083b6117c42a9a57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925474"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Procédure : Appliquer des modifications en Mode arrêt avec modifier et continuer (Visual Basic)
Vous pouvez utiliser Modifier & Continuer pour modifier votre code en mode Arrêt, puis continuer sans arrêter et redémarrer l'exécution.  
  
Pour connaître les limitations sur l’utilisation de modifier & Continuer pendant le débogage, consultez [pris en charge les modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).
  
### <a name="to-edit-code-in-break-mode"></a>Pour modifier du code en mode Arrêt  
  
1.  Passez en mode Arrêt en procédant de l'une des manières suivantes :  
  
    -   Définissez un point d’arrêt dans votre code, puis cliquez sur **Démarrer le débogage** dans le menu **Déboguer** et attendez que l’application parvienne au point d’arrêt.  
  
         - ou -  
  
    -   Démarrez le débogage, puis sélectionnez **Interrompre tout** dans le menu **Déboguer**.  
  
         - ou -  
  
    -   Lorsqu’une exception se produit, choisissez **activer la modification** sur le **Assistant Exception**.  
  
2.  Apportez les modifications de code souhaitées et pris en charge.  
  
     Pour plus d’informations, consultez [pris en charge les modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Si vous tentez d’effectuer une modification du code qui n’est pas autorisée par l’opération Modifier & Continuer, votre modification est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Il vous est impossible de continuer l'exécution du code sauf si vous annulez la modification de code non autorisée.  
  
3.  Dans le menu **Déboguer**, cliquez sur **Continuer** pour reprendre l’exécution.  
  
     Votre code s'exécute désormais avec les modifications que vous avez appliquées dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des modifications de Code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 [Modifier & Continuer (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
