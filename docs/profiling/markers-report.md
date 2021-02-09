---
title: Marqueurs, rapport | Documents Microsoft
description: Découvrez comment le rapport marqueurs répertorie les marqueurs dans le laps de temps affiché et comment le panoramique ou le zoom peut entraîner l’apparition ou la disparition de marqueurs.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3b674a2051a0b8b7b96a9c9bf0fb114f0fef46e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876925"
---
# <a name="markers-report"></a>Rapport des marqueurs
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
> Le rapport Marqueurs peut afficher 1 000 marqueurs. Pour voir tous les marqueurs, exportez le rapport complet vers un fichier CSV.