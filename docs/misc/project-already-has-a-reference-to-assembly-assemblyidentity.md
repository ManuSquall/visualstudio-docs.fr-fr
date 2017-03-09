---
title: "Le projet a d&#233;j&#224; une r&#233;f&#233;rence &#224; l’assembly &lt;identit&#233;_assembly&gt; | Microsoft Docs"
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
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le projet a d&#233;j&#224; une r&#233;f&#233;rence &#224; l’assembly &lt;identit&#233;_assembly&gt;
Le projet a déjà une référence à l’assembly \<identité\_assembly\>. Une seconde référence à '\<chemin\_fichier\>' ne peut pas être ajoutée.  
  
 Un projet référence plusieurs fois le même assembly.  
  
 L’identité de l’assembly comprend le nom de l’assembly, sa version, sa clé publique, le cas échéant, et sa culture.  
  
 Cette erreur peut également être causée par une référence à une autre copie de l’assembly via un chemin de fichier autre que celui de la référence d’origine.  
  
 **ID d’erreur :** BC32208  
  
### Pour corriger cette erreur  
  
-   Supprimez la deuxième référence. Elle est inutile, car elle fait référence au même assembly.  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)