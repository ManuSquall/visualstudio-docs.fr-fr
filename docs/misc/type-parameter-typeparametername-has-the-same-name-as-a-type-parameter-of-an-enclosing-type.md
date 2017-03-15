---
title: "Le param&#232;tre de type &#39;&lt;nom_type_param&#232;tre&gt;&#39; a le m&#234;me nom qu’un param&#232;tre de type d’un type englobant | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_type_param&#232;tre&gt;&#39; a le m&#234;me nom qu’un param&#232;tre de type d’un type englobant
Un paramètre de type d’un type générique est déclaré avec le même nom qu’un paramètre de type d’un type générique conteneur.  
  
 Dans la liste des paramètres de type d’un type générique, chaque paramètre de type doit avoir un nom différent de tous les noms suivants :  
  
-   Chaque autre paramètre de type dans la même liste de paramètres de type  
  
-   Chaque paramètre de type présent dans la liste des paramètres de type d’un type générique conteneur, et  
  
-   Le nom du type générique lui\-même  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40048  
  
### Pour corriger cette erreur  
  
-   Renommez le paramètre de type pour qu’il soit distinct de chaque nom cité dans la liste de cette page d’aide.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)