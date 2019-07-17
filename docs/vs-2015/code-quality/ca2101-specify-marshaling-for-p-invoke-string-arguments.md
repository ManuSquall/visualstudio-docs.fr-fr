---
title: 'CA2101 : Spécifiez le marshaling pour les arguments de chaîne P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11916609f2efa9c0b6e208548ba51795bd276015
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154394"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Catégorie|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un code non managé membre autorise les appelants partiellement approuvés, a un paramètre de chaîne et ne marshale pas explicitement la chaîne.

## <a name="rule-description"></a>Description de la règle
 Lorsque vous convertissez à partir d’Unicode en ANSI, il est possible que pas tous les caractères Unicode peuvent être représentés dans une page de codes ANSI spécifique. *Le mappage ajusté* tente de résoudre ce problème en remplaçant un caractère pour le caractère qui ne peut pas être représenté. L’utilisation de cette fonctionnalité peut provoquer une faille de sécurité, car vous ne pouvez pas contrôler le caractère qui est choisi. Par exemple, code malveillant pourrait créer intentionnellement une chaîne Unicode qui contient des caractères qui ne figurent pas dans une page de codes particulier, qui sont converties en caractères spéciaux de système de fichier tel que '..' ou '/'. Notez également que les vérifications de sécurité pour les caractères spéciaux se produisent fréquemment avant la chaîne est convertie au format ANSI.

 Le mappage ajusté est la valeur par défaut pour la conversion non managée, WChar en Mo. Sauf si vous désactivez explicitement le mappage ajusté, votre code peut présenter une faille de sécurité exploitable en raison de ce problème.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marshaler explicitement des types de données de chaîne.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui enfreint cette règle et montre ensuite comment corriger la violation.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
