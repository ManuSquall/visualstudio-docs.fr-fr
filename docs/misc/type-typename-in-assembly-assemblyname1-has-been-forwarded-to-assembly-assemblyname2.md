---
title: "Le type &#39;&lt;nom_type&gt;&#39; dans l’assembly &#39;&lt;nom_assembly1&gt;&#39; a &#233;t&#233; transmis &#224; l’assembly &#39;&lt;nom_assembly2&gt;&#39; | Microsoft Docs"
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
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "transfert de type"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; dans l’assembly &#39;&lt;nom_assembly1&gt;&#39; a &#233;t&#233; transmis &#224; l’assembly &#39;&lt;nom_assembly2&gt;&#39;
Le type '\<nom\_type\>' dans l’assembly '\<nom\_assembly1\>' a été transmis à l’assembly '\<nom\_assembly2\>'. Soit une référence à '\<nom\_assembly2\>' est absente du projet, soit le type '\<nom\_type\>' est absent de l’assembly '\<nom\_assembly2\>'.  
  
 Une expression dans le code source d’un assembly fait référence à un type qui a été transféré à un autre assembly, mais le type est introuvable dans l’assembly de destination.  
  
 Le *transfert de type* consiste à réassigner la définition d’une classe, structure, interface, délégué ou énumération à un assembly autre que celui dans lequel il ou elle a été initialement défini\(e\). On l’utilise souvent conjointement avec la *refactorisation de code*, qui consiste à fractionner un assembly en plusieurs assemblys ou à déplacer du code d’un assembly vers un autre.  
  
 Même si le type est encore momentanément disponible dans l’assembly d’origine, il est probable qu’il devienne indéfini quand la refactorisation du code le supprime de l’assembly d’origine.  
  
 **ID d’erreur :** BC31424  
  
### Pour corriger cette erreur  
  
-   Vérifiez que le type est présent dans l’assembly de destination.  
  
-   Vérifiez que votre projet a une référence à l’assembly de destination.  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB Procédure : ajout ou suppression de références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)