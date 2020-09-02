---
title: Scénarios de débogage non pris en charge dans le Concepteur de workflow
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77d1318dbdb23516902523e9c7865dad781cb06b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593035"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scénarios de débogage non pris en charge dans le Concepteur de workflow

Le Concepteur de flux de travail ne prend pas en charge les scénarios de débogage suivants :

- Impossible de continuer l'exécution une fois que le code a été modifié.

- Impossible de continuer l'exécution à partir d'un point arbitraire dans le workflow (Définir l'instruction suivante).

- Impossible de continuer l'exécution tant que la ligne qui contient le curseur n'est pas atteinte (Exécuter jusqu'au curseur).

- Impossible d'utiliser le Concepteur de workflow pour déboguer les workflows créés à l'aide de code sans utiliser le concepteur.

- Les flux de travail créés dans les versions antérieures de Windows Workflow Foundation (WF) ne peuvent pas être débogués dans .NET Framework 4 ou version ultérieure.

- Impossible de définir des points d'arrêt sur les liaisons entre activités ou nœuds <xref:System.Activities.Statements.Flowchart>.

- Le Presse-papiers n'est pas disponible lors du débogage.

- Les points d'arrêt ne sont pas conservés lorsque les activités sont copiées ou collées.

- Impossible de définir des points d'arrêt de workflow dans la fenêtre Pile des appels.

- Lorsque vous créez des points d’arrêt dans le concepteur, les paramètres de **ligne** et de **caractère** de la boîte de dialogue **nouveau point d’arrêt** ne sont pas utilisés.

- La fenêtre ou le menu contextuel Point d'arrêt ne prend pas en charge les colonnes ou options suivantes pour le débogage de flux de travail :

  - Condition

  - Nombre d'accès

  - Lorsqu'il est atteint

  - Fonction

  - Données

  - Process

  - Atteindre le code machine
