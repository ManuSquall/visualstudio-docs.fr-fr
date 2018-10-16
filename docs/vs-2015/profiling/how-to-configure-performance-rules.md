---
title: Guide pratique pour configurer les règles de performance | Microsoft Docs
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
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2131a2857c5611f1653d305f63c07fcca1a3953f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199613"
---
# <a name="how-to-configure-performance-rules"></a>Guide pratique pour configurer les règles de performance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les avertissements de performance des outils de profilage Visual Studio signalent les problèmes qui surviennent dans une application profilée et qui peuvent ralentir l’exécution du programme. Les avertissements peuvent également vous informer que vous devez changer de méthode de collecte pour collecter des données plus utiles. Les avertissements de performance sont générés automatiquement dans une session de profilage et s’affichent dans la fenêtre **Liste d’erreurs** lorsque vous ouvrez un fichier de données de profilage dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Certains avertissements peuvent ne pas s’appliquer aux scénarios qui vous intéressent, et certains avertissements peuvent ne pas être déclenchés de manière appropriée. Vous pouvez configurer l’affichage et le masquage des avertissements de performance.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Pour configurer les avertissements de performance du profileur  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Développez **Outils d’analyse des performances**, puis cliquez sur **Règles**.  
  
3.  Pour activer ou désactiver un avertissement, cochez ou décochez la case située en face de l’**ID** et du nom de l’avertissement.  
  
4.  Pour spécifier le niveau d’avertissement d’une règle, cliquez sur la cellule **Action** à côté de la règle, puis cliquez sur le niveau d’avertissement.  
  
    -   **Désactivé** : désactive la règle (cela revient au même que décocher la case à côté de l’ID de règle).  
  
    -   **Avertissement** : affiche la règle sous forme d’avertissement.  
  
    -   **Erreur** : arrête l’exécution du profilage et affiche la règle sous forme d’erreur.  
  
    -   **Informations** : affiche la règle à titre d’information uniquement.



