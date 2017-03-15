---
title: "Utilisez l’option de ligne de commande &#39;&lt;option&gt;&#39; ou les param&#232;tres de projet appropri&#233;s plut&#244;t que &#39;&lt;param&#232;tre&gt;&#39; | Microsoft Docs"
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
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Utilisez l’option de ligne de commande &#39;&lt;option&gt;&#39; ou les param&#232;tres de projet appropri&#233;s plut&#244;t que &#39;&lt;param&#232;tre&gt;&#39;
La meilleure façon de spécifier un fichier contenant une clé publique ou un conteneur de clé publique pour un assembly, ou un assembly partiellement signé est d’utiliser les options du compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. L’utilisation des attributs <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> ou <xref:System.Reflection.AssemblyDelaySignAttribute> dans votre code n’est pas recommandée.  
  
 **ID d’erreur :** BC41008  
  
### Pour corriger cette erreur  
  
1.  Utilisez les options du compilateur [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile), [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) ou [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] au lieu des attributs <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> ou <xref:System.Reflection.AssemblyDelaySignAttribute> dans votre code.  
  
## Voir aussi  
 [Comment : créer des assemblys Friend signés](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)