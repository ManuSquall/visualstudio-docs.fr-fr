---
title: 'CA1409 : Types visibles par COM doivent pouvoir être créés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7bd52ad75c67f9c8faa80e84eb5ae09c22c25280
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678878"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par Com doivent pouvoir être créés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Qualification des Types .NET pour l’interopérabilité](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interopération avec du Code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
