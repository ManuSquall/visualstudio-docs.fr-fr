---
title: "CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 073ce1d22662b46a19bf5cf36305df63500347a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type tranparent ou une méthode est marquée de façon déclarative avec un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` à la demande ou la méthode appelle la <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> (méthode).  
  
## <a name="rule-description"></a>Description de la règle  
 Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Le code transparent de sécurité doit utiliser des demandes complètes pour prendre des décisions de sécurité et le code critique sécurisé ne doit pas dépendre du code transparent pour l'exécution de ces demandes. Tout code qui effectue des vérifications de sécurité, telles que les demandes de sécurité doit être critique de sécurité à la place.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 En général, pour corriger une violation de cette règle, marquez la méthode avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut. Vous pouvez également supprimer la demande.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 La règle de fichiers sur le code suivant, car une méthode transparente effectue une demande de sécurité déclarative.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)