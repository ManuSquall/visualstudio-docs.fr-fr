---
title: Personnaliser les tâches de débogage de build à l’aide de tasks.vs.json launch.vs.json
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca5a80c07cb64cfd638542da4e1deefe7e373b18
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342398"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Personnaliser des tâches de génération et de débogage pour le développement « Ouvrir le dossier »

Visual Studio sait comment exécuter de nombreux langages et codes de base, mais il ne sait pas comment exécuter tous les éléments. Si vous [avez ouvert un dossier de code](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) dans Visual Studio et que Visual Studio sait comment exécuter votre code, vous pouvez l’exécuter immédiatement sans aucune configuration supplémentaire.

Si le code base utilise des outils de génération personnalisés que Visual Studio ne reconnaît pas, vous devez fournir des détails de configuration pour exécuter et déboguer le code dans Visual Studio. Vous indiquez à Visual Studio comment générer votre code en définissant des *tâches de génération*. Vous pouvez créer une ou plusieurs tâches de génération pour spécifier tous les éléments dont un langage a besoin pour générer et exécuter son code. Vous pouvez également créer des tâches arbitraires qui peuvent faire pratiquement tout ce que vous souhaitez. Par exemple, vous pouvez créer une tâche visant à répertorier le contenu d’un dossier ou à renommer un fichier.

Personnalisez votre code base sans projet en utilisant les fichiers *.json* suivants :

|Nom de fichier|Objectif|
|-|-|
|*tasks.vs.json*|Spécifiez des commandes de génération personnalisée, des commutateurs de compilation ainsi que des tâches arbitraires (non liées à la génération).<br>Accessible par l’élément de menu contextuel (clic droit) **Configurer les tâches** de **l’Explorateur de solutions**.|
|*launch.vs.json*|Spécifiez les arguments de ligne de commande pour le débogage.<br>Accessible par l’élément de menu contextuel (clic droit) **Paramètres de débogage et de lancement** de **l’Explorateur de solutions**.|

Ces fichiers *.json* se trouvent dans un dossier masqué appelé *.vs* dans le dossier racine de votre code base. Les fichiers *tasks.vs.json* et *launch.vs.json* sont créés par Visual Studio selon les besoins lorsque vous choisissez l’option **Configurer les tâches** ou **Paramètres de débogage et de lancement** pour un fichier ou dossier dans **l’Explorateur de solutions**. Les fichiers *.json* sont masqués car les utilisateurs ne souhaitent généralement pas les vérifier dans le contrôle de code source. Toutefois, si vous souhaitez être en mesure de les vérifier dans le contrôle de code source, faites glisser les fichiers à la racine de votre code base, où ils sont visibles.

> [!TIP]
> Pour voir les fichiers masqués dans Visual Studio, cliquez sur le bouton **Afficher tous les fichiers** de la barre d’outils de **l’Explorateur de solutions**.

## <a name="define-tasks-with-tasksvsjson"></a>Définir de tâches avec tasks.vs.json

Vous pouvez automatiser les scripts de génération ou d’autres opérations externes sur les fichiers de votre espace de travail actuel en les exécutant comme des tâches directement dans l’IDE. Vous pouvez configurer une nouvelle tâche en cliquant sur un fichier ou dossier puis en sélectionnant **Configurer les tâches**.

![Configurer le menu Tâches](../ide/media/customize-configure-tasks-menu.png)

Permet de créer (ou d’ouvrir) le fichier *tasks.vs.json* dans le dossier *.vs*. Vous pouvez définir une tâche de build ou n’importe quelle tâche dans ce fichier, puis l’appeler en utilisant le nom que vous lui avez attribué dans le menu contextuel (clic droit) de **l’Explorateur de solutions**.

Des tâches personnalisée peuvent être ajoutées à chaque fichier ou à l’ensemble des fichiers d’un type spécifique. Par exemple, les fichiers du package NuGet peuvent être configurés de manière à obtenir une tâche « Restaurer les packages », ou tous les fichiers sources peuvent être configurés afin d’obtenir une tâche d’analyse statique, par exemple un linter pour tous les fichiers *.js*.

