---
title: "&#39;&lt;constructeur&gt;&#39; dans le type g&#233;n&#233;r&#233; par le concepteur &#39;&lt;type&gt;&#39; doit appeler la m&#233;thode InitializeComponent | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;constructeur&gt;&#39; dans le type g&#233;n&#233;r&#233; par le concepteur &#39;&lt;type&gt;&#39; doit appeler la m&#233;thode InitializeComponent
Un constructeur dans un type généré par le concepteur n’appelle pas la méthode `InitializeComponent` du type.  
  
 Chaque constructeur dans un type généré par le concepteur doit appeler la méthode `InitializeComponent` du type.  
  
 **ID d’erreur :** BC40054  
  
### Pour corriger cette erreur  
  
-   Ajoutez un appel à la méthode `InitializeComponent` dans le constructeur.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)