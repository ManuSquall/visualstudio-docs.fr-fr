---
title: "CA1061&#160;: Ne pas masquer les m&#233;thodes de la classe de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# CA1061&#160;: Ne pas masquer les m&#233;thodes de la classe de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type dérivé déclare une méthode avec le même nom et le même nombre de paramètres que l'une de ses méthodes de base, un ou plusieurs des paramètres est un type de base du paramètre correspondant dans la méthode de base et tous paramètres restants ont des types qui sont identiques aux paramètres correspondants dans la méthode de base.  
  
## Description de la règle  
 Une méthode dans un type de base est masquée par une méthode portant le même nom dans un type dérivé lorsque la signature de paramètre de la méthode dérivée diffère uniquement par les types qui sont dérivés plus faiblement que les types correspondants dans la signature de paramètre de la méthode de base.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez ou renommez la méthode, ou modifiez la signature de paramètre afin que la méthode ne masque pas la méthode de base.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente une méthode qui enfreint la règle.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]