---
title: 'CA1011 : Si possible, transmettez les types de base en tant que paramètres'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236409"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011 : Si possible, transmettez les types de base en tant que paramètres

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une déclaration de méthode comprend un paramètre formel qui est un type dérivé, et la méthode appelle uniquement les membres du type de base du paramètre.

## <a name="rule-description"></a>Description de la règle

Lorsqu'un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu'argument correspondant à la méthode. Lorsque l’argument est utilisé dans le corps de la méthode, la méthode spécifique qui est exécutée dépend du type de l’argument. Si les fonctionnalités supplémentaires fournies par le type dérivé ne sont pas requises, l’utilisation du type de base permet une utilisation plus étendue de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez le type du paramètre par son type de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle

- Si la méthode requiert la fonctionnalité spécifique fournie par le type dérivé

     \- ou -

- pour garantir que seul le type dérivé, ou un type plus dérivé, est passé à la méthode.

Dans ces cas, le code sera plus robuste en raison de la vérification de type fort fournie par le compilateur et le Runtime.

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode, `ManipulateFileStream`, qui peut être utilisée uniquement avec un <xref:System.IO.FileStream> objet, qui enfreint cette règle. Une deuxième méthode, `ManipulateAnyStream`, répond à la règle en remplaçant le <xref:System.IO.FileStream> paramètre à l’aide <xref:System.IO.Stream>d’un.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Règles associées

[CA1059 Les membres ne doivent pas exposer certains types concrets](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)