---
title: 'CA1303 : Ne pas transmettre des littéraux localisées comme paramètres | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fcb7f9f4cd57f287ec7a2bab900a78d21f23846
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588118"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1303 : ne pas transmettre des littéraux paramètres localisés comme](https://docs.microsoft.com/visualstudio/code-quality/ca1303-do-not-pass-literals-as-localized-parameters).

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode passe une littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] de classes de bibliothèque et de cette chaîne doit être localisable.

 Cet avertissement est déclenché lorsqu’une chaîne littérale est passée en tant que valeur à un paramètre ou une propriété et un ou plusieurs des cas suivants sont vrai :

-   Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.

-   Le nom de paramètre ou une propriété contient « Text », « Message » ou « Caption ».

-   Le nom du paramètre de chaîne qui est passé à une méthode Console.Write ou Console.WriteLine est « value » ou « format ».

## <a name="rule-description"></a>Description de la règle
 Les littéraux de chaîne incorporés dans le code source sont difficiles à localiser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée via une instance de la <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la bibliothèque de code n’est pas localisée, ou si la chaîne n’est pas exposée à l’utilisateur final ou un développeur à l’aide de la bibliothèque de code.

 Les utilisateurs peuvent éliminer le bruit sur les méthodes qui ne doivent pas être passées des chaînes localisées, soit en renommant le paramètre ou une propriété nommée, ou en marquant ces éléments comme conditionnels.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui lève une exception lorsqu’une de ses deux arguments est hors limites. Pour le premier argument, le constructeur d’exception est passé à une chaîne littérale qui enfreint cette règle. Pour le deuxième argument, le constructeur reçoit correctement une chaîne récupérée via un <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Ressources dans des applications de bureau](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



