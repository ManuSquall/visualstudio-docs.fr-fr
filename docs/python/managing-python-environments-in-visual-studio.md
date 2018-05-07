---
title: Gérer des interpréteurs et des environnements Python
description: Utilisez la fenêtre Environnements Python pour gérer les environnements globaux, virtuels et conda, installer des interpréteurs et des packages Python et affecter des environnements à des projets Visual Studio.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: f3a3fa14a2772171b2968514867d35ea4ad126f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Comment créer et gérer des environnements Python dans Visual Studio

Un *environnement* Python est un contexte d’exécution de code Python, qui comprend des environnements globaux, virtuels et conda. Un comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio sous Windows, la fenêtre [Environnements Python](#managing-python-environments-in-visual-studio), décrite dans cet article, permet de gérer ces environnements et d’en sélectionner un par défaut pour les nouveaux projets. Pour un projet donné, il est également possible de sélectionner un environnement en particulier, plutôt que d’utiliser l’environnement par défaut.

**Remarque**: si vous utilisez Python dans Visual Studio, consultez les articles suivants pour obtenir les informations nécessaires :

- [Utilisation de Python dans Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installation de la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md)

Sachez également qu’il n’est pas possible de gérer des environnements pour du code Python ouvert uniquement en tant que dossier à l’aide de la commande **Fichier > Ouvrir > Dossier**. Il faut au contraire [créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md) pour bénéficier des fonctionnalités d’environnement de Visual Studio.

Si vous souhaitez installer des packages dans un environnement, reportez-vous à l’[onglet Packages](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Types d’environnements

### <a name="global-environments"></a>Environnements globaux

Chaque installation de Python (par exemple, Python 2.7, Python 3.6, Anaconda 4.4.0, etc. – voir [Sélectionner et installer des interpréteurs Python](installing-python-interpreters.md)) gère son propre environnement global. Chaque environnement se compose de l’interpréteur Python spécifique, de sa bibliothèque standard et d’un ensemble de packages préinstallés. L’installation d’un package dans un environnement global le rend disponible à tous les projets qui utilisent cet environnement. Si l’environnement se trouve dans une zone protégée du système de fichiers (par exemple `c:\program files`), l’installation des packages nécessite des privilèges d’administrateur.

Les environnements globaux sont disponibles à tous les projets sur l’ordinateur. Dans Visual Studio, vous sélectionnez un environnement global par défaut, qui est utilisé pour tous les projets, sauf si vous choisissez spécifiquement un autre environnement pour un projet. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Environnements virtuels

Les packages installés dans un environnement global étant accessibles à tous les projets qui utilisent cet environnement, des conflits peuvent survenir lorsque deux projets requièrent des packages incompatibles ou différentes versions du même package. Les environnements virtuels évitent de tels conflits en utilisant l’interpréteur et la bibliothèque standard d’un environnement global, mais en conservant ses propres magasins de package dans des dossiers isolés.

Dans Visual Studio, vous pouvez créer un environnement virtuel pour un projet en particulier, qui est stocké dans un sous-dossier du projet. Visual Studio fournit une commande pour générer un fichier `requirements.txt` à partir de l’environnement virtuel, ce qui permet de recréer facilement l’environnement sur d’autres ordinateurs. Pour plus d'informations, voir [Utilisation des environnements virtuels](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Environnements conda

Un environnement conda est un environnement créé à l’aide de l’outil `conda`. Ils sont généralement stockés dans le dossier `envs` au sein d’une installation Anaconda et, par conséquent, se comportent de la même façon que les environnements globaux. Par exemple, le fait d’installer un nouveau package dans un environnement conda le rend accessible à tous les projets qui utilisent cet environnement.

À l’heure actuelle, Visual Studio ne détecte pas automatiquement les environnements conda, mais il est possible de les indiquer manuellement à Visual Studio. Consultez la section [Identifier manuellement un environnement existant](#manually-identifying-an-existing-environment).

## <a name="the-python-environments-window"></a>Fenêtre Environnements Python

Les environnements connus de Visual Studio s’affichent sur la fenêtre **Environnements Python**. Pour ouvrir cette fenêtre, suivez l’une des méthodes ci-dessous :

- Sélectionnez la commande de menu **Affichage > Other Windows (Autres fenêtres) > Environnements Python**.
- Cliquez avec le bouton droit sur le nœud **Environnements Python** d’un projet dans l’Explorateur de solutions, et sélectionnez **Afficher tous les environnements Python** :

    ![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments-view-all.png)

Dans les deux cas, la fenêtre **Environnements Python** s’affiche comme un onglet de la même famille que l’Explorateur de solutions :

![Fenêtre Environnements Python](media/environments-default-view.png)

L’image ci-dessus montre que Visual Studio a détecté deux installations de Python 3.6 (32 bits), de même qu’Anaconda 5.0.0.

L’environnement par défaut en gras est Python 3.6 (ici au sein d’une installation Anaconda), que Visual Studio utilise pour tous les nouveaux projets. Les commandes dans la partie inférieure de la fenêtre s’appliquent à l’interpréteur Python 3.6 sélectionné, qui correspond comme on peut le voir à l’installation spécifique dans `C:\Python36-32`. Si un environnement attendu n’apparaît pas, consultez la section [Identifier manuellement un environnement existant](#manually-identifying-an-existing-environment).

À droite de chaque environnement apparaît un contrôle qui ouvre une fenêtre interactive pour cet environnement. Un autre contrôle peut apparaître qui actualise la base de données IntelliSense pour cet environnement (consultez [Référence sur la fenêtre Environnements](python-environments-window-tab-reference.md#intellisense-tab) pour plus d’informations sur la base de données).

Sous la liste des environnements se trouve une liste déroulante pour les options **Vue d’ensemble**, **Packages** et **IntelliSense** décrites sur la page [Référence sur les onglets de la fenêtre Environnements Python](python-environments-window-tab-reference.md). Par ailleurs, si vous agrandissez suffisamment la fenêtre **Environnements Python**, ces options s’affichent sous forme d’onglets, sans doute plus pratiques à utiliser :

![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

> [!Note]
> Bien que Visual Studio respecte l’option system-site-packages, il ne fournit pas de moyen permettant de la modifier à partir de Visual Studio.

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sur des environnements Python dans Visual Studio (2 min35s).|

### <a name="what-if-no-environments-appear"></a>Que faire si aucun environnement n’apparaît ?

Si aucun environnement ne s’affiche, cela signifie que Visual Studio n’est parvenu à détecter aucune installation de Python dans les emplacements standard. Par exemple, vous avez peut-être installé Visual Studio 2017 mais désactivé toutes les options de l’interpréteur dans le programme d’installation de la charge de travail Python. Il est également possible que vous ayez installé Visual Studio 2015 ou une version antérieure sans installer manuellement un interpréteur (consultez la page [Installer des interpréteurs Python](installing-python-interpreters.md)).

Si vous savez que vous disposez d’un interpréteur Python sur votre ordinateur, mais que Visual Studio (quelle que soit sa version) ne l’a pas détecté, utilisez la commande **+ Personnalisé...**  pour spécifier son emplacement manuellement. Consultez la section suivante, [Identifier manuellement un environnement existant](#manually-identifying-an-existing-environment).

> [!Tip]
> Visual Studio détecte les mises à jour sur un interpréteur existant, telles que la mise à niveau Python 2.7.11 à 2.7.14 à l’aide de programmes d’installation de python.org. Pendant le processus d’installation, l’ancien environnement disparaît de la liste **Environnements Python** avant que la mise à jour n’apparaisse à la place.
>
> Toutefois, si vous déplacez manuellement un interpréteur et son environnement à l’aide du système de fichiers, Visual Studio ne sera pas informé du nouvel emplacement. Pour plus d’informations, consultez la section [Déplacer un interpréteur](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Identifier manuellement un environnement existant

Suivez les étapes ci-dessous pour identifier un environnement installé à un emplacement non standard, y compris un environnement conda :

1. Sélectionnez **+ Personnalisé...**  dans la fenêtre **Environnements Python** pour ouvrir l’onglet **Configurer** :

    ![Affichage par défaut pour un nouvel environnement personnalisé](media/environments-custom-1.png)

1. Entrez un nom pour l’environnement dans le champ **Description**.

1. Entrez ou recherchez (avec **...***) le chemin d’accès de l’interpréteur dans le champ **Chemin du préfixe**.

1. Si Visual Studio détecte un interpréteur Python à cet emplacement (par exemple, le chemin d’accès indiqué ci-dessous pour un environnement conda), il fait apparaître la commande **Détection automatique**. Cette commande **Détection automatique* remplit les champs restants. Vous pouvez également les compléter manuellement.

    ![Activation de la commande Détection automatique](media/environments-custom-2.png)

    ![Saisie semi-automatique des champs d’environnement après détection automatique](media/environments-custom-3.png)

1. Dès que les champs contiennent les valeurs souhaitées, sélectionnez **Appliquer** pour enregistrer la configuration. Vous pouvez maintenant utiliser l’environnement comme n’importe quel autre environnement au sein de Visual Studio.

1. Si vous devez supprimer un environnement identifié manuellement, sélectionnez la commande **Supprimer** de l’onglet **Configurer**. Les environnements détectés automatiquement ne fournissent pas cette option. Pour plus d’informations, consultez la section [Onglet Configurer](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Voir aussi

- [Installer des interpréteurs Python](installing-python-interpreters.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)