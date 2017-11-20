---
title: "CA1026 : Les paramètres par défaut ne doivent pas utilisés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d7a850c959787282cdf6f9d24b392ef4684b7dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026 : Les paramètres par défaut ne doivent pas être utilisés
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type visible de l’extérieur contient une méthode extérieurement visible qui utilise un paramètre par défaut.  
  
## <a name="rule-description"></a>Description de la règle  
 Les méthodes qui utilisent les paramètres par défaut sont autorisées sous le Common Language Specification (CLS) ; Toutefois, cette spécification permet aux compilateurs d’ignorer les valeurs assignées à ces paramètres. Code qui est écrit pour les compilateurs qui ignorent les valeurs de paramètre par défaut doit fournir explicitement des arguments pour chaque paramètre par défaut. Pour préserver le comportement souhaité entre les langages de programmation, les méthodes qui utilisent les paramètres par défaut doivent être remplacées par les surcharges de méthode qui fournissent les paramètres par défaut.  
  
 Le compilateur ignore les valeurs de paramètres par défaut pour les extensions managées pour C++ lorsqu’il accède à du code managé. Le compilateur Visual Basic prend en charge les méthodes qui ont des paramètres par défaut qui utilisent le [facultatif](/dotnet/visual-basic/language-reference/modifiers/optional) (mot clé).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez la méthode qui utilise les paramètres par défaut avec des surcharges de méthode qui fournissent les paramètres par défaut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui utilise les paramètres par défaut et les méthodes surchargées qui offrent une fonctionnalité équivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1025 : Remplacez les arguments répétitifs par un tableau params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indépendance du langage et composants indépendants du langage](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)