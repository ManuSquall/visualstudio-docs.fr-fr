---
title: Collecter les données temporelles détaillées à l’aide de l’instrumentation
description: Utilisez la méthode d’instrumentation Outils de profilage pour obtenir des informations de temporisation détaillées sur une section de votre code, et pour comprendre l’impact des opérations d’e/s.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17c569a9f5a50b769af0881d47fe810afe18058e
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533847"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Collecter les données temporelles détaillées à l’aide de l’instrumentation
La méthode d’instrumentation des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] injecte le code de profilage dans une copie d’un module. Le code enregistre chaque entrée, sortie et appel des fonctions dans le module pendant une exécution du profilage. La méthode d’instrumentation est utile pour rassembler des informations de temporisation détaillées sur une section de votre code et comprendre l’impact des opérations d’entrée et de sortie sur les performances de l’application.

 Vous pouvez spécifier la méthode d’instrumentation à l’aide de l’une des procédures suivantes :

- Dans la première page de l’Assistant Profilage, sélectionnez **Instrumentation**.

- Dans la barre d’outils de l’ **Explorateur de performances** , dans la liste **Méthode** , cliquez sur **Instrumentation**.

- Dans la page **Général** de la boîte de dialogue Propriétés de la session de performance, sélectionnez **Instrumentation**.

## <a name="common-tasks"></a>Tâches courantes
 Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :

- Dans **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.

  Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue des **pages de propriétés** de la _session de performance_ lorsque vous profilez à l’aide de la méthode d’instrumentation.

|Tâche|Contenu associé|
|----------|---------------------|
|Dans la page **Général** , ajoutez l’allocation de mémoire .NET et les données de durée de vie, et spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|-   [Collecter les données d’allocation et de durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procédure : définir les options de nom de fichier de données de performances](../profiling/how-to-set-performance-data-file-name-options.md)|
|Dans la page **Lancer** , si vous avez plusieurs projets .exe dans votre solution, spécifiez l’application à démarrer et l’ordre de démarrage.|-   [Comment : spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|
|Dans la page **Fichiers binaires** , spécifiez un emplacement pour les copies instrumentées des modules. Par défaut, les fichiers binaires d’origine sont déplacés vers un dossier de sauvegarde.|-   [Comment : déplacer des binaires instrumentés](../profiling/how-to-relocate-instrumented-binaries.md)|
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|-   [Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|
|Dans la page **Instrumentation** , excluez les petites fonctions du profilage pour réduire les surcharges de profilage, profilez le code JavaScript dans des pages web ASP.NET et spécifiez les commandes à exécuter dans une invite de commandes avant et après le processus d’instrumentation.|-   [Comment : exclure ou inclure les fonctions courtes de l’instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Comment : profiler du code JavaScript dans des pages Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Guide pratique pour spécifier des commandes de pré-instrumentation et de post-instrumentation](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Dans la page **Compteurs UC** , spécifiez un ou plusieurs compteurs de performance du processeur à ajouter aux données de profilage.|-   [Guide pratique collecter les données des compteurs UC](../profiling/how-to-collect-cpu-counter-data.md)|
|Dans la page **Événements Windows** , sélectionnez un ou plusieurs événements de suivi d’événements pour Windows (ETW) à collecter avec les données d’échantillonnage.|-   [Comment : collecter des données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|-   [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Dans la page **Avancé** , spécifiez les options supplémentaires que vous voulez passer au programme d’instrumentation VSInstr, notamment les options permettant d’inclure ou d’exclure des fonctions spécifiques.|-   [Guide pratique pour spécifier des options d’instrumentation supplémentaires](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Comment : limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
