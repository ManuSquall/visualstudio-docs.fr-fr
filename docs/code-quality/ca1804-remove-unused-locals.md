---
title: "CA1804 : Supprimez les variables locales inutilisées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d75bc10407e9eae1c23ad06fdc2bd9515bdd505f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1804-remove-unused-locals"></a>CA1804 : Supprimez les variables locales inutilisées
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Category|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode déclare une variable locale, mais n’utilise pas la variable sauf éventuellement en tant que le destinataire d’une instruction d’assignation. Pour l’analyse par cette règle, l’assembly testé doit être construit avec les informations de débogage et le fichier de base de données (.pdb) de programme associé doit être disponible.  
  
## <a name="rule-description"></a>Description de la règle  
 Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez ou utilisez la variable locale. Notez que le compilateur c# qui est inclus avec [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] supprime les variables locales inutilisées lorsque le `optimize` est activée.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle si la variable a été émise par un compilateur. Il est également recommandé de supprimer un avertissement de cette règle, ou pour désactiver la règle, si performances et maintenance du code ne sont pas des préoccupations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre plusieurs variables locales inutilisées.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)