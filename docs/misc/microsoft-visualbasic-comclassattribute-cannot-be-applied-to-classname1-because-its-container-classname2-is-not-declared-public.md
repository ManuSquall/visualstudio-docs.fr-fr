---
title: "Impossible d’appliquer &#39;Microsoft.VisualBasic.ComClassAttribute&#39; &#224; &#39;&lt;nom_classe1&gt;&#39;, car son conteneur &#39;&lt;nom_classe2&gt;&#39; n’est pas d&#233;clar&#233; &#39;Public&#39; | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer &#39;Microsoft.VisualBasic.ComClassAttribute&#39; &#224; &#39;&lt;nom_classe1&gt;&#39;, car son conteneur &#39;&lt;nom_classe2&gt;&#39; n’est pas d&#233;clar&#233; &#39;Public&#39;
Une classe qui utilise un bloc d’attributs `COMClassAttribute` est déclarée à l’intérieur d’une classe qui n’est pas `Public`. Si une classe doit être exposée comme objet COM, sa hiérarchie de contenance entière doit être déclarée avec un accès `Public`.  
  
 **ID d’erreur :** BC32504  
  
### Pour corriger cette erreur  
  
-   Déclarez toutes les classes conteneurs `Public` ou supprimez le bloc d’attributs `COMClassAttribute`.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)