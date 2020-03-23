---
title: Sélectionner un environnement et un interpréteur Python pour un projet
description: Vous pouvez sélectionner un environnement Python, y compris les environnements Anaconda et virtuels, à appliquer à un projet spécifique.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 34ceb2ec7cc923f6642977cf4c70fbfae07bf523
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302727"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Guide pratique pour sélectionner l’environnement Python d’un projet

L’ensemble du code d’un projet Python s’exécute dans le contexte d’un environnement spécifique, par exemple un environnement Python global, un environnement Anaconda, un environnement virtuel ou un environnement conda. Visual Studio utilise également cet environnement pour le débogage, les complétions d’importations et de membres, la vérification syntaxique ainsi que les autres tâches qui nécessitent des services de langage spécifiques à la version de Python et un ensemble de packages installés.

Tous les nouveaux projets Python de Visual Studio sont initialement configurés pour utiliser l’environnement global par défaut, qui apparaît sous le nœud **Python Environments** dans **Solution Explorer**:

![Environnement Python global par défaut indiqué dans l’Explorateur de solutions](media/environments/environments-project.png)

::: moniker range="vs-2017"
Pour modifier l’environnement d’un projet, cliquez à droite sur le nœud **Python Environments** et **sélectionnez Les environnements Add/Remove Python**. Dans la liste affichée, qui inclut les environnements de type global, virtuel et conda, sélectionnez tous ceux que vous souhaitez voir apparaître sous le nœud **Environnements Python** :

![Boîte de dialogue Ajouter/supprimer des environnements Python](media/environments/environments-add-remove.png)

Une fois que vous avez sélectionné **OK**, tous les environnements sélectionnés apparaissent sous le nœud **Environnements Python**. L’environnement actuellement activé apparaît en gras :

![Plusieurs environnements Python qui s’affichent dans l’Explorateur de solutions](media/environments/environments-project-multiple.png)

Pour activer rapidement un autre environnement, cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**. Votre choix sera enregistré avec le projet, et cet environnement sera activé chaque fois que vous ouvrirez le projet. Si vous désactivez toutes les options de la boîte de dialogue **Ajouter/supprimer des environnements Python**, Visual Studio active l’environnement global par défaut.

Le menu contextuel sur le nœud **Environnements Python** propose également des commandes supplémentaires :

