---
title: 'Ca1057 : les surcharges d’URI de chaîne appellent les surcharges de System. Uri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603078"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d’un paramètre de chaîne par un paramètre <xref:System.Uri?displayProperty=fullName>, et la surcharge qui prend le paramètre de chaîne n’appelle pas la surcharge qui prend le paramètre <xref:System.Uri>.

## <a name="rule-description"></a>Description de la règle
 Étant donné que les surcharges diffèrent uniquement par le paramètre String/<xref:System.Uri>, la chaîne est supposée représenter un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe <xref:System.Uri> fournit ces services de manière sûre et sécurisée. Pour tirer parti des avantages de la classe <xref:System.Uri>, la surcharge de chaîne doit appeler la surcharge <xref:System.Uri> à l’aide de l’argument String.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Implémentez à nouveau la méthode qui utilise la représentation sous forme de chaîne de l’URI afin qu’elle crée une instance de la classe <xref:System.Uri> à l’aide de l’argument String, puis passe l’objet <xref:System.Uri> à la surcharge qui a le paramètre <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre une surcharge de chaîne correctement implémentée.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
