---
title: 'DA0007 : Ne pas utiliser d’exceptions pour le flux de contrôle | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 088b42862065f031347f51bec791ec866b6fb87e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639139"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007 : Ne pas utiliser d’exceptions pour le flux de contrôle

|||
|-|-|
|ID de règle|DA0007|
|Category|Utilisation du .NET Framework|
|Méthodes de profilage|Tous|
|Message|De nombreuses exceptions sont levées. Réduisez l’utilisation d’exceptions dans la logique du programme.|
|Type de message|Warning|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 Un taux élevé de gestionnaires d’exceptions .NET Framework ont été appelés dans les données de profilage. Utilisez une autre logique de flux de contrôle pour réduire le nombre d’exceptions levées.

## <a name="rule-description"></a>Description de la règle
 Si l’utilisation de gestionnaires d’exceptions pour intercepter des erreurs et autres événements qui interrompent l’exécution des programmes constitue une bonne pratique, l’utilisation d’un gestionnaire d’exceptions dans le cadre de la logique d’exécution des programmes peut être coûteuse et doit être évitée. Dans la plupart des cas, les exceptions ne doivent être utilisées que pour les événements rares et inattendus. Les exceptions ne doivent pas être utilisées pour retourner des valeurs dans le cadre d’un flux de programme normal. Dans de nombreux cas, vous pouvez éviter la levée des exceptions en validant les valeurs et en utilisant une logique conditionnelle qui arrête l’exécution des instructions qui causent le problème.

 Pour plus d’informations, consultez la section [Exception Management](http://go.microsoft.com/fwlink/?LinkID=177825) dans **Chapter 5 — Improving Managed Code Performance** qui fait partie de la documentation **Improving .NET Application Performance and Scalability** de la bibliothèque **Microsoft Patterns and Practices** sur MSDN.

## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue Marques. Recherchez la colonne qui contient les mesures **Exceptions .NET CLR(@ProcessInstance)\\Nombre d’exceptions levées/s**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles la gestion des exceptions est plus fréquente. À l’aide d’un profil d’échantillonnage, essayez d’identifier les instructions throw et les blocs try/catch qui génèrent fréquemment des exceptions. Si nécessaire, ajoutez une logique aux blocs catch pour identifier plus facilement les exceptions qui sont gérées le plus fréquemment. Si possible, remplacez les instructions throw ou les blocs catch fréquemment exécutés par une logique simple de contrôle de flux ou par du code de validation.

 Par exemple, si votre application gère des exceptions DivideByZeroException fréquentes, le fait d’ajouter une logique à votre programme pour rechercher des dénominateurs avec des valeurs nulles améliore les performances de l’application.