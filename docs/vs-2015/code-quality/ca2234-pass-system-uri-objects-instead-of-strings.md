---
title: 'CA2234 : passer des objets System. URI à la place de chaînes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545208"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234 : Passez des objets System.Uri à la place de chaînes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un appel est effectué à une méthode qui a un paramètre de chaîne dont le nom contient « URI », « Uri », « URN », « URN », « URL » ou « URL »; et le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un <xref:System.Uri?displayProperty=fullName> paramètre.

## <a name="rule-description"></a>Description de la règle
 Un nom de paramètre est divisé en jetons en fonction de la Convention de casse mixte, puis chaque jeton est vérifié pour voir s’il est égal à « URI », « Uri », « URN », « URN », « URL » ou « URL ». En cas de correspondance, le paramètre est supposé représenter un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La <xref:System.Uri> classe fournit ces services de manière sûre et sécurisée. Lorsqu’il existe un choix entre deux surcharges qui diffèrent uniquement en ce qui concerne la représentation d’un URI, l’utilisateur doit choisir la surcharge qui prend un <xref:System.Uri> argument.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez la surcharge qui prend l' <xref:System.Uri> argument.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `ErrorProne` , qui enfreint la règle et une méthode, `SaferWay` , qui appelle correctement la <xref:System.Uri> surcharge.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1057 : Les surcharges d'URI de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056 : Les propriétés URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054 : Les paramètres URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
