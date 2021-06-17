---
title: Gérer des projets d’application Python
description: Les projets dans Visual Studio gèrent les dépendances entre les fichiers et la complexité des relations dans une application.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9a20ea3baee84657e26e2d98bb5726c20ceba9e
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254899"
---
# <a name="python-projects-in-visual-studio"></a>Projets Python dans Visual Studio

Les applications Python sont généralement définies à l’aide de fichiers et de dossiers uniquement, mais cette structure peut s’avérer complexe à mesure que les applications deviennent plus volumineuses et impliquent éventuellement des fichiers générés automatiquement, JavaScript pour les applications web, etc. Un projet Visual Studio permet de gérer cette complexité. Le projet (un fichier *.pyproj*) identifie tous les fichiers sources et de contenu associés à votre projet, contient des informations de génération pour chaque fichier, conserve les informations pour l’intégration aux systèmes de contrôle de code source et vous permet d’organiser votre application en composants logiques.

![Projet Python dans l’Explorateur de solutions](media/projects-solution-explorer.png)

En outre, les projets sont toujours gérés dans une *solution* Visual Studio, qui peut contenir n’importe quel nombre de projets pouvant faire référence les uns aux autres. Par exemple, un projet Python peut faire référence un projet C++ qui implémente un module d’extension. Avec cette relation, Visual Studio génère automatiquement le projet C++ (si nécessaire) lorsque vous commencez à déboguer le projet Python. (Pour obtenir des informations d’ordre général à ce sujet, consultez [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio fournit divers modèles de projet Python pour configurer rapidement un certain nombre de structures d’application, y compris un modèle pour créer un projet à partir d’une arborescence de dossiers existante et un modèle pour créer un projet propre et vide. Consultez la section [Modèles de projet](#project-templates) pour obtenir un index.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 prend en charge l’ouverture d’un dossier contenant le code Python et l’exécution de ce code sans créer de fichiers projet et solution Visual Studio. Pour plus d’informations, consultez [démarrage rapide : ouvrir et exécuter du code python dans un dossier](quickstart-05-python-visual-studio-open-folder.md). L’utilisation d’un fichier projet présente toutefois des avantages, comme expliqué dans cette section.
::: moniker-end

> [!Tip]
> Sans projet, toutes les versions de Visual Studio fonctionnent bien avec le code Python. Par exemple, vous pouvez ouvrir un fichier Python seul et profiter de la saisie semi-automatique, d’IntelliSense et du débogage (en cliquant avec le bouton droit dans l’éditeur et en sélectionnant **Démarrer avec débogage**). Étant donné que ce code utilise toujours l’environnement global par défaut, vous pouvez toutefois rencontrer des saisies semi-automatiques incorrectes ou des erreurs si le code est destiné à un autre environnement. En outre, Visual Studio analyse tous les fichiers et packages dans le dossier à partir duquel le fichier unique est ouvert, ce qui peut consommer beaucoup de temps processeur.
>
> Il est très simple de créer un projet Visual Studio à partir du code existant, comme décrit dans la section [Créer un projet à partir de fichiers existants](#create-project-from-existing-files).

![icône d’appareil photo pour la vidéo](../install/media/video-icon.png "Regarder une vidéo") [profonde : utilisez le contrôle de code source avec les projets python](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8 millions 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Ajouter des fichiers, attribuer un fichier de démarrage et définir des environnements

Quand vous développez votre application, vous devez généralement ajouter de nouveaux fichiers de différents types au projet. Pour ajouter de tels fichiers, cliquez avec le bouton droit sur le projet et sélectionnez **Ajouter** un  >  **élément existant** avec lequel vous recherchez un fichier à ajouter, ou **Ajoutez** un  >  **nouvel élément**, qui affiche une boîte de dialogue avec un large éventail de modèles d’élément. Comme décrit dans la référence [Modèle d’élément](python-item-templates.md), les options incluent des fichiers Python vides, une classe Python, un test unitaire et divers fichiers associés aux applications web. Vous pouvez explorer ces options avec un projet de test pour savoir ce qui est disponible dans votre version de Visual Studio.

Chaque projet Python comprend un fichier de démarrage attribué, indiqué en gras dans **l’Explorateur de solutions**. Le fichier de démarrage est le fichier qui est exécuté quand vous démarrez le débogage (F5 **ou Déboguer**  >  **Démarrer le débogage**) ou lorsque vous exécutez votre projet dans la fenêtre **interactive** (**MAJ** + **ALT** + **F5** ou **Déboguer**  >  **exécuter le projet dans python interactive**). Pour le modifier, cliquez avec le bouton droit sur le nouveau fichier et sélectionnez **Définir comme élément de démarrage** (ou **Définir comme fichier de démarrage** dans les versions antérieures de Visual Studio).

> [!Tip]
> Si vous supprimez le fichier de démarrage sélectionné d’un projet et que vous n’en sélectionnez pas un autre, Visual Studio ne sait pas avec quel fichier Python démarrer lorsque vous essayez d’exécuter le projet. Dans ce cas, Visual Studio 2017 versions 15.6 et ultérieures présente une erreur ; les versions antérieures ouvrent une fenêtre de sortie avec l’interpréteur Python en cours d’exécution, ou la fenêtre de sortie s’affiche mais disparaît presque immédiatement. Si vous rencontrez l’un de ces comportements, vérifiez que vous avez un fichier de démarrage assigné.
>
> Si vous voulez maintenir la fenêtre de sortie ouverte pour une raison quelconque, cliquez avec le bouton droit sur le projet, sélectionnez **Propriétés**, sélectionnez l’onglet **Déboguer**, puis ajoutez `-i` au champ **Arguments de l’interpréteur**. Cet argument fait en sorte que l’interpréteur passe en mode interactif à la fin d’un programme, ce qui maintient la fenêtre ouverte jusqu’à ce que vous entriez **CTRL** + **Z**  >  **entrée** pour quitter.

::: moniker range="vs-2017"
Un nouveau projet est toujours associé à l’environnement Python global par défaut. Pour associer le projet à un autre environnement (y compris les environnements virtuels), cliquez avec le bouton droit sur le nœud **Environnements Python** du projet, sélectionnez **Add/Remove Python Environments** (Ajouter/supprimer des environnement Python) et sélectionnez ceux que vous souhaitez.
::: moniker-end
::: moniker range=">=vs-2019"
Un nouveau projet est toujours associé à l’environnement Python global par défaut. Pour associer le projet à un autre environnement (y compris les environnements virtuels), cliquez avec le bouton droit sur le nœud **Environnements Python** du projet, sélectionnez **Ajouter un environnement...** et sélectionnez ceux que vous souhaitez. Vous pouvez également utiliser le contrôle de liste déroulante des environnements de la barre d’outils pour en sélectionner ou en ajouter un autre pour le projet.

![Ajouter une commande d’environnement dans la barre d’outils Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Pour modifier l’environnement actif, cliquez avec le bouton droit sur l’environnement souhaité dans l’**Explorateur de solutions** et sélectionnez **Activer l’environnement** comme indiqué ci-dessous. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](selecting-a-python-environment-for-a-project.md).

![Activation d’un environnement pour un projet Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Modèles de projet

Visual Studio vous propose diverses méthodes pour configurer un projet Python, que ce soit à partir de zéro ou en utilisant du code existant. Pour utiliser un modèle, sélectionnez la   >    >  commande de menu fichier nouveau **projet** , ou cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** et sélectionnez **Ajouter**  >  **un nouveau projet**, tous deux qui affichent la boîte de dialogue **nouveau projet** ci-dessous. Pour afficher les modèles spécifiques à python, effectuez une recherche sur « Python » ou sélectionnez le  >  nœud **python** installé :

![Boîte de dialogue Nouveau projet avec les modèles Python](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

Le tableau suivant résume les modèles disponibles dans Visual Studio 2017 (tous les modèles ne sont pas disponibles dans toutes les versions antérieures) :

| Modèle | Description |
| --- | --- |
| [**À partir de code Python existant**](#create-project-from-existing-files) | Crée un projet Visual Studio à partir du code Python existant dans une structure de dossiers.  |
| **Application Python** | Une structure de projet de base pour une nouvelle application Python avec un fichier source unique et vide. Par défaut, le projet s’exécute dans l’interpréteur de la console de l’environnement global par défaut, que vous pouvez modifier en [attribuant un autre environnement](selecting-a-python-environment-for-a-project.md). |
| [**Service Cloud Azure**](python-azure-cloud-service-project-template.md) | Un projet pour un service cloud Azure écrit en langage Python. |
| [**Projets Web**](python-web-application-project-templates.md) | Projets pour les applications web basées sur différents frameworks, notamment Bottle, Django et Flask. |
| **Application IronPython** | Semblable au modèle Python Application (Application Python), mais utilise IronPython par défaut pour l’activation de l’interopérabilité .NET et le débogage en mode mixte avec les langages .NET. |
| **Application WPF IronPython** | Une structure de projet utilisant IronPython avec les fichiers XAML Windows Presentation Foundation pour l’interface utilisateur de l’application. Visual Studio fournit un concepteur d’interface utilisateur XAML, code-behind peut être écrit en langage Python et l’application s’exécute sans affichage d’une console. |
| **Page web Silverlight IronPython** | Un projet IronPython qui s’exécute dans un navigateur à l’aide de Silverlight. Le code Python de l’application est inclus dans la page web en tant que script. Une balise de script réutilisable extrait du code JavaScript qui initialise IronPython s’exécutant dans Silverlight, à partir duquel votre code Python peut interagir avec DOM. |
| **Application Windows Forms IronPython** | Une structure de projet utilisant IronPython avec l’interface utilisateur créée à partir du code avec Windows Forms. L’application s’exécute sans affichage d’une console. |
| **Application d’arrière-plan (IoT)** | Prend en charge le déploiement de projets Python pour une exécution en tant que services d’arrière-plan sur les appareils. Visitez le [centre de développement Windows IoT](https://dev.windows.com/en-us/iot) pour plus d’informations. |
| **Module d’extension Python** | Ce modèle s’affiche sous Visual C++ si vous avez installé les **Outils de développement natifs Python** avec la charge de travail Python dans Visual Studio 2017 ou ultérieur (consultez [Installation](installing-python-support-in-visual-studio.md)). Il fournit la structure de base pour une DLL d’extension C++, similaire à ce qui est décrit dans [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md). |
::: moniker-end

::: moniker range=">=vs-2019"

Le tableau suivant récapitule les modèles disponibles dans Visual Studio 2019 (tous les modèles ne sont pas disponibles dans toutes les versions précédentes) :

| Modèle | Description |
| --- | --- |
| [**À partir de code Python existant**](#create-project-from-existing-files) | Crée un projet Visual Studio à partir du code Python existant dans une structure de dossiers.  |
| **Application Python** | Une structure de projet de base pour une nouvelle application Python avec un fichier source unique et vide. Par défaut, le projet s’exécute dans l’interpréteur de la console de l’environnement global par défaut, que vous pouvez modifier en [attribuant un autre environnement](selecting-a-python-environment-for-a-project.md). |
| [**Projets Web**](python-web-application-project-templates.md) | Projets pour les applications web basées sur différents frameworks, notamment Bottle, Django et Flask. |
| **Application IronPython** | Semblable au modèle Python Application (Application Python), mais utilise IronPython par défaut pour l’activation de l’interopérabilité .NET et le débogage en mode mixte avec les langages .NET. |
| **Application WPF IronPython** | Une structure de projet utilisant IronPython avec les fichiers XAML Windows Presentation Foundation pour l’interface utilisateur de l’application. Visual Studio fournit un concepteur d’interface utilisateur XAML, code-behind peut être écrit en langage Python et l’application s’exécute sans affichage d’une console. |
| **Page web Silverlight IronPython** | Un projet IronPython qui s’exécute dans un navigateur à l’aide de Silverlight. Le code Python de l’application est inclus dans la page web en tant que script. Une balise de script réutilisable extrait du code JavaScript qui initialise IronPython s’exécutant dans Silverlight, à partir duquel votre code Python peut interagir avec DOM. |
| **Application Windows Forms IronPython** | Une structure de projet utilisant IronPython avec l’interface utilisateur créée à partir du code avec Windows Forms. L’application s’exécute sans affichage d’une console. |
| **Application d’arrière-plan (IoT)** | Prend en charge le déploiement de projets Python pour une exécution en tant que services d’arrière-plan sur les appareils. Visitez le [centre de développement Windows IoT](https://dev.windows.com/en-us/iot) pour plus d’informations. |
| **Module d’extension Python** | Ce modèle s’affiche sous Visual C++ si vous avez installé les **Outils de développement natifs Python** avec la charge de travail Python dans Visual Studio 2017 ou ultérieur (consultez [Installation](installing-python-support-in-visual-studio.md)). Il fournit la structure de base pour une DLL d’extension C++, similaire à ce qui est décrit dans [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md). |
::: moniker-end

> [!Note]
> Python étant un langage interprété, les projets Python dans Visual Studio ne produisent aucun exécutable autonome, comme d’autres projets de langage compilé (C#, par exemple). Pour plus d’informations, consultez [Questions et réponses](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Créer un projet à partir de fichiers existants

> [!Important]
> Le processus décrit ici ne déplace pas ou ne copie pas les fichiers sources d’origine. Si vous voulez travailler avec une copie, dupliquez d’abord le dossier.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Fichiers liés

Les fichiers liés sont les fichiers placés dans un projet, mais qui se trouvent généralement en dehors des dossiers du projet de l’application. Ils apparaissent dans **l’Explorateur de solutions** en tant que fichiers normaux avec une icône de raccourci superposée : ![Icône de fichier lié](media/projects-linked-file-icon.png)

Les fichiers liés sont spécifiés dans le fichier *.pyproj* à l’aide de l’élément `<Compile Include="...">`. Les fichiers liés sont implicites s’ils utilisent un chemin d’accès relatif en dehors de la structure de répertoires, ou explicite s’ils utilisent des chemins d’accès dans **Explorateur de solutions**:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Les fichiers liés sont ignorés si l’une des conditions suivantes se présente :

- Le fichier lié contient les métadonnées de lien, et le chemin d’accès spécifié dans l’attribut Include se trouve dans le répertoire du projet.
- Le fichier lié duplique un fichier qui existe dans l’arborescence du projet
- Le fichier lié contient les métadonnées de lien, et le chemin de lien est un chemin d’accès relatif en dehors de l’arborescence du projet.
- Le chemin de lien est associé à une racine.

### <a name="work-with-linked-files"></a>Utiliser des fichiers liés

Pour ajouter un élément existant en tant que lien, cliquez avec le bouton droit sur le dossier du projet dans lequel vous souhaitez ajouter le fichier, puis sélectionnez **Ajouter** un  >  **élément existant**. Dans la boîte de dialogue qui s’affiche, sélectionnez un fichier et choisissez **Ajouter en tant que lien** dans la liste déroulante du bouton **Ajouter**. Si aucun fichier n’est en conflit, cette commande crée un lien dans le dossier sélectionné. Toutefois, le lien n’est pas ajouté s’il existe déjà un fichier portant le même nom ou si un lien vers ce fichier existe déjà dans le projet.

Si vous tentez de créer un lien vers un fichier qui existe déjà dans les dossiers du projet, il est ajouté en tant que fichier normal et non en tant que lien. Pour convertir un fichier en lien, sélectionnez **fichier**  >  **Enregistrer sous** pour enregistrer le fichier dans un emplacement en dehors de la hiérarchie de projet. Visual Studio le convertit automatiquement en lien. De même, un lien peut être reconverti en utilisant **fichier**  >  **Enregistrer sous** pour enregistrer le fichier quelque part dans la hiérarchie du projet.

Si vous déplacez un fichier lié dans **l’Explorateur de solutions**, le lien est déplacé, mais le fichier en lui-même n’est pas affecté. De même, la suppression d’un lien supprime le lien sans affecter le fichier.

Les fichiers liés ne peuvent pas être renommés.

## <a name="references"></a>Références

Les projets Visual Studio prennent en charge l’ajout de références aux projets et aux extensions, qui apparaissent sous le nœud **Références** dans **l’Explorateur de solutions** :

![Références d’extension dans les projets Python](media/projects-extension-references.png)

En général, les références d’extension indiquent les dépendances entre les projets et sont utilisées pour proposer IntelliSense au moment de la conception ou lors de la création de lien au moment de la compilation. Les projets Python utilisent des références de la même manière, mais en raison de la nature dynamique de Python, elles sont principalement utilisées au moment de la conception pour proposer des fonctionnalités IntelliSense améliorées. Elles peuvent également servir pour le déploiement sur Microsoft Azure, afin d’installer des dépendances supplémentaires.

### <a name="extension-modules"></a>Modules d’extension

Une référence à un fichier *.pyd* permet d’activer IntelliSense pour le module généré. Visual Studio charge le fichier *.pyd* dans l’interpréteur Python et pratique une introspection de ses types et fonctions. Il essaie également d’analyser les chaînes de document des fonctions, afin de fournir l’assistance pour la signature.

Si le module d’extension est mis à jour sur le disque, Visual Studio réanalyse le module en arrière-plan. Cette action n’a aucun effet sur le comportement au moment de l’exécution, mais certaines saisies semi-automatiques ne sont pas disponibles tant que l’analyse n’est pas terminée.

En outre, vous devrez peut-être ajouter un [chemin de recherche](search-paths.md) dans le dossier qui contient le module.

### <a name="net-projects"></a>Projets .NET

Quand vous utilisez IronPython, vous pouvez ajouter des références aux assemblys .NET pour activer IntelliSense. Pour les projets .NET dans votre solution, cliquez avec le bouton droit sur le nœud **Références** de votre projet Python, sélectionnez **Ajouter une référence**, puis l’onglet **Projets** et accédez au projet de votre choix. Pour les DLL que vous avez téléchargés séparément, sélectionnez plutôt l’onglet **Parcourir** et accédez au DLL de votre choix.

Les références dans IronPython n’étant pas disponibles tant qu’aucun appel à `clr.AddReference('<AssemblyName>')` n’a été émis, il est également nécessaire d’ajouter un appel `clr.AddReference` adéquat à l’assembly. En général, il est inséré au début du code. Par exemple, le code créé par le modèle de projet **Application Windows Forms IronPython** dans Visual Studio comporte deux appels en haut du fichier :

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Projets WebPI

Vous pouvez ajouter des références aux entrées de produit WebPI pour le déploiement sur Microsoft Azure Cloud Services où vous pouvez installer des composants supplémentaires via le flux WebPI. Par défaut, le flux affiché est spécifique à Python et inclut Django, CPython et d’autres composants de base. Vous pouvez également sélectionner votre propre flux comme illustré ci-dessous. Lorsque vous publiez vers Microsoft Azure, une tâche d’installation installe tous les produits référencés.

> [!IMPORTANT]
> Les projets WebPI ne sont pas disponibles dans Visual Studio 2017 ou Visual Studio 2019.

![Références WebPI](media/projects-webPI-components.png)
