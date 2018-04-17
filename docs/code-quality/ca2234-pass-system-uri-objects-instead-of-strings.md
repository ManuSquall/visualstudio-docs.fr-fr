---
title: 'CA2234 : Passez des objets System.Uri à la place des chaînes | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec09fe58e7a30f6b554afbf275ef0d8663cb0abb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234 : Passez des objets System.Uri à la place de chaînes
|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un appel est fait à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « Uri », « urn », « Urn », « url » ou « Url » ; et le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un <xref:System.Uri?displayProperty=fullName> paramètre.  
  
## <a name="rule-description"></a>Description de la règle  
 Un nom de paramètre est fractionné en jetons basés sur la convention de casse mixte, puis chaque jeton est vérifié pour voir si elle est égale à « uri », « Uri », « urn », « Urn », « url » ou « Url ». S’il existe une correspondance, le paramètre est censé pour représenter un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La <xref:System.Uri> classe fournit ces services de manière sûre et sécurisée. Lorsqu’il existe un choix entre deux surcharges qui diffèrent uniquement par la représentation sous forme d’un URI, l’utilisateur doit choisir la surcharge qui accepte un <xref:System.Uri> argument.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez la surcharge qui accepte le <xref:System.Uri> argument.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode, `ErrorProne`, ce qui enfreint la règle et une méthode, `SaferWay`, qui appelle correctement le <xref:System.Uri> de surcharge.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1057 : Les surcharges d’URI de chaîne appellent des surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)