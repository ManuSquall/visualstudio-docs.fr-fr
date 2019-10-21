---
title: 'CA2112 : les types sécurisés ne doivent pas exposer de champs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c91a7c9833d3d9d5ae283c28ae4d437bd07734
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658746"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112 : Les types sécurisés ne doivent pas exposer de champs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient des champs publics et est sécurisé par une [demande de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Description de la règle
 Si un code a accès à une instance d’un type sécurisé par une demande de liaison, ce code n’a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez les champs non publics et ajoutez des propriétés ou des méthodes publiques qui retournent les données de champ. Les vérifications de sécurité LinkDemand sur les types protègent l’accès aux propriétés et méthodes du type. Toutefois, la sécurité d’accès du code ne s’applique pas aux champs.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour les problèmes de sécurité et pour une bonne conception, vous devez corriger les violations en rendant les champs publics non publics. Vous pouvez supprimer un avertissement de cette règle si le champ ne contient pas d’informations qui doivent rester sécurisées et que vous ne vous fiez pas au contenu du champ.

## <a name="example"></a>Exemple
 L’exemple suivant est composé d’un type de bibliothèque (`SecuredTypeWithFields`) avec des champs non sécurisés, un type (`Distributor`) qui peut créer des instances du type de bibliothèque et qui passe des instances à des types ne sont pas autorisés à les créer, et le code d’application qui peut lire un champs de l’instance, même s’il n’a pas l’autorisation qui sécurise le type.

 Le code de bibliothèque suivant enfreint la règle.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Exemple
 L’application ne peut pas créer d’instance en raison de la demande de liaison qui protège le type sécurisé. La classe suivante permet à l’application d’obtenir une instance du type sécurisé.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre comment, sans l’autorisation d’accéder aux méthodes d’un type sécurisé, le code peut accéder à ses champs.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Cet exemple produit la sortie suivante.

 **Création d’une instance de SecuredTypeWithFields.** 
**champs de type sécurisé : 22, 33** 
**modification du champ du type sécurisé...** 
**champs d’objet mis en cache : 99, 33**
## <a name="related-rules"></a>Règles associées
 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi
 [Liaison des demandes](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [de données et de modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
