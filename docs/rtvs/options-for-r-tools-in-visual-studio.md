---
title: Options des Outils R
description: Document de référence pour les options dans Visual Studio pour le langage R et les fonctionnalités associées.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ed2ee29fb7a0a832dd3076cbd47a7f9cd1414d96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939472"
---
# <a name="r-tools-for-visual-studio-options"></a>Options des Outils R dans Visual Studio

Les paramètres sont accessibles par le biais du menu **Outils R**  >   , ou via les   >  **options** outils et en faisant défiler vers **Outils r**:

  ![Boîte de dialogue Options pour les Outils R](media/options-dialog.png)

Les options et paramètres propres à R sont accessibles à l’aide des méthodes ci-dessous. Vous devez cocher la case **Afficher tous les paramètres** située au bas de la boîte de dialogue **Options** pour que toutes ces sections apparaissent.

- Options de mise en forme de code (consultez [Options de l’éditeur](editing-r-code-in-visual-studio.md#editor-options)) : menu **Outils** > **Options**, puis sélectionnez **Éditeur de texte** > **R** > **Mise en forme**
- Options Linter (consultez [Linting](linting-r-code.md)) : menu **Outils** > **Options**, puis sélectionnez **Éditeur de texte** > **R** > **Lint**
- Options avancées de l’éditeur ([décrites dans cet article](#text-editor--r--advanced-options)) : menu **Outils** > **Options**, puis sélectionnez **Éditeur de texte** > **R** > **Avancé**
- Options comportementales ([décrites dans cet article](#r-tools--advanced-options)) : menu **Outils R** > **Options** ou **Outils** > **Options**, puis faites défiler jusqu’à **Outils R**.

La commande **Outils R**  >  **paramètres de science des données** affecte également un certain nombre de paramètres différents dans Visual Studio. Cette commande est décrite dans la section suivante.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Outils R > Paramètres de science des données

L’élément de menu **Outils R > Paramètres de science des données** configure l’IDE de Visual Studio avec une disposition optimisée pour les besoins des scientifiques des données. Plus précisément, cette option ouvre les fenêtres [Interactive](interactive-repl-for-r-in-visual-studio.md), [Explorateur de variables](variable-explorer.md) et [Espaces de travail](r-workspaces-in-visual-studio.md) :

![Disposition de fenêtre pour scientifique des données dans Visual Studio](media/installation-data-scientist-layout-result.png)

Pour revenir ultérieurement à d’autres paramètres de Visual Studio, utilisez d’abord la commande **Outils**  >  **Importer et exporter les paramètres** , sélectionnez **Exporter les paramètres d’environnement sélectionnés** et spécifiez un nom de fichier. Pour restaurer ces paramètres, utilisez la même commande et sélectionnez **Importer les paramètres d'environnement sélectionnés**. Vous pouvez aussi utiliser les mêmes commandes si vous changez la disposition pour les scientifiques des données et que vous souhaitez y revenir plus tard, au lieu d’utiliser directement la commande **Paramètres de science des données**.

## <a name="text-editor--r--advanced-options"></a>Éditeur de texte > R > Options avancées

Ces options contrôlent le comportement de mise en forme, IntelliSense, le mode plan, la mise en retrait et la vérification de syntaxe pour R.

![Boîte de dialogue Options pour les options avancées de l’éditeur de texte R](media/options-dialog-advanced-text-editor.png)

Chaque option est activée ou désactivée pour contrôler le comportement en question. Pour plus d’informations sur ce qui affecte chaque option, consultez le volet d’aide au bas de la boîte de dialogue. Notez que vous pouvez faire glisser le haut de ce volet d’aide pour l’agrandir.

![Volet d’aide développé dans la boîte de dialogue des options avancées de l’éditeur de texte R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Outils R > Options avancées

La   >   commande de menu Outils r permet d’ouvrir la boîte de dialogue **options** pour les options r :

  ![Boîte de dialogue Options pour les Outils R](media/options-dialog.png)

Les sections suivantes décrivent les différentes options disponibles dans cette page.

### <a name="debugging"></a>Débogage

Ces options contrôlent la façon dont les valeurs sont gérées dans l’[Explorateur de variables](variable-explorer.md) et dans les fenêtres du débogueur, comme Espion et Variables locales (consultez [Déboguer le code R](debugging-r-in-visual-studio.md)).

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Évaluer les liaisons actives | `True` | Quand cette option a la valeur `True`, vous voyez toujours la valeur de date la plus à jour lors de l’inspection des variables et des propriétés. Le risque est que l’évaluation des expressions peut avoir des effets secondaires, selon la façon dont elles ont été implémentées. |
| Afficher les variables préfixées par un point | `False` | Indique si les variables précédées de `.` sont affichées. |

### <a name="grid-view"></a>Affichage Grille

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Évaluation dynamique | `False` | Par défaut, la fonction `View(<expression>)` prend un instantané des données sous forme de cadre de données, ce qui peut consommer beaucoup de mémoire avec des jeux de données volumineux. La valeur `True` de cette option signifie que l’expression est évaluée lorsque la grille s’actualise pour extraire uniquement les données qui sont affichées. Toutefois, si l’expression change, les données changent également, ce qui peut ne pas convenir aux expressions dplyr pip. |

### <a name="help"></a>Aide

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Navigateur web (F1) | `Internal` | Contrôle l’affichage de l’aide lorsque vous recherchez un terme à l’aide de la **touche Ctrl** + **F1**. Quand cette option a la valeur `Internal`, l’aide est affichée dans une fenêtre d’outil dans Visual Studio. Quand elle a la valeur `External`, l’aide est affichée dans votre navigateur par défaut. |
| Chaîne de recherche web (F1) | `R site:stackoverflow.com` | Contrôle la façon dont les termes de recherche sont transmis à votre moteur de recherche lorsque vous appuyez sur **CTRL** + **F1** sur un terme dans l’éditeur. Par défaut, la chaîne est `R site:stackoverflow.com`, ce qui ajoute `R` à votre terme de recherche. `site:stackoverflow.com` est une directive destinée au moteur de recherche qui lui indique de limiter la recherche aux pages du domaine `stackoverflow.com`. |
| Navigateur de l’aide R | `Automatic` | Contrôle comment l’aide s’affiche quand vous effectuez une recherche dans la documentation de R en utilisant **F1**, **?** ou **??**. Quand cette option a la valeur `Automatic`, l’aide s’affiche dans la fenêtre appropriée. Par exemple, l’aide HTML s’affiche dans une fenêtre d’outil Visual Studio, tandis que les fichiers PDF s’affichent dans votre programme PDF par défaut. Quand elle a la valeur `External`, l’aide s’affiche dans le navigateur web par défaut. |

### <a name="history"></a>Historique

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Toujours enregistrer l’historique | `True` | Détermine si RTVS écrit votre historique des commandes dans un fichier *.RHistory* dans votre répertoire de travail chaque fois que le projet est fermé. L’enregistrement de l’historique se produit même si vous n’enregistrez pas votre projet avant de quitter. |
| Réinitialiser le filtre de recherche | `True` | Détermine si la fenêtre Historique peut filtrer votre historique des commandes pour afficher uniquement les commandes qui correspondent au terme du filtre dans la boîte de dialogue Historique R. Ce paramètre détermine s’il faut réinitialiser votre filtre de recherche de l’historique chaque fois que vous exécutez une nouvelle commande ou que vous basculez vers un nouveau projet, ce qui déclenche le chargement d’un autre fichier *.RHistory*. Le paramètre par défaut `True` évite d’être surpris quand vous exécutez une commande avec un filtre défini et que vous vous demandez pourquoi la commande que vous venez d’exécuter n’apparaît pas dans l’historique. |
| Utiliser la sélection multiligne | `True` | Spécifie si vous pouvez sélectionner une instruction sur plusieurs lignes dans l’historique avec un seul clic. Autorise également la navigation avec les flèches Haut/Bas dans les fenêtres Interactive par instructions plutôt que par lignes. |

### <a name="html"></a>HTML

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Navigateur de pages HTML | `External` | Détermine où est affiché le contenu tel qu’un tracé `ggvis` ou une application `shiny`. `Internal` affiche la sortie HTML dans une fenêtre d’outil dans Visual Studio. `External` affiche la sortie HTML dans votre navigateur par défaut. |

### <a name="logging"></a>Journalisation

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Événements du journal | `Normal` | Contrôle le niveau de détail de la journalisation pour les diagnostics RTV. Le paramètre par défaut `Normal` crée un fichier journal dans votre répertoire `TEMP`. Quand cette option a la valeur `Traffic`, RTVS enregistre toutes les commandes et les réponses dans votre session. Ces fichiers journaux ne quittent jamais votre ordinateur, mais ils peuvent être utiles pour diagnostiquer des problèmes dans RTVS. |

### <a name="markdown"></a>Markdown

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Navigateur d’aperçu Markdown | `External` | Détermine où est affichée la sortie HTML RMarkdown. `Internal` affiche le document HTML RMarkdown dans une fenêtre d’outil dans Visual Studio. `External` affiche le HTML RMarkdown à l’aide de votre navigateur par défaut. |

### <a name="r-engine"></a>Moteur R

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Page de codes | `(OS Default)` | Définit la page de codes (paramètres régionaux) pour R. Par défaut, les paramètres régionaux sous-jacents du système d’exploitation sont utilisés. |
| Miroir CRAN | `(Use .Rprofile)` | Définit la mise en miroir CRAN par défaut pour les installations de packages. Le paramètre par défaut `Use .Rprofile` respecte les paramètres de miroir CRAN dans votre fichier *.RProfile*. |

### <a name="workspace"></a>Espace de travail

| Option | Valeur par défaut | Description |
| --- | --- | --- |
| Charger l’espace de travail à l’ouverture du projet | `No` | `Yes` active le chargement des données de session à partir du fichier *.RData* dans l’environnement global à l’ouverture du projet. |
| Demander l’enregistrement de l’espace de travail en cas de réinitialisation | `Yes` | `No` désactive l’invite d’enregistrement de votre espace de travail quand vous cliquez sur le bouton Réinitialiser dans la fenêtre Interactive. |
| Enregistrer l’espace de travail à la fermeture du projet | `No` | `Yes` active l’enregistrement de l’environnement global dans le fichier *.RData* à la fermeture du projet. |
| Afficher la boîte de dialogue de confirmation avant de changer d’espace de travail | `Yes` | `No` désactive l’invite de confirmation lors du basculement entre différents espaces de travail. Voir [Basculer entre les espaces de travail](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Afficher l’indicateur de charge de l’ordinateur | `False` | Contrôle la visibilité de l’indicateur de la charge processeur/mémoire/réseau dans la barre d’état. Étant donné que l’indicateur génère du trafic réseau, il s’avère utile de conserver ce `False` dans les scénarios de limitation à distance. La modification de cette option vous oblige à redémarrer Visual Studio. |
