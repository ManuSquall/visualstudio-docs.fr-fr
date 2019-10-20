---
title: 'CA1054 : les paramètres d’URI ne doivent pas être des chaînes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2062c7518545300074a0377b7a9cca7ddf1a8aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603381"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054 : Les paramètres Uri ne doivent pas être des chaînes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type déclare une méthode avec un paramètre de chaîne dont le nom contient « URI », « Uri », « URN », « URN », « URL » ou « URL » et le type ne déclare pas une surcharge correspondante qui accepte un paramètre <xref:System.Uri?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Cette règle fractionne le nom de paramètre en jetons en fonction de la Convention de casse mixte et vérifie si chaque jeton est égal à « URI », « Uri », « URN », « URN », « URL » ou « URL ». En cas de correspondance, la règle suppose que le paramètre représente un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. Si une méthode prend une représentation sous forme de chaîne d’un URI, une surcharge correspondante doit être fournie pour prendre une instance de la classe <xref:System.Uri>, qui fournit ces services de manière sécurisée et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le paramètre par un type <xref:System.Uri> ; Il s’agit d’une modification avec rupture. Vous pouvez également fournir une surcharge de la méthode qui prend un paramètre <xref:System.Uri> ; Il s’agit d’une modification sans rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `ErrorProne`, qui enfreint cette règle, et un type, `SaferWay`, qui satisfait la règle.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057 : Les surcharges d’URI de chaîne appellent des surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
