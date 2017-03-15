---
title: "La propri&#233;t&#233; &#39;ReadOnly&#39; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre la cible d’une assignation. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; &#39;ReadOnly&#39; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre la cible d’une assignation.
Une propriété `ReadOnly` est utilisée dans un contexte qui lui assigne une valeur. Seules les variables, les propriétés et les éléments de tableau accessibles en écriture peuvent recevoir des valeurs durant l’exécution.  
  
 **ID d’erreur :** BC30098  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `ReadOnly` de l’instruction `Property` qui déclare la variable, ou supprimez l’instruction qui lui assigne une valeur.  
  
## Voir aussi  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)