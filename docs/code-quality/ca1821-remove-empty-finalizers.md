---
title: "CA1821 : Supprimez les finaliseurs vides | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 98aebdcc889cdd3bd2bbe124b00a572e066b0e4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821 : Supprimer les finaliseurs vides
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Category|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type implémente un finaliseur qui est vide, appelle uniquement le finaliseur du type de base ou appelle uniquement émises sous certaines conditions de méthodes.  
  
## <a name="rule-description"></a>Description de la règle  
 Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Le garbage collector exécutera le finaliseur avant de collecter l’objet. Cela signifie que les deux collections sont requises pour collecter l’objet. Un finaliseur vide entraîne cette charge mémoire supplémentaire sans aucun avantage.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimez le finaliseur vide. Si un finaliseur est requis pour le débogage, insérez-le entièrement dans `#if DEBUG / #endif` directives.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez pas un message de cette règle. Échec de supprimer la finalisation diminue les performances et n’apporte aucun avantage.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un finaliseur vide qui doit être supprimé, un finaliseur qui doit être placé dans `#if DEBUG / #endif` directives et un finaliseur qui utilise le `#if DEBUG / #endif` directives correctement.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]