| Commande | Description |
| --- | --- |
| **Ajouter un environnement virtuel** | Commence le processus de création d’un environnement virtuel dans le projet. Voir [Créer un environnement virtuel](#create-a-virtual-environment). |
| **Ajouter un environnement virtuel existant** | Vous invite à sélectionner un dossier contenant un environnement virtuel et l’ajoute à la liste sous **Environnements Python**, mais ne l’active pas. Consultez [Activer un environnement virtuel existant](#activate-an-existing-virtual-environment). |
| **Créer un environnement Conda** | Bascule vers la **fenêtre** *Environnements Python*, dans laquelle vous pouvez entrer un nom pour l’environnement et spécifier son interpréteur de base. Consultez [Environnements Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Pour modifier l’environnement pour un projet, cliquez avec le bouton droit sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement**, ou sélectionnez **Ajouter un environnement** dans la liste déroulante d’environnements dans la barre d’outils Python.

Dans la boîte de dialogue **Ajouter un environnement**, sélectionnez l’onglet **Environnement existant**, puis sélectionnez un nouvel environnement dans la liste déroulante **Environnement** :

![Sélection d’un environnement de projet dans la boîte de dialogue Ajouter des environnements](media/environments/environments-project-2019.png)

Si vous déjà ajouté un environnement autre que l’environnement global par défaut à un projet, vous devrez peut-être activer un environnement qui vient d’être ajouté. Cliquez avec le bouton droit sur cet environnement sous le nœud **Environnements Python** et sélectionnez **Activer l’environnement**. Pour supprimer un environnement du projet, sélectionnez **Supprimer**.

![Activation et suppression d’un environnement de projet](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Utiliser des environnements virtuels

Un environnement virtuel est une combinaison unique entre un interpréteur Python donné et un ensemble précis de bibliothèques, qui diffère des autres environnements globaux et conda. Un environnement virtuel est spécifique à un projet et conservé dans un dossier de projet. Ce dossier contient les bibliothèques installées de l’environnement, ainsi qu’un fichier *pyvenv.cfg* qui spécifie le chemin de l’*interpréteur de base* de l’environnement, ailleurs sur le système de fichiers. (Autrement dit, un environnement virtuel ne contient pas de copie de l’interpréteur, mais uniquement un lien vers celui-ci.)

Un des avantages de l’utilisation d’un environnement virtuel est qu’au fur et à mesure du développement du projet, l’environnement virtuel reflète toujours les dépendances exactes du projet. (Un environnement global partagé, d’autre part, contient un certain nombre de bibliothèques si vous les utilisez dans votre projet ou non.) Vous pouvez alors facilement créer un fichier *requirements.txt* à partir de l’environnement virtuel, qui est ensuite utilisé pour réinstaller ces dépendances sur un autre ordinateur de développement ou de production. Pour plus d’informations, consultez [Gérer les packages requis avec requirements.txt](managing-required-packages-with-requirements-txt.md).

Quand vous ouvrez un projet contenant un fichier *requirements.txt* dans Visual Studio, ce dernier vous propose automatiquement de recréer l’environnement virtuel. Sur les ordinateurs où Visual Studio n’est pas installé, vous pouvez utiliser `pip install -r requirements.txt` pour restaurer les packages.

Comme un environnement virtuel contient le chemin codé en dur de l’interpréteur de base, et que vous pouvez recréer l’environnement à l’aide de *requirements.txt*, vous omettez généralement l’ensemble du dossier de l’environnement virtuel à partir du contrôle de code source.

Les sections suivantes expliquent comment activer un environnement virtuel existant dans un projet et comment créer un environnement virtuel.

Dans Visual Studio, un environnement virtuel peut, comme n’importe quel autre environnement, être activé pour un projet via le nœud **Environnements Python** dans **l’Explorateur de solutions**.

Une fois qu’un environnement virtuel est ajouté à votre projet, il apparaît dans la fenêtre **Environnements Python**. Vous pouvez ensuite l’activer, comme tout autre environnement, et vous pouvez gérer ses packages.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Créer un environnement virtuel

Vous pouvez créer un nouvel environnement virtuel directement dans Visual Studio de la façon suivante :

1. Environnements **Python** à clic droit dans **Solution Explorer** et sélectionnez **Ajouter l’environnement virtuel**, qui évoque la boîte de dialogue suivante :

    ![Création d’un environnement virtuel](media/environments/environments-add-virtual-1.png)

1. Dans le champ **Emplacement de l’environnement virtuel**, spécifiez un chemin d’accès pour l’environnement virtuel. Si vous n’indiquez qu’un nom, l’environnement virtuel sera créé dans le projet actuel, dans un sous-dossier portant ce nom.

1. Sélectionnez un environnement comme interpréteur de base et cliquez sur **Créer**. Visual Studio affiche une barre de progression pendant qu’il configure l’environnement et télécharge les packages nécessaires. Lorsque l’opération est terminée, l’environnement virtuel apparaît dans la fenêtre **Environnements Python** du projet auquel il appartient.

1. L’environnement virtuel n’est pas activé par défaut. Pour l’activer pour le projet, cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.

> [!Note]
> Si le chemin d’emplacement identifie un environnement virtuel existant, Visual Studio détecte automatiquement l’interpréteur de base (à l’aide du fichier *orig-prefix.txt* situé dans le répertoire *lib* de l’environnement), puis remplace le bouton **Créer** par **Ajouter**.
>
> Si un fichier *requirements.txt* existe au moment de l’ajout d’un environnement virtuel, la boîte de dialogue **Ajouter un environnement virtuel** affiche une option qui permet d’installer les packages automatiquement, et donc de recréer un environnement sur un autre ordinateur en toute simplicité :
>
> ![Créer un environnement virtuel avec requirements.txt](media/environments/environments-requirements-txt.png)
>
> Quoi qu’il en soit, le résultat est le même que si vous aviez utilisé la commande **Add Existing Virtual Environment.**

### <a name="activate-an-existing-virtual-environment"></a>Activer un environnement virtuel existant

Si vous avez déjà créé un environnement virtuel ailleurs, vous pouvez l’activer pour un projet de la façon suivante :

1. Environnements **Python** à clic droit dans **Solution Explorer** et sélectionnez **Ajouter l’environnement virtuel existant**.

1. Dans le dialogue **Browse** qui apparaît, naviguer et sélectionner le dossier qui contient l’environnement virtuel, et sélectionnez **OK**. Si Visual Studio détecte un fichier *requirements.txt* dans cet environnement, il vous demande si vous souhaitez installer ces packages.

1. Après quelques instants, l’environnement virtuel apparaît sous le nœud **Python Environments** dans **Solution Explorer**. Il n’est pas activé par défaut : cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Créer un environnement virtuel

Vous pouvez créer un nouvel environnement virtuel directement dans Visual Studio de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’**Explorateur de solutions** et sélectionnez **Ajouter un environnement**, ou sélectionnez **Ajouter un environnement** dans la liste déroulante d’environnements dans la barre d’outils Python. Dans la boîte de dialogue **Ajouter un environnement** qui s’affiche, sélectionnez l’onglet **Environnement virtuel** :

    ![Onglet Environnement virtuel de la boîte de dialogue Ajouter un environnement](media/environments/environments-add-virtual-1-2019.png)

1. Spécifiez un nom pour l’environnement virtuel, sélectionnez un interpréteur de base et vérifiez son emplacement. Sous **Installer les packages à partir d’un fichier**, fournissez le chemin d’accès à un fichier *requirements.txt* si vous le souhaitez.

1. Passez en revue les autres options de la boîte de dialogue :

    | Option | Description |
    | --- | --- |
    | Définir en tant qu’environnement actuel | Active le nouvel environnement dans le projet sélectionné lorsque l’environnement est créé. |
    | Définir en tant qu’environnement par défaut pour les nouveaux projets | Définit et active automatiquement l’environnement virtuel dans tous les nouveaux projets créés dans Visual Studio. Lorsque vous utilisez cette option, l’environnement virtuel doit être placé dans un emplacement en dehors d’un projet spécifique.  |
    | Afficher dans la fenêtre Environnements Python | Spécifie l’ouverture ou non de la fenêtre **Environnements Python** après la création de l’environnement. |
    | Rendre cet environnement disponible globalement | Spécifie si l’environnement virtuel joue également un environnement global. Lorsque vous utilisez cette option, l’environnement virtuel doit être placé dans un emplacement en dehors d’un projet spécifique. |

1. Sélectionnez **Créer** pour finaliser l’environnement virtuel. Visual Studio affiche une barre de progression pendant qu’il configure l’environnement et télécharge les packages nécessaires. Lorsque l’opération est terminée, l’environnement virtuel est activé et apparaît sous le nœud **Environnements Python** dans l’**Explorateur de solutions** et dans la fenêtre **Environnements Python** du projet auquel il appartient.

### <a name="activate-an-existing-virtual-environment"></a>Activer un environnement virtuel existant

Si vous avez déjà créé un environnement virtuel ailleurs, vous pouvez l’activer pour un projet de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’**Explorateur de solutions**, puis sélectionnez **Ajouter un environnement**.

1. Dans le dialogue **Browse** qui apparaît, naviguer et sélectionner le dossier qui contient l’environnement virtuel, et sélectionnez **OK**. Si Visual Studio détecte un fichier *requirements.txt* dans cet environnement, il vous demande si vous souhaitez installer ces packages.

1. Après quelques instants, l’environnement virtuel apparaît sous le nœud **Python Environments** dans **Solution Explorer**. Il n’est pas activé par défaut : cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Retirer un environnement virtuel

1. Dans **Solution Explorer**, cliquez à droite sur l’environnement virtuel et **sélectionnez Supprimer**.

1. Visual Studio demande s’il faut retirer ou supprimer l’environnement virtuel. L’action **Retirer** le rend inaccessible au projet, mais elle le laisse sur le système de fichiers. L’action **Supprimer** retire l’environnement du projet et le supprime du système de fichiers. L’interpréteur de base n’est pas affecté.

## <a name="view-installed-packages"></a>Afficher les packages installés

Dans l’Explorateur de solutions, développez le nœud d’un environnement donné pour afficher rapidement les packages qui y sont installés (que vous pouvez donc importer et utiliser dans votre code lorsque l’environnement est actif) :

![Packages Python pour un environnement dans l’Explorateur de solutions](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Pour installer de nouveaux packages, cliquez avec le bouton droit sur l’environnement, puis sélectionnez **Installer un package Python** pour passer à l’onglet **Packages** approprié de la fenêtre **Environnements Python**. Entrez un critère recherche (en général, le nom de package) : Visual Studio affichera les packages correspondants.
::: moniker-end
::: moniker range=">=vs-2019"
Pour installer de nouveaux packages, cliquez avec le bouton droit sur l’environnement, puis sélectionnez **Gérer les packages Python** (ou utilisez le bouton de package dans la barre d’outils Python) pour passer à l’onglet **Packages** approprié de la fenêtre **Environnements Python**. Dans l’onglet **Packages**, entrez un critère de recherche (en général, le nom de package), Visual Studio affiche alors les packages correspondants.
::: moniker-end

Dans Visual Studio, les packages (et les dépendances) de la plupart des environnements sont téléchargés à partir de [Python Package Index (PyPI)](https://pypi.org), où vous pouvez également rechercher les packages disponibles. La barre d’état et la fenêtre Sortie de Visual Studio affichent des informations sur l’installation. Pour désinstaller un package, cliquez avec le bouton droit sur celui-ci, puis sélectionnez **Supprimer**.

Le gestionnaire de package conda utilise généralement `https://repo.continuum.io/pkgs/` comme canal par défaut, mais d’autres canaux est disponibles. Pour plus d’informations, consultez [Gérer les canaux](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Sachez que les entrées affichées ne sont pas toujours exactes, et que l’installation et la désinstallation ne sont pas forcément fiables ou disponibles. Visual Studio utilise le gestionnaire de packages pip s’il est disponible, et le télécharge et l’installe si besoin. Visual Studio peut également utiliser le gestionnaire de packages easy_install. Les packages installés en ligne de commande avec `pip` ou `easy_install` s’affichent également.

Sachez également que Visual Studio ne prend pas en charge pour le moment l’utilisation de `conda` pour installer des packages dans un environnement conda. Utilisez plutôt `conda` en ligne de commande.

> [!Tip]
> Une situation commune où pip ne parvient pas à installer un * \** paquet est lorsque le paquet comprend le code source pour les composants indigènes dans les fichiers .pyd. Si la version requise de Visual Studio n’est pas installée, pip n’est pas en mesure de compiler ces composants. Le message d’erreur affiché dans ce cas est **erreur : vcvarsall.bat est introuvable**. `easy_install`est souvent en mesure de télécharger des binaires pré-compilés, et vous [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)pouvez télécharger un compilateur approprié pour les anciennes versions de Python à partir de . Pour plus d’informations, consultez le billet [How to deal with the pain of "unable to find vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) (Comment gérer l’erreur « unable to find vcvarsallbat ») sur le blog de l’équipe Python Tools.

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Utilisation requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Informations de référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)
