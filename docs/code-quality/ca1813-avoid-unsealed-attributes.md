---
title: "CA1813 : Évitez les attributs unsealed | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ad548bd51985484ebcb39cb6022e994a5e0534a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813 : Évitez les attributs unsealed
|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Category|Microsoft.Performance|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public hérite <xref:System.Attribute?displayProperty=fullName>, n’est pas abstraite et n’est pas sealed (`NotInheritable` en Visual Basic).  
  
## <a name="rule-description"></a>Description de la règle  
 La bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d’héritage d’attribut ; par exemple <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> recherche le type d’attribut spécifié ou n’importe quel type d’attribut qui étend le type d’attribut spécifié. Le fait de sceller l’attribut élimine la recherche dans la hiérarchie d’héritage et peut améliorer les performances.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, scellez le type d’attribut ou rendez-le abstrait.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle. Vous devez le faire que si vous définissez une hiérarchie d’attribut et ne peut pas sceller l’attribut ou rendre abstraite.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un attribut personnalisé qui satisfait cette règle.  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1019 : Définissez des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018 : Marquez les attributs avec AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs](/dotnet/standard/design-guidelines/attributes)