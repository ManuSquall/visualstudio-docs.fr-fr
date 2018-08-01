---
title: Gérer des interpréteurs et des environnements Python
description: Utilisez la fenêtre Environnements Python pour gérer les environnements globaux, virtuels et conda, installer des interpréteurs et des packages Python et affecter des environnements à des projets Visual Studio.
ms.date: 07/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2b134dc54e2af31bb7d9fcb3f1dcdf3d31f799b5
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232216"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Comment créer et gérer des environnements Python dans Visual Studio

Un *environnement* Python est un contexte d’exécution de code Python, qui comprend des environnements globaux, virtuels et conda. Un comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio sur Windows, la fenêtre [Environnements Python](#the-python-environments-window), décrite dans cet article, permet de gérer ces environnements et d’en sélectionner un par défaut pour les nouveaux projets. Pour un projet donné, vous pouvez aussi [sélectionner un environnement en particulier](selecting-a-python-environment-for-a-project.md) au lieu d’utiliser l’environnement par défaut.

**Remarque**: si vous utilisez Python dans Visual Studio, consultez les articles suivants pour obtenir les informations nécessaires :

- [Utilisation de Python dans Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installation de la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md)

Sachez également qu’il n’est pas possible de gérer des environnements pour du code Python ouvert uniquement en tant que dossier à l’aide de la commande **Fichier** > **Ouvrir** > **Dossier**. Il faut au contraire [créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md) pour bénéficier des fonctionnalités d’environnement de Visual Studio.

Si vous voulez installer des packages dans un environnement, reportez-vous aux [Informations de référence sur l’onglet Packages](python-environments-window-tab-reference.md#packages-tab).

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

```cli
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

Visual Studio suit [PEP 514](https://www.python.org/dev/peps/pep-0514/) pour identifier les environnements installés à l’aide du Registre. Si un environnement attendu ne figure pas dans la liste, consultez [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

Le fait de sélectionner un environnement dans la liste affiche les différentes propriétés et commandes pour cet environnement sous l’onglet **Vue d’ensemble**. Par exemple, vous pouvez voir dans l’image ci-dessus que l’emplacement de l’interpréteur est `C:\Python36-32`. Utilisez la liste déroulante sous la liste des environnements pour accéder aux différents onglets, comme **Packages** et **IntelliSense**. Ces onglets sont décrits dans les [Informations de référence sur les onglets de la fenêtre Environnements Python](python-environments-window-tab-reference.md).

Le fait de sélectionner un environnement ne l’active pas. L’environnement par défaut, indiqué en gras dans la liste, est l’environnement actuellement activé que Visual Studio utilise pour les nouveaux projets. Pour activer un autre environnement, utilisez la commande **Définir cet environnement comme valeur par défaut pour les nouveaux projets**. Dans le contexte d’un projet, vous pouvez toujours activer un autre environnement. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

À droite de chaque environnement apparaît un contrôle qui ouvre une fenêtre interactive pour cet environnement. (Dans Visual Studio 2017 versions 15.5 et antérieures, un autre contrôle s’affiche, permettant d’actualiser la base de données IntelliSense pour cet environnement. Pour plus d’informations sur la base de données, consultez [Informations de référence sur la fenêtre Environnements](python-environments-window-tab-reference.md#intellisense-tab)).

> [!Tip]
> Quand vous agrandissez suffisamment la fenêtre **Environnements Python**, vous obtenez une vue complète de vos environnements, que vous pouvez trouver plus pratique à utiliser.
>
> ![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

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

## <a name="fix-or-delete-invalid-environments"></a>Corriger ou supprimer les environnements non valides

Si Visual Studio détecte des entrées de Registre pour un environnement, mais que le chemin vers l’interpréteur n’est pas valide, la fenêtre Environnements Python affiche le nom barré :

![Fenêtre Environnements Python montrant un environnement non valide](media/environments-invalid-entry.png)

Pour corriger un environnement que vous souhaitez conserver, essayez d’abord d’exécuter la procédure de **réparation** de son programme d’installation. Les programmes d’installation pour Python 3.x standard, par exemple, incluent cette option.

Pour corriger un environnement qui n’a pas d’option de réparation, ou pour supprimer un environnement non valide, effectuez les étapes suivantes afin de modifier directement le Registre. Visual Studio met automatiquement à jour la fenêtre Environnements Python quand vous apportez des modifications au Registre.

1. Exécutez `regedit.exe`.
1. Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Python` pour les interpréteurs 32 bits, ou à `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python` pour les interpréteurs 64 bits. Pour IronPython, recherchez plutôt `IronPython`.
1. Développez le nœud qui correspond à la distribution, tel que `PythonCore` pour CPython ou `ContinuumAnalytics` pour Anaconda. Pour IronPython, développez le nœud de numéro de version.
1. Inspectez les valeurs sous le nœud `InstallPath` :

    ![Entrées de Registre pour une installation standard de CPython](media/environments-registry-entries.png)

    - Si l’environnement existe toujours sur votre ordinateur, remplacez la valeur de `ExecutablePath` par l’emplacement correct. Corrigez également les valeurs `(Default)` et `WindowedExecutablePath` si nécessaire.
    - Si l’environnement n’existe plus sur votre ordinateur et que vous souhaitez le supprimer de la fenêtre Environnements Python, supprimez le nœud parent de `InstallPath`, tel que `3.6` dans l’image ci-dessus.

<a name="manually-identifying-an-existing-environment"></a>

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
