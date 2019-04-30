---
title: 'CA1409 : Les types visibles par Com doivent pouvoir être créés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05dbe964a16f838088fe8b053d59c1916daf38f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546399"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par Com doivent pouvoir être créés

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence marqué spécifiquement comme visible pour COM Component Object Model () contient un constructeur public paramétré, mais ne contient-elle pas de constructeur public par défaut (sans paramètre).

## <a name="rule-description"></a>Description de la règle
 Impossible de créer un type sans constructeur public par défaut par les clients COM. Toutefois, le type est toujours accessible par les clients COM si un autre moyen est disponible pour créer le type et passez-le au client (par exemple, via la valeur de retour d’un appel de méthode).

 La règle ignore les types qui sont dérivés de <xref:System.Delegate?displayProperty=fullName>.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans les types publics et tous les membres de types valeur publics.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> à partir du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si d’autres méthodes sont fournies pour créer et passez l’objet pour le client COM sans.

## <a name="related-rules"></a>Règles associées
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interopération avec du code non managé](/dotnet/framework/interop/index)