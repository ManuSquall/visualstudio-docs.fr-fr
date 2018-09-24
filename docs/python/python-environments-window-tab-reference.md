---
title: Référence sur la fenêtre Environnements Python
description: Cet article donne des informations sur chacun des onglets qui s’affichent sur la fenêtre Environnements Python dans Visual Studio.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 45a14fb5667d7eb28d4d298731886db662985d17
ms.sourcegitcommit: 9ea4b62163ad6be556e088da1e2a355f31366f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43996075"
---
# <a name="python-environments-window-tabs-reference"></a>Référence sur les onglets de la fenêtre Environnements Python

Pour ouvrir la fenêtre **Environnements Python** :

- Sélectionnez la commande de menu **Affichage** > **Autres fenêtres** > **Environnements Python**.
- Cliquez avec le bouton droit sur le nœud **Environnements Python** d’un projet dans l’**Explorateur de solutions**, puis sélectionnez **Afficher tous les environnements Python**.

Si vous agrandissez suffisamment la fenêtre **Environnements Python**, ces options s’affichent sous forme d’onglets, sans doute plus pratiques à utiliser. Dans un souci de clarté, les onglets de cet article apparaissent dans l’affichage développé.

![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Onglet Vue d’ensemble

Fournit des commandes et des informations de base pour l’environnement :

![Onglet Vue d’ensemble, Environnements Python](media/environments-overview-tab.png)

| Commande | Description |
| --- | --- |
| **Définir cet environnement par défaut pour les nouveaux projets** | Définit l’environnement actif, ce qui risque d’interrompre brièvement le fonctionnement de Visual Studio (2017 version 15.5 et antérieure) pendant le chargement de la base de données IntelliSense. Les environnements avec de nombreux packages peuvent être interrompus pendant plus longtemps. |
| **Visiter le site web du distributeur** | Dans un navigateur, ouvre l’URL fournie par la distribution Python. Python 3.x, par exemple, accède à python.org. |
| **Ouvrir une fenêtre interactive** | Ouvre la [fenêtre (REPL) interactive](python-interactive-repl-in-visual-studio.md) pour cet environnement au sein de Visual Studio, en appliquant tous les [scripts de démarrage (voir ci-dessous)](#startup-scripts). |
| **Explorer les scripts interactifs** | Consultez [Scripts de démarrage](#startup-scripts). |
| **Utiliser le mode interactif IPython** | Quand cette option est définie, ouvre la fenêtre **Interactive** avec IPython par défaut. Cela permet d’activer les tracés inline, ainsi que la syntaxe IPython étendue telle que `name?`pour afficher l’aide, et `!command` pour les commandes de l’interpréteur de commandes. Cette option est recommandée lors de l’utilisation d’une distribution Anaconda, car elle nécessite des packages supplémentaires. Pour plus d’informations, consultez [Utiliser IPython dans la fenêtre interactive](interactive-repl-ipython.md). |
| **Ouvrir dans PowerShell** | Démarre l’interpréteur dans une fenêtre Commande PowerShell. |
| (Liens du dossier et du programme) | Vous fournissent un accès rapide au dossier d’installation de l’environnement, à l’interpréteur *python.exe* et à l’interpréteur *pythonw.exe*. Le premier s’ouvre dans l’Explorateur Windows et les deux autres ouvrent une fenêtre de console. |

### <a name="startup-scripts"></a>Scripts de démarrage

Quand vous utilisez des fenêtres interactives dans votre flux de travail quotidien, vous développez probablement des fonctions d’assistance que vous utilisez régulièrement. Par exemple, vous pouvez créer une fonction qui ouvre un DataFrame dans Excel, puis vous pouvez enregistrer ce code en tant que script de démarrage pour qu’il soit toujours disponible dans la fenêtre **Interactive**.

Les scripts de démarrage contiennent du code que la fenêtre **Interactive** charge et exécute automatiquement, notamment les importations, les définitions de fonctions et, littéralement, tout autre élément. Ces scripts sont référencés de deux manières :

1. Quand vous installez un environnement, Visual Studio crée un dossier *Documents\Visual Studio 2017\Python Scripts\\\<environnement>* où &lt;environnement&gt; correspond au nom de l’environnement. Vous pouvez facilement accéder au dossier spécifique à l’environnement avec la commande **Explorer les scripts interactifs**. Quand vous démarrez la fenêtre **Interactive** pour cet environnement, elle charge et exécute tous les fichiers *.py* qui s’y trouvent dans l’ordre alphabétique.

1. Le contrôle **Scripts** sous l’onglet **Outils** > **Options** > **Python Tools** > **Fenêtres interactives** (consultez [Options des fenêtres interactives](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) est destiné à spécifier un dossier supplémentaire pour les scripts de démarrage qui sont chargés et exécutés dans tous les environnements. Toutefois, cette fonctionnalité ne fonctionne pas actuellement.

## <a name="configure-tab"></a>Onglet Configurer

S’il est disponible, il contient les informations décrites dans le tableau ci-dessous. Si cet onglet n’est pas affiché, cela signifie que Visual Studio gère automatiquement toutes les informations.

![Onglet Configurer, Environnements Python](media/environments-configure-tab.png)

| Champ | Description |
| --- | --- |
| **Description** | Le nom à donner à l’environnement. |
| **Prefix path** (Chemin du préfixe) | L’emplacement du dossier de base de l’interpréteur. En indiquant cette valeur et en cliquant sur **Détecter automatiquement**, Visual Studio tente de renseigner les autres champs pour vous. |
| **Interpreter Path** (Chemin d’interpréteur) | Chemin de l’exécutable de l’interpréteur. En règle générale, il s’agit du chemin de préfixe suivi de **python.exe** |
| **Windowed interpreter** (Interpréteur avec fenêtre) | Chemin de l’exécutable qui n’est pas celui de la console. Bien souvent, il s’agit du chemin de préfixe suivi de **pythonw.exe**. |
| **Chemin d’accès à la bibliothèque**<br/>(s’il est disponible) | Spécifie la racine de la bibliothèque standard, mais cette valeur peut être ignorée si Visual Studio est en mesure de demander un chemin d’accès plus précis à partir de l’interpréteur. |
| **Version du langage** | Sélectionnée à partir du menu déroulant. |
| **Architecture** | Normalement détectée et renseignée automatiquement, sinon **32 bits** ou **64 bits** est spécifié. |
| **Path environment variable** (Variable d’environnement de chemin d’accès) | La variable d’environnement que l’interpréteur utilise pour rechercher les chemins de recherche. Visual Studio modifie la valeur de la variable lors du démarrage de Python pour qu’il contienne les chemins de recherche du projet. En général, cette propriété doit avoir la valeur **PYTHONPATH**, mais certains interpréteurs utilisent une autre valeur. |

## <a name="packages-tab"></a>Onglet packages

*Également appelé « pip » dans les versions antérieures.*

Gère les packages installés dans l’environnement à l’aide de pip, ce qui vous permet également de rechercher des packages et d’en installer de nouveaux (y compris toutes les dépendances). Dans Visual Studio 2017 versions 15.7 et ultérieures, un onglet **Packages (Conda)** s’affiche et utilise le gestionnaire de package conda à la place. (Si vous ne voyez pas ce choix, définissez l’option **Outils** > **Options** > **Python** > **Expérimental** > **Utiliser le Gestionnaire de package Conda si disponible (au lieu de Pip)** et redémarrez Visual Studio.)

Les packages qui sont déjà installés apparaissent avec des contrôles pour mettre à jour (flèche vers le haut) et désinstaller (X dans un cercle) le package :

![Onglet packages, Environnements Python](media/environments-pip-tab-controls.png)

La saisie d’un terme de recherche filtre la liste des packages installés, ainsi que des packages qui peuvent être installés à partir de PyPI.

![Onglet packages, Environnements Python, avec recherche de « num »](media/environments-pip-tab.png)

Comme vous pouvez le voir dans l’image ci-dessus, les résultats de la recherche affichent plusieurs packages qui correspondent au terme de recherche. Toutefois, la première entrée de la liste est une commande qui permet d’exécuter **pip install \<nom>** directement. Si vous êtes sous l’onglet **Packages (Conda)**, vous voyez plutôt **conda install \<nom>**  :

![Onglet de packages Conda montrant une commande d’installation conda](media/environments-conda-tab-install.png)

Dans les deux cas, vous pouvez personnaliser l’installation en ajoutant des arguments dans la zone de recherche après le nom du package. Quand vous incluez des arguments, les résultats de la recherche affichent **pip install** ou **conda install** suivi du contenu de la zone de recherche :

![Utilisation d’arguments avec les commandes d’installation pip et conda](media/environments-pip-tab-arguments.png)

L’installation d’un package crée des sous-dossiers dans le dossier *Lib* de l’environnement sur le système de fichiers. Par exemple, si Python 3.6 est installé dans *c:\Python36*, les packages sont installés dans *c:\Python36\Lib*. Si Anaconda3 est installé dans *c:\Program Files\Anaconda3*, les packages sont installés dans *c:\Program Files\Anaconda3\Lib*.

### <a name="grant-administrator-privileges-for-package-install"></a>Octroyer des privilèges d’administrateur pour l’installation des packages

Au moment d’installer des packages dans un environnement situé dans une zone protégée du système de fichiers, par exemple *c:\Program Files\Anaconda3\Lib*, Visual Studio doit exécuter `pip install` avec une élévation de privilèges pour lui permettre de créer des sous-dossiers de package. Quand une élévation est nécessaire, Visual Studio affiche l’invite **Des privilèges d’administrateur peuvent être nécessaires pour installer, mettre à jour ou supprimer des packages pour cet environnement** :

![Invite d’élévation pour l’installation de packages](media/environments-pip-elevate.png)

**Élever les privilèges maintenant** accorde des privilèges d’administrateur à pip pour une seule opération, pouvant aussi faire l’objet d’une demande d’autorisations du système d’exploitation. Quand vous sélectionnez **Continuer sans privilège d’administrateur**, une tentative d’installation du package a lieu, mais pip ne parvient pas à créer de dossiers, et une sortie telle que **Erreur : impossible de créer « C:\Program Files\Anaconda3\Lib\site-packages\png.py » : Autorisation refusée** s’affiche.

En sélectionnant **Toujours élever les privilèges pour l’installation et la suppression des packages**, vous empêchez la boîte de dialogue de s’afficher pour l’environnement en question. Pour que la boîte de dialogue s’affiche à nouveau, accédez à **Outils** > **Options** > **Python Tools** > **Général**, puis sélectionnez le bouton **Réinitialiser toutes les boîtes de dialogue masquées définitivement**.

Sous ce même onglet **Options**, vous pouvez également sélectionner **Toujours exécuter pip comme administrateur** afin de supprimer la boîte de dialogue pour tous les environnements. Consultez [Options - Onglet Général](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Restrictions de sécurité avec les versions antérieures de Python

Quand Python 2.6, 3.1 et 3.2 sont utilisés, Visual Studio affiche un avertissement signalant qu’**en raison des restrictions de sécurité, l’installation à partir d’Internet est susceptible de ne pas fonctionner sur cette version de Python** :

![Message concernant les restrictions d’installation de pip avec l’ancienne version de Python](media/environments-old-version-restriction.png)

La raison de cet avertissement est que dans les versions plus anciennes de Python, `pip install` ne contient pas la prise en charge de la sécurité TLS (Transport Layer Security) 1.2, qui est nécessaire pour télécharger des packages à partir de la source de packages, pypi.org. Les builds Python personnalisées peuvent prendre en charge TLS 1.2, auquel cas `pip install` peut fonctionner.

Il est possible de télécharger le *get-pip.py* approprié pour un package à partir de [bootstrap.pypa.io](https://bootstrap.pypa.io/), de télécharger manuellement un package à partir de [pypi.org](https://pypi.org/), puis d’installer le package à partir de cette copie locale.

La recommandation, toutefois, est d’effectuer simplement une mise à niveau vers Python 2.7 ou 3.3 +, auquel cas l’alerte n’apparaît pas.

## <a name="intellisense-tab"></a>Onglet IntelliSense

Affiche l’état actuel de la base de données de saisie semi-automatique IntelliSense :

![Onglet IntelliSense, Environnements Python](media/environments-intellisense-tab.png)

- Dans **Visual Studio 2017 version 15.5** et versions précédentes, les saisies semi-automatiques IntelliSense dépendent d’une base de données qui a été compilée pour cette bibliothèque. La génération de la base de données est effectuée en arrière-plan quand une bibliothèque est installée, mais peut prendre du temps et ne pas être terminée lorsque vous démarrez l’écriture de code.
- **Visual Studio 2017 versions 15.6** et ultérieures utilise une méthode plus rapide pour fournir des complétions qui ne dépendent pas de la base de données par défaut. Pour cette raison, l’onglet est étiqueté **IntelliSense [base de données désactivée]**. Vous pouvez activer la base de données en désactivant l’option **Outils** > **Options** > **Python** > **Expérimental** > **Utiliser le nouveau style IntelliSense pour les environnements**.

Lorsque Visual Studio détecte un nouvel environnement (ou que vous en ajoutez un), il commence automatiquement à compiler la base de données en analysant les fichiers source de la bibliothèque. Ce processus peut prendre entre une minute et plus d’une heure, selon ce qui est installé. (Anaconda, par exemple, est fourni avec de nombreuses bibliothèques et la compilation de la base de données prend un certain temps). Une fois ce processus terminé, vous obtenez la base de données IntelliSense détaillée et n’avez pas à actualiser une nouvelle fois la base de données (avec le bouton **Refresh DB** (Actualiser base de données)) jusqu’à ce que vous installiez d’autres bibliothèques.

Les bibliothèques pour lesquelles les données n’ont pas été compilées sont marquées d’un **!**  ; si la base de données d’un environnement n’est pas complète, un **!** apparaît également en regard de celle-ci dans la liste principale des environnements.

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
