---
title: 'CA1303 : ne pas passer de littéraux en tant que paramètres localisés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539111"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303 : Ne pas passer de littéraux en paramètres localisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode passe un littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bibliothèque de classes et cette chaîne doit être localisable.

 Cet avertissement est déclenché quand une chaîne littérale est passée en tant que valeur à un paramètre ou une propriété et qu’un ou plusieurs des cas suivants sont vrais :

- L' <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de la propriété a la valeur true.

- Le nom du paramètre ou de la propriété contient « Text », « message » ou « Caption ».

- Le nom du paramètre de chaîne passé à une méthode Console. Write ou console. WriteLine est « value » ou « format ».

## <a name="rule-description"></a>Description de la règle
 Les littéraux de chaîne incorporés dans le code source sont difficiles à localiser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée par le biais d’une instance de la <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si la bibliothèque de code n’est pas localisée, ou si la chaîne n’est pas exposée à l’utilisateur final ou à un développeur à l’aide de la bibliothèque de code.

 Les utilisateurs peuvent éliminer le bruit par rapport aux méthodes qui ne doivent pas être passées aux chaînes localisées en renommant le paramètre ou la propriété nommée, ou en marquant ces éléments comme conditionnels.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui lève une exception lorsque l’un de ses deux arguments est hors limites. Pour le premier argument, une chaîne littérale, qui viole cette règle, est passée au constructeur d’exception. Pour le deuxième argument, une chaîne Récupérée à l’aide d’un est correctement passée au constructeur <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Ressources dans les applications de bureau](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
