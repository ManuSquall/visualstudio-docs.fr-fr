---
title: "Le projet &#39;&lt;nom_projet&gt;&#39; requiert une r&#233;f&#233;rence &#224; la version &#39;&lt;num&#233;ro_version1&gt;&#39; de l’assembly &#39;&lt;nom_assembly&gt;&#39;, mais r&#233;f&#233;rence la version &#39;&lt;num&#233;ro_version2&gt;&#39; de l’assembly &#39;&lt;nom_assembly&gt;&#39; (avertissement Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le projet &#39;&lt;nom_projet&gt;&#39; requiert une r&#233;f&#233;rence &#224; la version &#39;&lt;num&#233;ro_version1&gt;&#39; de l’assembly &#39;&lt;nom_assembly&gt;&#39;, mais r&#233;f&#233;rence la version &#39;&lt;num&#233;ro_version2&gt;&#39; de l’assembly &#39;&lt;nom_assembly&gt;&#39; (avertissement Visual Basic)
Le projet '\<nom\_projet\>' requiert une référence à la version '\<numéro\_version1\>' de l’assembly '\<nom\_assembly\>', mais référence la version '\<numéro\_version2\>' de l’assembly '\<nom\_assembly\>'. Une référence à la version '\<numéro\_version2\>' a été émise.  
  
 Un projet fait une référence indirecte à un assembly qui est défini ailleurs, mais le projet possède également une référence directe à une version antérieure de cet assembly.  
  
 Pour tenir compte de l’accès aux types et aux éléments de programmation définis dans la version ultérieure, mais pas dans la version antérieure, le compilateur utilise la référence indirecte à la version ultérieure lors de la résolution des accès.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42203  
  
### Pour corriger cette erreur  
  
-   Supprimez la référence directe à la version antérieure de l’assembly ou modifiez\-la pour faire référence à la version ultérieure.  
  
## Voir aussi  
 [Assemblys dans le Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB : Gestion des références](http://msdn.microsoft.com/fr-fr/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)