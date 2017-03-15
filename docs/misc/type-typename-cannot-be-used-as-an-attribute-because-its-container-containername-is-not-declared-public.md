---
title: "Impossible d’utiliser le type &#39;&lt;nom_type&gt;&#39; dans un attribut, car son conteneur &#39;&lt;nom_conteneur&gt;&#39; n’est pas d&#233;clar&#233; &#39;Public&#39; | Microsoft Docs"
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
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’utiliser le type &#39;&lt;nom_type&gt;&#39; dans un attribut, car son conteneur &#39;&lt;nom_conteneur&gt;&#39; n’est pas d&#233;clar&#233; &#39;Public&#39;
La classe ou le module où cet attribut est défini ne sont pas déclarés à l’aide du modificateur `Public`. Les classes et les modules qui ne spécifient pas un modificateur d’accès sont déclarés comme `Friend` par défaut.  
  
 **ID d’erreur :** BC31517  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le modificateur `Public` à la classe ou au module où est défini cet attribut.  
  
## Voir aussi  
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)