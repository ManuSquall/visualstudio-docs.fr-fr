---
title: "Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant la d&#233;finition de l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; est requise | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant la d&#233;finition de l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; est requise
Une référence à l’assembly '\<`assemblyname`\>' contenant la définition de l’événement '\<`eventname`\>' est requise Ajoutez une référence à votre projet.  
  
 L’événement est défini dans une bibliothèque de liens dynamiques \(DLL\) ou un assembly qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nécessite une référence afin d’éviter toute ambiguïté au cas où l’événement serait défini dans plusieurs DLL ou assemblys.  
  
 **ID d’erreur :** BC30005  
  
### Pour corriger cette erreur  
  
-   Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)