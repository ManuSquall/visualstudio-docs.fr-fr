---
title: "Sélectionner un environnement pour un projet | Microsoft Docs"
description: "L’Explorateur de solutions de Visual Studio permet de choisir l’interpréteur (environnement) Python à utiliser systématiquement pour un projet donné, en ignorant l’environnement par défaut. Vous pouvez également créer et gérer des environnements virtuels."
ms.custom: 
ms.date: 02/20/2018
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
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Sélectionner un environnement et un interpréteur Python à utiliser dans un projet

Tout le code d’un projet Python s’exécute dans le contexte d’un environnement précis. Visual Studio utilise également cet environnement pour le débogage, l’importation et les saisies semi-automatiques de membres, la vérification syntaxique et les autres tâches qui nécessitent un environnement.

Tous les nouveaux projets Python dans Visual Studio sont initialement configurés de façon à utiliser l’environnement global par défaut, qui s’affiche sous le nœud **Environnements Python** dans l’Explorateur de solutions :

![Environnement Python global par défaut indiqué dans l’Explorateur de solutions](media/environments-project.png)

Vous pouvez rendre d’autres environnements accessibles au projet, y compris des environnements virtuels. Il n’est possible d’activer qu’un seul environnement à un moment donné.

## <a name="using-global-environments"></a>Utiliser des environnements globaux

Pour mettre certains environnements globaux à la disposition du projet (y compris des environnements conda [identifiés manuellement](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)), cliquez avec le bouton droit sur le nœud **Environnements Python**, et sélectionnez **Ajouter/supprimer des environnements Python...**. Dans la liste qui s’affiche, sélectionnez les environnements souhaités :

![Boîte de dialogue Ajouter/supprimer des environnements Python](media/environments-add-remove.png)

Cliquez sur **OK** : tous les environnements sélectionnés s’affichent sous le nœud **Environnements Python**. L’environnement actuellement activé apparaît en gras :

![Plusieurs environnements Python qui s’affichent dans l’Explorateur de solutions](media/environments-project-multiple.png)

Pour activer un autre environnement, cliquez sur son nom avec le bouton droit et sélectionnez **Activer l’environnement**. Votre choix sera enregistré avec le projet, et cet environnement sera activé chaque fois que vous ouvrirez le projet.

Si vous désactivez toutes les options de la boîte de dialogue **Ajouter/supprimer des environnements Python**, Visual Studio active l’environnement global par défaut.

## <a name="using-virtual-environments"></a>Utiliser des environnements virtuels

Un environnement virtuel est une combinaison unique entre un interpréteur Python donné et un ensemble précis de bibliothèques, qui diffère des autres environnements globaux et conda. En général, on utilise un environnement virtuel pour répondre à des besoins spécifiques dans un projet sans avoir à modifier d’autres environnements.

Après avoir été ajouté à votre projet, l’environnement virtuel apparaît dans la fenêtre **Environnements Python** et vous pouvez l’activer comme tout autre environnement, ainsi que gérer ses packages.

