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
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539488"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054 : Les paramètres URI ne doivent pas être des chaînes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type déclare une méthode avec un paramètre de chaîne dont le nom contient « URI », « Uri », « URN », « URN », « URL » ou « URL » et le type ne déclare pas une surcharge correspondante qui accepte un <xref:System.Uri?displayProperty=fullName> paramètre.

## <a name="rule-description"></a>Description de la règle
 Cette règle fractionne le nom de paramètre en jetons en fonction de la Convention de casse mixte et vérifie si chaque jeton est égal à « URI », « Uri », « URN », « URN », « URL » ou « URL ». En cas de correspondance, la règle suppose que le paramètre représente un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. Si une méthode prend une représentation sous forme de chaîne d’un URI, une surcharge correspondante doit être fournie, qui prend une instance de la <xref:System.Uri> classe, qui fournit ces services de manière sécurisée et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le paramètre par un <xref:System.Uri> type ; il s’agit d’une modification avec rupture. Vous pouvez également fournir une surcharge de la méthode qui prend un <xref:System.Uri> paramètre ; il s’agit d’une modification sans rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `ErrorProne` , qui enfreint cette règle et un type, `SaferWay` , qui satisfait la règle.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1056 : Les propriétés URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234 : Passez des objets System.Uri à la place de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057 : Les surcharges d'URI de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
