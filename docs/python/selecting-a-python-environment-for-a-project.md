---
title: Sélectionner un environnement et un interpréteur Python pour un projet
description: Guide pratique pour attribuer l’environnement Python à utiliser pour un projet Visual Studio, ainsi que des instructions sur la création d’environnements virtuels.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e738eb52ce8cb7cef4090dd9812f6c421a7d11fd
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101132"
---
# <a name="how-to-assign-which-python-environment-is-used-for-a-project"></a>Guide pratique pour attribuer l’environnement Python à utiliser pour un projet

Tout le code d’un projet Python s’exécute dans le contexte d’un environnement précis. Visual Studio utilise également cet environnement pour le débogage, l’importation et les saisies semi-automatiques de membres, la vérification syntaxique et les autres tâches qui nécessitent un environnement.

Tous les nouveaux projets Python dans Visual Studio sont initialement configurés pour utiliser l’environnement global par défaut, qui s’affiche sous le nœud **Environnements Python** dans l’**Explorateur de solutions** :

![Environnement Python global par défaut indiqué dans l’Explorateur de solutions](media/environments-project.png)

Pour changer l’environnement d’un projet, cliquez avec le bouton droit sur le nœud **Environnements Python**, puis sélectionnez **Ajouter/Supprimer des environnements Python**. Dans la liste affichée, qui inclut les environnements de type global, virtuel et conda, sélectionnez tous ceux que vous souhaitez voir apparaître sous le nœud **Environnements Python** :

![Boîte de dialogue Ajouter/supprimer des environnements Python](media/environments-add-remove.png)

Une fois que vous avez sélectionné **OK**, tous les environnements sélectionnés apparaissent sous le nœud **Environnements Python**. L’environnement actuellement activé apparaît en gras :

![Plusieurs environnements Python qui s’affichent dans l’Explorateur de solutions](media/environments-project-multiple.png)

Pour activer rapidement un autre environnement, cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**. Votre choix sera enregistré avec le projet, et cet environnement sera activé chaque fois que vous ouvrirez le projet. Si vous désactivez toutes les options de la boîte de dialogue **Ajouter/supprimer des environnements Python**, Visual Studio active l’environnement global par défaut.

Le menu contextuel sur le nœud **Environnements Python** propose également des commandes supplémentaires :

