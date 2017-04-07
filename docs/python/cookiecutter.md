---
title: Extension CookieCutter avec Python Tools pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 783da5fd-726c-4716-994e-aa04d6b75896
caps.latest.revision: 1
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
ms.openlocfilehash: e9a822b98d4cbcf2fd52d96a199e596cec4e2c3b
ms.lasthandoff: 03/10/2017

---

# <a name="using-the-cookiecutter-extension"></a>Utilisation de l’extension Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fournit une interface utilisateur graphique pour découvrir des modèles, des options de modèle d’entrée et créer des projets et des fichiers. Cette extension est incluse avec Visual Studio 2017 et peut être installée séparément dans les versions antérieures de Visual Studio.

Cookiecutter nécessite Python 3.3 ou version ultérieure (32 ou 64 bits) ou Anaconda 3 4.2 ou version ultérieure (32 ou 64 bits). Si aucun interpréteur Python approprié n’est disponible, Visual Studio affiche un avertissement. Si vous installez un interpréteur Python pendant l’exécution de Visual Studio, cliquez sur le bouton Accueil dans la barre d’outils Cookiecutter pour détecter l’interpréteur nouvellement installé.

Une fois l’installation terminée, sélectionnez **Affichage > Cookiecutter Explorer** (Explorateur Cookiecutter) pour ouvrir sa fenêtre :

