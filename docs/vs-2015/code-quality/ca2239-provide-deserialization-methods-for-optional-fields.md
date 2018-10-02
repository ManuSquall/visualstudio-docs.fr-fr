---
title: 'CA2239 : Spécifiez méthodes de désérialisation pour les champs facultatifs | Microsoft Docs'
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
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 235880285ce80d74fec67e5bcd497f046f3aa842
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590065"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2239 : fournir des méthodes de désérialisation pour les champs facultatifs](https://docs.microsoft.com/visualstudio/code-quality/ca2239-provide-deserialization-methods-for-optional-fields).

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type a un champ qui est marqué avec le <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> attribut et le type ne fournit pas de méthodes de gestion des événements de désérialisation.

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribut n’a aucun effet sur la sérialisation ; un champ marqué avec l’attribut est sérialisé. Toutefois, le champ est ignoré lors de la sérialisation de déduplication et conserve la valeur par défaut associée à son type. Gestionnaires d’événements de désérialisation doivent être déclarés pour définir le champ au cours du processus de désérialisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez des méthodes pour le type de gestion des événements de désérialisation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le champ doit être ignoré pendant le processus de désérialisation.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type avec un champ facultatif et un événement de désérialisation des méthodes de gestion.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)