| Commande | Description |
| --- | --- |
| **Ajouter un environnement virtuel** | Commence le processus de création d’un environnement virtuel dans le projet. Voir [Créer un environnement virtuel](#create-a-virtual-environment). |
| **Ajouter un environnement virtuel existant** | Vous invite à sélectionner un dossier contenant un environnement virtuel et l’ajoute à la liste sous **Environnements Python**, mais ne l’active pas. Consultez [Activer un environnement virtuel existant](#activate-an-existing-virtual-environment). |
| **Créer un environnement Conda** | Bascule vers la **fenêtre** *Environnements Python*, dans laquelle vous pouvez entrer un nom pour l’environnement et spécifier son interpréteur de base. |

## <a name="use-virtual-environments"></a>Utiliser des environnements virtuels

Un environnement virtuel est une combinaison unique entre un interpréteur Python donné et un ensemble précis de bibliothèques, qui diffère des autres environnements globaux et conda. Un environnement virtuel est spécifique à un projet et conservé dans un dossier de projet. Ce dossier contient les bibliothèques installées de l’environnement, ainsi qu’un fichier *pyvenv.cfg* qui spécifie le chemin de l’*interpréteur de base* de l’environnement, ailleurs sur le système de fichiers. (Autrement dit, un environnement virtuel ne contient pas de copie de l’interpréteur, mais uniquement un lien vers celui-ci.) 

Un des avantages de l’utilisation d’un environnement virtuel est qu’au fur et à mesure du développement du projet, l’environnement virtuel reflète toujours les dépendances exactes du projet. (En revanche, un environnement global partagé contient un certain nombre de bibliothèques, que vous les utilisiez ou non dans votre projet.) Vous pouvez donc facilement créer un fichier *requirements.txt* à partir de l’environnement virtuel, lequel est ensuite utilisé pour réinstaller ces dépendances sur un autre ordinateur de développement ou de production. Pour plus d’informations, consultez [Gérer les packages requis avec requirements.txt](managing-required-packages-with-requirements-txt.md).

Quand vous ouvrez un projet contenant un fichier *requirements.txt* dans Visual Studio, ce dernier vous propose automatiquement de recréer l’environnement virtuel. Sur les ordinateurs où Visual Studio n’est pas installé, vous pouvez utiliser `pip install -r requirements.txt` pour restaurer les packages.

Comme un environnement virtuel contient le chemin codé en dur de l’interpréteur de base, et que vous pouvez recréer l’environnement à l’aide de *requirements.txt*, vous omettez généralement l’ensemble du dossier de l’environnement virtuel à partir du contrôle de code source.

Les sections suivantes expliquent comment activer un environnement virtuel existant dans un projet et comment créer un environnement virtuel.

Dans Visual Studio, un environnement virtuel peut, comme n’importe quel autre environnement, être activé pour un projet via le nœud **Environnements Python** dans **l’Explorateur de solutions**.

Une fois qu’un environnement virtuel est ajouté à votre projet, il apparaît dans la fenêtre **Environnements Python**. Vous pouvez ensuite l’activer, comme tout autre environnement, et vous pouvez gérer ses packages.

### <a name="create-a-virtual-environment"></a>Créer un environnement virtuel

Vous pouvez créer un nouvel environnement virtuel directement sur Visual Studio de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’**Explorateur de solutions**, puis sélectionnez **Ajouter un environnement virtuel**, ce qui entraîne l’affichage de la boîte de dialogue suivante :

    ![Création d’un environnement virtuel](media/environments-add-virtual-1.png)

1. Dans le champ **Emplacement de l’environnement virtuel**, spécifiez un chemin d’accès pour l’environnement virtuel. Si vous n’indiquez qu’un nom, l’environnement virtuel sera créé dans le projet actuel, dans un sous-dossier portant ce nom.

1. Sélectionnez un environnement comme interpréteur de base et cliquez sur **Créer**. Visual Studio affiche une barre de progression pendant qu’il configure l’environnement et télécharge les packages nécessaires. À ce stade, l’environnement virtuel apparaît dans la fenêtre **Environnements Python** du projet auquel il appartient.

1. L’environnement virtuel n’est pas activé par défaut. Pour l’activer pour le projet, cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.

> [!Note]
> Si le chemin d’emplacement identifie un environnement virtuel existant, Visual Studio détecte automatiquement l’interpréteur de base (à l’aide du fichier *orig-prefix.txt* situé dans le répertoire *lib* de l’environnement), puis remplace le bouton **Créer** par **Ajouter**.
>
> Si un fichier *requirements.txt* existe au moment de l’ajout d’un environnement virtuel, la boîte de dialogue **Ajouter un environnement virtuel** affiche une option qui permet d’installer les packages automatiquement, et donc de recréer un environnement sur un autre ordinateur en toute simplicité :
>
> ![Créer un environnement virtuel avec requirements.txt](media/environments-requirements-txt.png)
>
> Dans les deux cas, le résultat est le même qu’avec la commande **Ajouter un environnement virtuel existant**.

### <a name="activate-an-existing-virtual-environment"></a>Activer un environnement virtuel existant

Si vous avez déjà créé un environnement virtuel ailleurs, vous pouvez l’activer pour un projet de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’**Explorateur de solutions**, puis sélectionnez **Ajouter un environnement virtuel existant**.

1. Dans la boîte de dialogue **Parcourir** qui s’affiche, accédez au dossier contenant l’environnement virtuel, sélectionnez-le, puis cliquez sur **OK**. Si Visual Studio détecte un fichier *requirements.txt* dans cet environnement, il vous demande si vous souhaitez installer ces packages.

1. Après quelques instants, l’environnement virtuel apparaît sous le nœud **Environnements Python** dans l’**Explorateur de solutions**. Il n’est pas activé par défaut : cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.

### <a name="remove-a-virtual-environment"></a>Retirer un environnement virtuel

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur l’environnement virtuel, puis sélectionnez **Supprimer**.

1. Visual Studio demande s’il faut retirer ou supprimer l’environnement virtuel. L’action **Retirer** le rend inaccessible au projet, mais elle le laisse sur le système de fichiers. L’action **Supprimer** retire l’environnement du projet et le supprime du système de fichiers. L’interpréteur de base n’est pas affecté.

## <a name="view-installed-packages"></a>Afficher les packages installés

Dans l’Explorateur de solutions, développez le nœud d’un environnement donné pour afficher rapidement les packages qui y sont installés (que vous pouvez donc importer et utiliser dans votre code lorsque l’environnement est actif) :

![Packages Python pour un environnement dans l’Explorateur de solutions](media/environments-installed-packages.png)

Pour installer de nouveaux packages, cliquez avec le bouton droit sur l’environnement, puis sélectionnez **Installer un package Python** pour passer à l’onglet **Packages** de la fenêtre **Environnements Python**. Entrez un critère recherche (en général, le nom de package) : Visual Studio affichera les packages correspondants.

Dans Visual Studio, les packages (et les dépendances) sont téléchargés à partir de [Python Package Index (PyPI)](https://pypi.org), où vous pouvez également rechercher les packages disponibles. La barre d’état et la fenêtre Sortie de Visual Studio affichent des informations sur l’installation. Pour désinstaller un package, cliquez avec le bouton droit sur celui-ci, puis sélectionnez **Supprimer**.

Sachez que les entrées affichées ne sont pas toujours exactes, et que l’installation et la désinstallation ne sont pas forcément fiables ou disponibles. Visual Studio utilise le gestionnaire de packages pip s’il est disponible, et le télécharge et l’installe si besoin. Visual Studio peut également utiliser le gestionnaire de packages easy_install. Les packages installés en ligne de commande avec `pip` ou `easy_install` s’affichent également.

Sachez également que Visual Studio ne prend pas en charge pour le moment l’utilisation de `conda` pour installer des packages dans un environnement conda. Utilisez plutôt `conda` en ligne de commande.

> [!Tip]
> Il est courant que pip ne parvienne pas à installer un package quand celui-ci inclut du code source pour les composants natifs dans les fichiers *\*.pyd*. Si la version requise de Visual Studio n’est pas installée, pip n’est pas en mesure de compiler ces composants. Le message d’erreur affiché dans ce cas est **erreur : vcvarsall.bat est introuvable**. `easy_install` est souvent capable de télécharger des binaires précompilés, et vous pouvez télécharger un compilateur approprié pour les versions antérieures de Python à partir de [https://aka.ms/VCPython27](https://aka.ms/VCPython27). Pour plus d’informations, consultez le billet [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Comment gérer l’erreur « unable to find vcvarsallbat ») sur le blog de l’équipe Python Tools.

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)