### <a name="define-custom-build-tasks"></a>Définir des tâches de génération personnalisées

Si votre code base utilise des outils de génération personnalisés que Visual Studio ne reconnaît pas, vous ne pourrez pas exécuter et déboguer le code dans Visual Studio tant que vous n’aurez pas effectué certaines étapes de configuration. Visual Studio fournit des *tâches de génération* dans lesquelles vous pouvez indiquer à Visual Studio comment générer, regénérer et nettoyer votre code. Le fichier de la tâche de génération *tasks.vs.json* associe la boucle de développement interne de Visual Studio aux outils de génération personnalisée utilisés par le code de base.

Prenons un code base composé d’un seul fichier cC# appelé *hello.cs*. Le fichier *makefile* d’un tel code base pourrait se présenter comme ceci :

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Pour ce fichier *makefile* contenant des cibles de génération, de nettoyage et de regénération, vous pouvez définir le fichier *tasks.vs.json* suivant. Il contient trois tâches pour la génération, la régénération et le nettoyage du code base, en utilisant NMAKE comme outil de génération.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Une fois définies les tâches de génération dans *tasks.vs.json*, d’autres éléments de menu contextuel (clic droit) sont ajoutés aux fichiers correspondants dans **l’Explorateur de solutions**. Pour cet exemple, les options « Générer », « Regénérer » et « Nettoyer » sont ajoutées au menu contextuel des fichiers *makefile*.

