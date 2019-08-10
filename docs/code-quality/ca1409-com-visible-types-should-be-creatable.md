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
ms.openlocfilehash: 4196cb91e1b866453de54347b8a67edd3dc2dc96
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921896"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par Com doivent pouvoir être créés

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Catégorie|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type référence qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre).

## <a name="rule-description"></a>Description de la règle
Un type sans constructeur public par défaut ne peut pas être créé par des clients COM. Toutefois, les clients COM peuvent toujours accéder au type si un autre moyen est disponible pour créer le type et le passer au client (par exemple, via la valeur de retour d’un appel de méthode).

La règle ignore les types dérivés de <xref:System.Delegate?displayProperty=fullName>.

Par défaut, les éléments suivants sont visibles par COM: assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si d’autres méthodes sont fournies pour créer et passer l’objet au client COM.

## <a name="related-rules"></a>Règles associées
[CA1017 Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interopération avec du code non managé](/dotnet/framework/interop/index)