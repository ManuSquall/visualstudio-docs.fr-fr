---
title: Options et paramètres pour Python
description: Document de référence pour les différents paramètres dans Visual Studio concernant des projets et du code Python.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 33c519d737f510e3c987d791e420f1bd6c2d39d2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117756"
---
# <a name="options-for-python-in-visual-studio"></a>Options pour Python dans Visual Studio

Pour afficher les options pour Python, utilisez la commande de menu **Outils > Options**, vérifiez que la case **Afficher tous les paramètres** est cochée, puis accédez à **Python Tools** :

![Boîte de dialogue Options pour Python, onglet Général](media/options-general.png)

Il existe également des options supplémentaires spécifiques à Python dans l’onglet **Éditeur de texte > Python > Avancé** et dans l’onglet **Environnement > Polices et couleurs** au sein du groupe « Éditeur de texte ».

> [!Note]
> Le groupe **Expérimental** contient des options pour des fonctionnalités encore en cours de développement qui ne sont pas décrites ici. Celles-ci sont souvent décrites dans les posts du [blog sur l’ingénierie Python chez Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="general-options"></a>Options générales

(Onglet **Outils > Options > Python**.)

| Option | Par défaut | Description |
| --- | --- | --- |
| Afficher la fenêtre Sortie pendant la création d’environnements virtuels| Activé | Désactivez-la pour empêcher la fenêtre Sortie de s’afficher. |
| Afficher la fenêtre Sortie pendant l’installation ou la suppression des packages | Activé | Désactivez-la pour empêcher la fenêtre Sortie de s’afficher. |
| Toujours exécuter pip comme administrateur | Off | Élève toujours les privilèges des opérations `pip install` pour tous les environnements. Lors de l’installation des packages, Visual Studio vous invite à entrer des privilèges d’administrateur si l’environnement se trouve dans une zone protégée du système de fichiers, par exemple `c:\Program Files`. Dans cette invite, vous pouvez choisir de toujours élever les privilèges de `pip install` pour cet environnement uniquement. Consultez [l’onglet packages](python-environments-window-tab-reference.md#packages-tab). |
| Générer automatiquement la base de données de saisie semi-automatique à la première utilisation | Activé | *S’applique à Visual Studio 2017 version 15.5, versions antérieures et versions ultérieures lorsque vous utilisez une base de données IntelliSense.* Donne la priorité à l’achèvement de la base de données pour une bibliothèque quand vous écrivez du code qui l’utilise. Pour plus d’informations, consultez [Référence sur la fenêtre Environnements - onglet Intellisense](python-environments-window-tab-reference.md). |
| Ignorer les variables PYTHONPATH à l’échelle du système | Activé | PYTHONPATH est ignoré par défaut, car Visual Studio fournit un moyen plus direct de spécifier des chemins de recherche dans les projets et environnements. Consultez la page [Chemins de recherche](search-paths.md) pour plus d’informations. |
| Mettre à jour les chemins de recherche lors de l’ajout de fichiers liés | Activé | Quand cette option est définie, l’ajout d’un [fichier lié](managing-python-projects-in-visual-studio.md#linked-files) à un projet met à jour les [Chemins de recherche](search-paths.md) afin qu’IntelliSense puisse inclure le contenu du dossier du fichier lié dans sa base de données de saisie semi-automatique. Désactivez cette option pour exclure ce contenu de la base de données de saisie semi-automatique. |
| Avertir quand le module importé est introuvable | Activé | Désactivez cette option pour supprimer les avertissements quand vous savez qu’un module importé n’est actuellement pas disponible, mais n’affecte pas par ailleurs le fonctionnement du code. |
| Signaler une indentation incohérente comme | Avertissements | Comme l’interpréteur Python dépend fortement d’une mise en retrait appropriée pour déterminer la portée, Visual Studio émet par défaut des avertissements quand il détecte des mises en retrait incohérentes pouvant indiquer des erreurs de codage. Option définie sur *Erreurs* pour être encore plus stricte, ce qui entraîne la fermeture du programme dans ces cas. Pour désactiver complètement ce comportement, sélectionnez *Ne pas le faire*. |
| Rechercher une étude/actualité | Une fois par semaine | Définit la fréquence à laquelle vous permettez à Visual Studio d’ouvrir une fenêtre contenant une page web avec des nouveautés et des études liées à Python, le cas échéant. Les options sont *Jamais*, *Une fois par jour*, *Une fois par semaine* et *Une fois par mois*. |
| Réinitialiser toutes les boîtes de dialogue masquées définitivement (bouton) | N/A | Différentes boîtes de dialogue fournissent des options telles que **Ne plus afficher ce message**. Utilisez ce bouton pour effacer ces options et entraîner le retour des boîtes de dialogue. |

![Boîte de dialogue Options pour Python, onglet Général](media/options-general.png)

## <a name="debugging-options"></a>Options de débogage

(Onglet **Outils > Options > Python > Débogage**.)

| Option | Par défaut | Description |
| --- | --- | --- |
| Demander avant d’exécuter en présence d’erreurs | Activé | Quand cette option est définie, vous êtes invité à confirmer que vous souhaitez exécuter le code qui contient des erreurs. Désactivez cette option pour désactiver l’avertissement. |
| Attendre une entrée quand le processus quitte de manière inhabituelle<br/><br/>Attendre une entrée quand le processus quitte de manière habituelle | Activées (toutes deux) | Un programme Python démarré à partir de Visual Studio s’exécute dans sa propre fenêtre de console. Par défaut, la fenêtre attend que vous appuyiez sur une touche avant de se fermer, quelle que soit la façon dont le programme se termine. Pour supprimer cette invite et fermer la fenêtre automatiquement, désactivez l’une de ces options, ou les deux. |
| Sortie du programme Tee dans la fenêtre Sortie du débogage | Activé | Affiche la sortie du programme dans une fenêtre de console distincte et la fenêtre Sortie de Visual Studio. Désactivez cette option pour afficher la sortie uniquement dans la fenêtre de console distincte. |
| Arrêter en cas d’exception SystemExit avec le code de sortie zéro | Off | Si cette option est définie, arrête le débogueur sur cette exception. Quand elle est désactivée, le débogueur se ferme sans s’arrêter. |
| Activer le débogage de la bibliothèque Python standard | Off | Permet d’effectuer un pas à pas détaillé dans le code source de la bibliothèque standard pendant le débogage, mais augmente le temps nécessaire au démarrage du débogueur.|

![Boîte de dialogue Options pour Python, onglet Débogage](media/options-debugging.png)

## <a name="diagnostics-options"></a>Options des diagnostics

(Onglet **Outils > Options > Python > Diagnostics**.)

| Option | Par défaut | Description |
| --- | --- | --- |
| Inclure les journaux d’analyse | Activé | Inclut des journaux détaillés relatifs à l’analyse des environnements Python installés lors de l’enregistrement des diagnostics dans un fichier ou en les copiant dans le Presse-papiers à l’aide des boutons. Cette option peut augmenter considérablement la taille du fichier généré, mais elle est souvent nécessaire pour diagnostiquer les problèmes IntelliSense. |
| Enregistrer les diagnostics dans un fichier (bouton) | N/A | Demande un nom de fichier, puis enregistre le journal dans un fichier texte. |
| Copier les diagnostics dans le Presse-papiers (bouton) | N/A | Copie l’intégralité du journal dans le Presse-papiers ; cette opération peut prendre un certain temps, en fonction de la taille du journal. |

![Boîte de dialogue Options pour Python, onglet Diagnostics](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Options des fenêtres interactives

(Onglet **Outils > Options > Python > Windows Interactive**.)

| Option | Par défaut | Description |
| --- | --- | --- |
| scripts ; | N/A | Spécifie un dossier général pour les scripts de démarrage à appliquer aux fenêtres interactives pour tous les environnements. Consultez [Scripts de démarrage](python-environments-window-tab-reference.md#startup-scripts). Notez, toutefois, que cette fonctionnalité ne fonctionne pas pour l’instant. |
| Les flèches Haut/Bas explorent l’historique | Activé | Utilise les touches de direction pour parcourir l’historique dans la fenêtre interactive. Désactivez ce paramètre pour utiliser les touches de direction afin de naviguer dans la sortie de la fenêtre interactive à la place. |
| Mode de saisie semi-automatique | Évaluer uniquement les expressions sans appel de fonction | Le processus permettant de déterminer les membres disponibles sur une expression dans la fenêtre interactive peut nécessiter l’évaluation de l’expression non terminée actuelle, ce qui peut aboutir à des effets secondaires ou des fonctions appelées à plusieurs reprises. Le paramètre par défaut, *Évaluer uniquement les expressions sans appel de fonction*, exclut les expressions qui apparaissent pour appeler une fonction, mais évalue les autres expressions. Par exemple, il évalue `a.b` mais pas `a().b`.  *Ne jamais évaluer les expressions* empêche tous les effets secondaires, en utilisant uniquement le moteur IntelliSense normal pour obtenir des suggestions. *Évaluer toutes les expressions* évalue l’expression complète pour obtenir des suggestions, indépendamment des effets secondaires. |
| Masquer les suggestions d’analyse statique | Off | Quand cette option est définie, n’affiche que les suggestions obtenues en évaluant l’expression. Associée au mode de saisie semi-automatique *Ne jamais évaluer les expressions*, aucune saisie semi-automatique utile ne s’affiche dans la fenêtre interactive. |

![Boîte de dialogue Options pour Python, onglet Fenêtres interactives](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Options avancées de l’éditeur Python

(Onglet **Outils > Options > Éditeur de texte > Python > Avancé**.)

### <a name="completion-results"></a>Résultats de la saisie semi-automatique

| Option | Par défaut | Description |
| --- | --- | --- |
| La saisie semi-automatique des membres affiche l’intersection des membres | Off | Quand cette option est définie, affiche uniquement les saisies semi-automatiques qui sont prises en charge par tous les types possibles. |
| Liste de filtres basée sur une chaîne de recherche | Activé | Applique le filtrage des suggestions de saisie semi-automatique quand vous tapez (activée par défaut). |
| Afficher automatiquement la saisie semi-automatique pour tous les identificateurs | Activé | Désactivez cette option pour désactiver les saisies semi-automatiques dans l’éditeur et les fenêtres interactives. |

### <a name="selection-in-completion-list"></a>Sélection dans la liste de saisie semi-automatique

| Option | Par défaut | Description |
| --- | --- | --- |
| Validé en tapant les caractères suivants | `{}[]().,:;+-*/%&&#124;^~=<>#@\` | Comme ces caractères suivent généralement un identificateur qui peut être sélectionné dans une liste de saisie semi-automatique, il est pratique de valider la saisie semi-automatique simplement en tapant un caractère. Vous pouvez supprimer ou ajouter des caractères spécifiques dans la liste si vous le souhaitez.  |
| Entrée valide la saisie semi-automatique actuelle | Activé | Quand cette option est définie, la touche Entrée choisit et applique la saisie semi-automatique sélectionnée comme avec les caractères ci-dessus (mais, bien entendu, il n’existe pas de caractère pour la touche Entrée pouvant être intégré directement dans cette liste !). |
| Ajouter une ligne avec entrée après le mot complet tapé | Off | Par défaut, si vous tapez le mot entier qui s’affiche dans la fenêtre contextuelle de saisie semi-automatique et appuyez sur Entrée, vous validez cette saisie. En définissant cette option, vous validez effectivement les saisies semi-automatiques quand vous avez fini de taper l’identificateur, de sorte qu’Entrée insère une nouvelle ligne. |

### <a name="miscellaneous-options"></a>Options diverses

| Option | Par défaut | Description |
| --- | --- | --- |
| Passer en mode Plan à l'ouverture des fichiers | Activé | Activez automatiquement la fonctionnalité de mode Plan de Visual Studio dans l’éditeur lors de l’ouverture d’un fichier de code Python. |
| Le collage supprime les invites REPL | Activé | Supprime >>> et ... du texte collé, ce qui permet de transférer facilement le code de la fenêtre interactive vers l’éditeur. Désactivez cette option si vous devez conserver ces caractères lors du collage à partir d’autres sources. |
| Noms de couleur basés sur les types | Activé | Active les couleurs de syntaxe dans le code Python. |

![Boîte de dialogue Options de l’éditeur Python, onglet Avancé](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Options Polices et couleurs

(Onglet **Environnement > Polices et couleurs** au sein du groupe « Éditeur de texte ».)

Les noms des options Python ont toutes le préfixe « Python » et sont explicites. La police par défaut pour tous les thèmes de couleurs Visual Studio est 10 pt Consolas regular (non gras). Les couleurs par défaut varient selon le thème. En règle générale, vous modifiez une police ou une couleur si vous la lecture du texte est difficile avec les paramètres par défaut.

![Options de police et de couleur Python](media/options-fonts-and-colors.png)