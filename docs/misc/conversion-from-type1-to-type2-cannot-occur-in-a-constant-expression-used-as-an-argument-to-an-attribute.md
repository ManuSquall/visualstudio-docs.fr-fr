---
title: "La conversion de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39; ne peut pas se produire dans une expression constante utilis&#233;e en tant qu’argument d’un attribut | Microsoft Docs"
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
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La conversion de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39; ne peut pas se produire dans une expression constante utilis&#233;e en tant qu’argument d’un attribut
Une expression utilisée pour un argument d’attribut est évaluée à un type de données différent de celui du paramètre d’attribut correspondant, et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n’autorise pas la conversion de type requise pour les arguments d’attributs.  
  
 Un attribut fournit des métadonnées pour l’élément auquel il est appliqué, et le compilateur doit pouvoir construire toutes les métadonnées au moment de la compilation. Pour cette raison, chaque attribut doit utiliser des valeurs constantes au moment de la compilation. Ainsi, chaque argument d’attribut doit être évalué à une valeur constante au moment de la compilation.  
  
 Certaines conversions de type ne peuvent pas produire de valeurs constantes au moment de la compilation. Par exemple, la conversion de `String` en `Double` ou `Date` dépend des paramètres régionaux au moment de l’exécution. D’autres conversions, telles que celle d’un tableau d’un type dérivé vers un tableau de `Object`, présentent de nombreux problèmes qui ne permettent pas au compilateur de les autoriser sur les arguments d’attributs.  
  
 **ID d’erreur :** BC30934  
  
### Pour corriger cette erreur  
  
-   Utilisez une expression qui est évaluée au même type de données que le paramètre correspondant, tel que défini par l’attribut.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)