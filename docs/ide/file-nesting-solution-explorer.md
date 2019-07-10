---
title: Règles d’imbrication de fichiers pour l’Explorateur de solutions
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: a36ca2535785f72756ad66a69c2ebe4d7d5a373b
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587025"
---
# <a name="file-nesting-in-solution-explorer"></a>Imbrication de fichiers dans l’Explorateur de solutions

**L’Explorateur de solutions** imbrique les fichiers associés pour aider à les organiser et les rendre plus faciles à localiser. Par exemple, si vous ajoutez un formulaire Windows Forms à un projet, le fichier de code pour le formulaire est imbriqué sous le formulaire dans **l’Explorateur de solutions**. Dans les projets ASP.NET Core, l’imbrication de fichiers peut entreprendre une étape supplémentaire. Vous pouvez choisir entre les présélections d’imbrication de fichiers **Désactivé**, **Par défaut** et **Web**. Vous pouvez également [personnaliser la façon dont les fichiers sont imbriqués](#customize-file-nesting) ou [créer des paramètres spécifiques au projet et à la solution](#create-project-specific-settings).

> [!NOTE]
> La fonctionnalité est prise en charge uniquement pour les projets ASP.NET Core.

## <a name="file-nesting-options"></a>Options d’imbrication de fichiers

![Bouton permettant d’activer/de désactiver l’imbrication de fichiers](media/filenesting_onoff.png)

Les options disponibles pour l’imbrication de fichiers non personnalisée sont les suivantes :

* **Désactivé** : cette option vous permet d’obtenir une liste de fichiers sans imbrication.

* **Par défaut** : cette option vous permet d’obtenir le comportement d’imbrication de fichiers par défaut dans l’**Explorateur de solutions**. S’il n’existe aucun paramètre pour un type de projet donné, aucun fichier du projet n’est imbriqué. S’il existe des paramètres, par exemple, pour un projet web, l’imbrication est appliquée.

* **Web** : cette option applique le comportement d’imbrication de fichiers **web** à tous les projets de la solution actuelle. Elle comporte de nombreuses règles. Nous vous encourageons à y jeter un coup d’œil pour nous dire ce que vous en pensez. La capture d’écran suivante présente quelques exemples du comportement d’imbrication de fichiers lié cette option :

   ![Imbrication de fichiers dans l’Explorateur de solutions](media/filenesting.png)

## <a name="customize-file-nesting"></a>Personnaliser l’imbrication de fichiers

Si vous n’aimez pas ce qui vous est proposé, vous pouvez créer vos propres paramètres d’imbrication de fichiers personnalisés pour indiquer à l’**Explorateur de solutions** comment imbriquer les fichiers. Vous pouvez ajouter autant de paramètres d’imbrication de fichiers personnalisés que vous le souhaitez, et vous pouvez passer de l’un à l’autre comme bon vous semble. Pour créer un paramètre personnalisé, commencez avec un fichier vide ou utilisez les paramètres **web** comme point de départ :

![Ajouter des règles d’imbrication de fichiers personnalisées](media/filenesting_addcustom.png)

Nous vous recommandons d’utiliser les paramètres **web** comme point de départ, car il est plus facile de travailler avec quelque chose qui fonctionne déjà. Si vous utilisez les paramètres **web** comme point de départ, le fichier *.filenesting.json* ressemble au fichier suivant :

![Utiliser les règles d’imbrication de fichiers existantes en tant que base pour des paramètres personnalisés](media/filenesting_editcustom.png)

Concentrons-nous sur le nœud **dependentFileProviders** et ses nœuds enfants. Chaque nœud enfant est un type de règle que Visual Studio peut utiliser pour imbriquer des fichiers. Par exemple, **a le même nom de fichier mais avec une extension différente** est un type de règle. Les règles disponibles sont les suivantes :

* **extensionToExtension** : utilisez ce type de règle pour imbriquer *file.js* sous *file.ts*.

* **fileSuffixToExtension** : utilisez ce type de règle pour imbriquer *file-vsdoc.js* sous *file.js*.

* **addedExtension** : utilisez ce type de règle pour imbriquer *file.html.css* sous *file.html*.

* **pathSegment** : utilisez ce type de règle pour imbriquer *jquery.min.js* sous *jquery.js*.

* **allExtensions** : utilisez ce type de règle pour imbriquer *file.* * sous *file.js*.

* **fileToFile** : utilisez ce type de règle pour imbriquer *bower.json* sous *.bowerrc*.

### <a name="the-extensiontoextension-provider"></a>Fournisseur extensionToExtension

Ce fournisseur vous permet de définir des règles d’imbrication de fichiers à l’aide d’extensions de fichiers spécifiques. Prenons l'exemple suivant :

![Règles de l’exemple extentionToExtension](media/filenesting_extensiontoextension.png) ![Effet de l’exemple extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *cart.js* est imbriqué sous *cart.ts* en raison de la première règle **extensionToExtension**

* *cart.js* n’est pas imbriqué sous *cart.tsx*, car **.ts** vient avant **.tsx** dans les règles, et il ne peut exister qu’un seul parent

* *light.css* est imbriqué sous *light.sass* en raison de la deuxième règle **extensionToExtension**

* *home.html* est imbriqué sous *home.md* en raison de la troisième règle **extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Fournisseur fileSuffixToExtension

Ce fournisseur fonctionne exactement comme le fournisseur **extensionToExtension**, la seule différence étant que la règle examine le suffixe du fichier et non simplement l’extension. Prenons l'exemple suivant :

![Règles de l’exemple fileSuffixToExtension](media/filenesting_filesuffixtoextension.png) ![Effet de l’exemple fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* est imbriqué sous *portal.js* en raison de la règle **fileSuffixToExtension**

* tous les autres aspects de la règle fonctionnent de la même manière que **extensionToExtension**

### <a name="the-addedextension-provider"></a>Fournisseur addedExtension

Ce fournisseur imbrique les fichiers avec une extension supplémentaire sous le fichier sans extension supplémentaire. L’extension supplémentaire doit apparaître uniquement à la fin du nom de fichier complet.

Prenons l'exemple suivant :

![Règles de l’exemple addedExtension](media/filenesting_addedextension.png) ![Effet de l’exemple addedExtension](media/filenesting_addedextension_effect.png)

* *file.html.css* est imbriqué sous *file.html* en raison de la règle **addedExtension**

> [!NOTE]
> Vous ne spécifiez pas les extensions de fichier pour la règle `addedExtension` ; elle s’applique automatiquement à toutes les extensions de fichier. Autrement dit, n’importe quel fichier avec le même nom et la même extension qu’un autre fichier avec une extension supplémentaire à la fin est imbriqué sous l’autre fichier. Vous ne pouvez pas limiter l’effet de ce fournisseur à certaines extensions de fichier.

### <a name="the-pathsegment-provider"></a>Fournisseur pathSegment

Ce fournisseur imbrique les fichiers avec une extension supplémentaire sous un fichier sans extension supplémentaire. L’extension supplémentaire doit apparaître uniquement au milieu du nom de fichier complet.

Prenons l'exemple suivant :

![Règles de l’exemple pathSegment](media/filenesting_pathsegment.png) ![Effet de l’exemple pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* est imbriqué sous *jquery.js* en raison de la règle **pathSegment**

> [!NOTE]
> - Si vous ne spécifiez pas d’extensions de fichier spécifiques pour la règle `pathSegment`, elle s’applique à toutes les extensions de fichier. Autrement dit, n’importe quel fichier avec le même nom et la même extension qu’un autre fichier avec une extension supplémentaire au milieu est imbriqué sous l’autre fichier.
> - Vous pouvez limiter l’effet de la règle `pathSegment` à des extensions de fichier spécifiques en les spécifiant dans la manière suivante :
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>Fournisseur allExtensions

Ce fournisseur vous permet de définir des règles d’imbrication de fichiers pour les fichiers ayant une extension quelconque mais le même nom de fichier de base. Prenons l'exemple suivant :

![Règles de l’exemple allExtensions](media/filenesting_allextensions.png) ![Effet de l’exemple allExtensions](media/filenesting_allextensions_effect.png)

* *template.cs* et *template.doc* sont imbriqués sous *template.tt* en raison de la règle **allExtensions**.

### <a name="the-filetofile-provider"></a>Fournisseur fileToFile

Ce fournisseur vous permet de définir des règles d’imbrication de fichiers basées sur des noms de fichiers entiers. Prenons l'exemple suivant :

![Règles de l’exemple fileToFile](media/filenesting_filetofile.png) ![Effet de l’exemple fileToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* est imbriqué sous *bower.json* en raison de la règle **fileToFile**.

### <a name="rule-order"></a>Ordre des règles

L’ordre a son importance dans toutes les parties de votre fichier de paramètres personnalisés. Vous pouvez changer l’ordre dans lequel les règles sont exécutées en les déplaçant vers le haut ou vers le bas dans le nœud **dependentFileProvider**. Par exemple, si vous avez une règle qui fait de **file.js** le parent de **file.ts**, et une autre règle qui fait de **file.coffee** le parent de **file.ts**, l’ordre dans lequel ils apparaissent dans le fichier dicte le comportement d’imbrication quand les trois fichiers sont présents. Dans la mesure où **file.ts** ne peut avoir qu’un seul parent, la première règle qui s’exécute l’emporte.

L’ordre a également son importance pour les sections de règle elles-mêmes, pas seulement pour les fichiers présents dans une section. Dès qu’une paire de fichiers est associée à une règle d’imbrication de fichiers, les autres règles situées plus bas dans le fichier sont ignorées, et la paire de fichiers suivante est traitée.

### <a name="file-nesting-button"></a>Bouton d’imbrication de fichiers

Vous pouvez gérer tous les paramètres, notamment vos paramètres personnalisés, via le même bouton dans l’**Explorateur de solutions** :

![Activer des règles d’imbrication de fichiers personnalisées](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Créer des paramètres spécifiques au projet

Vous pouvez créer des paramètres propres à la solution ou au projet dans le menu contextuel (clic droit) de chaque solution ou projet :

![Règles d’imbrication spécifiques à la solution et au projet](media/filenesting_solutionprojectspecific.png)

Les paramètres spécifiques à la solution et au projet sont associés aux paramètres actifs de Visual Studio. Par exemple, même si vous avez un fichier de paramètres vide spécifique au projet, l’**Explorateur de solutions** imbrique quand même les fichiers. Le comportement d’imbrication provient des paramètres spécifiques à la solution ou des paramètres de Visual Studio. La priorité de fusion des paramètres d’imbrication de fichiers est la suivante : Visual Studio > Solution > Projet.

Vous pouvez indiquer à Visual Studio d’ignorer les paramètres spécifiques à la solution et au projet, même si les fichiers existent sur le disque, en activant l’option **Ignorer les paramètres de solution et de projet** sous **Outils** > **Options** > **ASP.NET Core** > **Imbrication de fichiers**.

Vous pouvez faire le contraire et indiquer à Visual Studio d’utiliser *uniquement* les paramètres spécifiques à la solution ou au projet, en affectant au nœud **racine** la valeur **true**. Visual Studio cesse de fusionner les fichiers à ce niveau et de les associer à des fichiers situés plus haut dans la hiérarchie.

Vous pouvez archiver les paramètres spécifiques à la solution et au projet dans le contrôle de code source. Ainsi, toute l’équipe qui travaille sur la base de code peut les partager.

## <a name="disable-file-nesting-rules-for-a-project"></a>Désactiver les règles d’imbrication de fichiers pour un projet

Vous pouvez désactiver les règles d’imbrication de fichiers globales pour des solutions ou des projets spécifiques. Pour ce faire, utilisez l’action **remove** sur un fournisseur au lieu de l’action **add**. Par exemple, si vous ajoutez à un projet le code suivant pour des paramètres, toutes les règles **pathSegment** qui peuvent exister globalement pour ce projet spécifique sont désactivées :

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Voir aussi

- [Personnaliser l’IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Solutions et projets dans Visual Studio](solutions-and-projects-in-visual-studio.md)