![menu contextuel makefile avec générer, régénerer et nettoyer](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Les commandes apparaissent dans le menu contextuel, sous la commande **Configurer les tâches** en raison de leurs paramètres `contextType`. Les commandes « générer », « régénérer » et « nettoyer » étant des commandes de génération, elles apparaissent dans la section de génération au milieu du menu contextuel.

Lorsque vous sélectionnez une de ces options, la tâche s’exécute. La sortie s’affiche dans la fenêtre **Sortie** et les erreurs de génération apparaissent dans la **liste d’erreurs**.

### <a name="define-arbitrary-tasks"></a>Définir des tâches arbitraires

Vous pouvez définir des tâches arbitraires dans le fichier *tasks.vs.json* et faire ainsi à peu près tout ce que vous voulez. Par exemple, vous pouvez définir une tâche afin d’afficher le nom du fichier actuellement sélectionné dans la fenêtre **Sortie**, ou pour répertorier les fichiers d’un répertoire spécifié.

L’exemple suivant montre un fichier *tasks.vs.json* qui définit une tâche unique. Lorsqu’elle est appelée, la tâche affiche le nom de fichier de fichier *.js* actuellement sélectionné.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` spécifie le nom qui apparaît dans le menu contextuel (clic droit).
- `appliesTo` spécifie les fichiers que lesquels la commande peut être exécutée.
- La propriété `command` spécifie la commande à appeler. Dans cet exemple, la variable d’environnement `COMSPEC` sert à identifier l’interpréteur de ligne de commande, en général *cmd.exe*.
- La propriété `args` spécifie les arguments à passer à la commande appelée.
- La macro `${file}` extrait le fichier sélectionné dans **l’Explorateur de solutions**.

Après avoir enregistré *tasks.vs.json*, vous pouvez cliquer avec le bouton droit sur n’importe quel fichier *.js* dans le dossier, puis choisir **Echo nomfichier**. Le nom de fichier apparaît dans la fenêtre **Sortie** .

> [!NOTE]
> Si votre code base ne contient aucun fichier *tasks.vs.json*, vous pouvez en créer un en choisissant l’élément de menu contextuel **Configurer les tâches** en cliquant avec le bouton droit sur un fichier dans **l’Explorateur de solutions**.

L’exemple suivant définit une tâche qui répertorie les fichiers et sous-dossiers du répertoire *bin*.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` est une macro personnalisée qui est d’abord définie avant le bloc `tasks`. Elle est ensuite appelée dans la propriété `args`.

Cette tâche s’applique à tous les fichiers. Lorsque vous ouvrez le menu contextuel de n’importe quel fichier dans **l’Explorateur de solutions**, le nom de la tâche **Répertorier les sorties** apparaît au bas du menu. Lorsque vous choisissez **Répertorier les sorties**, le contenu du répertoire *bin* est répertorié dans la fenêtre **Sortie** de Visual Studio.

![Tâche arbitraire dans le menu contextuel](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Portée des paramètres

Plusieurs fichiers *tasks.vs.json* peuvent exister à la racine et les sous-répertoires d’un code base. Cette conception offre la flexibilité de pouvoir bénéficier d’un comportement différent dans les divers sous-répertoires du code base. Visual Studio regroupe ou substitue les paramètres dans l’ensemble du code base, en hiérarchisation les fichiers dans l’ordre suivant :

- Les fichiers de paramètres dans le dossier racine du répertoire *.vs*.
- Le répertoire dans lequel un paramètre est calculé.
- Le répertoire parent du répertoire actuel, jusqu'au répertoire racine.
- Les fichiers de paramètres dans le dossier racine.

Ces règles d’agrégation s’appliquent à *tasks.vs.json*. Pour plus d’informations sur la façon dont les paramètres d’un autre fichier sont agrégés, consultez la section correspondante à ce fichier dans cet article.

### <a name="properties-for-tasksvsjson"></a>Propriétés de tasks.vs.json

Cette section décrit certaines des propriétés que vous pouvez spécifier dans *tasks.vs.json*.

#### <a name="appliesto"></a>appliesTo

Vous pouvez créer des tâches pour tout fichier ou dossier en spécifiant son nom dans le champ `appliesTo`, par exemple `"appliesTo": "hello.js"`. Les masques de fichier suivants peuvent être utilisés comme valeurs :

|||
|-|-|
|`"*"`| la tâche est disponible pour tous les fichiers et dossiers dans l’espace de travail|
|`"*/"`| la tâche est disponible pour tous les dossiers dans l’espace de travail|
|`"*.js"`| la tâche est disponible pour tous les fichiers avec l’extension *.js* dans l’espace de travail|
|`"/*.js"`| la tâche est disponible pour tous les fichiers avec l’extension *.js* à la racine de l’espace de travail|
|`"src/*/"`| la tâche est disponible pour tous les sous-dossiers du dossier *src*|
|`"makefile"`| la tâche est disponible pour tous les fichiers *makefile* dans l’espace de travail|
|`"/makefile"`| la tâche est disponible seulement dans le fichier *makefile* à la racine de l’espace de travail|

#### <a name="macros-for-tasksvsjson"></a>Macros pour tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Spécifie toute variable d’environnement (par exemple, ${env.PATH}, ${env.COMSPEC}, etc.) définie pour l’invite de commandes développeur. Pour plus d’informations, consultez [Invite de commandes développeur pour Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Le chemin complet vers le dossier de l’espace de travail (par exemple *C:\sources\hello*)|
|`${file}`| Le chemin complet du fichier ou du dossier sur lequel exécuter cette tâche (par exemple *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Le chemin relatif du fichier ou du dossier (par exemple *src\hello.js*)|
|`${fileBasename}`| Le nom du fichier sans chemin ni extension (par exemple *hello*)|
|`${fileDirname}`| Le chemin complet du fichier, sans le nom de fichier (par exemple *C:\sources\hello\src*)|
|`${fileExtname}`| L’extension du fichier sélectionné (par exemple *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Configurer le débogage avec launch.vs.json

1. Afin de configurer votre code base pour le débogage, dans **l’Explorateur de solutions** choisissez l’élément de menu contextuel **Paramètres de débogage et de lancement** en cliquant avec le bouton droit sur votre fichier exécutable.

   ![Menu contextuel Paramètres de débogage et de lancement](media/customize-debug-launch-menu.png)

1. Dans la boîte de dialogue **Sélectionner un débogueur**, choisissez une option, puis cliquez sur le bouton **Sélectionner**.

   ![Sélectionner une boîte de dialogue de débogueur](media/customize-select-a-debugger.png)

   Si le fichier *launch.vs.json* n’existe pas déjà, il est créé.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Cliquez ensuite avec le bouton droit sur le fichier exécutable dans l'**Explorateur de solutions**, puis choisissez **Définir comme élément de démarrage**.

   Le fichier exécutable est désigné comme élément de démarrage pour votre code base, et l’intitulé du bouton **Démarrer** du mode débogage change pour refléter le nom de votre fichier exécutable.

   ![Bouton Démarrer personnalisé](media/customize-start-button.png)

   Lorsque vous choisissez **F5**, le débogueur démarre et s’arrête au point d’arrêt que vous avez déjà défini. Toutes les fenêtres du débogueur habituelles sont disponibles et opérationnelles.

   > [!IMPORTANT]
   > Pour plus d’informations sur les tâches de génération et C++ de débogage personnalisées dans les projets de dossiers ouverts, consultez [ouvrir la prise en charge des dossiers pour les C++ systèmes de génération dans Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Spécifier des arguments pour le débogage

Vous pouvez spécifier des arguments de ligne de commande à passer pour le débogage dans le fichier *launch.vs.json*. Ajoutez les arguments au tableau `args`, comme indiqué dans l’exemple suivant :

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Lorsque vous enregistrez ce fichier, le nom de la nouvelle configuration apparaît dans le menu déroulant cible de débogage, et vous pouvez le sélectionner pour démarrer le débogueur. Vous pouvez créer autant de configurations de débogage que vous le souhaitez.

![Liste déroulante des configurations de débogage](media/customize-debug-configurations.png)

> [!NOTE]
> La propriété de tableau `configurations` dans *launch.vs.json* est lue à partir de deux emplacements de fichiers&mdash;le répertoire racine du code base et le répertoire *.vs*. En cas de conflit, la priorité est donnée à la valeur dans *.vs\launch.vs.json*.

## <a name="additional-settings-files"></a>Autres fichiers de paramètres

Outre les trois fichiers *.json* décrits dans cette rubrique, Visual Studio lit également les paramètres de certains autres fichiers, s’ils existent dans votre code base.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio lit les paramètres limités d’un fichier nommé *settings.json* si celui-ci se trouve dans un répertoire nommé *.vscode*. Cette fonctionnalité est fournie pour les codes base qui ont déjà été développés dans Visual Studio Code. Actuellement, le seul paramètre lu à partir de *.vscode\settings.json* est `files.exclude`, qui filtre les fichiers visuellement dans l’Explorateur de solutions et de certains outils de recherche.

Votre code base peut comporter n’importe quel nombre de fichiers *.vscode\settings.json*. Les paramètres lus à partir de ce fichier sont appliqués au répertoire parent de *.vscode* et à tous ses sous-répertoires.

### <a name="gitignore"></a>.gitignore

Les fichiers *.gitignore* sont utilisés pour indiquer à Git quels fichiers ignorer, c’est-à-dire les fichiers et les répertoires que vous ne souhaitez pas archiver. Les fichiers *.gitignore* font généralement partie d’un code base afin de pouvoir partager les paramètres avec tous les développeurs du code base. Visual Studio lit les schémas dans les fichiers *.gitignore* pour filtrer les éléments visuellement à partir de certains outils de recherche.

Les paramètres lus à partir du fichier *.gitignore* sont appliqués à son répertoire parent et à tous les sous-répertoires.

## <a name="see-also"></a>Voir aussi

- [Développer du code sans projet ou solution](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Projets Ouvrir un dossier pour C++](/cpp/build/open-folder-projects-cpp)
- [Projets CMake pour C++](/cpp/build/cmake-projects-in-visual-studio)
- [Référence NMAKE](/cpp/build/reference/nmake-reference)
- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
