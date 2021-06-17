---
title: Gérer des interpréteurs et des environnements Python
description: Utilisez la fenêtre Environnements Python pour gérer les environnements globaux, virtuels et conda, installer des interpréteurs et des packages Python et affecter des environnements à des projets Visual Studio.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 26bcf0fa4d56d4e8df100a0d3e65904d065d8757
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254873"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Comment créer et gérer des environnements Python dans Visual Studio

Un **environnement python** est un contexte dans lequel vous exécutez le code Python et comprend des environnements globaux, virtuels et Conda. Un comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio sur Windows, utilisez la fenêtre **Environnements Python** décrite dans cet article afin de gérer les environnements et d’en sélectionner un par défaut pour les nouveaux projets. Vous trouverez d’autres aspects relatifs aux environnements dans les articles suivants :

- Pour un projet donné, vous pouvez [sélectionner un environnement spécifique](selecting-a-python-environment-for-a-project.md) au lieu d’utiliser l’environnement par défaut.

- Pour plus d’informations sur la création et l’utilisation d’environnements virtuels pour les projets Python, consultez [Utiliser des environnements virtuels](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Si vous voulez installer des packages dans un environnement, reportez-vous aux [Informations de référence sur l’onglet Packages](python-environments-window-tab-reference.md#packages-tab).

- Pour installer un autre interpréteur Python, consultez [Installer les interpréteurs Python](installing-python-interpreters.md). En règle générale, si vous téléchargez et exécutez un programme d’installation pour une distribution Python principale, Visual Studio détecte cette nouvelle installation. L’environnement apparaît dans la fenêtre **Environnements Python**, et vous pouvez le sélectionner pour des projets.

Si vous découvrez Python dans Visual Studio, les articles suivants fournissent également des informations générales :

- [Utiliser Python dans Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installer la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Vous ne pouvez pas gérer les environnements pour le code Python qui est ouvert uniquement en tant que dossier à l’aide de la commande **fichier**  >  **ouvrir** le  >  **dossier** . Il faut au contraire [créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md) pour bénéficier des fonctionnalités d’environnement de Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Vous pouvez gérer les environnements pour le code python ouvert en tant que dossier à l’aide de la commande **fichier**  >  **ouvrir** le  >  **dossier** . La barre d’outils Python vous permet de basculer entre tous les environnements détectés et d’ajouter un nouvel environnement. Les informations d’environnement sont stockées dans le fichier PythonSettings.json dans le dossier .vs Workspace.
::: moniker-end

## <a name="the-python-environments-window"></a>Fenêtre Environnements Python

Les environnements connus de Visual Studio s’affichent sur la fenêtre **Environnements Python**. Pour ouvrir cette fenêtre, suivez l’une des méthodes ci-dessous :

- Sélectionnez la commande de menu **Afficher** d'  >  **autres**  >  **environnements Windows python** .
- Cliquez avec le bouton droit sur le nœud **environnements python** d’un projet dans **Explorateur de solutions** , puis sélectionnez **Afficher tous les environnements python**:

    ::: moniker range="vs-2017"
    ![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments/environments-view-all-2019.png)
    ::: moniker-end

Dans les deux cas, la fenêtre **Environnements Python** apparaît à côté de l’**Explorateur de solutions** :

::: moniker range="vs-2017"
![Fenêtre Environnements Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Fenêtre Environnements Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio recherche les environnements globaux installés à l’aide du Registre (conformément au [PEP 514](https://www.python.org/dev/peps/pep-0514/)) ainsi que les environnements virtuels et les environnements conda (consultez [Types d’environnement](#types-of-environments)). Si un environnement attendu ne figure pas dans la liste, consultez [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

Lorsque vous sélectionnez un environnement dans la liste, Visual Studio affiche différentes propriétés et commandes pour cet environnement sous l’onglet **vue d’ensemble** . Par exemple, vous pouvez voir dans l’image ci-dessus que l’emplacement de l’interpréteur est *C:\Python36-32*. Les quatre commandes au bas de l’onglet **Vue d’ensemble** ouvrent chacune une invite de commandes avec l’interpréteur en cours d’exécution. Pour plus d’informations, consultez [Informations de référence sur les onglets de la fenêtre Environnements Python - Vue d’ensemble](python-environments-window-tab-reference.md#overview-tab).

Utilisez la liste déroulante sous la liste des environnements pour accéder aux différents onglets, comme **Packages** et **IntelliSense**. Ces onglets sont également décrits dans les [Informations de référence sur les onglets de la fenêtre Environnements Python](python-environments-window-tab-reference.md).

La sélection d’un environnement ne change pas sa relation avec les projets. L’environnement par défaut, en gras dans la liste, est celui utilisé par Visual Studio pour tous les nouveaux projets. Pour utiliser un autre environnement avec de nouveaux projets, utilisez la commande **Définir cet environnement comme valeur par défaut pour les nouveaux projets**. Dans le contexte d’un projet, vous pouvez toujours sélectionner un environnement spécifique. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

À droite de chaque environnement de la liste se trouve un contrôle qui ouvre une fenêtre **interactive** pour cet environnement. (Dans Visual Studio 2017 versions 15.5 et antérieures, un autre contrôle s’affiche, permettant d’actualiser la base de données IntelliSense pour cet environnement. Pour plus d’informations sur la base de données, consultez [Informations de référence sur la fenêtre Environnements](python-environments-window-tab-reference.md)).

::: moniker range="vs-2017"
> [!Tip]
> Quand vous agrandissez suffisamment la fenêtre **Environnements Python**, vous obtenez une vue complète de vos environnements, que vous pouvez trouver plus pratique à utiliser.
>
> ![Affichage développé de la fenêtre Environnements Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Quand vous agrandissez suffisamment la fenêtre **Environnements Python**, vous obtenez une vue complète de vos environnements, que vous pouvez trouver plus pratique à utiliser.
>
> ![Affichage développé de la fenêtre Environnements Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Bien que Visual Studio respecte l’option system-site-packages, il ne fournit pas de moyen permettant de la modifier à partir de Visual Studio.

### <a name="what-if-no-environments-appear"></a>Que faire si aucun environnement n’apparaît ?

Si aucun environnement ne s’affiche, cela signifie que Visual Studio n’est parvenu à détecter aucune installation de Python dans les emplacements standard. Par exemple, vous avez peut-être installé Visual Studio 2017 ou version ultérieure mais désactivé toutes les options de l’interpréteur dans le programme d’installation de la charge de travail Python. Il est également possible que vous ayez installé Visual Studio 2015 ou une version antérieure sans installer manuellement un interpréteur (consultez la page [Installer des interpréteurs Python](installing-python-interpreters.md)).

Si vous savez que vous avez un interpréteur Python sur votre ordinateur, mais que Visual Studio (n’importe quelle version) ne l’a pas détecté, utilisez la commande **+ personnalisée** pour spécifier son emplacement manuellement. Consultez la section suivante, [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio détecte les mises à jour d’un interpréteur existant, telles que la mise à niveau de Python 2.7.11 vers 2.7.14 à l’aide des programmes d’installation de python.org. Pendant le processus d’installation, l’ancien environnement disparaît de la liste des **environnements python** avant que la mise à jour ne s’affiche à la place.
>
> Toutefois, si vous déplacez manuellement un interpréteur et son environnement à l’aide du système de fichiers, Visual Studio ne sera pas informé du nouvel emplacement. Pour plus d’informations, consultez la section [Déplacer un interpréteur](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Types d’environnements

Vous pouvez utiliser Visual Studio avec des environnements globaux, virtuels et conda.

#### <a name="global-environments"></a>Environnements globaux

Chaque installation de Python, par exemple Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0, etc., (consultez [Installer des interpréteurs Python](installing-python-interpreters.md)) gère son propre *environnement global*. Chaque environnement est composé de l’interpréteur Python spécifique, de sa bibliothèque standard, d’un ensemble de packages préinstallés et des packages supplémentaires que vous installez pendant que cet environnement est activé. L’installation d’un package dans un environnement global le rend disponible à tous les projets qui utilisent cet environnement. Si l’environnement se trouve dans une zone protégée du système de fichiers (par exemple, dans *c:\program files*), l’installation des packages nécessite des privilèges d’administrateur.

Les environnements globaux sont disponibles à tous les projets sur l’ordinateur. Dans Visual Studio, vous sélectionnez un environnement global par défaut, qui est utilisé pour tous les projets, sauf si vous choisissez spécifiquement un autre environnement pour un projet. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Environnements virtuels

Bien que le fait de travailler dans un environnement global offre un moyen facile de commencer, avec le temps, cet environnement va être encombré par les nombreux packages distincts que vous aurez installés pour les différents projets. Un tel encombrement rend difficile le test approfondi d’une application par rapport à un ensemble spécifique de packages ayant des versions connues, ce qui correspond précisément au genre d’environnement configuré sur un serveur de builds ou un serveur web. Des conflits peuvent également se produire quand deux projets nécessitent des packages incompatibles ou des versions distinctes du même package.

C’est la raison pour laquelle les développeurs créent souvent un *environnement virtuel* pour un projet. Un environnement virtuel est un sous-dossier d’un projet qui contient une copie d’un interpréteur spécifique. Quand vous activez l’environnement virtuel, tous les packages que vous installez sont installés uniquement dans le sous-dossier de cet environnement. Quand vous exécutez ensuite un programme Python dans cet environnement, vous savez qu’il s’exécute uniquement en fonction de ces packages spécifiques.

Visual Studio prend en charge directement la création d’un environnement virtuel pour un projet. Par exemple, si vous ouvrez un projet qui contient un fichier *requirements.txt*, ou si vous créez un projet à partir d’un modèle qui inclut ce fichier, Visual Studio vous invite à créer automatiquement un environnement virtuel et à installer ces dépendances.

À tout moment dans un projet ouvert, vous pouvez créer un environnement virtuel. Dans l’**Explorateur de solutions**, développez le nœud de projet, cliquez avec le bouton droit sur **Environnements Python**, puis sélectionnez Ajouter un environnement virtuel. Pour plus d’informations, consultez [Créer un environnement virtuel](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).

Visual Studio fournit également une commande qui permet de générer un fichier *requirements.txt* à partir d’un environnement virtuel, ce qui facilite la recréation de l’environnement sur d’autres ordinateurs. Pour plus d’informations, consultez [Utiliser des environnements virtuels](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Environnements conda

Vous créez un environnement conda à l’aide de l’outil `conda`, ou avec la gestion conda intégrée dans Visual Studio 2017 15.7 et versions ultérieures. (Nécessite Anaconda ou Miniconda, qui sont disponibles via le programme d’installation de Visual Studio ; consultez [Installation](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. Sélectionnez **+ Créer un environnement conda** dans la fenêtre **Environnements Python** ; cette opération ouvre un onglet **Créer un environnement conda** :

    ![Onglet pour la création d’un environnement conda](media/environments/environments-conda-1.png)

1. Entrez un nom pour l’environnement dans le champ **Nom**, sélectionnez un interpréteur Python de base dans le champ **Python**, puis sélectionnez **Créer**.

1. La fenêtre **Sortie** affiche la progression pour le nouvel environnement, avec quelques instructions CLI une fois la création terminée :

    ![Création réussie d’un environnement conda](media/environments/environments-conda-2.png)

1. Dans Visual Studio, vous pouvez activer un environnement conda pour un projet comme vous le feriez pour tout autre environnement, comme décrit dans [Sélectionner un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

1. Pour installer des packages dans l’environnement, utilisez [l’onglet Packages](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Sélectionnez **Ajouter un environnement...** dans la fenêtre **environnements python** (ou à partir de la barre d’outils Python), qui ouvre la boîte de dialogue **Ajouter un environnement** . Dans cette boîte de dialogue, sélectionnez l’onglet **Environnement Conda** :

    ![Onglet Environnement Conda dans la boîte de dialogue Ajouter un environnement](media/environments/environments-conda-1-2019.png)

1. Configurez les champs suivants :

    | Champ | Description |
    | --- | --- |
    | Project | Projet dans lequel créer l’environnement (si vous avez plusieurs projets dans la même solution Visual Studio). |
    | Nom | Nom de l’environnement conda. |
    | Ajouter des packages depuis | Choisissez **Fichier d’environnement** si vous avez un fichier *environment.yml* décrivant vos dépendances de fichiers, ou choisissez **un ou plusieurs noms de packages Anaconda** et répertoriez au moins un package Python ou une version de Python dans le champ situé en dessous. La liste des packages indique à conda de créer un environnement Python. Pour installer la dernière version de Python, utilisez `python` ; pour installer une version spécifique, utilisez `python=,major>.<minor>` comme dans `python=3.7`. Vous pouvez également utiliser le bouton de package pour sélectionner des versions de Python et des packages communs à partir d’une série de menus. |
    | Définir en tant qu’environnement actuel | Active le nouvel environnement dans le projet sélectionné lorsque l’environnement est créé. |
    | Définir en tant qu’environnement par défaut pour les nouveaux projets | Définit et active automatiquement l’environnement conda dans tous les nouveaux projets créés dans Visual Studio. Cette option est identique à l’option **Définir cet environnement comme valeur par défaut pour les nouveaux projets** dans la fenêtre **Environnements Python**. |
    | Afficher dans la fenêtre Environnements Python | Spécifie l’affichage ou non de la fenêtre **Environnements Python** après la création de l’environnement. |

    > [!Important]
    > Lorsque vous créez un environnement conda, veillez à spécifier au moins une version de Python ou un package Python à l’aide de `environments.yml` ou de la liste des packages, ce qui garantit que l’environnement contient un runtime Python. Sinon, Visual Studio ignore l’environnement : l’environnement n’apparaît nulle part dans la fenêtre **Environnements Python**, n’est pas être défini en tant qu’environnement actuel pour un projet et n’est pas disponible en tant qu’environnement global.
    >
    > S’il vous créez un environnement conda sans version de Python, utilisez la commande `conda info` pour afficher les emplacements de dossiers d’environnement conda, puis supprimer manuellement le sous-dossier de l’environnement de cet emplacement.

1. Sélectionnez **Créer** et observez la progression dans la fenêtre **Sortie**. Une fois la création terminée, la sortie inclut avec quelques instructions CLI :

    ![Création réussie d’un environnement conda](media/environments/environments-conda-2-2019.png)

1. Dans Visual Studio, vous pouvez activer un environnement conda pour un projet comme vous le feriez pour tout autre environnement, comme décrit dans [Sélectionner un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

1. Pour installer d’autres packages dans l’environnement, utilisez l’[onglet Packages](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Pour de meilleurs résultats avec les environnements conda, utilisez conda 4.4.8 ou version ultérieure (les versions conda diffèrent des versions Anaconda). Vous pouvez installer les versions appropriées de Miniconda (Visual Studio 2019) et d’Anaconda (Visual Studio 2017) via le programme d’installation de Visual Studio.

Pour voir la version conda, où sont stockés les environnements conda et d’autres informations, exécutez `conda info` à partir d’une invite de commandes Anaconda (autrement dit, une invite de commandes où Anaconda fait partie du chemin) :

```cli
conda info
```

Vos dossiers d’environnement conda apparaissent comme suit :

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Étant donné que les environnements conda ne sont pas stockés avec un projet, ils agissent de la même façon que les environnements globaux. Par exemple, le fait d’installer un nouveau package dans un environnement conda le rend accessible à tous les projets qui utilisent cet environnement.

Pour Visual Studio 2017 versions15.6 et antérieures, vous pouvez utiliser des environnements conda en pointant sur ceux-ci manuellement comme décrit dans [Identifier manuellement un environnement existant](#manually-identify-an-existing-environment).

Visual Studio 2017 versions 15.7 et ultérieures détecte automatiquement les environnements conda et les affiche dans la fenêtre **Environnements Python** comme décrit dans la section suivante.

## <a name="manually-identify-an-existing-environment"></a>Identifier manuellement un environnement existant

Suivez les étapes ci-dessous pour identifier un environnement installé à un emplacement non standard (y compris un environnement conda dans Visual Studio 2017 versions 15.6 et antérieures) :

::: moniker range="vs-2017"

1. Sélectionnez **+ Personnalisé** dans la fenêtre **Environnements Python** pour ouvrir l’onglet **Configurer** :

    ![Affichage par défaut pour un nouvel environnement personnalisé](media/environments/environments-custom-1.png)

1. Entrez un nom pour l’environnement dans le champ **Description**.

1. Entrez ou parcourez (en utilisant **...**) le chemin d’accès de l’interpréteur dans le champ du chemin d' **accès du préfixe** .

1. Si Visual Studio détecte un interpréteur Python à cet emplacement (par exemple, le chemin d’accès indiqué ci-dessous pour un environnement conda), il fait apparaître la commande **Détection automatique**. La sélection de **détection automatique** remplit les champs restants. Vous pouvez également les compléter manuellement.

    ![Activation de la commande Détection automatique](media/environments/environments-custom-2.png)

    ![Saisie semi-automatique des champs d’environnement après détection automatique](media/environments/environments-custom-3.png)

1. Dès que les champs contiennent les valeurs souhaitées, sélectionnez **Appliquer** pour enregistrer la configuration. Vous pouvez maintenant utiliser l’environnement comme n’importe quel autre environnement au sein de Visual Studio.

1. Si vous devez supprimer un environnement identifié manuellement, sélectionnez la commande **supprimer** sous l’onglet **configurer** . Les environnements détectés automatiquement ne fournissent pas cette option. Pour plus d’informations, consultez la section [Onglet Configurer](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Sélectionnez **Ajouter un environnement...** dans la fenêtre **environnements python** (ou à partir de la barre d’outils Python), qui ouvre la boîte de dialogue **Ajouter un environnement** . Dans cette boîte de dialogue, sélectionnez l’onglet **Environnement existant** :

    ![Onglet Environnement existant dans la boîte de dialogue Ajouter un environnement](media/environments/environments-custom-1-2019.png)

1. Sélectionnez la liste déroulante **Environnement**, puis sélectionnez **Personnalisé** :

    ![Onglet Environnement personnalisé dans la boîte de dialogue Ajouter un environnement](media/environments/environments-custom-2-2019.png)

1. Dans les champs de la boîte de dialogue, entrez ou recherchez (à l’aide de **...**) le chemin d’accès de l’interpréteur sous **Chemin du préfixe**, qui renseigne la plupart des autres champs. Une fois les valeurs révisées et modifiées si nécessaire, sélectionnez **Ajouter**.

    ![Champs pour spécifier les détails d’une option d’environnement personnalisé dans la boîte de dialogue Ajouter un environnement](media/environments/environments-custom-3-2019.png)

1. Les détails de l’environnement peuvent être révisés et modifiés à tout moment dans la fenêtre **Environnements Python**. Dans cette fenêtre, sélectionnez l’environnement, puis sélectionnez l’onglet **configurer** . Après avoir apporté les modifications nécessaires, sélectionnez la commande **appliquer** . Vous pouvez également supprimer l’environnement à l’aide de la commande **Supprimer** (non disponible pour les environnements détectés automatiquement). Pour plus d’informations, consultez la section [Onglet Configurer](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Corriger ou supprimer les environnements non valides

Si Visual Studio recherche des entrées de Registre pour un environnement, mais que le chemin d’accès à l’interpréteur n’est pas valide, la fenêtre **environnements python** affiche le nom avec une police de barré :

::: moniker range="vs-2017"
![Fenêtre Environnements Python montrant un environnement non valide](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Fenêtre Environnements Python montrant un environnement non valide](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Pour corriger un environnement que vous souhaitez conserver, essayez d’abord d’exécuter la procédure de **réparation** de son programme d’installation. Les programmes d’installation pour Python 3.x standard, par exemple, incluent cette option.

Pour corriger un environnement qui n’a pas d’option de réparation, ou pour supprimer un environnement non valide, effectuez les étapes suivantes afin de modifier directement le Registre. Visual Studio met automatiquement à jour la fenêtre **environnements python** quand vous apportez des modifications au registre.

1. Exécutez *regedit.exe*.
1. Accédez à **HKEY_LOCAL_MACHINE\SOFTWARE\Python** ou **HKEY_CURRENT_USER\SOFTWARE\Python**. Pour IronPython, recherchez plutôt **IronPython**.
1. Développez le nœud qui correspond à la distribution, tel que **PythonCore** pour CPython ou **ContinuumAnalytics** pour Anaconda. Pour IronPython, développez le nœud de numéro de version.
1. Inspectez les valeurs sous le nœud **InstallPath** :

    ![Entrées de Registre pour une installation standard de CPython](media/environments/environments-registry-entries.png)

    - Si l’environnement existe toujours sur votre ordinateur, remplacez la valeur de **ExecutablePath** par l’emplacement correct. Corrigez également les valeurs **(Par défaut)** et **WindowedExecutablePath** valeurs en fonction des besoins.
    - Si l’environnement n’existe plus sur votre ordinateur et que vous souhaitez le supprimer de la fenêtre **Environnements Python**, supprimez le nœud parent d’**InstallPath**, par exemple **3.6**, dans l’image ci-dessus.
    - Paramètres non valides dans **HKEY_CURRENT_USER\SOFTWARE\Python** substituer les paramètres dans **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Voir aussi

- [Installer les interpréteurs Python](installing-python-interpreters.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utilisation requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Informations de référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)