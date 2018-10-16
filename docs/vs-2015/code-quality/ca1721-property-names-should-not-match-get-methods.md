---
title: 'CA1721 : Les noms de propriétés ne doivent pas correspondre aux méthodes get | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f756c2adaf403bd9945c405b0134d025be36ae5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217027"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre public ou protégé commence par 'Get' et sinon correspond au nom d’une propriété publique ou protégée. Par exemple, un type qui contient une méthode nommée 'GetColor' et une propriété nommée 'Color' enfreint cette règle.

## <a name="rule-description"></a>Description de la règle
 Méthodes Get doivent avoir des noms distinguant clairement leur fonction.

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifiez le nom afin qu’il ne correspond pas au nom d’une méthode qui est précédé de 'Get'.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

> [!NOTE]
>  Cet avertissement peut être exclu si la méthode Get est causée par l’implémentation de IExtenderProvider (interface).

## <a name="example"></a>Exemple
 L’exemple suivant contient une méthode ou une propriété qui violent cette règle.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)



