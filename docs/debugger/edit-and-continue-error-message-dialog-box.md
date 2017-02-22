---
title: "Message d&#39;erreur de Modifier &amp; Continuer, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Message d'erreur de Modifier & Continuer (boîte de dialogue)"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Message d&#39;erreur de Modifier &amp; Continuer, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue apparaît lorsque vous déboguez dans un langage qui prend en charge Modifier & Continuer, mais que **Modifier & Continuer** n'est pas disponible pour le type des modifications de code que vous avez apportées.  Le message d'erreur affiché dans la boîte de dialogue fournit une explication plus détaillée.  Les raisons pouvant justifier l'affichage de cette boîte de dialogue sont les suivantes :  
  
-   Vous avez essayé de modifier un code managé alors que le débogage non managé était activé.  Modifier & Continuer ne fonctionne pas en débogage en mode mixte.  
  
-   Vous avez essayé de modifier le code SQL Server.  
  
-   Vous avez essayé de modifier le code en déboguant un Dr.  Dr. Watson.  
  
-   Vous avez essayé de modifier le code après qu'une exception non gérée se soit produite, et que l'option **Dérouler la pile des appels sur les exceptions non gérées** n'était pas sélectionnée.  
  
-   Vous avez essayé de modifier le code pendant le débogage d'une application d'exécution incorporée.  
  
-   Vous avez essayé de modifier le code dans un programme auquel vous vous êtes attaché plutôt que de commencer au menu **Déboguer**.  
  
-   Vous avez essayé de modifier un code optimisé.  
  
-   Vous avez essayé de modifier du code managé alors que la cible est une application 64 bits.  Pour utiliser Modifier & Continuer, vous devez affecter x86 à la cible. \(Propriétés de *Project*, onglet **Compiler**, **Paramètres avancés du compilateur**\).  
  
-   Vous avez tenté de modifier le code d'un assembly qui a été modifié pendant le débogage et a été rechargé.  
  
-   Vous avez tenté de modifier le code d'un assembly qui n'a pas été chargé.  
  
-   Vous avez commencé à déboguer une version ancienne de votre application \(étant donné que la nouvelle version comporte des erreurs de build\).  
  
-   Vous avez tenté de modifier le code d'édition pendant son exécution.  
  
## Liste UIElement  
 **OK**  
 Fermez la boîte de dialogue et annulez la tentative de modification précédente.  
  
## Voir aussi  
 [Limitations et modifications de code prises en charge \(C\+\+\)](../debugger/supported-code-changes-cpp.md)