---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; un &#39;Get&#39; ou &#39;Set&#39; | Microsoft Docs"
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
  - "vbc31524"
  - "bc31524"
helpviewer_keywords: 
  - "BC31524"
ms.assetid: 3603e33a-a80b-448d-83e0-e5dbc9af4dcf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; un &#39;Get&#39; ou &#39;Set&#39;
L’attribut `DllImportAttribute` a été appliqué à une procédure de propriété `Get` ou `Set`.  
  
 **ID d’erreur :** BC31524  
  
### Pour corriger cette erreur  
  
1.  Supprimez `DllImportAttribute` des procédures de propriété `Get` et `Set`.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)