![Fenêtre principale Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Flux de travail Cookiecutter

L’utilisation de Cookiecutter est un processus de navigation et de sélection d’un modèle, son clonage sur votre ordinateur local, la définition des options, puis la création de code à partir de ce modèle, comme décrit dans les sections suivantes.

### <a name="browsing-templates"></a>Modèles de navigation

La page d’accueil Cookiecutter affiche une liste des modèles que vous pouvez choisir, organisés selon les groupes suivants :

| Regrouper | Description | 
| --- | --- |
| Installé | Les modèles qui ont été installés sur votre ordinateur local. Lorsqu’un modèle en ligne est utilisé, son référentiel est automatiquement cloné dans un sous-dossier de `~/.cookiecutters`. Vous pouvez supprimer un modèle installé sélectionné en appuyant sur **Suppr**. |
| Recommandé | Les modèles chargés à partir du flux recommandé. Le flux par défaut est organisé par Microsoft. Consultez la section [Options de Cookiecutter](#cookiecutter-options) ci-dessous pour plus d’informations sur la personnalisation du flux. |
| GitHub | Les résultats de recherche GitHub pour le mot clé cookiecutter. Les résultats de GitHub reviennent paginés ; si plus de résultats sont disponibles, **Load More** (Charger plus) apparaît à la fin de la liste. |
| Personnalisé | Lorsqu’un emplacement personnalisé est entré dans la zone de recherche, il apparaît dans ce groupe. Vous pouvez renseigner un chemin complet vers le référentiel GitHub, ou le chemin complet vers un dossier sur votre disque local. |

### <a name="cloning"></a>clonage

Lorsque vous sélectionnez un modèle suivi par **Suivant**, Cookiecutter fait une copie locale à partir de laquelle travailler.

Si vous sélectionnez un modèle à partir des groupes **Recommandé** ou **GitHub** ou si vous saisissez une URL personnalisée dans la zone de recherche et sélectionnez ce modèle, il est cloné et installé sur votre ordinateur local. Si ce modèle a été installé dans une session précédente de Visual Studio, il est automatiquement supprimé et la version la plus récente est clonée.

Si vous sélectionnez un modèle à partir du groupe **Installé** ou si vous saisissez un chemin d’accès au dossier personnalisé dans la zone de recherche et sélectionnez ce modèle, Visual Studio charge ce modèle sans effectuer de clonage.

> [!Important]
> Les modèles de Cookiecutter sont clonés dans un seul dossier `~/.cookiecutters`. Chaque sous-dossier est nommé d’après le nom du référentiel git, qui n’inclut pas le nom d’utilisateur GitHub. Des conflits peuvent se produire si vous clonez différents modèles portant le même nom mais provenant de divers auteurs. Dans ce cas, Cookiecutter vous empêche d’écraser le modèle existant avec un autre modèle du même nom. Pour installer l’autre modèle, vous devez d’abord supprimer le modèle existant.

### <a name="setting-template-options"></a>Définition des options de modèle

Une fois le modèle installé localement, Cookiecutter affiche une page d’options dans laquelle vous pouvez spécifier l’endroit où Cookiecutter doit générer des fichiers, ainsi que d’autres options :

![Page d’options de Cookiecutter](media/cookiecutter-template-options.png)

Chaque modèle Cookiecutter définit son propre ensemble d’options et spécifie une valeur par défaut pour chacune d’elles (affichée en tant que texte suggéré dans chaque champ d’entrée). Une valeur par défaut peut être un extrait de code, souvent lorsqu’il s’agit d’une valeur dynamique qui utilise d’autres options. 

Il est possible de personnaliser les valeurs par défaut pour des options spécifiques avec un fichier de configuration utilisateur. Lorsque l’extension Cookiecutter détecte un fichier de configuration utilisateur, elle remplace les valeurs par défaut du modèle avec des valeurs par défaut de la configuration de l’utilisateur. Ce sujet est abordé dans la section [User Config (0.7.0+)](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) (Configuration utilisateur (0.7.0+)) de la documentation Cookiecutter.

Si le modèle indique des tâches Visual Studio spécifiques à exécuter après la génération du code, une option **Run additional tasks on completion** (Exécuter des tâches supplémentaires à la fin) s’affiche et vous permet de refuser ces tâches. Les tâches consistent généralement à ouvrir un navigateur web, ouvrir des fichiers dans l’éditeur, installer des dépendances, etc.

### <a name="create"></a>Créer

Une fois vos options définies, sélectionnez **Créer** pour générer du code. Notez que si le dossier de sortie n’est pas vide, un avertissement apparaîtra. Si vous êtes familier avec la sortie du modèle et si remplacer fichiers ne vous dérange pas, vous pouvez ignorer l’avertissement. Sinon, sélectionnez **Annuler**, spécifiez un dossier vide, puis copiez manuellement les fichiers créés dans votre dossier de sortie non vide.

Une fois les fichiers créés, Cookiecutter propose une option permettant d’ouvrir les fichiers dans **l’Explorateur de solutions** :

![Commande de Cookiecutter affichant l’Explorateur de solutions](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Options de Cookiecutter

Les options de Cookiecutter sont accessibles via **Outils > Options > Cookiecutter** :

![Options de Cookiecutter](media/cookiecutter-tools-options.png)

| Option | Description |
| --- | --- |
| Recommended Feed URL (URL de flux recommandé) | L’emplacement du flux de modèles recommandé. Il peut s’agir d’une URL ou d’un chemin d’accès à un fichier local. Laissez l’URL vide pour utiliser le flux organisé par Microsoft par défaut. Le flux fournit une simple liste d’emplacements de modèles, séparés par des sauts de ligne. Pour demander à modifier le flux organisé, effectuez une requête d’extraction dans [la source sur GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| Afficher l’aide | Contrôle la visibilité de la barre d’informations d’aide en haut de la fenêtre Cookiecutter. |

## <a name="optimizing-cookiecutter-templates-for-visual-studio"></a>Optimisation des modèles de Cookiecutter pour Visual Studio

Pour les bases de la création d’un modèle Cookiecutter, consultez la [documentation Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Notez que l’extension Cookiecutter pour Visual Studio prend en charge les modèles créés pour Cookiecutter v1.4.

Le rendu par défaut des variables d’un modèle varie selon le type de données (chaîne ou liste) :

- Chaîne : une étiquette pour le nom de variable, une zone de texte pour la saisie de valeur et un filigrane indiquant la valeur par défaut. L’info-bulle dans la zone de texte affiche la valeur par défaut.
- Liste : une étiquette pour le nom de variable, une zone de liste modifiable pour la sélection d’une valeur. L’info-bulle dans la zone de liste modifiable affiche la valeur par défaut.

Il est possible d’améliorer cela en spécifiant des métadonnées supplémentaires dans votre fichier `cookiecutter.json` qui est spécifique à Visual Studio (et ignoré par l’interface de ligne de commande de Cookiecutter). Toutes les propriétés sont facultatives :

| Propriété | Description |
| --- | --- |
| Ajouter des contrôles | Spécifie ce qui apparaît au-dessus de l’éditeur pour la variable, au lieu du nom de la variable. |
| Description | Spécifie l’info-bulle qui apparaît sur le contrôle d’édition qui affichera cette description, au lieu de la valeur par défaut de cette variable. |
| URL | Transforme l’étiquette en lien hypertexte, avec une info-bulle qui affiche l’URL. Cliquer sur le lien hypertexte redirigera vers cette URL en ouvrant le navigateur par défaut de l’utilisateur. |
| Sélecteur | Autorise la personnalisation de l’éditeur pour une variable. Les sélecteurs suivants sont actuellement pris en charge :<ul><li>`string` : zone de texte standard, valeur par défaut pour les chaînes.</li><li>`list` : zone de liste modifiable, valeur par défaut pour les listes.</li><li>`yesno` : zone de liste modifiable permettant de choisir entre `y` et `n`, pour les chaînes.</li><li>`odbcConnection` : zone de texte avec un bouton « ... » qui fait apparaître une boîte de dialogue de connexion de base de données.</li></ul> |

Exemple :

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="running-visual-studio-tasks"></a>Exécution de tâches Visual Studio

Cookiecutter dispose d’une fonctionnalité appelée *Post-Generate Hooks* (Hooks post-génération) qui permet l’exécution de code Python arbitraire une fois que les fichiers sont générés. Bien que flexible, cette fonctionnalité ne permet pas un accès facile à Visual Studio.

Par exemple, vous souhaitez peut-être ouvrir un fichier dans l’éditeur Visual Studio, ou dans son navigateur web, ou déclencher l’interface utilisateur Visual Studio qui invite l’utilisateur à créer un environnement virtuel et installer les spécifications d’un package.

Pour autoriser ces scénarios, Visual Studio recherche des métadonnées étendues dans `cookiecutter.json` qui décrivent les commandes à exécuter une fois que l’utilisateur a ouvert les fichiers générés dans l’Explorateur de solutions ou après que les fichiers ont été ajoutés à un projet existant. (Là encore, l’utilisateur peut refuser l’exécution des tâches en désactivant **Run additional tasks on completion** (Exécuter des tâches supplémentaires à la fin) dans les options de modèle.)

Exemple :

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Les commandes sont spécifiées par nom et doivent utiliser le nom non localisé (en anglais) pour travailler sur les installations localisées de Visual Studio. Vous pouvez tester et détecter les noms de commande dans la fenêtre Commande de Visual Studio.

Si vous souhaitez transmettre un seul argument, spécifiez-le en tant que chaîne, comme dans l’exemple précédent.

Si vous n’avez pas besoin de transmettre un argument, laissez une chaîne vide ou omettez-le dans JSON :

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Utilisez un tableau pour plusieurs arguments. Pour les commutateurs, diviser le commutateur et sa valeur en arguments distincts assure une mise entre guillemets appropriée. Exemple :

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Les arguments peuvent faire référence à d’autres variables Cookiecutter. Dans les exemples ci-dessus, la variable `_output_folder_path` interne est utilisée pour former un chemin d’accès absolu vers les fichiers générés.

Notez que la commande `Python.InstallProjectRequirements` fonctionne uniquement lorsque vous ajoutez des fichiers à un projet existant. Cela s’explique par le fait qu’elle est traitée par le projet Python dans l’Explorateur de solutions, et qu’il n’existe aucun projet pour recevoir le message une fois dans l’affichage des dossiers de l’Explorateur de solutions. Nous espérons corriger cette limitation dans une version ultérieure (une meilleure prise en charge de l’affichage des dossiers en général).

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="error-loading-template"></a>Erreur lors du chargement du modèle

Certains modèles peuvent utiliser des types de données non valides, tel que booléen, dans leur `cookiecutter.json`. Cela doit être signalé à l’auteur du modèle. Cliquez sur le lien **Problèmes** dans le volet d’informations du modèle.

### <a name="hook-script-failed"></a>Échec du script Hook

Certains modèles peuvent utiliser des scripts post-génération qui sont incompatibles avec l’interface utilisateur Cookiecutter. Par exemple, les scripts qui interrogent l’utilisateur à saisir des valeurs échoueront, faute de console de terminal.

### <a name="hook-script-not-supported-on-windows"></a>Script Hook non pris en charge sur Windows

Si le script post-génération est `.sh`, il peut ne pas être associé à une application sur votre ordinateur Windows. Une boîte de dialogue Windows peut s’afficher et vous demander de trouver une application compatible dans le Windows Store.

### <a name="templates-with-known-issues"></a>Modèles avec des problèmes connus

Échecs de clonage :

- **wildfish/cookiecutter-django-crud** (caractère non valide `|` dans le nom du sous-dossier)
- **cookiecutter-pyvanguard** (caractère non valide `|` dans le nom du sous-dossier)

Échecs de chargement :

- **chrisdev/wagtail-cookiecutter-foundation** (utilise un type booléen dans cookiecutter.json)
- **quintoandar/cookiecutter-android** (aucun dossier de modèle)

Échecs d’exécution :

- **iknite/cookiecutter-ansible-role** (le script Hook post-génération requiert une entrée de console)
- **benregn/cookiecutter-django-ansible** (erreur jinja)

Utilise un interpréteur de commandes (pas irrécupérable) :

- **openstack-dev/cookiecutter**

