---
title: "CA1065 : Ne pas lever d'exceptions dans des emplacements inattendus"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b338b37d62f3612dd5eb6d575b6ef0d57202c1f8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900661"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065 : Ne pas lever d'exceptions dans des emplacements inattendus

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode dont l'objet n'est pas de lever des exceptions lève une exception.

## <a name="rule-description"></a>Description de la règle

Les méthodes qui ne sont pas prévues de lever des exceptions peuvent être classés comme suit :

- Méthodes Get de propriété

- Méthodes d’accesseur d’événement

- Méthodes Equals

- Méthodes GetHashCode

- Méthodes ToString

- Constructeurs statiques

- Finaliseurs

- Méthodes de suppression

- Opérateurs d'égalité

- Opérateurs de Cast implicites

Les sections suivantes traitent de ces types de méthode.

### <a name="property-get-methods"></a>Méthodes Get de propriété

Les propriétés sont essentiellement des champs intelligents. Par conséquent, elles doivent se comporter comme un champ autant que possible. Les champs ne lèvent pas d’exceptions et les propriétés doivent. Si vous avez une propriété qui lève une exception, envisagez d’en faire une méthode.

Les exceptions suivantes peuvent être levées à partir d’une méthode get de propriété :

- <xref:System.InvalidOperationException?displayProperty=fullName> et tous les dérivés (y compris <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> et tous les dérivés

- <xref:System.ArgumentException?displayProperty=fullName> (uniquement à partir d’indexée get)

- <xref:System.Collections.Generic.KeyNotFoundException> (uniquement à partir d’indexée get)

### <a name="event-accessor-methods"></a>Méthodes d’accesseur d’événement

Accesseurs d’événement doivent être des opérations simples qui ne lèvent pas d’exceptions. Un événement ne doit pas lever une exception lorsque vous essayez d’ajouter ou supprimer un gestionnaire d’événements.

Les exceptions suivantes peuvent être levées à partir d’un accesseur d’événement :

- <xref:System.InvalidOperationException?displayProperty=fullName> et tous les dérivés (y compris <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> et tous les dérivés

- <xref:System.ArgumentException> et dérivés

### <a name="equals-methods"></a>Méthodes Equals

Les éléments suivants **est égal à** méthodes ne doivent pas lever les exceptions :

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Un **est égal à** méthode doit retourner `true` ou `false` au lieu de lever une exception. Par exemple, si vous égal à est passé de deux types incompatibles elle doit simplement retourner `false` au lieu de lever une <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Méthodes GetHashCode

Les éléments suivants **GetHashCode** méthodes généralement lever d’exceptions :

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** doit toujours retourner une valeur. Sinon, vous risquez de perdre des éléments dans la table de hachage.

Les versions de **GetHashCode** qui prennent un argument peut lever une <xref:System.ArgumentException>. Toutefois, **Object.GetHashCode** ne doit jamais lever une exception.

### <a name="tostring-methods"></a>Méthodes ToString

Le débogueur utilise <xref:System.Object.ToString%2A?displayProperty=fullName> pour afficher des informations sur les objets sous forme de chaîne. Par conséquent, **ToString** ne doit pas modifier l’état d’un objet, et il ne doit pas lever d’exceptions.

### <a name="static-constructors"></a>Constructeurs statiques

Lever des exceptions à partir d’un constructeur statique provoque le type inutilisable dans le domaine d’application actuel. Vous devez disposer d’une bonne raison (par exemple, un problème de sécurité) pour lever une exception à partir d’un constructeur statique.

### <a name="finalizers"></a>Finaliseurs

Lever une exception à partir d’un finaliseur provoque l’échec rapide, le CLR détruisant le processus. Par conséquent, lever des exceptions dans un finaliseur doit toujours être évitée.

### <a name="dispose-methods"></a>Méthodes de suppression

A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> méthode ne doit pas lever une exception. Méthode Dispose est souvent appelée dans le cadre de la logique de nettoyage dans un `finally` clause. Par conséquent, la lever explicitement une exception de la méthode Dispose oblige l’utilisateur à ajouter la gestion des exceptions dans le `finally` clause.

Le **dispose (false)** chemin d’accès du code ne doit jamais lever des exceptions, car Dispose est presque toujours appelé à partir d’un finaliseur.

### <a name="equality-operators--"></a>Opérateurs d’égalité (==, ! =)

Comme les méthodes Equals, les opérateurs d’égalité doivent retourner `true` ou `false`, pas lever d’exceptions.

### <a name="implicit-cast-operators"></a>Opérateurs de Cast implicites

Étant donné que l’utilisateur est souvent pas conscients qu’un opérateur de cast implicite a été appelé, une exception levée par l’opérateur de conversion implicite est inattendue. Par conséquent, aucune exception ne doit être levée à partir des opérateurs cast implicites.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour les accesseurs Get de propriété, soit modifiez la logique afin qu’il n’a plus à lever une exception ou modifiez la propriété dans une méthode.

Pour tous les autres types de méthode répertoriées précédemment, modifiez la logique afin qu’il doit n’est plus lever une exception.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Si la violation a été provoquée par une déclaration d’exception au lieu d’une exception levée, il est possible de supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées

- [CA2219 : Ne levez pas d’exceptions dans les clauses d’exception](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la conception](../code-quality/design-warnings.md)