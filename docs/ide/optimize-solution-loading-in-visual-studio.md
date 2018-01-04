---
redirect_url: /visualstudio/ide/optimize-visual-studio-startup-time/
ms.openlocfilehash: 6ba351d5b395caaddd12021b09f8792cd19b2905
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
title: "Optimiser le chargement de solutions dans Visual Studio | Microsoft Docs" ms.custom: "" ms.date: 08/31/2017 ms.reviewer: "" ms.suite: "" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "vitesse de démarrage [Visual Studio]"
  - "optimisation de la vitesse de démarrage [Visual Studio]"
  - "améliorer la vitesse de démarrage [Visual Studio]" ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138 caps.latest.revision: 4 author: "gewarren" ms.author: "gewarren" manager: ghogen f1_keywords: 
  - "vs.performancecenter" ms.technology: 
  - "vs-ide-general"
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Optimiser le chargement de solutions dans Visual Studio
De nombreuses solutions contiennent un grand nombre de projets, ce qui affecte le temps nécessaire pour charger ces solutions. Toutefois, dans les environnements d’équipe, les développeurs travaillent généralement sur différents sous-ensembles de ces projets et n’ont pas besoin de charger tous les projets individuels.

Visual Studio 2017 prend en charge le **chargement de solution allégé**. Quand le mode Chargement de solution allégé (LSL, Lightweight Solution Load) est activé, Visual Studio 2017 charge un petit sous-ensemble de projets au lieu de charger tous les projets d’une solution de grande taille. La plupart des fonctionnalités de l’IDE couramment utilisées fonctionnent en mode LSL. Vous pouvez ainsi effectuer des générations, des recherches et des débogages sur l’ensemble de la solution. (La principale fonctionnalité non prise en charge en mode LSL est Modifier & Continuer.)  

> [!NOTE]
> Ce contenu s’applique à Visual Studio 2017 Update 3.

Pour les solutions de grande taille comportant plus de 30 projets, LSL charge généralement les solutions deux fois en tant plus vite (en moyenne). Alors que la plupart des fonctionnalités de l’IDE fonctionnent en mode LSL, certaines peuvent nécessiter le chargement de tous les projets. Dans ce cas-là, Visual Studio charge automatiquement l’ensemble de la solution pour vous permettre d’utiliser la fonctionnalité. Dans le pire des cas, vous finissez par charger tous les projets en mode allégé. 

Si vous utilisez une fonctionnalité de l’IDE sur un projet qui n’est actuellement pas chargé, Visual Studio charge automatiquement le ou les projets appropriés. Par exemple, si vous tentez de créer ou d’ouvrir un diagramme de classes pour un projet non ouvert, Visual Studio charge automatiquement les projets appropriés. La liste détaillée des fonctionnalités est référencée dans les sections suivantes.

Les sections suivantes montrent comment activer le chargement de solution allégé. Elles vous permettent également de déterminer s’il faut, ou non, activer la fonctionnalité.

## <a name="enable-or-disable-lightweight-solution-load"></a>Activer ou désactiver le chargement de solutions allégé

Vous pouvez cliquer avec le bouton droit sur le nom de la solution dans l’Explorateur de solutions, puis sélectionner **Activer le chargement de solutions allégé**. Après avoir sélectionné l’option, vous devez fermer et rouvrir la solution afin d’activer le chargement de solutions allégé.

> [!NOTE]
> La procédure de désactivation de LSL est similaire. Pour désactiver le chargement de solution allégé, sélectionnez **Désactiver le chargement de solution allégé**, puis fermez et rouvrez la solution. 

