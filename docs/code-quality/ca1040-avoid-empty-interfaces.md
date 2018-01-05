---
title: "CA1040 : Éviter les interfaces vides | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1b2dd61f70328ed4aa8ca08c518cebf8d6abbedb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040 : Éviter les interfaces vides
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 L’interface ne déclare aucun membre ni implémenter deux ou plusieurs autres interfaces.  
  
## <a name="rule-description"></a>Description de la règle  
 Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit pas de tous les membres. Par conséquent, il ne définit pas un contrat qui peut être implémenté.  
  
 Si votre conception comprend vide les interfaces que les types sont censés implémenter, vous utilisez probablement une interface en tant qu’un marqueur ou d’un moyen d’identifier un groupe de types. Si cette identification se produit au moment de l’exécution, la méthode correcte pour y parvenir est d’utiliser un attribut personnalisé. Utilisez la présence ou l’absence de l’attribut, ou les propriétés de l’attribut, pour identifier les types de cibles. Si l’identification doit se produire au moment de la compilation, il est acceptable d’utiliser une interface vide.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimer l’interface ou ajouter des membres. Si l’interface vide est utilisé pour étiqueter un ensemble de types, remplacez l’interface avec un attribut personnalisé.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque l’interface est utilisée pour identifier un ensemble de types au moment de la compilation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une interface vide.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]