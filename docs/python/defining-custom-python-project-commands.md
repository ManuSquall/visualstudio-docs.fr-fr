---
title: Guide pratique pour définir des commandes de menu personnalisées pour les projets Python
description: Montre comment modifier des fichiers projet et des fichiers de cibles pour ajouter des commandes personnalisées dans le menu contextuel du projet Python dans Visual Studio. Les commandes peuvent être appelées sur des programmes exécutables, des scripts, des modules, des extraits de code inline et des commandes pip.
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
ms.openlocfilehash: 6d6113b9c102ff367d4b41bd4780c365c1928705
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117909"
---
# <a name="defining-custom-commands-for-python-projects"></a>Définition de commandes personnalisées pour les projets Python

Quand vous travaillez avec des projets Python, il vous arrive peut-être de passer à une fenêtre de commande pour exécuter des scripts, des modules ou des commandes pip spécifiques ou pour exécuter un autre outil arbitraire. Pour améliorer votre workflow, vous pouvez ajouter des commandes personnalisées au sous-menu **Python** dans le menu contextuel du projet Python. Ces commandes peuvent s’exécuter dans une fenêtre de console ou dans la fenêtre de sortie Visual Studio. Vous pouvez également utiliser des expressions régulières pour que Visual Studio sache comment analyser les erreurs et les avertissements de la sortie de la commande.

Par défaut, ce menu ne contient que la commande **Exécuter PyLint** :

![Apparence par défaut du sous-menu Python dans le menu contextuel d’un projet](media/custom-commands-default-menu.png)

Les commandes personnalisées apparaissent dans ce même menu contextuel. Les commandes personnalisées sont directement ajoutées à un fichier projet, où elles s’appliquent à ce projet en particulier. Vous pouvez également définir des commandes personnalisées dans un fichier `.targets` qui peut facilement être importé dans plusieurs fichiers projet.

Certains modèles de projet Python dans Visual Studio ajoutent déjà leurs propres commandes personnalisées au moyen de leur fichier `.targets`. Par exemple, les modèles Projet web Bottle et Projet web Flask ajoutent deux commandes : **Démarrer le serveur** et **Démarrer le serveur de débogage**. Le modèle Projet web Django ajoute les mêmes commandes et quelques autres :

![Apparence du sous-menu Python dans le menu contextuel d’un projet Django](media/custom-commands-django-menu.png)

Chaque commande personnalisée peut faire référence à un fichier Python, un module Python, du code Python inline, un exécutable arbitraire ou une commande pip. Vous pouvez également spécifier comment et où la commande s’exécute.

> [!Tip]
> Chaque fois que vous changez un fichier projet dans un éditeur de texte, vous devez recharger le projet dans Visual Studio pour appliquer ces changements. Par exemple, après avoir ajouté des définitions de commandes personnalisées, vous devez recharger un projet pour qu’elles apparaissent dans le menu contextuel du projet.
>
> Comme vous le savez, Visual Studio permet de modifier directement le fichier projet. Cliquez tout d’abord avec le bouton droit sur le fichier projet, sélectionnez **Décharger le projet**, refaites un clic droit, puis sélectionnez **Modifier (nom du projet)** pour ouvrir le projet dans l’éditeur Visual Studio. Apportez vos modifications et enregistrez-les, refaites un clic droit sur le projet, puis sélectionnez **Recharger le projet**. Vous êtes alors invité à confirmer la fermeture du fichier projet dans l’éditeur.
>
> Quand vous développez une commande personnalisée, tous ces clics peuvent devenir fastidieux. Pour améliorer l’efficacité de votre workflow, chargez le projet dans Visual Studio et ouvrez également le fichier `'.pyproj` dans un éditeur distinct (par exemple, une autre instance de Visual Studio, Visual Studio Code, le Bloc-notes, etc.). Quand vous enregistrez vos changements dans l’éditeur et que vous passez à Visual Studio, ce dernier détecte les changements apportés et vous demande s’il faut recharger le projet (« Le projet [nom] a été modifié en dehors de l’environnement. »). Sélectionnez **Recharger**. Vos changements sont alors appliqués immédiatement en une seule étape.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Procédure pas à pas : ajouter une commande dans un fichier projet

