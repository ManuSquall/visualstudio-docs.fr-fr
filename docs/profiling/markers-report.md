---
title: Marqueurs, rapport | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ccb9c11d39d0500eab0698dc2907ab983964753
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881623"
---
# <a name="markers-report"></a>Marqueurs, rapport
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