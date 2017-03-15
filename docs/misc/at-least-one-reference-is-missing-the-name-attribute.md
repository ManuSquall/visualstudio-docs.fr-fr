---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
Chaque référence doit être associée à une propriété **Name**, comme indiqué ci\-dessous :  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 Cette erreur indique que la propriété **Name** est introuvable pour au moins une référence.  
  
 La cause la plus probable de cette erreur est la modification manuelle du fichier projet.  
  
 **Pour corriger cette erreur**  
  
-   Rajoutez la référence.  
  
     Toute référence affectée ne sera pas ajoutée au projet.  
  
## Voir aussi  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)