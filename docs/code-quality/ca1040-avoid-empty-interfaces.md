---
title: 'CA1040 : Éviter les interfaces vides'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffdea7cadbf7bfc2803573a78fdd9bbc74b1d287
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936864"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040 : Éviter les interfaces vides

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 L’interface ne déclare aucun membre ni implémenter deux ou plusieurs autres interfaces.

## <a name="rule-description"></a>Description de la règle
 Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit pas de membres. Par conséquent, il ne définit pas un contrat qui peut être implémenté.

 Si votre conception inclut vide interfaces que les types sont censés implémenter, vous utilisez probablement une interface en tant qu’un marqueur ou un moyen d’identifier un groupe de types. Si cette identification se produit au moment de l’exécution, la méthode correcte pour ce faire consiste à utiliser un attribut personnalisé. Utilisez la présence ou l’absence de l’attribut, ou les propriétés de l’attribut, pour identifier les types de cibles. Si l’identification doit avoir lieu au moment de la compilation, il est acceptable d’utiliser une interface vide.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimer l’interface ou ajouter des membres. Si l’interface vide est utilisé pour étiqueter un ensemble de types, remplacez l’interface avec un attribut personnalisé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque l’interface est utilisée pour identifier un ensemble de types au moment de la compilation.

## <a name="example"></a>Exemple
 L’exemple suivant montre une interface vide.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]