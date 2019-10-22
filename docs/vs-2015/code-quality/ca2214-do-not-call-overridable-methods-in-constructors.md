---
title: 'CA2214 : ne pas appeler les méthodes substituables dans les constructeurs | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662907"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214 : N'appelez pas de méthodes substituables dans les constructeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le constructeur d’un type non scellé appelle une méthode virtuelle définie dans sa classe.

## <a name="rule-description"></a>Description de la règle
 Quand une méthode virtuelle est appelée, le type réel qui exécute la méthode n’est pas sélectionné jusqu’au moment de l’exécution. Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, n’appelez pas les méthodes virtuelles d’un type à partir des constructeurs du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Le constructeur doit être repensé pour éliminer l’appel à la méthode virtuelle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre l’effet de la violation de cette règle. L’application de test crée une instance de `DerivedType`, ce qui entraîne l’exécution de son constructeur de classe de base (`BadlyConstructedType`). le constructeur de `BadlyConstructedType` appelle incorrectement la méthode virtuelle `DoSomething`. Comme le montre la sortie, `DerivedType.DoSomething()` s’exécute, et avant l’exécution du constructeur de `DerivedType`.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Cet exemple produit la sortie suivante.

 **Appel du constructeur de base.** 
**un fait dérivé est appelé-Initialized ? Aucune** 
**appelant le constructeur dérivé.**
