---
title: 'DA0007 : Ne pas utiliser d’exceptions pour le flux de contrôle | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a86c36c55d11f91daff8e876e852daed2f222307
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737096"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007 : Ne pas utiliser d'exceptions pour le flux de contrôle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0007 |  
| Catégorie de |. Utilisation de NET Framework |  
| Méthodes de profilage | Tous les |  
| Message | Un nombre élevé d’exceptions est levé. Envisagez de réduire l’utilisation d’exceptions dans la logique de programme. |  
| Type de message | Avertissement |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Un taux élevé de gestionnaires d’exceptions .NET Framework ont été appelés dans les données de profilage. Utilisez une autre logique de flux de contrôle pour réduire le nombre d’exceptions levées.  
  
## <a name="rule-description"></a>Description de la règle  
 Si l’utilisation de gestionnaires d’exceptions pour intercepter des erreurs et autres événements qui interrompent l’exécution des programmes constitue une bonne pratique, l’utilisation d’un gestionnaire d’exceptions dans le cadre de la logique d’exécution des programmes peut être coûteuse et doit être évitée. Dans la plupart des cas, les exceptions ne doivent être utilisées que pour les événements rares et inattendus. Les exceptions ne doivent pas être utilisées pour retourner des valeurs dans le cadre d’un flux de programme normal. Dans de nombreux cas, vous pouvez éviter la levée des exceptions en validant les valeurs et en utilisant une logique conditionnelle qui arrête l’exécution des instructions qui causent le problème.  
  
 Pour plus d’informations, consultez la section [Exception Management](http://go.microsoft.com/fwlink/?LinkID=177825) de la rubrique **Chapter 5 — Improving Managed Code Performance** qui fait partie de la documentation **Improving .NET Application Performance and Scalability**, disponible sur le site MSDN, dans la bibliothèque **Microsoft Patterns and Practices**.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue Marques. Recherchez la colonne qui contient les mesures **Exceptions .NET CLR(@ProcessInstance)\\Nombre d’exceptions levées/s**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles la gestion des exceptions est plus fréquente. À l’aide d’un profil d’échantillonnage, essayez d’identifier les instructions throw et les blocs try/catch qui génèrent fréquemment des exceptions. Si nécessaire, ajoutez une logique aux blocs catch pour identifier plus facilement les exceptions qui sont gérées le plus fréquemment. Si possible, remplacez les instructions throw ou les blocs catch fréquemment exécutés par une logique simple de contrôle de flux ou par du code de validation.  
  
 Par exemple, si votre application gère des exceptions DivideByZeroException fréquentes, le fait d’ajouter une logique à votre programme pour rechercher des dénominateurs avec des valeurs nulles peut améliorer les performances de l’application.



