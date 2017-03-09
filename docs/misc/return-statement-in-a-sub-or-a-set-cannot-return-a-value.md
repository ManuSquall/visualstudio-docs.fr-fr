---
title: "L’instruction &#39;Return&#39; dans un Sub ou un Set ne peut pas retourner de valeur | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;Return&#39; dans un Sub ou un Set ne peut pas retourner de valeur
Les procédures `Sub` et les procédures `Set` de propriétés ne peuvent pas retourner de valeurs.  
  
 **ID d’erreur :** BC30647  
  
### Pour corriger cette erreur  
  
-   Remplacez la procédure active par une fonction, ou par une procédure de propriété `Get` si la procédure active fait partie d’une propriété.  
  
-   Vous pouvez retourner des valeurs à partir des procédures `Sub` en modifiant la valeur des paramètres passés par référence à l’aide du mot clé `ByRef`.  
  
## Voir aussi  
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function, procédures](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)