Notez que les environnements virtuels présentent l’inconvénient de contenir des chemins d’accès aux fichiers codés en dur et sont donc plus difficiles à partager ou à transférer vers d’autres ordinateurs de développement. Heureusement, vous pouvez utiliser le fichier `requirements.txt` pour autoriser les destinataires de votre projet à restaurer l’environnement en toute simplicité. Pour plus d’informations, consultez la page [Gérer les packages requis avec requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="activating-an-existing-virtual-environment"></a>Activer un environnement virtuel existant

Si vous avez déjà créé un environnement virtuel ailleurs, vous pouvez l’activer pour un projet de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions, puis sélectionnez **Ajouter un environnement virtuel existant...**.

1. Dans la boîte de dialogue **Parcourir** qui s’affiche, accédez au dossier contenant l’environnement virtuel, sélectionnez-le et cliquez sur **OK**. Si Visual Studio détecte un fichier `requirements.txt` dans cet environnement, il demande s’il faut installer ces packages.

1. Après quelques instants, l’environnement virtuel apparaît sous le nœud **Environnements Python** de l’Explorateur de solutions. Il n’est pas activé par défaut : cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.

### <a name="creating-a-virtual-environment"></a>Création d’un environnement virtuel

Vous pouvez créer un nouvel environnement virtuel directement sur Visual Studio de la façon suivante :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions, puis sélectionnez **Ajouter un environnement virtuel...** pour afficher la boîte de dialogue suivante :

    ![Création d’un environnement virtuel](media/environments-add-virtual-1.png)

1. Dans le champ **Emplacement de l’environnement virtuel**, spécifiez un chemin d’accès pour l’environnement virtuel. Si vous n’indiquez qu’un nom, l’environnement virtuel sera créé dans le projet actuel, dans un sous-dossier portant ce nom.

1. Sélectionnez un environnement comme interpréteur de base et cliquez sur **Créer**. Visual Studio affiche une barre de progression pendant qu’il configure l’environnement et télécharge les packages nécessaires. L’environnement virtuel apparaît maintenant sur la fenêtre **Environnements Python** du projet auquel il appartient.

1. L’environnement virtuel n’est pas activé par défaut. Pour l’activer pour le projet, cliquez dessus avec le bouton droit et sélectionnez **Activer l’environnement**.

> [!Note]
> Si le chemin d’accès identifie un environnement virtuel existant, Visual Studio détecte automatiquement l’interpréteur de base (à l’aide du fichier `orig-prefix.txt` dans le répertoire `lib` de l’environnement) et remplace le bouton Créer par **Ajouter**.
>
> Si un fichier `requirements.txt` existe lors de l’ajout d’un environnement virtuel, la boîte de dialogue **Ajouter un environnement virtuel** affiche une option permettant d’installer les packages automatiquement, et donc de recréer un environnement sur un autre ordinateur en toute simplicité :
>
> ![Créer un environnement virtuel avec requirements.txt](media/environments-requirements-txt.png)
>
> Dans les deux cas, le résultat est le même qu’avec la commande **Ajouter un environnement virtuel existant...** .

### <a name="remove-a-virtual-environment"></a>Retirer un environnement virtuel

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur l’environnement virtuel et sélectionnez **Retirer**.

1. Visual Studio demande s’il faut retirer ou supprimer l’environnement virtuel. L’action **Retirer** le rend inaccessible au projet, mais elle le laisse sur le système de fichiers. L’action **Supprimer** retire l’environnement du projet et le supprime du système de fichiers. L’interpréteur de base n’est pas affecté.

## <a name="viewing-installed-packages"></a>Afficher les packages installés

Dans l’Explorateur de solutions, développez le nœud d’un environnement donné pour afficher rapidement les packages qui y sont installés (que vous pouvez donc importer et utiliser dans votre code lorsque l’environnement est actif) :

![Packages Python pour un environnement dans l’Explorateur de solutions](media/environments-installed-packages.png)

Pour installer de nouveaux packages, cliquez avec le bouton droit sur l’environnement, puis sélectionnez **Installer un package Python...**  pour basculer vers l’onglet **Packages** sur la fenêtre **Environnements Python**. Entrez un critère recherche (en général, le nom de package) : Visual Studio affichera les packages correspondants.

Dans Visual Studio, les packages (et les dépendances) sont téléchargés à partir de [Python Package Index (PyPI)](https://pypi.python.org/pypi), où vous pouvez également rechercher les packages disponibles. La barre d’état et la fenêtre Sortie de Visual Studio affichent des informations sur l’installation. Pour désinstaller un package, cliquez avec le bouton sur celui-ci et sélectionnez **Supprimer**.

Sachez que les entrées affichées ne sont pas toujours exactes, et que l’installation et la désinstallation ne sont pas forcément fiables ou disponibles. Visual Studio utilise le gestionnaire de packages pip s’il est disponible, et le télécharge et l’installe si besoin. Visual Studio peut également utiliser le gestionnaire de packages easy_install. Les packages installés en ligne de commande avec `pip` ou `easy_install` s’affichent également.

Sachez également que Visual Studio ne prend pas en charge pour le moment l’utilisation de `conda` pour installer des packages dans un environnement conda. Utilisez plutôt `conda` en ligne de commande.

> [!Tip]
> Il est courant que pip ne parvienne pas à installer un package quand celui-ci inclut le code source pour les composants natifs dans les fichiers `*.pyd`. Si la version requise de Visual Studio n’est pas installée, pip n’est pas en mesure de compiler ces composants. Le message d’erreur affiché dans ce cas est `error: Unable to find vcvarsall.bat`. `easy_install` est souvent capable de télécharger des binaires précompilés, et vous pouvez télécharger un compilateur approprié pour les versions antérieures de Python à partir de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Pour plus d’informations, consultez le billet [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Comment gérer l’erreur « unable to find vcvarsallbat ») sur le blog de l’équipe Python Tools.

## <a name="see-also"></a>Voir aussi

- [Gestion des environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)