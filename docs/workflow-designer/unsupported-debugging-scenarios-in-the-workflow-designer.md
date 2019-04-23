---
title: Scénarios de débogage non pris en charge dans le Concepteur de workflow
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 83c9b1158319b580bc860982b6c51c9c28edf5af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099648"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scénarios de débogage non pris en charge dans le Concepteur de workflow

Le Concepteur de Workflow dans .NET Framework 4 ajouté de nombreuses nouvelles fonctionnalités, mais il existe toujours qu’il ne prend pas en charge certains scénarios de débogage.

Le Concepteur de Workflow non pris en charge le débogage des scénarios sont les suivants :

- Impossible de continuer l'exécution une fois que le code a été modifié.

- Impossible de continuer l'exécution à partir d'un point arbitraire dans le workflow (Définir l'instruction suivante).

- Impossible de continuer l'exécution tant que la ligne qui contient le curseur n'est pas atteinte (Exécuter jusqu'au curseur).

- Impossible d'utiliser le Concepteur de workflow pour déboguer les workflows créés à l'aide de code sans utiliser le concepteur.

- Flux de travail créés dans les versions antérieures de Windows Workflow Foundation (WF) ne peut pas être débogué dans le concepteur .NET Framework 4.

- Impossible de définir des points d'arrêt sur les liaisons entre activités ou nœuds <xref:System.Activities.Statements.Flowchart>.

- Le Presse-papiers n'est pas disponible lors du débogage.

- Les points d'arrêt ne sont pas conservés lorsque les activités sont copiées ou collées.

- Impossible de définir des points d'arrêt de workflow dans la fenêtre Pile des appels.

- Lors de la création des points d’arrêt dans le concepteur, le **ligne** et **caractère** paramètres dans le **nouveau point d’arrêt** boîte de dialogue ne sont pas utilisés.

- La fenêtre ou le menu contextuel Point d'arrêt ne prend pas en charge les colonnes ou options suivantes pour le débogage de flux de travail :

    - Condition

    - Nombre d’accès

    - Lorsqu'il est atteint

    - Fonction

    - Données

    - Process

    - Atteindre le code machine