![Explorateur de solutions](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Configurer les paramètres globaux du chargement de solution allégé

Vous pouvez désactiver ou configurer globalement LSL pour toutes les solutions en choisissant **Outils > Options > Projets et solutions**.

![Options des outils, boîte de dialogue](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>Comment le chargement de solution allégé fonctionne-t-il en arrière-plan ?

Quand vous chargez votre solution, Visual Studio se souvient des projets précédemment ouverts et charge uniquement ces projets. Tous les autres projets sont visibles dans l’Explorateur de solutions, mais ne sont pas chargés. Dès que vous développez un projet ou que vous cliquez avec le bouton droit sur un projet, Visual Studio le charge automatiquement. Le chargement automatique de projets prend généralement moins d’une seconde, mais il peut nécessiter plus de temps pour certains projets. Toutefois, Visual Studio active des fonctionnalités de l’IDE telles que la recherche, le débogage, la génération et le contrôle de code source qui fonctionnent sur l’ensemble de la solution. Par exemple, vous pouvez effectuer une recherche dans l’ensemble d’une solution même si seuls quelques projets sont chargés en mode allégé. 

Quand vous développez plus de projets, Visual Studio mémorise la liste des projets développés. Quand une solution est rouverte, Visual Studio charge automatiquement les projets que vous avez précédemment développés.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio envoie une invite aux développeurs susceptibles d’accroître les performances de manière significative

D’après la télémétrie de Visual Studio, le mode LSL est très utile pour les solutions de grande taille comprenant plus de 30 projets. Par conséquent, nous incitons les développeurs des solutions de grande taille d’essayer le mode LSL. La majorité des développeurs qui essaient LSL pour la première fois finissent par l’utiliser régulièrement. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Visual Studio utilise une méthode heuristique pour formuler des recommandations relatives à l’activation du chargement de solution allégé

Par défaut, Visual Studio active LSL pour les utilisateurs les plus susceptibles d’en tirer parti. Si vous avez plusieurs solutions, Visual Studio propose le mode LSL pour celles qui sont le plus susceptibles de voir des améliorations significatives des performances. Si vous sélectionnez l’option de mode allégé **Laisser Visual Studio décider** (option par défaut), Visual Studio peut ouvrir la solution en mode allégé en fonction de l’heuristique. Une barre des messages indique si la solution est en mode allégé. Quand elle s’affiche, vous pouvez choisir entre en savoir plus ou mettre à jour les paramètres.

![Fenêtre contextuelle](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Fonctionnalités de l’IDE entièrement prises en charge en mode allégé

|Fonctionnalité|Prise en charge en mode allégé ?|
|-|-|-|
|IntelliSense|Oui|
|Rechercher|Oui|
|Débogage|Oui|
|Générer|Oui|
|Navigation dans le code (Atteindre la définition et Rechercher toutes les références)|Oui|
|CodeLens|Oui|
|Analyse statique du code|Oui|
|Déployer et publier|Oui|
|Ajout et suppression de références|Oui|
|Multi-ciblage|Oui|
|IntelliTrace|Oui|
|Live Unit Testing|Oui|
|IntelliTest|Oui|
|Microsoft Fakes|Oui|
|Modifier & Continuer|Non pris en charge|
|Test unitaire|Nécessite le chargement de projets de test suivi d’une build de solution|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Scénarios dans lesquels le chargement de solution allégé charge le ou les projets appropriés pour accomplir l’opération

Si vous ne travaillez pas sur un projet de la solution, le projet n’est pas chargé en mode allégé. Pour certaines fonctionnalités, des projets supplémentaires sont automatiquement chargés pour prendre en charge le scénario des fonctionnalités. (Nous avons l’intention de réduire cette liste de scénarios. ) Pour ces scénarios, Visual Studio charge le ou les projets eux-mêmes ou vous invite à les charger en fonction des besoins.

|Catégorie|Problème|
|-|-|-|
|Test unitaire|Les projets qui ne sont pas actuellement chargés n’apparaissent pas dans la liste des projets de test pour les Assistants « Créer IntelliTest » et « Créer un test unitaire ». </br>Vous devez charger les projets pour lesquels vous souhaitez créer des tests. (Pour ce faire, vous pouvez développer le nœud du projet.)|
|Diagrammes de classes|Si vous créez ou ouvrez un diagramme de classes d’un projet, Visual Studio charge automatiquement les projets qui sont des dépendances directes de ce projet. </br>Si l’ensemble de la solution n’est pas chargé, nous désactivons la validation des artefacts obsolètes référencés par un schéma de validation de dépendances.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Scénarios dans lesquels le chargement de solution allégé charge l’ensemble de la solution 

Pour certaines fonctionnalités, Visual Studio charge automatiquement l’ensemble de la solution pour prendre en charge le scénario. Cette action vous garantit de toujours disposer de toutes les fonctionnalités. Par exemple, certaines opérations TFS peuvent nécessiter que la solution soit chargée dans son intégralité. Pour offrir des fonctionnalités complètes, Visual Studio charge l’ensemble de la solution.

|Catégorie|Scénario|
|-|-|-|
|Commande de contrôle de code source TFS sur le nœud de la solution|Si une commande de contrôle de code source est déclenchée sur le nœud de la solution (dans l’Explorateur de solutions), Visual Studio charge automatiquement l’ensemble de la solution avant d’exécuter la commande.|
|Chargement de projet|Si votre solution contient les projets .NET Core et des projets partagés, Visual Studio charge automatiquement ces projets au moment-même du chargement de la solution initiale. Ces projets ne prennent actuellement pas en charge le mode allégé.|
|Gestionnaire de configuration de la solution|Si vous utilisez le gestionnaire de configuration de la solution ou la génération en tâche de fond, Visual Studio charge automatiquement l’ensemble de la solution pour offrir une expérience complète.|
|Gestionnaire de package NuGet|Si vous ouvrez l’interface utilisateur du Gestionnaire de package NuGet, ou sa console, Visual Studio charge automatiquement l’ensemble de la solution pour offrir une expérience complète.|

## <a name="known-issues"></a>Problèmes connus

Il existe certains scénarios qui peuvent ne pas fonctionner en mode LSL et nécessiter le chargement de projets supplémentaires ou l’ensemble de la solution. Nous nous efforçons activement de traiter ces cas. 

|Catégorie|Problème|Solution de contournement|
|-|-|-|-|
|IntelliSense|Il est possible qu’IntelliSense ne soit pas mis à jour après un changement de configuration (par exemple, lors du passage d’une build Release à une build Debug, et vice versa). L’impact dépend des différences de code liées au changement de configuration.|Rechargez la solution après avoir changé la configuration.|
|Refactorisation des limitations pour les projets C#/VB|Les correctifs du code qui changent les fichiers projet peuvent échouer silencieusement la première fois.|Chargez les projets si vous devez corriger du code dans des fichiers de ces projets. Le mode allégé n’applique pas de correctifs à des projets qui ne sont pas chargés.|
|Découverte de tests unitaires|Les tests détectés sur des projets différés ne s’exécutent pas quand un projet est chargé manuellement.|Régénérez le projet pour redétecter les tests et réexécutez les tests sélectionnés.|
|Live Unit Testing (LUT)|En mode LSL, vous pouvez voir que LUT n’est pas activé. Il n’est pas activé car LUT a besoin de l’un des projets de test pour être chargé.|Chargez un projet de test pour activer Live Unit Testing pour la solution.|
|Recherche Explorateur de solutions|1.    La recherche dans l’Explorateur de solutions en mode LSL n’effectue pas de recherche dans les fichiers et il n’y a pas de résultats de progression (autrement dit, seuls les fichiers sont affichés sous l’arbre de recherche, mais pas les classes, les méthodes, etc.).</br>2.    Tous les fichiers appartenant à un projet sont affichés sous la forme d’une liste plate plutôt que d’une arborescence. Quand les fichiers appartiennent à un dossier d’un projet, nous affichons le chemin relatif du fichier, plutôt que simplement le nom du fichier dans la vue de recherche.</br>Aucun menu contextuel n’est disponible pour les éléments de fichier dans la vue de recherche.|Chargez l’ensemble de la solution en mode non-LSL pour obtenir la recherche dans l’Explorateur de solutions traditionnelle.</br>Vous pouvez également utiliser la recherche dans l’IDE Visual Studio.|
|Explorateur d’objets pour les projets C++|L’Explorateur d’objets affiche les références d’assembly/WinMD uniquement pour les projets chargés.|Chargez les projets pour lesquels vous souhaitez afficher les informations dans l’Explorateur d’objets.|

> [!Note]
> Grâce à nos partenaires, les extensions populaires, notamment Resharper, fonctionnent également bien avec le chargement de solution allégée.

Nous sommes enthousiasmés par les innovations destinées à optimiser les performances de temps de chargement des solutions pour les développeurs. Dans la mesure où il s’agit d’une nouvelle fonctionnalité, nous examinons activement les commentaires des clients et résolvons les problèmes connus. Nous attendons vos commentaires avec impatience. Vous pouvez envoyer un e-mail à l’équipe d’optimisation du chargement de solutions Visual Studio à l’adresse lslsupport@microsoft.com

## <a name="see-also"></a>Voir aussi
[Conseils et astuces pour les performances dans Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)  