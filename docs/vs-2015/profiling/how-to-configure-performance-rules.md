---
title: Guide pratique pour configurer les règles de performance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc91bff6819cc5a1ed1e22864157143843f88ba9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790427"
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
