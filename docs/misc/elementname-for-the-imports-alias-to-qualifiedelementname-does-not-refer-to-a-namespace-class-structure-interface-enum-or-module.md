---
title: "&#39;&lt;nom_&#233;l&#233;ment&gt;&#39; utilis&#233; pour l’alias Imports de &#39;&lt;nom_&#233;l&#233;ment_qualifi&#233;&gt;&#39; ne fait pas r&#233;f&#233;rence &#224; un Namespace, Class, Structure, Interface, Enum ou Module | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; utilis&#233; pour l’alias Imports de &#39;&lt;nom_&#233;l&#233;ment_qualifi&#233;&gt;&#39; ne fait pas r&#233;f&#233;rence &#224; un Namespace, Class, Structure, Interface, Enum ou Module
[Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) spécifie un élément de programmation qui ne peut pas être importé.  
  
 L’instruction `Imports` permet de réduire ou d’éliminer la nécessité d’une chaîne qualifiante devant un nom d’élément. Vous qualifiez l’élément dans l’instruction `Imports` pour fournir un chemin non équivoque à une déclaration unique de l’élément. Ensuite, il est inutile de qualifier les références à l’élément.  
  
 `Imports` est le plus souvent utilisé pour les espaces de noms, mais vous pouvez également importer une classe, un module, une structure, une interface ou une énumération pour permettre le référencement à leurs éléments sans une longue chaîne qualifiante.  
  
 Pour plus d’informations, consultez la section « Importation d’éléments conteneurs » dans [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
 **ID d’erreur :** BC30798  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe des éléments dans la chaîne de qualification de l’instruction `Imports`, en particulier le dernier élément de la chaîne puisqu’il s’agit de l’élément que vous qualifiez.  
  
2.  Vérifiez que le type de l’élément que vous qualifiez est éligible \(espace de noms, classe, module, structure, interface ou énumération\). Si ce n’est pas le cas, supprimez l’instruction `Imports`.  
  
## Voir aussi  
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)