---
title: "CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd79751c67ca5540cb22eb692b2d11c0941005a6
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349047"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d’un paramètre de chaîne par un paramètre <xref:System.Uri?displayProperty=fullName>, et la surcharge qui prend le paramètre de chaîne n’appelle pas la surcharge qui prend le paramètre <xref:System.Uri>.

## <a name="rule-description"></a>Description de la règle
Étant donné que les surcharges diffèrent uniquement par la chaîne ou le paramètre <xref:System.Uri>, la chaîne est supposée représenter un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe <xref:System.Uri> fournit ces services de manière sûre et sécurisée. Pour tirer parti des avantages de la classe <xref:System.Uri>, la surcharge de chaîne doit appeler la surcharge <xref:System.Uri> à l’aide de l’argument String.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Réimplémentez la méthode qui utilise la représentation sous forme de chaîne de l’URI afin qu’elle crée une instance de la classe <xref:System.Uri> à l’aide de l’argument de chaîne, puis passe l’objet <xref:System.Uri> à la surcharge qui a le paramètre <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.

## <a name="example"></a>Exemple
L’exemple suivant montre une surcharge de chaîne correctement implémentée.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234.md)

[CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)