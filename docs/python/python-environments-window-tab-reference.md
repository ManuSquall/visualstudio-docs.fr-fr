---
title: "Référence sur la fenêtre Environnements Python – Visual Studio | Microsoft Docs"
description: "Cet article donne des informations sur chacun des onglets qui s’affichent sur la fenêtre Environnements Python dans Visual Studio."
ms.custom: 
ms.date: 03/05/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 13d84eb160b4ba82d4a03d48fe814cb0d92388b0
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="python-environments-window-tabs-reference"></a>Référence sur les onglets de la fenêtre Environnements Python

Pour ouvrir la fenêtre **Environnements Python** :

- Sélectionnez la commande de menu **Affichage > Other Windows (Autres fenêtres) > Environnements Python**.
- Cliquez avec le bouton droit sur le nœud **Environnements Python** d’un projet dans l’Explorateur de solutions, et sélectionnez **Afficher tous les environnements Python**.

Si vous agrandissez suffisamment la fenêtre **Environnements Python**, ces options s’affichent sous forme d’onglets, sans doute plus pratiques à utiliser. Dans un souci de clarté, les onglets de cet article apparaissent dans l’affichage développé.

![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Onglet Vue d’ensemble

Fournit des commandes et des informations de base pour l’environnement :

![Onglet Vue d’ensemble, Environnements Python](media/environments-overview-tab.png)

| Commande | Description |
| --- | --- |
| Make this environment the default for new projects (Définir cet environnement par défaut pour les nouveaux projets) | Définit l’environnement actif, ce qui risque d’interrompre brièvement le fonctionnement de Visual Studio lors du chargement de la base de données IntelliSense. Les environnements avec de nombreux packages peuvent être interrompus pendant plus longtemps. |
| Visit the distributor’s website (Visiter le site web du serveur de distribution) | Dans un navigateur, ouvre l’URL fournie par la distribution Python. Python 3.x, par exemple, accède à python.org. |
| Ouvrir une fenêtre interactive | Ouvre la [fenêtre (REPL) interactive](python-interactive-repl-in-visual-studio.md) pour cet environnement au sein de Visual Studio, en appliquant tous les [scripts de démarrage (voir ci-dessous)](#startup-scripts). |
| Explorer les scripts interactifs | Consultez [Scripts de démarrage](#startup-scripts). |
| Utiliser le mode interactif IPython | Quand cette option est définie, ouvre la fenêtre interactive avec IPython par défaut. Cela permet d’activer les tracés inline ainsi que la syntaxe IPython étendue comme `name?` pour afficher l’aide et `!command` pour les commandes de l’interpréteur de commandes. Cette option est recommandée lors de l’utilisation d’une distribution Anaconda, car elle nécessite des packages supplémentaires. Pour plus d’informations, consultez [Utilisation d’IPython dans la fenêtre interactive](interactive-repl-ipython.md). |
| Ouvrir dans PowerShell | Démarre l’interpréteur dans une fenêtre Commande PowerShell. |
| (Liens du dossier et du programme) | Vous fournissent un accès rapide au dossier d’installation de l’environnement, à l’interpréteur python.exe et à l’interpréteur pythonw.exe. Le premier s’ouvre dans l’Explorateur Windows et les deux autres ouvrent une fenêtre de console. |

### <a name="startup-scripts"></a>Scripts de démarrage

Quand vous utilisez des fenêtres interactives dans votre flux de travail quotidien, vous développez probablement des fonctions d’assistance que vous utilisez régulièrement. Par exemple, vous pouvez créer une fonction qui ouvre une tramedonnées dans Excel, puis enregistrer ce code comme un script de démarrage afin qu’il soit toujours disponible dans la fenêtre interactive.

Les scripts de démarrage contiennent du code que la fenêtre interactive charge et exécute automatiquement, dont les importations, les définitions de fonctions et, littéralement, tout autre élément. Ces scripts sont référencés de deux manières :

1. Quand vous installez un environnement, Visual Studio crée un dossier `Documents\Visual Studio 2017\Python Scripts\<environment>` où &lt;environnement&gt; correspond au nom de l’environnement. Vous pouvez facilement accéder au dossier spécifique à l’environnement avec la commande **Explorer les scripts interactifs**. Quand vous démarrez la fenêtre interactive pour cet environnement, elle charge et exécute tous les fichiers `.py` qui s’y trouvent dans l’ordre alphabétique.

1. Le contrôle **Scripts** dans l’onglet **Outils > Options > Python Tools > Fenêtres interactives** (consultez [Options des fenêtres interactives](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) est destiné à spécifier un dossier supplémentaire pour les scripts de démarrage qui sont chargés et exécutés dans tous les environnements. Toutefois, cette fonctionnalité ne fonctionne pas actuellement.

## <a name="configure-tab"></a>Onglet Configurer

S’il est disponible, il contient les informations décrites dans le tableau ci-dessous. Si cet onglet n’est pas affiché, cela signifie que Visual Studio gère automatiquement toutes les informations.

![Onglet Configurer, Environnements Python](media/environments-configure-tab.png)

| Champ | Description |
| --- | --- |
| **Description** | Le nom à donner à l’environnement. |
| **Prefix path** (Chemin du préfixe) | L’emplacement du dossier de base de l’interpréteur. En indiquant cette valeur et en cliquant sur **Détecter automatiquement**, Visual Studio tente de renseigner les autres champs pour vous. |
| **Interpreter Path** (Chemin d’interpréteur) | Le chemin d’accès à l’interpréteur exécutable, généralement le chemin de préfixe suivi de `python.exe`. |
| **Windowed interpreter** (Interpréteur avec fenêtre) | Le chemin d’accès à l’exécutable autre qu’une console, souvent le chemin de préfixe suivi de `pythonw.exe`. |
| **Chemin d’accès à la bibliothèque**<br/>(s’il est disponible) | Spécifie la racine de la bibliothèque standard, mais cette valeur peut être ignorée si Visual Studio est en mesure de demander un chemin d’accès plus précis à partir de l’interpréteur. |
| **Version du langage** | Sélectionnée à partir du menu déroulant. |
| **Architecture** | Normalement détectée et renseignée automatiquement, sinon, 32 bits ou 64 bits est spécifié. |
| **Path environment variable** (Variable d’environnement de chemin d’accès) | La variable d’environnement que l’interpréteur utilise pour rechercher les chemins de recherche. Visual Studio modifie la valeur de la variable lors du démarrage de Python pour qu’il contienne les chemins de recherche du projet. En général, cette propriété doit être définie sur `PYTHONPATH`, mais certains interpréteurs utilisent une autre valeur. |

## <a name="packages-tab"></a>Onglet packages

*Également appelé « pip » dans les versions antérieures.*

Gère les packages installés dans l’environnement, ce qui vous permet également de rechercher des packages et d’en installer de nouveaux (y compris toutes les dépendances).

Les packages qui sont déjà installés apparaissent avec des contrôles pour mettre à jour (flèche vers le haut) et désinstaller (X dans un cercle) le package :

![Onglet packages, Environnements Python](media/environments-pip-tab-controls.png)

La saisie d’un terme de recherche filtre la liste des packages installés, ainsi que des packages qui peuvent être installés à partir de PyPI.

![Onglet packages, Environnements Python, avec recherche de « num »](media/environments-pip-tab.png)

En outre, vous pouvez entrer directement une commande `pip install` dans la zone de recherche, y compris les indicateurs tels que `--user` ou `--no-deps`.

L’installation d’un package crée des sous-dossiers au sein du dossier `Lib` de l’environnement sur le système de fichiers. Par exemple, si Python 3.6 est installé dans `c:\Python36`, les packages sont installés dans `c:\Python36\Lib` ; si Anaconda 3 est installé dans `c:\Program Files\Anaconda3`, les packages sont installés dans `c:\Program Files\Anaconda3\Lib`.

Dans le dernier cas, étant donné que l’environnement se trouve dans une zone protégée du système de fichiers, `c:\Program Files`, Visual Studio doit exécuter une `pip install` avec élévation de privilèges pour lui permettre de créer des sous-dossiers de package. Quand une élévation est requise, Visual Studio affiche l’invite « Des privilèges d’administrateur peuvent être nécessaires pour installer, mettre à jour ou supprimer des packages pour cet environnement. » :

![Invite d’élévation pour l’installation de packages](media/environments-pip-elevate.png)

**Élever les privilèges maintenant** accorde des privilèges d’administrateur à pip pour une seule opération, pouvant aussi faire l’objet d’une demande d’autorisations du système d’exploitation. En sélectionnant **Continuer sans privilège d’administrateur**, une tentative d’installation du package est effectuée, mais pip échoue en essayant de créer des dossiers avec une sortie telle que « Erreur. Impossible de créer 'C:\Program Files\Anaconda3\Lib\site-packages\png.py' : Autorisation refusée. ».

En sélectionnant **Toujours élever les privilèges pour l’installation et la suppression des packages**, vous empêchez la boîte de dialogue de s’afficher pour l’environnement en question. Pour que la boîte de dialogue s’affiche à nouveau, accédez à **Outils > Options > Python Tools > Général** et sélectionnez le bouton **Réinitialiser toutes les boîtes de dialogue masquées définitivement**.

Dans ce même onglet d’options, vous pouvez également sélectionner **Toujours exécuter pip comme administrateur** pour supprimer la boîte de dialogue pour tous les environnements. Consultez [Options - Onglet Général](python-support-options-and-settings-in-visual-studio.md#general-options).

## <a name="intellisense-tab"></a>Onglet IntelliSense

Affiche l’état actuel de la base de données de saisie semi-automatique IntelliSense :

![Onglet IntelliSense, Environnements Python](media/environments-intellisense-tab.png)

Dans **Visual Studio 2017 version 15.5** et versions précédentes, les saisies semi-automatiques IntelliSense dépendent d’une base de données qui a été compilée pour cette bibliothèque. La génération de la base de données est effectuée en arrière-plan quand une bibliothèque est installée, mais peut prendre du temps et ne pas être terminée lorsque vous démarrez l’écriture de code. **Visual Studio 2017 versions 15.6** et ultérieures utilise une méthode plus rapide pour fournir des saisies semi-automatiques qui ne dépendent pas de la base de données, sauf si vous choisissez spécifiquement de l’activer.

Lorsque Visual Studio détecte un nouvel environnement (ou que vous en ajoutez un), il commence automatiquement à compiler la base de données en analysant les fichiers source de la bibliothèque. Ce processus peut prendre entre une minute et plus d’une heure, selon ce qui est installé. (Anaconda, par exemple, est fourni avec de nombreuses bibliothèques et la compilation de la base de données prend un certain temps). Une fois ce processus terminé, vous obtenez la base de données IntelliSense détaillée et n’avez pas à actualiser une nouvelle fois la base de données (avec le bouton **Refresh DB** (Actualiser base de données)) jusqu’à ce que vous installiez d’autres bibliothèques.

Les bibliothèques pour lesquelles les données n’ont pas été compilées sont marquées d’un **!** ; si la base de données d’un environnement n’est pas complète, un **!** apparaît également en regard de celle-ci dans la liste principale des environnements.

## <a name="see-also"></a>Voir aussi

- [Gestion des environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
