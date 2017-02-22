---
title: "CA2208&#160;: Instanciez les exceptions d&#39;argument comme il se doit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2208&#160;: Instanciez les exceptions d&#39;argument comme il se doit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Plusieurs causes sont possibles :  
  
-   Le constructeur par défaut \(sans paramètre\) d'un type d'exception qui correspond à ou dérive de [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True) est appelé.  
  
-   Un argument de chaîne incorrect est passé à un constructeur paramétré d'un type d'exception qui correspond à ou dérive de [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True)  
  
## Description de la règle  
 Au lieu d'appeler le constructeur par défaut, appelez l'une des surcharges de constructeur qui permettent de fournir un message d'exception plus explicite.  Le message d'exception doit s'adresser au développeur et clairement expliquer la condition d'erreur ainsi que la manière de corriger ou éviter l'exception.  
  
 Les signatures des premier et second constructeurs string de <xref:System.ArgumentException> et ses types dérivés ne sont pas cohérents en ce qui concerne les paramètres `message` et `paramName`.  Assurez\-vous que ces constructeurs sont appelés avec les arguments string corrects.  Les signatures sont les suivantes :  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre, ou les deux, et assurez\-vous que les arguments sont adaptés au type de <xref:System.ArgumentException> appelé.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle uniquement si un constructeur paramétré est appelé avec les arguments string corrects.  
  
## Exemple  
 L'exemple suivant présente un constructeur qui n'instancie pas correctement une instance du type ArgumentNullException.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Exemple  
 L'exemple suivant résout la violation ci\-dessus en changeant les arguments du constructeur.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]