---
title: 'Comment : utiliser modifier & Continuer (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839737"
---
# <a name="how-to-use-edit-and-continue-c"></a>Comment : utiliser Modifier &amp; Continuer (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec Modifier &amp; Continuer pour C#, vous pouvez modifier votre code en mode arrêt pendant le débogage. Les modifications peuvent être appliquées sans qu'il soit nécessaire d'arrêter et de redémarrer la session de débogage.  
  
 Modifier & Continuer est appelé automatiquement lorsque vous apportez des modifications en mode arrêt, puis choisissez une commande d’exécution du débogueur, telle que **Continuer**, **exécuter pas à pas**ou **définir l’instruction suivante**, ou évaluer une fonction dans une fenêtre du débogueur.  
  
> [!NOTE]
> Modifier & Continuer n’est pas pris en charge lors du débogage de Compact Framework, du code optimisé, du code mixte natif/managé ou du code d’intégration SQL Server common language runtime (CLR). Si vous essayez d’appliquer des modifications de code dans l’un de ces scénarios, le débogueur insère une boîte de dialogue qui explique que modifier & Continuer n’est pas pris en charge.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Pour appeler modifier & continuer automatiquement  
  
1. En mode arrêt, apportez une modification à votre code source.  
  
2. Dans le menu **Déboguer** , cliquez sur **Continuer**, **exécuter pas à pas**, ou **définir l’instruction suivante** ou évaluer une fonction dans une fenêtre du débogueur.  
  
     Le nouveau code est compilé et le débogage se poursuit avec le nouveau code. Certaines modifications ne sont pas prises en charge par modifier & continuer. Pour plus d’informations, consultez [modifications de code prises en charge (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier &amp; Continuer  
  
1. Dans le menu **Outils** , cliquez sur **Options**.  
  
2. Dans la boîte de dialogue **options** , développez le nœud **débogage** , puis sélectionnez **Modifier & Continuer**.  
  
3. Dans la page Modifier & **Continuer** de la boîte de dialogue **options** , cochez ou décochez la case **activer modifier et continuer** .  
  
     Le paramètre prend effet lorsque vous redémarrez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifications du code prises en charge (C#)](../debugger/supported-code-changes-csharp.md)   
 [Erreurs et avertissements de modifier & Continuer (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
