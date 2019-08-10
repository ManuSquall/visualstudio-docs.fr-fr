---
title: 'CA1301 : Éviter les accélérateurs en double'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16cd44f00db13027d737b6a6b496877075ac6fa9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922263"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301 : Éviter les accélérateurs en double

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type étend <xref:System.Windows.Forms.Control?displayProperty=fullName> et contient deux contrôles de niveau supérieur ou plus qui ont des clés d’accès identiques stockées dans un fichier de ressources.

## <a name="rule-description"></a>Description de la règle

Une touche d’accès rapide, également appelée accélérateur, permet l’accès au clavier à un contrôle à l’aide de la touche **ALT** . Lorsque plusieurs contrôles possèdent la même clé d’accès, le comportement de la clé d’accès n’est pas bien défini. L’utilisateur peut ne pas être en mesure d’accéder au contrôle souhaité à l’aide de la clé d’accès et un contrôle autre que celui prévu peut être activé.

L’implémentation actuelle de cette règle ignore les éléments de menu. Toutefois, les éléments de menu du même sous-menu ne doivent pas avoir des clés d’accès identiques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, définissez des clés d’accès uniques pour tous les contrôles.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
L’exemple suivant montre une forme minimale qui contient deux contrôles qui ont des clés d’accès identiques. Les clés sont stockées dans un fichier de ressources, qui n’est pas affiché. Toutefois, leurs valeurs apparaissent dans les lignes en `checkBox.Text` sortie commentées. Le comportement des accélérateurs dupliqués peut être examiné en échangeant `checkBox.Text` les lignes avec les équivalents commentés. Toutefois, dans ce cas, l’exemple ne génère pas d’avertissement à partir de la règle.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressources dans des applications de bureau](/dotnet/framework/resources/index)