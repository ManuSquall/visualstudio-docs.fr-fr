---
title: "&#39;&lt;nom_type&gt;&#39; porte le m&#234;me nom qu’un autre type expos&#233; dans un groupe &#39;My&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; porte le m&#234;me nom qu’un autre type expos&#233; dans un groupe &#39;My&#39;
'\<nom\_type\>' porte le même nom qu’un autre type exposé dans un groupe 'My'. Renommez le formulaire ou son espace de noms englobant.  
  
 Une classe ou structure est déclarée avec le même nom qu’une classe ou structure dans l’un des objets `My`.  
  
 Un conflit de noms n’a pas pu être évitée entre deux classes accessibles par le biais d’un objet `My`, comme `My.Forms`.  
  
 S’il existe un conflit de noms potentiel entre les classes dans un objet `My`, le compilateur remplace le nom de propriété du type *ClassName* par *RootNamespace*\_*Namespace*\_*ClassName*. Par exemple, prenons deux formulaires nommés `Form1`. Si l’un de ces formulaires se trouve dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1`, vous accédez à ce formulaire par le biais de `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 Cette erreur peut se produire si les deux classes portent le même nom et se trouvent dans des espaces de noms imbriqués qui comportent des traits de soulignement dans leurs noms. Quand le compilateur construit les nouveaux noms de propriété pour les classes, il existe encore un conflit de noms.  
  
 **ID d’erreur :** BC36015  
  
### Pour corriger cette erreur  
  
1.  Renommez le nouveau formulaire.  
  
2.  Renommez les espaces de noms.  
  
     Éviter de nommer une classe ou structure avec le même nom qu’une classe ou structure existante.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [My.Forms Object](/dotnet/visual-basic/language-reference/objects/my-forms-object)