Pour vous familiariser avec les commandes personnalisées, cette section décrit un exemple simple qui exécute directement le fichier de démarrage d’un projet avec python.exe. (Cette commande revient à utiliser **Déboguer > Démarrer sans débogage**.)

1. Créez un projet nommé « Python-CustomCommands » en utilisant le modèle « Application Python ». (Consultez [Démarrage rapide : créer un projet de Python à partir d’un modèle](quickstart-02-python-in-visual-studio-project-from-template.md) pour obtenir des instructions si vous ne connaissez pas encore le processus.)

1. Dans `Python_CustomCommands.py`, ajoutez le code `print("Hello custom commands")`.

1. Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Python**. Notez que la seule commande qui s’affiche dans le sous-menu est **Exécuter PyLint**. Vos commandes personnalisées s’affichent dans ce même sous-menu.

1. Comme indiqué dans l’introduction, ouvrez `Python-CustomCommands.pyproj` dans un éditeur de texte distinct. Ajoutez ensuite les lignes suivantes à la fin du fichier, à l’intérieur du `</Project>` de fermeture, puis enregistrez le fichier.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Revenez à Visual Studio et sélectionnez **Recharger** quand il vous notifie que le fichier a été modifié. Examinez à nouveau le menu **Python** pour voir si la commande **Exécuter PyLint** est toujours la seule affichée dans cette zone, car les lignes que vous avez ajoutées répliquent seulement le groupe de propriétés `<PythonCommands>` par défaut contenant la commande PyLint.

1. Passez à l’éditeur contenant le fichier projet et ajoutez la définition `<Target>` suivante après `<PropertyGroup>`. Comme expliqué plus loin dans cet article, cet élément `Target` définit une commande personnalisée pour exécuter le fichier de démarrage (identifié par la propriété « StartupFile ») en utilisant `python.exe` dans une fenêtre de console. L’attribut `ExecuteIn="consolepause"` utilise une console qui attend que vous appuyiez sur une touche avant sa fermeture.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Ajoutez la valeur de l’attribut `Name` de la cible au groupe de propriétés `<PythonCommands>` ajouté précédemment pour que l’élément ressemble au code ci-dessous. C’est l’ajout du nom de la cible à cette liste qui le fait apparaître dans le menu **Python**.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Si vous souhaitez que votre commande apparaisse avant celles définies dans `$(PythonCommands)`, placez-les avant ce jeton.

