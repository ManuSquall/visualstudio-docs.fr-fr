---
title: 'CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b621306bab673172c1c437ca0a959e4bc36f6da
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés
|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode passe une littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bibliothèque de classes et cette chaîne doit être localisable.

 Cet avertissement est déclenché lorsqu’une chaîne littérale est passée comme valeur pour un paramètre ou une propriété et un ou plusieurs des cas suivants sont vrai :

-   Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.

-   Le nom de paramètre ou la propriété contient « Texte », « Message » ou « Caption ».

-   Le nom du paramètre de chaîne qui est passé à une méthode Console.Write ou Console.WriteLine est « value » ou « format ».

## <a name="rule-description"></a>Description de la règle
 Littéraux de chaîne qui sont incorporés dans le code source sont difficiles à localiser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée via une instance de la <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la bibliothèque de code n’est pas localisée, ou si la chaîne n’est pas exposée à l’utilisateur final ou un développeur à l’aide de la bibliothèque de code.

 Les utilisateurs peuvent éliminer le bruit sur les méthodes qui ne doivent pas être passées des chaînes localisées, soit en renommant le paramètre ou la propriété nommée, ou en marquant ces éléments comme conditionnels.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui lève une exception lorsqu’un de ses deux arguments sont hors limites. Pour le premier argument, le constructeur de l’exception est passé à une chaîne littérale, ce qui enfreint cette règle. Pour le second argument, le constructeur reçoit correctement une chaîne récupérée via un <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Voir aussi
 [Ressources dans des applications de bureau](/dotnet/framework/resources/index)