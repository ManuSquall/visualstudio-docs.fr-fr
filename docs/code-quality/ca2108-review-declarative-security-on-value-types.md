---
title: "CA2108 : Vérifiez la sécurité déclarative dans les types valeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b05873b87767fa39cc6e0d675980bf658d76c584
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108 : Vérifiez la sécurité déclarative dans les types valeur
|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Category|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type valeur public ou protégé est sécurisé par un [données et modélisation](/dotnet/framework/data/index) ou [les demandes de liaison](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Description de la règle  
 Types valeur sont alloués et initialisés par leurs constructeurs par défaut avant d’exécutent d’autres constructeurs. Si un type valeur est sécurisé par une demande ou d’un LinkDemand, et l’appelant n’a pas d’autorisations qui satisfont la vérification de sécurité, un constructeur autre que la valeur par défaut échoue et une exception de sécurité est levée. Le type de valeur n’est pas libéré ; Il est conservé dans l’état défini par son constructeur par défaut. Ne supposez pas qu’un appelant qui passe une instance du type valeur est autorisé à créer ou accéder à l’instance.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Vous ne pouvez pas corriger une violation de cette règle, sauf si vous supprimez la vérification de sécurité à partir du type, et utiliser la sécurité au niveau méthode vérifie à la place. Notez que la correction de la violation de cette manière n’empêche pas les appelants dotés d’autorisations inadéquates d’obtenir des instances du type valeur. Vous devez vous assurer qu’une instance du type valeur, dans son état par défaut, n’expose pas d’informations sensibles et ne peut pas être utilisée de façon préjudiciable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si un appelant peut obtenir des instances du type valeur dans son état par défaut sans que cela constitue une menace pour la sécurité.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une bibliothèque contenant un type valeur qui enfreint cette règle. Notez que le `StructureManager` type suppose qu’un appelant qui passe une instance du type valeur dispose d’autorisation de créer ou d’accéder à l’instance.  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’application suivante montre la faiblesse de la bibliothèque.  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Cet exemple produit la sortie suivante.  
  
 **Constructeur personnalisé de structure : échouée de la demande.**  
**Nouvelles valeurs SecuredTypeStructure 100 100**  
**Nouvelles valeurs SecuredTypeStructure 200 200**   
## <a name="see-also"></a>Voir aussi  
 [Demandes de liaison](/dotnet/framework/misc/link-demands)   
 [Données et modélisation](/dotnet/framework/data/index)