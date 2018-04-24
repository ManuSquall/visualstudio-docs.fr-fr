---
title: 'CA1409 : Les types visibles par COM doivent pouvoir être créés'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b2a7157c405eba52a2a7dc5de3b290a7ff26dc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par COM doivent pouvoir être créés
|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence marqué spécifiquement comme visible pour COM Component Object Model () contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre).

## <a name="rule-description"></a>Description de la règle
 Impossible de créer un type sans constructeur public par défaut par les clients COM. Toutefois, le type toujours accessibles par les clients COM si un autre moyen est disponible pour créer le type et le passer au client (par exemple, via la valeur de retour d’un appel de méthode).

 La règle ignore les types qui sont dérivés de <xref:System.Delegate?displayProperty=fullName>.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans des types publics et tous les membres de types valeur publics.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> à partir du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si d’autres moyens sont fournis pour créer et passez l’objet vers le client COM sans.

## <a name="related-rules"></a>Règles associées
 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 [Qualifier des Types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interopération avec du Code non managé](/dotnet/framework/interop/index)