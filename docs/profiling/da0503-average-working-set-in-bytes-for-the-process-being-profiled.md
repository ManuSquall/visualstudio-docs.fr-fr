---
title: DA0503-jeu de travail moyen en octets pour le processus en cours de profilage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6717f524f6a2d3f9f09290ac9bfbd8f02fc23fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544545"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503 : Jeu de travail moyenne en octets pour le processus en cours de profilage

|Élément|Valeur|
|-|-|
|ID de règle|DA0503|
|Category|Analyse des ressources|
|Méthode de profilage|Tous|
|Message|Uniquement à titre d’informations. Le compteur Jeu de travail de processus mesure l’utilisation de la mémoire physique par le processus en cours de profilage. La valeur signalée correspond à la moyenne pour tous les intervalles de mesure.|
|Type de règle|Information|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="rule-description"></a>Description de la règle
 Ce message signale la quantité moyenne de mémoire physique que le processus utilise actuellement, en octets (le jeu de travail). Le jeu de travail du processus comprend les pages de l’espace d’adressage de processus qui résident actuellement dans la mémoire physique.

 La valeur signalée comprend les pages résidant dans les segments de mémoire partagée que le processus a référencées. Les DLL partagées que le processus référence sont incluses dans les segments de mémoire partagée qui sont comptabilisés. La valeur du jeu de travail du processus peut être supérieure à la quantité de mémoire virtuelle que le processus a allouée, en raison des segments de mémoire partagée.

 La valeur signalée correspond à la moyenne de tous les intervalles de mesure pendant lesquels le processus profilé était actif.

 La taille du jeu de travail du processus correspond à la mémoire virtuelle que le processus utilise activement. Elle est également affectée par la quantité de mémoire physique (ou RAM) disponible pour exécuter l’application, et par les conflits entre cette mémoire physique et d’autres processus en cours d’exécution. Si la mémoire physique est limitée, la valeur du jeu de travail de processus peut varier considérablement lorsque les systèmes d’exploitation tentent d’équilibrer l’utilisation de la mémoire entre les processus actifs en supprimant périodiquement les pages relativement inactives des jeux de travail de processus.

 Pour plus d’informations sur les jeux de travail de processus, consultez [Jeu de travail](/windows/win32/memory/working-set) dans la documentation MSDN relative à la gestion de la mémoire dans Windows.

## <a name="how-to-use-rule-data"></a>Comment utiliser les données de règle
 Utilisez la valeur de la règle pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de profilage.

 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue [Marques](../profiling/marks-view.md) des données de profilage. Accédez aux colonnes **Processus\Jeu de travail** et **Mémoire\Pages/s**. Comparez les deux colonnes et déterminez si des phases de l’exécution du programme ont connu une augmentation de l’activité d’E/S de pagination.
