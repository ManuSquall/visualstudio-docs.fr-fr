---
title: 'CA2112 : Types sécurisés ne doivent pas exposer de champs | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a52b952437ce136773d796972c6619a9733749
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687327"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112 : Les types sécurisés ne doivent pas exposer de champs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient des champs publics et est sécurisé par un [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Description de la règle
 Si un code a accès à une instance d’un type sécurisé par une demande de liaison, ce code n’a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez les champs non publics et ajoutez les propriétés publiques ou des méthodes qui retournent les données de champ. Vérifications de sécurité LinkDemand sur les types de protégeant l’accès aux propriétés et les méthodes du type. Toutefois, la sécurité d’accès du code ne s’applique pas aux champs.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Les problèmes de sécurité et de design, vous devez corriger les violations en rendant les champs publics non publics. Vous pouvez supprimer un avertissement de cette règle si le champ ne contient pas les informations qui doivent rester sécurisées, et vous ne comptez pas sur le contenu du champ.

## <a name="example"></a>Exemple
 L’exemple suivant est composé d’un type de bibliothèque (`SecuredTypeWithFields`) avec des champs non sécurisés, un type (`Distributor`) peut créer des instances du type de bibliothèque et des instances de passes erronée aux types n’ont pas d’autorisation pour les créer, et code d’application peut lire les champs d’une instance même s’il n’a pas l’autorisation qui sécurise le type.

 Le code de bibliothèque suivant enfreint la règle.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Exemple
 L’application ne peut pas créer une instance en raison de la demande de liaison qui protège le type sécurisé. La classe suivante permet à l’application obtenir une instance du type sécurisé.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre comment procéder, sans être autorisé à accéder aux méthodes d’un type sécurisé, code peut accéder à ses champs.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Cet exemple produit la sortie suivante.

 **Création d’une instance de SecuredTypeWithFields. ** 
 **Les champs de type sécurisé : 22, 33**
**sécurisé du champ du type de modification... ** 
 **Champs d’objet mis en cache : 99, 33**
## <a name="related-rules"></a>Règles associées
 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi
 [Demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
