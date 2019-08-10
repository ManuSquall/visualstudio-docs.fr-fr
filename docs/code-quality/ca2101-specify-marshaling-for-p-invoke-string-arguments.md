---
title: 'CA2101 : Spécifiez le marshaling pour les arguments de chaîne P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1eb4c2535060f9a110d149e88ac2532e6ad1412
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921098"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un membre d’appel de code non managé autorise les appelants de confiance partielle, a un paramètre de chaîne et ne marshale pas explicitement la chaîne.

## <a name="rule-description"></a>Description de la règle
Lors de la conversion d’Unicode en ANSI, il est possible que tous les caractères Unicode ne puissent pas être représentés dans une page de codes ANSI spécifique. Le *mappage le mieux adapté* tente de résoudre ce problème en substituant un caractère au caractère qui ne peut pas être représenté. L’utilisation de cette fonctionnalité peut provoquer une faille de sécurité potentielle, car vous ne pouvez pas contrôler le caractère choisi. Par exemple, du code malveillant pourrait créer intentionnellement une chaîne Unicode qui contient des caractères qui ne se trouvent pas dans une page de codes particulière, qui sont convertis en caractères spéciaux du système de fichiers tels que'.. ' ou «/». Notez également que les vérifications de sécurité pour les caractères spéciaux se produisent fréquemment avant la conversion de la chaîne en ANSI.

Le mappage le mieux adapté est la valeur par défaut pour la conversion non managée, WChar en Mo. À moins que vous désactiviez explicitement le mappage le mieux adapté, votre code peut contenir une faille de sécurité exploitable en raison de ce problème.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, marshalez explicitement les types de données de chaîne.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre une méthode qui enfreint cette règle, puis montre comment corriger la violation.

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]