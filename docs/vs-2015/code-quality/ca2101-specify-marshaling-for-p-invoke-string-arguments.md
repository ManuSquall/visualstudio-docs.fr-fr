---
title: 'CA2101 : Spécifiez le marshaling pour les arguments de chaîne P-Invoke | Microsoft Docs'
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
ms.openlocfilehash: 2cc137c2b086de5507082be34726c3eb3a9294f2
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588039"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2101 : spécifiez le marshaling pour les arguments de chaîne P-Invoke](https://docs.microsoft.com/visualstudio/code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments).

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft.Globalization|
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



