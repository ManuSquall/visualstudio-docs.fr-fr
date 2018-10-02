---
title: 'DA0006 : Remplacez Equals() pour les types valeur | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4e7535775946c99d6b176f36ca10288a8bc9da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503608"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006 : Remplacer Equals() pour les types valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DA0006 : remplacer les méthodes Equals() pour les types valeur](https://docs.microsoft.com/visualstudio/profiling/da0006-override-equals-parens-for-value-types).  
  
Id de règle | DA0006 |  
| Catégorie de |. Utilisation de NET Framework |  
| Méthodes de profilage | Échantillonnage |  
| Message | Remplacer Equals et l’opérateur d’égalité sur les types valeur. |  
| Type de messages | Avertissement |  
  
## <a name="cause"></a>Cause  
 Les appels à la méthode Equals ou aux opérateurs d’égalité d’un type valeur public représentent une part importante des données de profilage. Implémentez une méthode plus efficace.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour les types valeur, l’implémentation héritée de Equals utilise la bibliothèque <xref:System.Reflection> et compare le contenu de tous les champs du type. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. Si votre langage de programmation prend en charge la surcharge des opérateurs, vous devez également fournir une implémentation des opérateurs d’égalité et d’inégalité.  
  
 Pour plus d’informations sur la façon de remplacer Equals et les opérateurs d’égalité, consultez [Conseils pour l’implémentation de Equals et de l’opérateur d’égalité (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Pour obtenir un exemple d’implémentation de Equals et des opérateurs d’égalité, consultez la règle d’analyse du code [CA1815 : Remplacez Equals et l’opérateur égal à dans les types valeur](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)



