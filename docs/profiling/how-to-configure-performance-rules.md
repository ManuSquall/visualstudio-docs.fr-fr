---
title: Guide pratique pour configurer les règles de performance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe6e10c42188cab23c75262d947c7deb9c28ea5
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816027"
---
# <a name="how-to-configure-performance-rules"></a>Guide pratique pour configurer les règles de performance
Les avertissements de performance des outils de profilage Visual Studio signalent les problèmes qui surviennent dans une application profilée et qui peuvent ralentir l’exécution du programme. Les avertissements peuvent également vous informer que vous devez changer de méthode de collecte pour collecter des données plus utiles. Les avertissements de performance sont générés automatiquement dans une session de profilage et s’affichent dans la fenêtre **Liste d’erreurs** lorsque vous ouvrez un fichier de données de profilage dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Certains avertissements peuvent ne pas s’appliquer aux scénarios qui vous intéressent, et certains avertissements peuvent ne pas être déclenchés de manière appropriée. Vous pouvez configurer l’affichage et le masquage des avertissements de performance.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Pour configurer les avertissements de performance du profileur  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Développez **Outils d’analyse des performances**, puis cliquez sur **Règles**.  
  
3.  Pour activer ou désactiver un avertissement, cochez ou décochez la case située en face de l’**ID** et du nom de l’avertissement.  
  
4.  Pour spécifier le niveau d’avertissement d’une règle, cliquez sur la cellule **Action** à côté de la règle, puis cliquez sur le niveau d’avertissement.  
  
    -   **Désactivé** : désactive la règle (cela revient au même que décocher la case à côté de l’ID de règle).  
  
    -   **Avertissement** : affiche la règle sous forme d’avertissement.  
  
    -   **Erreur** : arrête l’exécution du profilage et affiche la règle sous forme d’erreur.  
  
    -   **Informations** : affiche la règle à titre d’information uniquement.