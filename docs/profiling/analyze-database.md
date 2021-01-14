---
title: Analyser l’utilisation des bases de données pour les projets .NET Core | Microsoft Docs
description: Utilisez l’outil de base de données pour enregistrer les requêtes de base de données de votre application, puis analysez-les pour trouver des moyens d’améliorer les performances.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205461"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analyser les performances de base de données à l’aide de l’outil base de données

Utilisez l’outil de base de données pour enregistrer les requêtes de base de données que votre application effectue pendant une session de diagnostic. Vous pouvez ensuite analyser des informations sur des requêtes individuelles pour trouver des emplacements afin d’améliorer les performances de votre application.

> [!NOTE]
> L’outil de base de données nécessite Visual Studio 2019 version 16,3 ou ultérieure et un projet .NET Core sur Windows à l’aide de [ADO.net]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) ou [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Programme d’installation

1. Appuyez sur **ALT + F2** pour ouvrir le profileur de performances dans Visual Studio.

1. Activez la case à cocher **base de données** .

   ![Outil de base de données sélectionné](./media/db-launch.png "Outil de base de données sélectionné")

   > [!NOTE]
   > Si l’outil n’est pas disponible pour la sélection, désactivez la case à cocher de tous les autres outils, car certains outils doivent s’exécuter seuls. Pour en savoir plus sur l’exécution conjointe d’outils, consultez [utilisation des outils de profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Si l’outil n’est toujours pas disponible, vérifiez que votre projet répond à la configuration requise précédente. Assurez-vous que votre projet est en mode mise en sortie pour capturer les données les plus précises.

1. Sélectionnez le bouton **Démarrer** pour exécuter l’outil.

1. Une fois l’exécution de l’outil terminée, parcourez le scénario que vous souhaitez profiler dans votre application. Sélectionnez ensuite **arrêter la collecte** ou fermez votre application pour afficher vos données.

1. Après l’arrêt de la collection, vous voyez un tableau des requêtes qui ont été exécutées pendant votre session de profilage.

   ![Arrêt de l’outil de base de données](./media/db-after.png "Arrêt de l’outil de base de données")

Les requêtes sont organisées par ordre chronologique, mais vous pouvez les trier selon l’une des colonnes. Vous pouvez afficher plus de colonnes en cliquant avec le bouton droit sur les titres des colonnes. La sélection de la colonne **durée** classe les requêtes du plus long au plus petit.

Une fois que vous avez trouvé une requête que vous souhaitez examiner, cliquez avec le bouton droit sur la requête. Sélectionnez ensuite **atteindre le fichier source** pour voir quel code est responsable de cette requête.

![Atteindre le fichier source sélectionné](./media/db-gotosource.png "Atteindre le fichier source sélectionné")

Si vous sélectionnez une plage de temps sur un graphique, la table de requête affiche uniquement les requêtes qui se sont produites pendant cette période. Ce comportement est particulièrement utile lorsque vous exécutez également l' [outil utilisation](./cpu-usage.md?view=vs-2019&preserve-view=true)de l’UC.

## <a name="see-also"></a>Voir aussi

- [Optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md)