---
title: Observateur d’événements | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 0be00f2333a2e732d9ba4472004c383b132c0bf2
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075063"
---
# <a name="events-viewer"></a>Observateur d’événements

La visionneuse des événements génériques montre l’activité de l’application via une liste d’événements tels que le chargement du module, le démarrage du thread et la configuration du système. Cette vue vous aide à mieux diagnostiquer le fonctionnement de votre application dans le profileur Visual Studio.

## <a name="setup"></a>Programme d’installation

1. Appuyez sur **ALT + F2** pour ouvrir le profileur de performances dans Visual Studio.

1. Activez la case à cocher **Observateur d’événements** .

   ![Case à cocher observateur d’événements activée](../profiling/media/eventsviewerselected.png "Case à cocher observateur d’événements activée")

1. Sélectionnez le bouton **Démarrer** pour exécuter l’outil.

1. Une fois l’exécution de l’outil terminée, parcourez le scénario pour le Profiler dans votre application. Sélectionnez ensuite **arrêter la collecte** ou fermez votre application pour afficher vos données.

   ![Fenêtre d’arrêt de la collecte](../profiling/media/stopcollectioneventsviewer.png "Fenêtre d’arrêt de la collecte")

Pour plus d’informations sur la façon de rendre l’outil plus efficace, consultez [optimisation des paramètres de profilage](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Comprendre vos données

![Une trace de l’observateur d’événements](../profiling/media/eventviewertrace.png "Une trace de l’observateur d’événements")

|Nom de la colonne|Description|
|----------|---------------------|
|Nom du fournisseur|Source de l’événement|
|Nom de l'événement|Événement spécifié par son fournisseur.|
|Texte|Descriptions du fournisseur, du nom d’événement et de l’ID de l’événement|
|Horodateur (MS)|Lorsque l’événement a eu lieu|
|GUID du fournisseur|ID du fournisseur d’événements|
|ID de l’événement|ID de l’événement|
|ID du processus|Processus à partir duquel l’événement s’est produit (s’il est connu)|
|Nom du processus|Nom du processus s’il est en cours d’exécution|
|ID du thread|ID du thread à partir duquel l’événement s’est produit (s’il est connu)|

Si une colonne est manquante par défaut, cliquez avec le bouton droit sur l’un des en-têtes de colonnes existants, puis sélectionnez la colonne que vous souhaitez ajouter.

![Ajout de colonnes à l’observateur d’événements](../profiling/media/eventvieweraddcolumns.png "Ajout de colonnes à l’observateur d’événements")

Lorsque vous sélectionnez un événement, la fenêtre **propriétés supplémentaires** s’affiche. **Propriétés communes** affiche la liste des propriétés qui s’affichent pour tous les événements. **Propriétés de charge utile** affiche des propriétés spécifiques à l’événement. Pour certains événements, vous pouvez également afficher des **piles**.

![Observateur d’événements présentant les piles](../profiling/media/eventviewerstacks.png "Observateur d’événements présentant les piles")

## <a name="organize-your-data"></a>Organiser vos données

Toutes les colonnes à l’exception de la colonne **Text** peuvent être triées.

![Trace de l’observateur d’événements](../profiling/media/eventviewertrace.png "Trace de l’observateur d’événements")

L’observateur d’événements affiche jusqu’à 20 000 événements à la fois. Pour vous concentrer sur les événements qui vous intéressent, vous pouvez filtrer l’affichage des événements en sélectionnant le filtre d’événement. Vous pouvez également voir le pourcentage du nombre total d’événements qui se sont produits pour chaque fournisseur. Pointez sur un filtre d’événement unique pour afficher une info-bulle qui affiche les éléments suivants :

- Nom d'événement
- Fournisseur
- GUID
- Pourcentage du nombre total d’événements
- Nombre d’événements

![Filtre d’événements de l’observateur d’événements](../profiling/media/eventviewereventfilter.png "Filtre d’événements de l’observateur d’événements")

Le filtre du fournisseur affiche le pourcentage du nombre total d’événements qui se sont produits pour chaque fournisseur. Pointez sur un fournisseur unique pour afficher une info-bulle similaire avec le nom du fournisseur, le pourcentage du nombre total d’événements et le nombre d’événements.

![Filtre du fournisseur de l’observateur d’événements](../profiling/media/eventviewerproviderfilter.png "Filtre du fournisseur de l’observateur d’événements")
