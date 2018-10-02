---
title: 'CA1052 : Les types de conteneurs statiques doivent être sealed | Microsoft Docs'
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
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a912276f2f4008d1bea95027a5f2a1b67ff83e55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589727"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1052 : les types de conteneurs statiques doivent être sealed](https://docs.microsoft.com/visualstudio/code-quality/ca1052-static-holder-types-should-be-sealed).

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modificateur.

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être héritée, de le, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` modificateur d’empêcher son utilisation comme un type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez le type comme `sealed`. Si vous ciblez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 ou une version antérieure, une meilleure approche consiste à marquer le type comme `static`. De cette manière, vous évitez d’avoir à déclarer un constructeur privé pour empêcher la création de la classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité. L’absence de la `sealed` modificateur suggère que le type est utile comme type de base.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre un type qui viole la règle.

### <a name="code"></a>Code
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur Static

### <a name="description"></a>Description
 L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec le `static` modificateur.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)



