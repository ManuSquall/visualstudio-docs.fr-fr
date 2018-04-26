---
title: Scénarios de débogage non pris en charge dans le Concepteur de workflow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scénarios de débogage non pris en charge dans le Concepteur de workflow

Le Concepteur de Workflow dans .NET Framework 4 ajouté de nombreuses nouvelles fonctionnalités, mais il ne prend pas en charge certains scénarios de débogage sont encore.

Le Concepteur de Workflow non pris en charge les scénarios de débogage sont les suivants :

-   Impossible de continuer l'exécution une fois que le code a été modifié.

-   Impossible de continuer l'exécution à partir d'un point arbitraire dans le workflow (Définir l'instruction suivante).

-   Impossible de continuer l'exécution tant que la ligne qui contient le curseur n'est pas atteinte (Exécuter jusqu'au curseur).

-   Impossible d'utiliser le Concepteur de workflow pour déboguer les workflows créés à l'aide de code sans utiliser le concepteur.

-   Impossible de déboguer des workflows créés dans les versions antérieures de Windows Workflow Foundation (WF) dans le Concepteur de .NET Framework 4.

-   Impossible de définir des points d'arrêt sur les liaisons entre activités ou nœuds <xref:System.Activities.Statements.Flowchart>.

-   Le Presse-papiers n'est pas disponible lors du débogage.

-   Les points d'arrêt ne sont pas conservés lorsque les activités sont copiées ou collées.

-   Impossible de définir des points d'arrêt de workflow dans la fenêtre Pile des appels.

-   Lors de la création de points d’arrêt dans le concepteur, le **ligne** et **caractère** paramètres dans le **nouveau point d’arrêt** boîte de dialogue ne sont pas utilisés.

-   La fenêtre ou le menu contextuel Point d'arrêt ne prend pas en charge les colonnes ou options suivantes pour le débogage de flux de travail :

    -   Condition

    -   Nombre d'accès

    -   Lorsqu'il est atteint

    -   Fonction

    -   Données

    -   Processus

    -   Atteindre le code machine