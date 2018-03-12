---
title: "DA0012 : Quantité importante de réflexion | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 203de647342affb9d81f0a57d0bcd44ac983f307
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012 : Quantité importante de réflexion
|||  
|-|-|  
|ID de règle|DA0012|  
|Category|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage|  
|Message|Vous utilisez trop de réflexion. C’est une opération coûteuse.|  
|Type de règle|Warning|  
  
## <a name="cause"></a>Cause  
 Les appels aux méthodes System.Reflection, telles que InvokeMember et GetMember, ou aux méthodes de type telles que MemberInvoke, représentent une part importante des données de profilage. Si possible, remplacez ces méthodes par une liaison anticipée aux méthodes des assemblys dépendants.  
  
## <a name="rule-description"></a>Description de la règle  
 La réflexion est une fonctionnalité souple du .NET Framework qui peut être utilisée pour créer une liaison tardive entre votre application et un assembly de runtime dépendant, ou pour créer et exécuter dynamiquement de nouveaux types pendant l’exécution. Toutefois, ces techniques peuvent dégrader les performances si elles sont fréquemment utilisées ou appelées dans des boucles serrées.  
  
 Pour plus d’informations, consultez la section [Reflection and Late Binding](http://go.microsoft.com/fwlink/?LinkId=177826) de la rubrique Chapter 5 — Improving Managed Code Performance qui fait partie de la documentation Improving .NET Application Performance and Scalability, disponible sur le site MSDN, dans la bibliothèque Microsoft Patterns and Practices.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage. Examinez les fonctions appelantes de la méthode System.Type ou System.Reflection pour rechercher les sections du programme qui utilisent le plus fréquemment les API de réflexion .NET. Évitez d’utiliser des méthodes qui retournent des métadonnées. Si les performances de votre application sont critiques, évitez d’utiliser des liaisons tardives et de créer dynamiquement des types au moment de l’exécution.