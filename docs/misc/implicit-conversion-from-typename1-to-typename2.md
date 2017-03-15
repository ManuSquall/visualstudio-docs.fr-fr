---
title: "Conversion implicite de &#39;&lt;nom_type1&gt;&#39; en &#39;&lt;nom_type2&gt;&#39; | Microsoft Docs"
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
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conversion implicite de &#39;&lt;nom_type1&gt;&#39; en &#39;&lt;nom_type2&gt;&#39;
Une expression ou une instruction d’assignation accepte une valeur d’un type de données et la convertit en un autre type. Aucun mot clé de conversion n’a été utilisé, la conversion est donc *implicite*.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42016  
  
### Pour corriger cette erreur  
  
-   Si possible, utilisez des valeurs du même type de données, pour que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n’ait pas à effectuer de conversion.  
  
-   Utilisez `CType` ou l’un des autres mots clés de conversion pour que la conversion soit *explicite*.  
  
## Voir aussi  
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)