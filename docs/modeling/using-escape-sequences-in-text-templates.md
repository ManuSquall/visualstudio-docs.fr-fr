---
title: "Using Escape Sequences in Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, escape sequences"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Using Escape Sequences in Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser des séquences d'échappement dans les modèles de texte pour générer des balises de modèle de texte et \(dans le code C\# uniquement\) pour échapper des caractères de contrôle et des guillemets.  
  
 Pour imprimer les balises d'ouverture et de fermeture d'un bloc de code standard dans le fichier de sortie, échappez les balises comme suit :  
  
```  
\<# ... \#>  
```  
  
 Vous pouvez effectuer la même opération avec d'autres balises de bloc de code et de directive de modèle de texte.  
  
 Si un bloc de texte inclut des chaînes utilisées pour échapper des balises de modèle de texte, vous pouvez utiliser les séquences d'échappement suivantes :  
  
-   Si une balise de modèle de texte est précédée d'un nombre pair de caractères d'échappement \(\\\), l'analyseur de modèle inclura la moitié des caractères d'échappement, ainsi que la séquence en tant que balise de modèle de texte.  Par exemple, si le modèle de texte comporte quatre caractères d'échappement, le fichier généré contiendra deux caractères "\\".  
  
-   Si la balise de modèle de texte est précédée d'un nombre impair de caractères d'échappement \(\\\), l'analyseur de modèle inclura la moitié des caractères "\\", ainsi que la balise elle\-même \(\<\# ou \#\>\).  La balise n'est pas considérée comme une balise de modèle de texte.  
  
-   Si un caractère d'échappement \(\\\) figure dans une séquence où il ne sert pas à échapper un caractère de contrôle ou un guillemet \(en C\# uniquement\), il s'affichera directement.  
  
## Voir aussi  
 [How to: Generate Templates from Templates By Using Escape Sequences](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)