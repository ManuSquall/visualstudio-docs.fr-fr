---
title: Concepteur de flux de travail - débogage de Workflows hérités
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-legacy-workflows"></a>Débogage de workflows hérités

Si vous utilisez le Concepteur de flux de travail Windows hérité dans Visual Studio pour créer des applications de Windows Workflow Foundation (WF) qui ciblent Framework 3.0 ou 3.5, vous pouvez déboguer vos workflows comme tout autre programme en définissant des points d’arrêt, attacher au processus, et en examinant les threads et la pile des appels. Vous avez également la possibilité d'effectuer un débogage à distance.

> [!NOTE]
> Si plusieurs versions de Visual Studio ont été installées et désinstallées sur votre ordinateur, le débogage WF3 peut échouer pour l'une des raisons suivantes :
>
> -   Les points d'arrêt ne sont pas atteints.
> -   Le message suivant s'affiche :
>
> **Impossible de démarrer le débogage sur le serveur web. Le débogueur n'est pas installé correctement.  Impossible de déboguer le type de code demandé.  Exécutez le programme d’installation pour installer ou réparer le débogueur.**
>
> Si l'un de ces scénarios se produit lors du débogage de workflows .NET Framework 3.0 ou 3.5, réparez l'installation de Visual Studio.

 Windows Workflow Foundation s'intègre avec les fenêtres de débogage Visual Studio standard suivantes :

-   **Point d’arrêt**: fonctionne comme prévu, mais que vous spécifiez une activité pour le nom de fonction.

-   **Pile des appels**: modifiée pour fournir un plan des activités qui ont exécuté dans une instance de workflow. Les entrées dans le **pile des appels** sont une recherche en profondeur de l’exécution d’activités. Vous pouvez double-cliquer sur une entrée pour placer le focus sur l'activité sélectionnée.

-   **Threads**: fournit l’ID d’instance de l’instance de flux de travail qui est en cours de débogage.

 Visual Studio pour Windows Workflow Foundation ne prend pas en charge les fonctionnalités de débogage suivantes :

-   Points d'arrêt conditionnels sur l'aire du concepteur.

-   Espion express.

-   Définir l'instruction suivante.

-   Exécuter jusqu'au curseur.

-   Modifier &amp ; Continuer.

-   Débogage juste-à-temps.

-   Débogage en mode mixte.