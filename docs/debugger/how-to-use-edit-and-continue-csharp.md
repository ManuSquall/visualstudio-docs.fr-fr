---
title: "Comment : utiliser Modifier & Continuer (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: fe77428d1d9cfb5ff12554e87ec9afe15d6c86b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-edit-and-continue-c"></a>Comment : utiliser Modifier & Continuer (C#)
Avec Modifier & Continuer pour C#, vous pouvez modifier votre code en mode arrêt pendant le débogage. Les modifications peuvent être appliquées sans qu'il soit nécessaire d'arrêter et de redémarrer la session de débogage.  
  
 Modifier & Continuer est appelé automatiquement lorsque vous apportez des modifications en mode arrêt, puis choisissez une débogueur, l’exécution commande, telles que **continuer**, **étape**, ou **définir l’instruction suivante**, ou d’évaluer une fonction dans une fenêtre du débogueur.  
  
> [!NOTE]
>  Modifier & Continuer n’est pas pris en charge lorsque vous déboguez optimisé de code, le code mixte natif/managé ou code de l’intégration SQL Server common language runtime (CLR). Pour plus d’informations sur les autres scénarios non pris en charge, consultez [modifications de Code prises en charge (c# et Visual Basic)](../debugger/supported-code-changes-csharp.md). Si vous essayez d’appliquer les modifications de code dans un de ces scénarios, le débogueur affiche une boîte de dialogue zone qui explique que Modifier & Continuer n’est pas pris en charge.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Pour appeler Modifier & Continuer automatiquement  
  
1.  En mode arrêt, apporter une modification à votre code source.  
  
2.  À partir de la **déboguer** menu, cliquez sur **continuer**, **étape**, ou **définir l’instruction suivante** ou évaluez une fonction dans une fenêtre du débogueur.  
  
     Le nouveau code est compilé et le débogage se poursuit avec le nouveau code. Certaines modifications ne sont pas pris en charge par Modifier & Continuer. Pour plus d’informations, consultez [modifications de Code prises en charge (c# et Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier & Continuer  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, développez le **débogage** nœud et sélectionnez **Modifier & Continuer**.  
  
3.  Dans le **Options** boîte de dialogue **Modifier & Continuer** page, activez ou désactivez le **Activer Modifier & Continuer** case à cocher.  
  
     Le paramètre prend effet lorsque vous redémarrez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifications de Code prises en charge (c# et Visual Basic)](../debugger/supported-code-changes-csharp.md)   