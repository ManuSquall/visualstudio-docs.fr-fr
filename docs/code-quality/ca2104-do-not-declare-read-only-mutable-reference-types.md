---
title: "CA2104&#160;: Ne d&#233;clarez pas les types r&#233;f&#233;rence mutables en lecture seule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2104&#160;: Ne d&#233;clarez pas les types r&#233;f&#233;rence mutables en lecture seule
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type visible de l'extérieur contient un champ en lecture seule visible de l'extérieur qui constitue un type référence mutable.  
  
## Description de la règle  
 Un type mutable est un type dont les données d'instance peuvent être modifiées.  La classe <xref:System.Text.StringBuilder?displayProperty=fullName> est un exemple de type référence mutable.  Il contient des membres qui peuvent modifier la valeur d'une instance de la classe.  La classe <xref:System.String?displayProperty=fullName> est un exemple de type référence immuable.  Après son instanciation, sa valeur ne peut plus changer.  
  
 Le modificateur en lecture seule \([readonly](/dotnet/csharp/language-reference/keywords/readonly) en C\-, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [const](/visual-cpp/cpp/const-cpp) en C\+\+\) sur un champ de type référence \(pointeur en C\+\+\) empêche le remplacement du champ par une instance différente du type de référence.  Cependant, le modificateur n'empêche pas les données d'instance du champ d'être modifiées par le type référence.  
  
 Les champs de tableau en lecture seule sont exemptés de cette règle, mais engendrent en revanche une violation de la règle [CA2105 : Les champs de tableau ne doivent pas être en lecture seule](../code-quality/ca2105-array-fields-should-not-be-read-only.md).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule ou, si une modification sans rupture est acceptable, remplacez le champ par un type immuable.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le type du champ est immuable.  
  
## Exemple  
 L'exemple suivant présente une déclaration de champ qui provoque une violation de cette règle.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]