---
title: 'CA2101 : spécifiez le marshaling pour les arguments de chaîne P-Invoke | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ae65e922d1b4946300155bbf148abac574a2ec2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544376"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un membre d’appel de code non managé autorise les appelants de confiance partielle, a un paramètre de chaîne et ne marshale pas explicitement la chaîne.

## <a name="rule-description"></a>Description de la règle
 Lors de la conversion d’Unicode en ANSI, il est possible que tous les caractères Unicode ne puissent pas être représentés dans une page de codes ANSI spécifique. Le *mappage le mieux adapté* tente de résoudre ce problème en substituant un caractère au caractère qui ne peut pas être représenté. L’utilisation de cette fonctionnalité peut provoquer une faille de sécurité potentielle, car vous ne pouvez pas contrôler le caractère choisi. Par exemple, du code malveillant pourrait créer intentionnellement une chaîne Unicode qui contient des caractères qui ne se trouvent pas dans une page de codes particulière, qui sont convertis en caractères spéciaux du système de fichiers tels que'.. ' ou « / ». Notez également que les vérifications de sécurité pour les caractères spéciaux se produisent fréquemment avant la conversion de la chaîne en ANSI.

 Le mappage le mieux adapté est la valeur par défaut pour la conversion non managée, WChar en Mo. À moins que vous désactiviez explicitement le mappage le mieux adapté, votre code peut contenir une faille de sécurité exploitable en raison de ce problème.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marshalez explicitement les types de données de chaîne.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui enfreint cette règle, puis montre comment corriger la violation.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
