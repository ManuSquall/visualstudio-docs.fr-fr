---
title: 'CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b2d5181e04a9a44516716ff280802eb5232f8da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.  
  
## <a name="rule-description"></a>Description de la règle  
 La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour ce faire, les types doivent appeler leur classe de base <xref:System.Object.Finalize%2A> méthode à partir de leurs propres <xref:System.Object.Finalize%2A> (méthode). Le compilateur c# ajoute automatiquement l’appel au finaliseur de classe de base.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez le type de base <xref:System.Object.Finalize%2A> méthode à partir de votre <xref:System.Object.Finalize%2A> (méthode).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insérer un appel au finaliseur du type de base dans le langage intermédiaire Microsoft (MSIL). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas de l’appel, et vous devez l’ajouter à votre code.  
  
## <a name="example"></a>Exemple  
 L’exemple Visual Basic suivant présente un type `TypeB` qui appelle correctement le <xref:System.Object.Finalize%2A> méthode dans sa classe de base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)