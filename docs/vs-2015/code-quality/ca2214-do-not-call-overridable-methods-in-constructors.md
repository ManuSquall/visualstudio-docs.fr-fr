---
title: 'CA2214 : N’appelez pas de méthodes substituables dans les constructeurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a2e107429bb48b2bf17a625e25866a19c7781b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948096"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214 : N'appelez pas de méthodes substituables dans les constructeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le constructeur d’un type unsealed appelle une méthode virtuelle définie dans sa classe.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’une méthode virtuelle est appelée, le type réel qui exécute la méthode n’est pas sélectionné jusqu'à l’exécution. Lorsqu’un constructeur appelle une méthode virtuelle, il est possible que le constructeur pour l’instance qui appelle la méthode n’a pas été exécutée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, n’appelez pas les méthodes virtuelles d’un type à partir de dans les constructeurs du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Le constructeur doit être refondu pour éliminer l’appel à la méthode virtuelle.

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de violation de cette règle. L’application de test crée une instance de `DerivedType`, ce qui entraîne sa classe de base (`BadlyConstructedType`) constructeur à exécuter. `BadlyConstructedType`de manière incorrecte, le constructeur appelle la méthode virtuelle `DoSomething`. Comme le montre la sortie, `DerivedType.DoSomething()` s’exécute et ce avant `DerivedType`du constructeur s’exécute.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Cet exemple produit la sortie suivante.

 **Appel de constructeur de base. ** 
 **DoSomething dérivé est appelé - initialisé ? Ne**
**appel dérivée ctor.**