1. Enregistrez le fichier projet, passez à Visual Studio, puis rechargez le projet quand vous y êtes invité. Cliquez avec le bouton droit sur le projet « Python-CustomCommands », puis sélectionnez **Python**. Un élément **Run startup file** doit figurer dans le menu. Si vous ne voyez pas l’élément de menu, vérifiez que vous avez bien ajouté le nom à l’élément `<PythonCommands>`. Consultez également la section [Dépannage](#troubleshooting) plus loin dans cet article.

    ![Commande personnalisée apparaissant dans le sous-menu contextuel Python](media/custom-commands-walkthrough-menu-item.png)

1. Sélectionnez la commande **Run startup file**. Une fenêtre de commande doit s’afficher avec le texte « Hello custom commands » suivi de « Press any key to continue . . . ».  Appuyez sur une touche pour fermer la fenêtre.

    ![Sortie de commande personnalisée dans une fenêtre de console](media/custom-commands-walkthrough-console.png)

1. Revenez à l’éditeur contenant le fichier projet et remplacez la valeur de l’attribut `ExecuteIn` par `output`. Enregistrez le fichier, passez à Visual Studio, rechargez le projet, puis rappelez la commande. Cette fois, la sortie du programme s’affiche dans la fenêtre **Sortie** de Visual Studio :

    ![Sortie de commande personnalisée dans la fenêtre de sortie](media/custom-commands-walkthrough-output-window.png)

1. Pour ajouter d’autres commandes, définissez un élément `<Target>` adéquat pour chaque commande, ajoutez le nom de la cible dans le groupe de propriétés `<PythonCommands>` et rechargez le projet dans Visual Studio.

>[!Tip]
> Si vous appelez une commande qui utilise des propriétés de projet, comme `($StartupFile)`, et que la commande échoue car le jeton n’est pas défini, Visual Studio désactive la commande tant que vous ne rechargez pas le projet. Toutefois, le fait de changer le projet en vue de définir la propriété n’actualise pas l’état de ces commandes. Vous devez donc encore recharger le projet.

## <a name="command-target-structure"></a>Structure de la cible de la commande

La forme générale de l’élément `<Target>` est indiquée dans le pseudo-code suivant :

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Pour faire référence aux propriétés du projet ou aux variables d’environnement dans les valeurs d’attribut, utilisez le nom au sein d’un jeton `$()`, tel que `$(StartupFile)` et `$(MSBuildProjectDirectory)`. Pour plus d’informations, consultez [Propriétés MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Attributs Target

| Attribut | Obligatoire | Description |
| --- | --- | --- |
| Name | Oui | Identificateur de la commande dans le projet Visual Studio. Ce nom doit être ajouté au groupe de propriétés `<PythonCommands>` pour que la commande apparaisse dans le sous-menu Python. |
| Ajouter des contrôles | Oui | Nom d’affichage d’interface utilisateur qui apparaît dans le sous-menu Python. |
| Returns (Retours) | Oui | Doit contenir `@(Commands)`, qui identifie la cible en tant que commande. |

### <a name="createpythoncommanditem-attributes"></a>Attributs CreatePythonCommandItem

Toutes les valeurs d’attribut sont insensibles à la casse.

| Attribut | Obligatoire | Description |
| --- | --- | --- |
| TargetType | Oui | Spécifie ce que contient l’attribut Target et comment il est utilisé avec l’attribut Arguments :<ul><li>**executable** : exécute l’exécutable nommé dans Target, en ajoutant la valeur dans Arguments, comme si vous l’entriez directement sur la ligne de commande. La valeur doit contenir uniquement un nom de programme sans arguments.</li><li>**script** : exécute `python.exe` avec le nom de fichier dans Target, suivi de la valeur dans Arguments.</li><li>**module** : exécute `python -m`, suivi du nom du module dans Target, suivi de la valeur dans Arguments.</li><li>**code** : exécute le code inline contenu dans Target. La valeur Arguments est ignorée.</li><li>**pip** : exécute `pip` avec la commande dans Target, suivi d’Arguments ; toutefois, si ExecuteIn a la valeur « output », pip suppose la commande `install` et utilise Target comme nom de package.</li></ul> |
| une cible | Oui | Nom de fichier, nom du module, code ou commande pip à utiliser selon le TargetType. |
| Arguments | Facultatif | Spécifie une chaîne d’arguments (le cas échéant) à donner à la cible. Quand le TargetType a la valeur `script`, notez que les arguments sont fournis au programme Python, et non à `python.exe`. Ignoré pour le TargetType `code`. |
| ExecuteIn | Oui | Spécifie l’environnement dans lequel exécuter la commande :<ul><li>**console** : (par défaut) exécute Target et les arguments comme si vous les entriez directement sur la ligne de commande. Une fenêtre de commande s’affiche durant l’exécution de Target, puis se ferme automatiquement.</li><li>**consolepause** : identique à console, mais attend l’appui sur une touche avant de fermer la fenêtre.</li><li>**output** : exécute Target et affiche ses résultats dans la fenêtre Sortie de Visual Studio. Si TargetType a la valeur « pip », Visual Studio utilise Target comme nom du package et ajoute les arguments.</li><li>**repl** : exécute Target dans la [fenêtre interactive Python](python-interactive-repl-in-visual-studio.md) ; le nom d’affichage facultatif est utilisé pour le titre de la fenêtre.</li><li>**none** : se comporte comme console.</li></ul>|
| WorkingDirectory | Facultatif | Dossier dans lequel exécuter la commande. |
| ErrorRegex<br>WarningRegEx | Facultatif | Utilisé uniquement quand ExecuteIn a la valeur `output`. Les deux valeurs spécifient une expression régulière avec laquelle Visual Studio analyse le résultat de la commande pour afficher les erreurs et les avertissements dans sa fenêtre Liste d’erreurs. Si rien n’est spécifié, la commande n’affecte pas la fenêtre Liste d’erreurs. Pour plus d’informations sur ce que Visual Studio attend, consultez [Groupes de capture nommés](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Facultatif | Liste de spécifications de package pour la commande au même format que [requirements.txt](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). Par exemple, la commande **Exécuter PyLint** spécifie `pylint>=1.0.0`. Avant d’exécuter la commande, Visual Studio vérifie que tous les packages répertoriés dans la liste sont installés. Visual Studio utilise pip pour installer les packages manquants. |
| Environnement | Facultatif | Chaîne de variables d’environnement à définir avant d’exécuter la commande. Chaque variable utilise la forme NAME=VALUE avec plusieurs variables séparées par des points-virgules. Une variable contenant plusieurs valeurs doit être mise entre guillemets simples ou doubles. Par exemple : 'NAME=VALUE1;VALUE2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Groupes de capture nommés pour les expressions régulières

Lors de l’analyse des erreurs et des avertissements à partir de la sortie d’une commande, Visual Studio s’attend à ce que les expressions régulières dans les valeurs `ErrorRegex` et `WarningRegex` utilisent les groupes nommés suivants :

- `(?<message>...)` : texte de l’erreur.
- `(?<code>...)` : code de l’erreur.
- `(?<filename>...)` : nom du fichier pour lequel l’erreur est signalée.
- `(?<line>...)` : numéro de ligne de l’emplacement où l’erreur a été signalée dans le fichier.
- `(?<column>...)` : numéro de colonne de l’emplacement où l’erreur a été signalée dans le fichier.

Par exemple, PyLint produit des avertissements semblables à ce qui suit :

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Pour permettre à Visual Studio d’extraire les bonnes informations à partir de ces avertissements et de les afficher dans la fenêtre **Liste d’erreurs**, la valeur `WarningRegex` pour la commande **Exécuter Pylint** est la suivante :

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Notez que `msg_id` dans la valeur doit être `code`. Consultez le [problème 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="creating-a-targets-file-with-custom-commands"></a>Création d’un fichier .targets avec des commandes personnalisées

La définition de commandes personnalisées dans un fichier projet les rend uniquement disponibles dans ce fichier projet. Pour utiliser des commandes dans plusieurs fichiers projet, définissez à la place le groupe de propriétés `<PythonCommands>` et tous vos éléments `<Target>` dans un fichier `.targets`. Importez ensuite ce fichier dans chaque fichier projet individuel.

Le fichier `.targets` respecte le format suivant :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Pour charger un fichier `.targets` dans un projet, placez un élément `<Import Project="(path)">` n’importe où dans l’élément `<Project>`. Par exemple, si vous avez un fichier nommé `CustomCommands.targets` dans un sous-dossier `targets` de votre projet, utilisez le code suivant :

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Chaque fois que vous changez le fichier `.targets`, vous devez recharger la *solution* qui contient un projet, et pas simplement le projet.

## <a name="example-commands"></a>Exemples de commandes

### <a name="run-pylint-module-target"></a>Exécuter PyLint (cible de module)

Le code suivant s’affiche dans le fichier `Microsoft.PythonTools.targets` :

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Exécuter pip install avec un package spécifique (cible pip)

La commande suivante exécute `pip install my-package` dans la fenêtre Sortie. Vous pouvez utiliser une commande de ce genre pour développer un package et tester son installation. Notez que Target contient le nom du package et non la commande `install`, laquelle est supposée lors de l’utilisation de `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Afficher les packages pip obsolètes (cible pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Exécuter un exécutable avec consolepause

La commande suivante exécute simplement `where` pour afficher les fichiers Python qui démarrent dans le dossier du projet :

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Commandes Exécuter le serveur et Exécuter le serveur de débogage

Pour explorer comment les commandes **Démarrer le serveur** et **Démarrer le serveur de débogage** sont définies pour les projets web, examinez [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Installer un package pour le développement

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*À partir de [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), utilisé avec autorisation.*

### <a name="generate-windows-installer"></a>Générer le programme d’installation Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*À partir de [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), utilisé avec autorisation.*

### <a name="generate-wheel-package"></a>Générer un package de roue

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*À partir de [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), utilisé avec autorisation.*

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="message-the-project-file-could-not-be-loaded"></a>Message : « Impossible de charger le fichier projet. »

Indique que le fichier projet comprend des erreurs de syntaxe. Le message inclut l’erreur spécifique avec un numéro de ligne et la position du caractère.

### <a name="console-window-closes-immediately-after-command-is-run"></a>La fenêtre de console se ferme immédiatement après l’exécution de commande

Utilisez `ExecuteIn="consolepause"` à la place de `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>La commande n’apparaît pas dans le menu

Vérifiez que la commande figure dans le groupe de propriétés `<PythonCommands>` et que le nom dans la liste de commandes correspond au nom spécifié dans l’élément `<Target>`.

Par exemple, dans les éléments suivants, le nom « Example » dans le groupe de propriétés ne correspond pas au nom « ExampleCommand » dans la cible. Visual Studio ne trouvant pas de commande nommée « Example », aucune commande n’apparaît. Utilisez « ExampleCommand » dans la liste de commandes ou remplacez le nom de la cible par « Example ».

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Message : Une erreur s’est produite lors de l’exécution de (nom de la commande). Échec de l’obtention de la commande (nom de la cible) du projet.

Indique que le contenu de l’élément `<Target>` ou `<CreatePythonCommandItem>` est incorrect. Raisons possibles :

- L’attribut `Target` exigé est vide.
- L’attribut `TargetType` exigé est vide ou contient une valeur non reconnue.
- L’attribut `ExecuteIn` exigé est vide ou contient une valeur non reconnue.
- `ErrorRegex` ou `WarningRegex` est spécifié sans paramètre `ExecuteIn="output"`.
- Des attributs non reconnus existent dans l’élément. Par exemple, vous avez peut-être utilisé `Argumnets` (mal orthographié) au lieu de `Arguments`.

Les valeurs d’attribut peuvent être vides si vous faites référence à une propriété qui n’est pas définie. Par exemple, si vous utilisez le jeton `$(StartupFile)` mais qu’aucun fichier de démarrage n’a été défini dans le projet, le jeton est résolu en chaîne vide. Dans ce cas, vous souhaiterez sans doute définir la valeur par défaut. Par exemple, les commandes **Exécuter le serveur** et **Exécuter le serveur de débogage** définies dans les modèles de projet Bottle, Flask et Django ont par défaut la valeur `manage.py` si aucun fichier de démarrage de serveur n’a été spécifié dans les propriétés du projet.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio se bloque durant l’exécution de la commande

Vous tentez probablement d’exécuter une commande de console avec `ExecuteIn="output"`, auquel cas Visual Studio peut se bloquer quand il tente d’analyser la sortie. Utilisez plutôt `ExecuteIn="console"`. (Consultez le [problème 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operate-program-or-batch-file"></a>La commande executable « n’est pas reconnue en tant que commande interne ou externe, un programme exécutable ou un fichier de commandes »

Quand vous utilisez `TargetType="executable"`, la valeur de `Target` doit être *uniquement* le nom du programme sans arguments. Par exemple : « python » ou « python.exe » uniquement. Déplacez les arguments dans l’attribut `Arguments`.
