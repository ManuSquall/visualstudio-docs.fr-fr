---
title: "Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant la d&#233;finition pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; est requise | Microsoft Docs"
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
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant la d&#233;finition pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; est requise
Une référence au module '\<`modulename`\>' contenant la définition pour l’événement '\<`eventname`\>' est requise. Ajoutez\-en une à votre projet.  
  
 L’événement est défini dans un module qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nécessite une référence pour éviter toute ambiguïté au cas où l’événement serait défini dans plusieurs modules.  
  
 **ID d’erreur :** BC30006  
  
### Pour corriger cette erreur  
  
-   Ajoutez le nom du module non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB : Références aux espaces de noms et aux composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)