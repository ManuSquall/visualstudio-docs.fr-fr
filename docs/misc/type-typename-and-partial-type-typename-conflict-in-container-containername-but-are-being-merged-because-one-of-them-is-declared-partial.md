---
title: "Le type &#39;&lt;nom_type&gt;&#39; et le type partiel &#39;&lt;nom_type&gt;&#39; sont en conflit dans le conteneur &#39;&lt;nom_conteneur&gt;&#39;, mais sont fusionn&#233;s, car l’un d’eux est d&#233;clar&#233; partiel | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; et le type partiel &#39;&lt;nom_type&gt;&#39; sont en conflit dans le conteneur &#39;&lt;nom_conteneur&gt;&#39;, mais sont fusionn&#233;s, car l’un d’eux est d&#233;clar&#233; partiel
Une classe ou une structure apparaît dans plusieurs définitions du même type conteneur, et plusieurs définitions ne sont pas marquées comme `Partial`.  
  
 Vous devez utiliser le mot clé [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) sur au moins l’une des définitions d’une classe ou d’une structure, mais il est recommandé de l’utiliser sur toutes les définitions partielles.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40046  
  
### Pour corriger cette erreur  
  
-   Utilisez le mot clé [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) sur chaque définition partielle de la classe ou de la structure.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)