---
title: Projets Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 8ae79f6b8e7eb87c0138b0152d8f9ce46eac9a69
ms.lasthandoff: 03/10/2017

---

# <a name="python-projects"></a>Projets Python

Les applications Python sont généralement définies à l’aide de fichiers et de dossiers uniquement, mais cela peut s’avérer complexe à mesure que les applications deviennent plus volumineuses et impliquent éventuellement des fichiers générés automatiquement, JavaScript pour les applications web, etc. Vous pouvez créer des projets Visual Studio pour les applications Python, afin de gérer cette complexité. Un projet Python (un fichier `.pyproj`) identifie tous les fichiers source et de contenu associés à votre projet, contient des informations de génération pour chaque fichier, conserve les informations pour l’intégration aux systèmes de contrôle de code source et vous permet d’organiser votre application en composants logiques.

En outre, les projets sont toujours gérés dans une *solution* Visual Studio, qui peut contenir n’importe quel nombre de projets pouvant faire référence les uns aux autres. Par exemple, un projet Python peut faire référence à un projet C++ pour un module d’extension, de façon que Visual Studio génère automatiquement le projet C++ (si nécessaire) lorsque vous commencez à déboguer le projet Python. (Pour des informations d’ordre général à ce sujet, consultez [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

![Projet Python dans l’Explorateur de solutions](media/projects-solution-explorer.png)

Visual Studio fournit divers modèles de projet Python pour configurer rapidement un certain nombre de structures d’application, y compris un modèle pour créer un projet à partir d’une arborescence de dossiers existante et un modèle pour créer un projet propre et vide. Consultez la section [Modèles de projet](#project-templates) ci-dessous pour un index.

Dans cette rubrique :

- [Ajout de fichiers, attribution d’un fichier de démarrage et définition des environnements](#adding-file-assigning-a-startup-file-and-setting-environments)
- [Modèles de projet](#project-templates)
- [Fichiers liés](#linked-files)
- [Références](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> Même sans projet, Visual Studio fonctionne bien avec le code Python, car vous pouvez ouvrir un fichier Python seul et profiter de la saisie semi-automatique, d’IntelliSense et du débogage (en cliquant avec le bouton droit dans l’éditeur et en sélectionnant **Start [with | without] Debugging** (Démarrer [avec | sans] débogage)). Étant donné que ce code utilisera toujours l’environnement global par défaut, vous pouvez toutefois rencontrer des saisies semi-automatiques incorrectes ou des erreurs si le code est destiné à un autre environnement. En outre, Visual Studio analyse tous les fichiers et packages dans le dossier à partir duquel le fichier unique est ouvert, ce qui peut consommer beaucoup de temps processeur.
>
> Il est très simple de créer un projet Visual Studio à partir du code existant, comme décrit ci-dessous dans la section [Création d’un projet à partir de fichiers existants](#creating-a-project-from-existing-files).

Pour une introduction aux projets Python dans Visual Studio, visionnez la vidéo [Getting Started with Python Tools Part 2: Projects](https://youtu.be/KHPoVpL7zHg?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Prise en main de Python Tools, partie 2 : Projets ; youtube.com, 3 min18 s).

> [!VIDEO https://www.youtube.com/embed/KHPoVpL7zHg]

Visionnez également la vidéo [Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM) (Expérience approfondie : Utilisation du contrôle de code source avec les projets Python ; youtube.com, 8 min55 s).

> [!VIDEO https://www.youtube.com/embed/Aq8eqApnugM]


## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Ajout de fichiers, attribution d’un fichier de démarrage et définition des environnements

Lorsque vous développez votre application, vous devez généralement ajouter des fichiers de différents types pour le projet. Vous pouvez le faire en cliquant avec le bouton droit sur le projet et en sélectionnant **Ajouter > Élément existant...** pour rechercher un fichier à ajouter, ou en sélectionnant **Ajouter > Nouvel élément...**, qui affiche une boîte de dialogue avec un large éventail de modèles d’élément, y compris des fichiers Python vides, une classe Python, un test unitaire et divers fichiers associés aux applications web. Nous vous encourageons à explorer ces options avec un projet de test pour savoir ce qui est disponible dans votre version de Visual Studio.

Chaque projet Python comprend un fichier de démarrage attribué, indiqué en gras dans l’Explorateur de solutions. Il s’agit du fichier qui est exécuté lorsque vous démarrez le débogage (F5 ou **Déboguer > Démarrer le débogage**) ou exécutez votre projet dans la fenêtre interactive (Maj+Alt+F5 ou **Déboguer > Execute Project in Python Interactive** (Exécuter le projet dans la fenêtre interactive de Python)). Pour changer de fichier de démarrage, cliquez sur le nouveau fichier et sélectionnez **Set as Startup File** (Définir comme fichier de démarrage).

Un nouveau projet est toujours associé à l’environnement Python global par défaut. Pour associer le projet à un autre environnement (y compris les environnements virtuels), cliquez avec le bouton droit sur le nœud **Environnements Python** du projet, sélectionnez **Add/Remove Python Environments** (Ajouter/supprimer des environnement Python) et sélectionnez ceux que vous souhaitez. Pour modifier l’environnement actif, cliquez avec le bouton droit sur l’environnement souhaité et sélectionnez **Activate Environment** (Activer l’environnement) comme indiqué ci-dessous. Pour plus d’informations, consultez [Environnements Python](python-environments.md#project-specific-environments).

![Activation d’un environnement pour un projet Python](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>Modèles de projet

Visual Studio vous propose diverses méthodes pour configurer un projet Python, que ce soit à partir de zéro ou en utilisant du code existant. Pour utiliser un modèle, sélectionnez la commande de menu **Fichier > Nouveau > Projet...** ou cliquez avec le bouton droit sur la solution dans l’Explorateur de solutions, puis sélectionnez **Ajouter > Nouveau projet...**. Ces deux options permettent d’afficher la boîte de dialogue **Nouveau projet** ci-dessous. Pour afficher les modèles spécifiques à Python, effectuez une recherche sur « Python » ou sélectionnez le nœud **Modèles > Autres langages > Python** :

![Boîte de dialogue Nouveau projet avec les modèles Python](media/projects-new-project-dialog.png)

Le tableau suivant résume les modèles disponibles dans Visual Studio 2017 (tous les modèles ne sont pas disponibles dans toutes les versions antérieures) :

| Modèle | Description | 
| --- | --- |
| [From Existing Python Code](#creating-a-project-from-existing-files) (À partir du code Python existant) | Crée un projet Visual Studio à partir du code Python existant dans une structure de dossiers.  |
| Python Application (Application Python) | Une structure de projet de base pour une nouvelle application Python avec un fichier source unique et vide. Par défaut, le projet s’exécute dans l’interpréteur de la console de l’environnement global par défaut, que vous pouvez modifier en [attribuant un autre environnement](python-environments.md#project-specific-environments). |
| [Azure Cloud Service](template-azure-cloud-service.md) (Service cloud Azure) | Un projet pour un service cloud Azure écrit en langage Python. |
| [Projets Web](template-web.md) | Projets pour les serveurs web basés sur différentes infrastructures, notamment Bottle, Django, Flask et Flask/Jade. |
| IronPython Application (Application IronPython) | Semblable au modèle Python Application (Application Python), mais utilise IronPython par défaut pour l’activation de l’interopérabilité .NET et le débogage en mode mixte avec les langages .NET. |
| IronPython WPF Application (Application WPF IronPython) | Une structure de projet utilisant IronPython avec les fichiers XAML Windows Presentation Foundation pour l’interface utilisateur de l’application. Visual Studio fournit un concepteur d’interface utilisateur XAML, code-behind peut être écrit en langage Python et l’application s’exécute sans affichage d’une console. |
| IronPython Silverlight Web Page (Page web Silverlight IronPython) | Un projet IronPython qui s’exécute dans un navigateur à l’aide de Silverlight. Le code Python de l’application est inclus dans la page web en tant que script. Une balise de script réutilisable extrait du code JavaScript qui initialise IronPython s’exécutant dans Silverlight, à partir duquel votre code Python peut interagir avec DOM. |
| IronPython Windows Forms Application (Application Windows Forms IronPython) | Une structure de projet utilisant IronPython avec l’interface utilisateur créée à partir du code avec Windows Forms. L’application s’exécute sans affichage d’une console. |
| Background Application (IoT) (Application d’arrière-plan (IoT)) | Prend en charge le déploiement de projets Python pour une exécution en tant que services d’arrière-plan sur les appareils. Visitez le [centre de développement Windows IoT](https://dev.windows.com/en-us/iot) pour plus d’informations. |

<a name="create-project-from-existing-files"</a>
### <a name="creating-a-project-from-existing-files"></a>Création d’un projet à partir de fichiers existants

1. Sélectionnez le menu **Fichier > Nouveau > Projet...**, puis sélectionnez le modèle **From Existing Python Code** (À partir du code Python existant).
1. Dans la boîte de dialogue suivante, définissez le chemin d’accès à votre code existant, un filtre pour les types de fichier et les chemins de recherche nécessaires à votre projet, puis sélectionnez **Suivant** :

    ![Nouveau projet à partir du code existant, étape&1;](media/projects-from-existing-1.png)

1. Choisissez un environnement pour le projet et le fichier de démarrage, puis appuyez sur **Suivant**. (Notez que la boîte de dialogue affiche uniquement les fichiers dans la racine de l’arborescence de dossiers ; si le fichier que vous souhaitez utilisé se trouve dans un sous-dossier, laissez le champ correspondant au fichier de démarrage vide et définissez-le ultérieurement dans l’Explorateur de solutions).

    ![Nouveau projet à partir du code existant, étape&2;](media/projects-from-existing-2.png)

1. Sélectionnez l’emplacement pour enregistrer le fichier projet (cette opération ne déplace et ne copie pas les fichiers source d’origine ; si vous souhaitez une copie, vous devez la faire avant d’utiliser le modèle). Dans cette boîte de dialogue, vous pouvez également inclure la détection automatique des environnements virtuels et personnaliser le projet pour différentes infrastructures web.

    ![Nouveau projet à partir du code existant, étape&3;](media/projects-from-existing-3.png)

1.  Sélectionnez **Terminer**, et Visual Studio crée le projet et l’ouvre dans l’Explorateur de solutions. Si vous souhaitez déplacer le fichier .pyproj, sélectionnez-le dans l’Explorateur de solutions et choisissez **Fichier > Enregistrer sous**. Cela met à jour les références de fichier dans le projet, mais ne déplace pas de fichier de code.

## <a name="linked-files"></a>Fichiers liés

Les fichiers liés sont ceux qui sont placés dans un projet, mais qui se trouvent généralement en dehors des dossiers du projet de l’application. Ils apparaissent dans l’Explorateur de solutions en tant que fichiers normaux avec une icône de raccourci superposée : ![Icône de fichier lié](media/projects-linked-file-icon.png)

Les fichiers liés sont spécifiés dans le fichier `.pyproj` à l’aide de l’élément `<Compile Include="...">` normal. Ils peuvent être implicites s’ils utilisent un chemin d’accès relatif en dehors de la structure de répertoires, ou explicites en spécifiant leur chemin d’accès dans l’Explorateur de solutions :

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Les fichiers liés sont ignorés si l’une des conditions suivantes se présente :

- Le fichier lié contient les métadonnées de lien, et le chemin d’accès spécifié dans l’attribut Include se trouve dans le répertoire du projet.
- Le fichier lié duplique un fichier qui existe dans l’arborescence du projet.
- Le fichier lié contient les métadonnées de lien, et le chemin de lien est un chemin d’accès relatif en dehors de l’arborescence du projet.
- Le chemin de lien est associé à une racine.

### <a name="working-with-linked-files"></a>Utilisation des fichiers liés

Pour ajouter un élément existant en tant que lien, cliquez avec le bouton droit sur le dossier du projet dans lequel vous souhaitez ajouter le fichier, puis sélectionnez **Ajouter > Élément existant...**. Dans la boîte de dialogue qui s’affiche, sélectionnez un fichier et choisissez **Ajouter en tant que lien** dans la liste déroulante du bouton **Ajouter**. Si aucun fichier n’est en conflit, cela crée un lien dans le dossier sélectionné. Toutefois, le lien n’est pas ajouté s’il existe déjà un fichier portant le même nom ou si un lien vers ce fichier existe déjà dans le projet.

Si vous tentez de créer un lien vers un fichier qui existe déjà dans les dossiers du projet, il sera ajouté en tant que fichier normal et non en tant que lien. Pour convertir un fichier en lien, sélectionnez **Fichier > Enregistrer sous** pour enregistrer le fichier à un emplacement en dehors de l’arborescence du projet ; Visual Studio le convertira automatiquement en lien. De même, un lien peut être reconverti en fichier à l’aide de **Fichier > Enregistrer sous** pour enregistrer le fichier quelque part dans l’arborescence du projet. 

Si vous déplacez un fichier lié dans l’Explorateur de solutions, le lien est déplacé, mais le fichier en lui-même n’est pas affecté. De même, la suppression d’un lien supprime le lien sans affecter le fichier.

Les fichiers liés ne peuvent pas être renommés.

## <a name="references"></a>Références

Les projets Visual Studio prennent en charge l’ajout de références aux projets et aux extensions, qui apparaissent sous le nœud **Références** dans l’Explorateur de solutions :

![Références d’extension dans les projets Python](media/projects-extension-references.png)

En général, les références d’extension indiquent les dépendances entre les projets et sont utilisées pour proposer IntelliSense au moment de la conception ou lors de la création de lien au moment de la compilation. Les projets Python utilisent des références de la même manière, mais en raison de la nature dynamique de Python, elles sont principalement utilisées au moment de la conception pour proposer des fonctionnalités IntelliSense améliorées. Elles peuvent également servir pour le déploiement sur Microsoft Azure, afin d’installer des dépendances supplémentaires.

### <a name="extension-modules"></a>Modules d’extension

Une référence à un fichier `.pyd` permet d’activer IntelliSense pour le module généré. Visual Studio charge le fichier `.pyd` dans l’interpréteur Python et pratique une introspection de ses types et fonctions. Il essaie également d’analyser les chaînes de document des fonctions, afin de fournir l’assistance pour la signature.

Si le module d’extension est mis à jour sur le disque, Visual Studio analyse de nouveau le module en arrière-plan. Cela n’a aucun effet sur le comportement du runtime, mais certaines saisies semi-automatiques ne seront pas disponibles tant que l’analyse ne sera pas terminée.

En outre, vous devrez peut-être ajouter un [chemin de recherche](python-environments.md#search-paths) dans le dossier qui contient le module.

### <a name="net-projects"></a>Projets .NET

Lorsque vous travaillez avec IronPython, vous pouvez ajouter des références aux assemblys .NET pour activer IntelliSense. Pour les projets .NET dans votre solution, cliquez avec le bouton droit sur le nœud **Références** de votre projet Python, sélectionnez **Ajouter une référence**, puis l’onglet **Projets** et accédez au projet de votre choix. Pour les DLL que vous avez téléchargés séparément, sélectionnez plutôt l’onglet **Parcourir** et accédez au DLL de votre choix.

Les références dans IronPython n’étant pas disponibles tant qu’un appel à `clr.AddReference('AssemblyName')` n’est pas réalisé, vous devrez également ajouter un appel `clr.AddReference` à l’assembly.

### <a name="webpi-projects"></a>Projets WebPI

Vous pouvez ajouter des références aux entrées de produit WebPI pour le déploiement sur Microsoft Azure Cloud Service où vous pouvez installer des composants supplémentaires via le flux WebPI. Par défaut, le flux affiché est spécifique à Python et inclut Django, CPython et d’autres composants de base. Vous pouvez également sélectionner votre propre flux comme illustré ci-dessous. Lorsque vous publiez vers Microsoft Azure, une tâche d’installation installe tous les produits référencés.

![Références WebPI](media/projects-webPI-components.png)
