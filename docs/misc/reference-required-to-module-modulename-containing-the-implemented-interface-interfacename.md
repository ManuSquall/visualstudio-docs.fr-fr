---
title: "Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant l’interface impl&#233;ment&#233;e &#39;&lt;nom_interface&gt;&#39; est requise | Microsoft Docs"
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
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence au module &#39;&lt;nom_module&gt;&#39; contenant l’interface impl&#233;ment&#233;e &#39;&lt;nom_interface&gt;&#39; est requise
Une référence au module '\<nom\_module\>' contenant l’interface implémentée '\<nom\_interface\>' est requise. Ajoutez\-en une à votre projet.  
  
 L’interface est définie dans un module qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nécessite une référence pour éviter toute ambiguïté au cas où l’interface serait définie dans plusieurs modules.  
  
 **ID d’erreur :** BC30010  
  
### Pour corriger cette erreur  
  
-   Ajoutez le nom du module non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)