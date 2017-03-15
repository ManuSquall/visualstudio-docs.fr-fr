---
title: "Comment&#160;: utiliser Modifier &amp; Continuer (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifier & Continuer (C#), à propos de Modifier & Continuer"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: utiliser Modifier &amp; Continuer (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avec Modifier & Continuer pour C\#, vous pouvez modifier votre code en mode arrêt pendant le débogage.  Les modifications peuvent être appliquées sans qu'il soit nécessaire d'arrêter et de redémarrer la session de débogage.  
  
 Modifier & Continuer est appelé automatiquement lorsque vous apportez des modifications en mode arrêt, puis choisissez une commande d'exécution de débogueur, telle que **Continuer**, **Exécuter pas à pas** ou **Définir l'instruction suivante** ou évaluez une fonction dans une fenêtre de débogueur.  
  
> [!NOTE]
>  L'opération Modifier & Continuer n'est pas prise en charge lors du débogage de Compact Framework, de code optimisé, de code managé\/natif mixte Compact Framework ou de code d'intégration du Common Language Runtime \(CLR\) SQL Server.  Si vous tentez de procéder à des modifications de code dans l'un de ces scénarios, le débogueur affiche une boîte de dialogue qui explique que Modifier & Continuer n'est pas pris en charge.  
  
### Pour appeler Modifier & Continuer automatiquement  
  
1.  En mode arrêt, modifiez votre code source.  
  
2.  Dans le menu **Déboguer**, cliquez sur **Continuer**, **Exécuter pas à pas** ou **Définir l'instruction suivante** ou évaluez une fonction dans une fenêtre de débogueur.  
  
     Le nouveau code est compilé et permet de poursuivre le débogage.  Certaines modifications ne sont pas prises en charge par Modifier & Continuer.  Pour plus d'informations, consultez [Modifications de code prises en charge \(C\#\)](../debugger/supported-code-changes-csharp.md).  
  
### Pour activer ou désactiver Modifier & Continuer  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, développez le nœud **Débogage** et sélectionnez **Modifier & Continuer**.  
  
3.  À la page **Modifier & Continuer** de la boîte de dialogue **Options**, activez ou désactivez la case à cocher **Activer Modifier & Continuer**.  
  
     Le paramètre entre en vigueur lorsque vous redémarrez la session de débogage.  
  
## Voir aussi  
 [Modifier & Continuer \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifications de code prises en charge \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [Erreurs et avertissements de Modifier & Continuer \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)