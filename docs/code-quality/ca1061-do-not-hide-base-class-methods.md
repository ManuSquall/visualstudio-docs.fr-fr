---
title: "CA1061 : Ne pas masquer les méthodes de classe de base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c2cd6c6cfd06be965581d422b835014f09dd96b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061 : Ne pas masquer les méthodes de la classe de base
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type dérivé déclare une méthode portant le même nom et avec le même nombre de paramètres qu’une de ses méthodes de base ; un ou plusieurs des paramètres sont un type de base du paramètre correspondant dans la méthode de base ; et tous les paramètres restants ont des types qui sont identiques aux paramètres correspondants dans la méthode de base.  
  
## <a name="rule-description"></a>Description de la règle  
 Une méthode dans un type de base est masquée par une méthode portant le même nommée dans un type dérivé lorsque la signature de paramètre de la méthode dérivée diffère uniquement par les types qui sont dérivés plus faiblement que les types correspondants dans la signature de paramètre de la méthode de base.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez ou renommez la méthode ou modifiez la signature de paramètre afin que la méthode ne masque pas la méthode de base.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui enfreint la règle.  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]