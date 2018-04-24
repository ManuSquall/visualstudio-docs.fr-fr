---
title: 'DA0504 : Jeu de travail maximal en octets pour le processus en cours de profilage | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6bb6c62a785815db0c678d0a1f0ff38ebea14d70
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504 : Jeu de travail maximal en octets pour le processus en cours de profilage
|||  
|-|-|  
|ID de règle|DA0504|  
|Category|Gestion des ressources|  
|Méthode de profilage|Tous|  
|Message|Uniquement à titre d’informations. Le compteur Jeu de travail de processus mesure l’utilisation de la mémoire physique par le processus en cours de profilage. La valeur signalée correspond à la valeur maximale observée dans l’ensemble des intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Ce message signale la quantité maximale de mémoire physique, en octets, que le processus utilise. Le jeu de travail du processus comprend les pages de l’espace d’adressage de processus qui résident actuellement dans la mémoire physique. Cette règle signale la valeur maximale du jeu de travail du processus pendant que le profilage était actif.  
  
 La valeur signalée comprend les pages résidant dans les segments de mémoire partagée que le processus a référencées. Les DLL partagées que le processus référence sont incluses dans les segments de mémoire partagée qui sont comptabilisés. La valeur du jeu de travail du processus peut être supérieure à la quantité de mémoire virtuelle que le processus a allouée, en raison des segments de mémoire partagée.  
  
 La taille du jeu de travail du processus correspond à la mémoire virtuelle que le processus utilise activement. Elle est également affectée par la quantité de mémoire physique (ou RAM) disponible pour exécuter l’application, et par les conflits entre cette mémoire physique et d’autres processus en cours d’exécution. Pour plus d’informations sur les jeux de travail de processus, consultez [Jeu de travail](http://go.microsoft.com/fwlink/?LinkId=177830) dans la documentation MSDN relative à la gestion de la mémoire dans Windows.  
  
## <a name="how-to-use-rule-data"></a>Comment utiliser des données de règle  
 La règle rassemble ces données de mesure à partir de la fonctionnalité d’analyse des performances de Windows et les fournit dans un but informatif. Utilisez ces données pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de test.  
  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Marques](../profiling/marks-view.md) des données de profilage. Accédez aux colonnes de compteur **Processus\Jeu de travail** et **Mémoire\Pages/s**. Recherchez la valeur maximale de la colonne **Processus\Jeu de travail** et comparez-la à celle de la colonne **Mémoire\Pages/s**. Souvent, la valeur maximale du jeu de travail est associée à un intervalle durant lequel une baisse de l’activitité d’E/S de pagination s’est produite, en particulier si la mémoire de l’ordinateur est limitée.