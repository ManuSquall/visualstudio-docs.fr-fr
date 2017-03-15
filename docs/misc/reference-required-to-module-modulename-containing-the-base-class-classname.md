---
title: "Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant la classe de base &#39;&lt;nom_classe&gt;&#39; est requise | Microsoft Docs"
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
  - "vbc30008"
  - "bc30008"
helpviewer_keywords: 
  - "BC30008"
ms.assetid: ec8de475-8a8b-4aa5-86c9-6fcc44dcec06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant la classe de base &#39;&lt;nom_classe&gt;&#39; est requise
Une référence au module '\<nom\_module\>' contenant la classe de base '\<nom\_classe\>' est requise. Ajoutez\-en une à votre projet.  
  
 La classe est définie dans un module qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nécessite une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs modules.  
  
 **ID d’erreur :** BC30008  
  
### Pour corriger cette erreur  
  
-   Ajoutez le nom du module non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)