---
title: 'CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 443fec0c9f20148d775a734137941cd7c78da889
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444391"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode passe un littéral de chaîne en tant que paramètre à un constructeur .NET ou une méthode et cette chaîne doit être localisable.

Cet avertissement est déclenché quand une chaîne littérale est passée en tant que valeur à un paramètre ou une propriété et qu’un ou plusieurs des cas suivants sont vrais :

- L’attribut <xref:System.ComponentModel.LocalizableAttribute> du paramètre ou de la propriété a la valeur true.

- Le nom du paramètre ou de la propriété contient « Text », « message » ou « Caption ».

- Le nom du paramètre de chaîne passé à une méthode Console. Write ou console. WriteLine est « value » ou « format ».

## <a name="rule-description"></a>Description de la règle

Les littéraux de chaîne incorporés dans le code source sont difficiles à localiser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée par le biais d’une instance de la classe <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si la bibliothèque de code n’est pas localisée ou si la chaîne n’est pas exposée à l’utilisateur final ou à un développeur à l’aide de la bibliothèque de code.

Les utilisateurs peuvent éliminer le bruit sur les méthodes qui ne doivent pas être passées aux chaînes localisées en renommant le paramètre ou la propriété, ou en marquant ces éléments comme conditionnels.

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode qui lève une exception lorsque l’un de ses deux arguments est hors limites. Pour le premier argument, une chaîne littérale, qui viole cette règle, est passée au constructeur d’exception. Pour le deuxième argument, une chaîne Récupérée à l’aide d’un <xref:System.Resources.ResourceManager> est correctement passée au constructeur.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Ressources dans les applications de bureau](/dotnet/framework/resources/index)
