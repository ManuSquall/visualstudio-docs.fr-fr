---
title: Marqueurs, rapport | Documents Microsoft
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
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1777f2f9fbd63ba659e74d0ce471962b29b15fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811066"
---
# <a name="markers-report"></a>Marqueurs, rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le rapport Marqueurs répertorie les marqueurs dans le délai affiché.  Des marqueurs peuvent apparaître ou disparaître en fonction des mouvements panoramiques, des zooms ou des masquages de couloirs effectués. Le rapport contient les informations suivantes sur chaque marqueur :  
  
- L’heure à laquelle il a commencé, par rapport au début de la trace.  
  
- Sa durée. La durée est égale à zéro pour les indicateurs et les messages, car ils représentent un instant.  
  
- L’ID du thread qui l’a généré.  
  
- Le fournisseur de suivi des événements pour Windows (ETW) qui l’a généré.  
  
- La série de marqueurs à partir de laquelle il a été écrit.  
  
- La catégorie d’événements à laquelle il appartient.  
  
- Son niveau d’importance.  
  
- Son type (étendue, indicateur ou message).  
  
- Une description générale de ce qu’il représente.  
  
  Choisissez le bouton **Exporter** pour enregistrer le rapport Marqueurs dans un fichier CSV. Vous pouvez utiliser les données contenues dans le fichier CSV avec d’autres applications ou outils.  
  
> [!NOTE]
>  Le rapport Marqueurs peut afficher 1 000 marqueurs. Pour voir tous les marqueurs, exportez le rapport complet vers un fichier CSV.



