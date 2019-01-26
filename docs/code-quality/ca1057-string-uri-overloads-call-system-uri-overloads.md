---
title: "CA1057 : Les surcharges d'URI de chaîne appellent les surcharges de System.Uri"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f92340541de528b794f728bbbc1fe61a7d0853b9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012922"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057 : Les surcharges d'URI de chaîne appellent les surcharges de System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d’un paramètre de chaîne avec un <xref:System.Uri?displayProperty=fullName> paramètre et la surcharge qui accepte le paramètre de chaîne n’appelle pas la surcharge qui accepte le <xref:System.Uri> paramètre.

## <a name="rule-description"></a>Description de la règle
 Étant donné que les surcharges diffèrent uniquement par la chaîne ou <xref:System.Uri> paramètre, la chaîne est supposée pour représenter un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. Le <xref:System.Uri> classe fournit ces services de manière sûre et sécurisée. Pour profiter des avantages de la <xref:System.Uri> classe, la surcharge de chaîne doit appeler la <xref:System.Uri> surcharger à l’aide de l’argument de chaîne.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Implémenter de nouveau la méthode qui utilise la représentation sous forme de chaîne de l’URI pour qu’il crée une instance de la <xref:System.Uri> classe à l’aide de l’argument de chaîne, puis transmet le <xref:System.Uri> objet à la surcharge qui a le <xref:System.Uri> paramètre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre une surcharge de chaîne correctement implémenté.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056 : Propriétés de l’URI ne doivent pas être de chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054 : Paramètres de l’URI ne doivent pas être de chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055 : Les valeurs doivent être pas des chaînes de retour URI](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)