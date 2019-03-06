---
title: Explorateur de performances, fenêtre | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8ffa5340ceaa00adb5e86100d8e58c307f41d40
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647031"
---
# <a name="performance-explorer-window"></a>Explorateur de performances, fenêtre

La fenêtre **Explorateur de performances** de l’IDE de Visual Studio permet de configurer et de démarrer des sessions de performance à l’aide des Outils de profilage de Visual Studio. Si vous avez besoin d’ouvrir la fenêtre, suivez les instructions indiquées dans [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Barre d’outils de l’Explorateur de performances

Vous trouverez les options suivantes dans la barre d’outils de l’**Explorateur de performances** :

- **Lancer l’Assistant Performance** : affiche l’Assistant Performance qui permet d’ajouter une nouvelle session de performance à la fenêtre Explorateur de performances.

- **Nouvelle session de performance** : permet d’ajouter une session de performance vide à la fenêtre Explorateur de performances.

- **Lancer** : la liste du bouton de commande **Lancer** vous permet de démarrer l’application cible dont le profilage est activé immédiatement (**Démarrer avec le profilage**) ou avec le profilage suspendu (**Démarrer avec le profilage suspendu**).

- **Méthode** : permet de spécifier la méthode de profilage de la session (échantillonnage ou instrumentation).

- **Arrêter** : permet de quitter immédiatement l’application cible et le profileur.

- **Attacher/Détacher** : affiche la boîte de dialogue **Attacher le profileur au processus** pour un processus en cours d’exécution auquel attacher le profileur.

## <a name="performance-explorer-window"></a>Fenêtre Explorateur de performances

La fenêtre **Explorateur de performances** contient un contrôle d’arborescence qui affiche les fichiers binaires et les fichiers de données des rapports d’une ou de plusieurs sessions de performance.

- **Nom de la session** : la racine du contrôle d’arborescence contient le nom de la session. Cliquez avec le bouton droit sur le nom de la session pour définir les propriétés de la session ou pour démarrer l’application cible et le profileur.

- **Cibles** : affiche le nom des fichiers binaires à profiler dans la session. Cliquez avec le bouton droit sur **Cibles** pour ajouter ou supprimer un fichier binaire, un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou un site web. Cliquez avec le bouton droit sur le nom d’une cible pour définir les propriétés d’un fichier binaire.

- **Rapports** : affiche le nom des fichiers de données du profileur générés pour la session. Cliquez avec le bouton droit sur **Rapports** pour ajouter un rapport existant ou comparer deux fichiers de données du profileur. Cliquez avec le bouton droit sur le nom d’un rapport pour ouvrir, supprimer ou exporter un fichier de données du profileur.

## <a name="see-also"></a>Voir aussi

[Vues d’ensemble](../profiling/overviews-performance-tools.md)
[Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)
[Contrôle de la collecte de données](../profiling/controlling-data-collection.md)