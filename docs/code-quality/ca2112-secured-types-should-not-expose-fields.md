---
title: 'CA2112 : Les types sécurisés ne doivent pas exposer de champs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9784ec48193ae580d7ed41cb745f0befb1f1fde9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915246"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112 : Les types sécurisés ne doivent pas exposer de champs
|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient des champs publics et est sécurisé par un [les demandes de liaison](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Description de la règle
 Si un code a accès à une instance d’un type sécurisé par une demande de liaison, ce code n’a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez les champs non publics et ajoutez les propriétés publiques ou des méthodes qui retournent les données du champ. Vérifications de sécurité LinkDemand sur les types de protégeant l’accès aux propriétés et les méthodes du type. Toutefois, la sécurité d’accès du code ne s’applique pas aux champs.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Les problèmes de sécurité et de design, vous devez corriger les violations en rendant les champs publics non publics. Vous pouvez supprimer un avertissement de cette règle si le champ ne conserve pas les informations qui doivent rester sécurisées, et vous ne comptez pas sur le contenu du champ.

## <a name="example"></a>Exemple
 L’exemple suivant est composé d’un type de bibliothèque (`SecuredTypeWithFields`) avec des champs non sécurisés, un type (`Distributor`) qui peuvent créer des instances du type de bibliothèque et les instances de passes erronée aux types n’ont pas d’autorisation de créer les code d’application peut lire les champs d’une instance même s’il n’a pas l’autorisation qui sécurise le type.

 Le code de bibliothèque suivant enfreint la règle.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example"></a>Exemple
 L’application ne peut pas créer une instance en raison de la demande de liaison qui protège le type sécurisé. La classe suivante permet à l’application obtenir une instance du type sécurisé.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example"></a>Exemple
 L’application suivante illustre comment procéder, sans l’autorisation d’accéder aux méthodes d’un type sécurisé, code peut accéder à ses champs.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

 Cet exemple produit la sortie suivante.

 **Création d’une instance de SecuredTypeWithFields. ** 
 **Des champs de type sécurisé : 22, 33**
**la modification du champ de type sécurisé... ** 
 **Champs mis en cache l’objet : 99, 33**
## <a name="related-rules"></a>Règles associées
 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi
 [Demandes de liaison](/dotnet/framework/misc/link-demands) [données et modélisation](/dotnet/framework/data/index)