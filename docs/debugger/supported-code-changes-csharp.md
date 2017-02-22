---
title: "Modifications de code prises en charge (C#) | Microsoft Docs"
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
  - "Modifier & Continuer (C#), modifications de code prises en charge"
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Modifications de code prises en charge (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifier & Continuer gère la plupart des types de modifications du code dans le corps des méthodes.  Toutefois, la plupart des modifications en dehors du corps des méthodes et quelques autres à l'intérieur ne peuvent pas s'appliquer pendant le débogage.  Pour appliquer ces modifications non prises en charge, vous devez arrêter le débogage et redémarrer avec une version nouvelle du code.  
  
 Les modifications suivantes ne peuvent pas être appliquées à du code C\# pendant une session de débogage :  
  
-   Modifications à l'instruction en cours ou à toute autre instruction active.  
  
     Les instructions actives incluent toutes les instructions, dans les fonctions figurant dans la pile des appels, qui ont été appelées pour parvenir à l'instruction en cours.  
  
     L'instruction en cours est marquée par un arrière\-plan jaune dans la fenêtre source.  D'autres instructions actives sont marquées par un arrière\-plan grisé et sont en lecture seule.  Ces couleurs par défaut peuvent être modifiées dans la boîte de dialogue **Options**.  
  
-   Modification de la signature d'un type.  
  
-   Ajout d'une méthode anonyme qui capture une variable qui n'a pas été capturée auparavant.  
  
-   Ajout, suppression ou modification d'attributs.  
  
-   Ajout, suppression ou modification de directives `using`.  
  
-   Ajout d'un `foreach`, d'un `using` ou d'un `lock` autour de l'instruction active.  
  
## Code unsafe  
 Les modifications apportées à du code unsafe présentent les mêmes restrictions que celles qui portent sur du code sécurisé, avec une restriction supplémentaire : Modifier & Continuer ne prend pas en charge les modifications de code unsafe dans une méthode qui contient l'opérateur `stackalloc`.  
  
## Exceptions  
 Modifier & Continuer prend en charge les modifications apportées aux blocs `catch` et `finally`, à l'exception de l'ajout d'un bloc `catch` ou `finally` autour de l'instruction active, qui n'est pas autorisé.  
  
## Scénarios non pris en charge  
 Modifier & Continuer n'est pas disponible dans les scénarios de débogage suivants :  
  
-   Débogage du code LINQ dans certaines circonstances.  Pour plus d'informations, consultez [Débogage LINQ](../debugger/debugging-linq.md).  
  
    -   Capture d'une variable qui n'a pas été capturée auparavant.  
  
    -   Modification du type de l'expression de requête \(par exemple, select a \=\> select new { A \= a };\)  
  
    -   Suppression d'un `where` qui contient une instruction active.  
  
    -   Suppression d'un `let` qui contient une instruction active.  
  
    -   Suppression d'un `join` qui contient une instruction active.  
  
    -   Suppression d'un `orderby` qui contient une instruction active.  
  
-   Débogage en mode mixte \(natif\/managé\).  
  
-   Débogage SQL.  
  
-   Débogage d'un dump  Dr. Watson.  
  
-   Modification de code après une exception non gérée, lorsque l'option « **Dérouler la pile des appels sur les exceptions non gérées** » n'est pas sélectionnée.  
  
-   Débogage d'une application runtime incorporée.  
  
-   Débogage d'une application avec **Attacher à** au lieu d'exécuter l'application en sélectionnant **Démarrer** dans le menu **Déboguer**.  
  
-   Débogage de code optimisé.  
  
-   Débogage d'une version ancienne de votre code après l'échec de génération d'une nouvelle version en raison d'erreurs de build.  
  
## Voir aussi  
 [Modifier & Continuer \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Comment : utiliser Modifier & Continuer \(C\#\)](../debugger/how-to-use-edit-and-continue-csharp.md)