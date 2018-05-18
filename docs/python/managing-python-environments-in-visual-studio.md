---
title: Gérer des interpréteurs et des environnements Python
description: Utilisez la fenêtre Environnements Python pour gérer les environnements globaux, virtuels et conda, installer des interpréteurs et des packages Python et affecter des environnements à des projets Visual Studio.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1ba3902fde77e297148c2006f89dd61bca1e902b
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Comment créer et gérer des environnements Python dans Visual Studio

Un *environnement* Python est un contexte d’exécution de code Python, qui comprend des environnements globaux, virtuels et conda. Un comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio sur Windows, la fenêtre [Environnements Python](#the-python-environments-window), décrite dans cet article, permet de gérer ces environnements et d’en sélectionner un par défaut pour les nouveaux projets. Pour un projet donné, il est également possible de sélectionner un environnement en particulier, plutôt que d’utiliser l’environnement par défaut.

**Remarque**: si vous utilisez Python dans Visual Studio, consultez les articles suivants pour obtenir les informations nécessaires :

- [Utilisation de Python dans Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installation de la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md)

Sachez également qu’il n’est pas possible de gérer des environnements pour du code Python ouvert uniquement en tant que dossier à l’aide de la commande **Fichier** > **Ouvrir** > **Dossier**. Il faut au contraire [créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md) pour bénéficier des fonctionnalités d’environnement de Visual Studio.

Si vous souhaitez installer des packages dans un environnement, reportez-vous à l’[onglet Packages](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Types d’environnements

### <a name="global-environments"></a>Environnements globaux

Chaque installation de Python (par exemple, Python 2.7, Python 3.6, Anaconda 4.4.0, etc. – voir [Sélectionner et installer des interpréteurs Python](installing-python-interpreters.md)) gère son propre environnement global. Chaque environnement se compose de l’interpréteur Python spécifique, de sa bibliothèque standard et d’un ensemble de packages préinstallés. L’installation d’un package dans un environnement global le rend disponible à tous les projets qui utilisent cet environnement. Si l’environnement se trouve dans une zone protégée du système de fichiers (par exemple `c:\program files`), l’installation des packages nécessite des privilèges d’administrateur.

Les environnements globaux sont disponibles à tous les projets sur l’ordinateur. Dans Visual Studio, vous sélectionnez un environnement global par défaut, qui est utilisé pour tous les projets, sauf si vous choisissez spécifiquement un autre environnement pour un projet. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Environnements virtuels

Les packages installés dans un environnement global étant accessibles à tous les projets qui utilisent cet environnement, des conflits peuvent survenir lorsque deux projets requièrent des packages incompatibles ou différentes versions du même package. Les environnements virtuels évitent de tels conflits en utilisant l’interpréteur et la bibliothèque standard d’un environnement global, mais en conservant ses propres magasins de package dans des dossiers isolés.

Dans Visual Studio, vous pouvez créer un environnement virtuel pour un projet en particulier, qui est stocké dans un sous-dossier du projet. Visual Studio fournit une commande pour générer un fichier `requirements.txt` à partir de l’environnement virtuel, ce qui permet de recréer facilement l’environnement sur d’autres ordinateurs. Pour plus d'informations, voir [Utilisation des environnements virtuels](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Environnements conda

Vous créez un environnement conda à l’aide de l’outil `conda`, ou avec la gestion conda intégrée dans Visual Studio 2017 15.7 et versions ultérieures. (Nécessite Anaconda ou Miniconda ; Anaconda est disponible par le biais du programme d’installation de Visual Studio ; consultez [Installation - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

> [!Note]
> Pour de meilleurs résultats avec les environnements conda, utilisez conda 4.4.8 ou version ultérieure (les versions conda diffèrent des versions Anaconda). Installation d’Anaconda 5.1 à partir du programme d’installation de Visual Studio 2017

Pour voir la version conda, où sont stockés les environnements conda et d’autres informations, exécutez `conda info` à partir d’une invite de commandes Anaconda (autrement dit, une invite de commandes où Anaconda fait partie du chemin) :

```bash
conda info
```
Vos dossiers d’environnement conda apparaissent comme suit :

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Étant donné que les environnements conda ne sont pas stockés avec un projet, ils agissent de la même façon que les environnements globaux. Par exemple, le fait d’installer un nouveau package dans un environnement conda le rend accessible à tous les projets qui utilisent cet environnement.

Pour Visual Studio 2017 versions15.6 et antérieures, vous pouvez utiliser des environnements conda en pointant sur ceux-ci manuellement comme décrit dans [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

Visual Studio 2017 versions 15.7 et ultérieures détecte automatiquement les environnements conda et les affiche dans la fenêtre **Environnements Python** comme décrit dans la section suivante.

## <a name="the-python-environments-window"></a>Fenêtre Environnements Python

Les environnements connus de Visual Studio s’affichent sur la fenêtre **Environnements Python**. Pour ouvrir cette fenêtre, suivez l’une des méthodes ci-dessous :

- Sélectionnez la commande de menu **Affichage** > **Autres fenêtres** > **Environnements Python**.
- Cliquez avec le bouton droit sur le nœud **Environnements Python** d’un projet dans l’Explorateur de solutions, et sélectionnez **Afficher tous les environnements Python** :

    ![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments-view-all.png)

Dans les deux cas, la fenêtre **Environnements Python** s’affiche comme un onglet de la même famille que l’Explorateur de solutions :

![Fenêtre Environnements Python](media/environments-default-view.png)

L’environnement par défaut en gras est Python 3.6, qu’utilise Visual Studio pour tous les nouveaux projets. Tout environnement répertorié, de tout type, peut être utilisé en tant qu’environnement par défaut.

Les commandes dans la partie inférieure de la fenêtre s’appliquent à l’interpréteur sélectionné, qui correspond comme on peut le voir à l’installation spécifique dans `C:\Python36-32` (l’environnement par défaut en gras fait partie d’une installation Anaconda). Si un environnement attendu n’apparaît pas, consultez la section [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

À droite de chaque environnement apparaît un contrôle qui ouvre une fenêtre interactive pour cet environnement. (Dans Visual Studio 2017 versions 15.5 et antérieures, un autre contrôle s’affiche, permettant d’actualiser la base de données IntelliSense pour cet environnement. Consultez [Référence de la fenêtre Environnements](python-environments-window-tab-reference.md#intellisense-tab) pour plus d’informations sur la base de données).

Sous la liste des environnements se trouve une liste déroulante pour les options **Vue d’ensemble**, **Packages** et **IntelliSense** décrites sur la page [Référence sur les onglets de la fenêtre Environnements Python](python-environments-window-tab-reference.md). Par ailleurs, si vous agrandissez suffisamment la fenêtre **Environnements Python**, ces options s’affichent sous forme d’onglets, sans doute plus pratiques à utiliser :

![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

Dans l’illustration ci-dessus, vous pouvez voir la liste complète des environnements sur cet ordinateur en particulier, ainsi que des commandes supplémentaires pour créer des environnements.

> [!Note]
> Bien que Visual Studio respecte l’option system-site-packages, il ne fournit pas de moyen permettant de la modifier à partir de Visual Studio.

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sur des environnements Python dans Visual Studio (2 min35s).|

### <a name="what-if-no-environments-appear"></a>Que faire si aucun environnement n’apparaît ?

Si aucun environnement ne s’affiche, cela signifie que Visual Studio n’est parvenu à détecter aucune installation de Python dans les emplacements standard. Par exemple, vous avez peut-être installé Visual Studio 2017 mais désactivé toutes les options de l’interpréteur dans le programme d’installation de la charge de travail Python. Il est également possible que vous ayez installé Visual Studio 2015 ou une version antérieure sans installer manuellement un interpréteur (consultez la page [Installer des interpréteurs Python](installing-python-interpreters.md)).

Si vous savez que vous disposez d’un interpréteur Python sur votre ordinateur, mais que Visual Studio (quelle que soit sa version) ne l’a pas détecté, utilisez la commande **+ Personnalisé...**  pour spécifier son emplacement manuellement. Consultez la section suivante, [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio détecte les mises à jour sur un interpréteur existant, telles que la mise à niveau Python 2.7.11 à 2.7.14 à l’aide de programmes d’installation de python.org. Pendant le processus d’installation, l’ancien environnement disparaît de la liste **Environnements Python** avant que la mise à jour n’apparaisse à la place.
>
> Toutefois, si vous déplacez manuellement un interpréteur et son environnement à l’aide du système de fichiers, Visual Studio ne sera pas informé du nouvel emplacement. Pour plus d’informations, consultez la section [Déplacer un interpréteur](installing-python-interpreters.md#moving-an-interpreter).

<a name="manually-identifying-an-existing-environment></a>

## <a name="manually-identify-an-existing-environment"></a>Identifier manuellement un environnement existant

Suivez les étapes ci-dessous pour identifier un environnement installé à un emplacement non standard (y compris un environnement conda dans Visual Studio 2017 versions 15.6 et antérieures) :

1. Sélectionnez **+ Personnalisé** dans la fenêtre **Environnements Python** pour ouvrir l’onglet **Configurer** :

    ![Affichage par défaut pour un nouvel environnement personnalisé](media/environments-custom-1.png)

1. Entrez un nom pour l’environnement dans le champ **Description**.

1. Entrez ou recherchez (avec **...***) le chemin d’accès de l’interpréteur dans le champ **Chemin du préfixe**.

1. Si Visual Studio détecte un interpréteur Python à cet emplacement (par exemple, le chemin d’accès indiqué ci-dessous pour un environnement conda), il fait apparaître la commande **Détection automatique**. Cette commande **Détection automatique* remplit les champs restants. Vous pouvez également les compléter manuellement.

    ![Activation de la commande Détection automatique](media/environments-custom-2.png)

    ![Saisie semi-automatique des champs d’environnement après détection automatique](media/environments-custom-3.png)

1. Dès que les champs contiennent les valeurs souhaitées, sélectionnez **Appliquer** pour enregistrer la configuration. Vous pouvez maintenant utiliser l’environnement comme n’importe quel autre environnement au sein de Visual Studio.

1. Si vous devez supprimer un environnement identifié manuellement, sélectionnez la commande **Supprimer** de l’onglet **Configurer**. Les environnements détectés automatiquement ne fournissent pas cette option. Pour plus d’informations, consultez la section [Onglet Configurer](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Créer un environnements conda

*Visual Studio 2017 versions 15.7 et ultérieures.*

1. Sélectionnez **+ Créer un environnement conda** dans la fenêtre **Environnements Python** ; cette opération ouvre un onglet **Créer un environnement conda** :

    ![Onglet pour la création d’un environnement conda](media/environments-conda-1.png)

1. Entrez un nom pour l’environnement dans le champ **Nom**, sélectionnez un interpréteur Python de base dans le champ **Python**, puis sélectionnez **Créer**.

1. La fenêtre **Sortie** affiche la progression pour le nouvel environnement, avec quelques instructions CLI une fois la création terminée :

    ![Création réussie d’un environnement conda](media/environments-conda-2.png)

1. Dans Visual Studio, vous pouvez activer un environnement conda pour un projet comme vous le feriez pour tout autre environnement comme décrit dans [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

1. Pour installer des packages dans l’environnement, utilisez [l’onglet Packages](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>Voir aussi

- [Installer des interpréteurs Python](installing-python-interpreters.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)