---
title: Créer une application ASP.NET Core avec la machine à écrire
description: Dans ce didacticiel, vous allez créer une application à l’aide de ASP.NET Core et de la machine à écrire
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 40011b035afdf4a04eb760d13c001e39d9c578c4
ms.sourcegitcommit: 91a054beb6b3a16ed5140f9f829239ec31bbbec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75810581"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Didacticiel : créer une application ASP.NET Core avec une machine à écrire dans Visual Studio

Dans ce didacticiel pour le développement Visual Studio ASP.NET Core et la création d’une machine à écrire, vous créez une application Web simple, ajoutez du code machine à écrire, puis exécutez l’application. 

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Créer un projet ASP.NET Core
> * Ajouter le package NuGet pour la prise en charge de la machine à écrire
> * Ajouter du code de machine à écrire
> * Exécuter l'application

## <a name="prerequisites"></a>Configuration requise

* Vous devez avoir installé Visual Studio et la charge de travail de développement Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail, mais que vous avez déjà installé Visual Studio, cliquez sur **Outils** > **Obtenir les outils et fonctionnalités...** , qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Créer un projet ASP.NET Core MVC

Visual Studio gère les fichiers d’une seule application dans un *projet*. Le projet comprend le code source, les ressources et les fichiers config.

Dans ce didacticiel, vous commencez avec un projet simple contenant du code pour une application ASP.NET Core MVC.

1. Ouvrez Visual Studio.

1. Créez un nouveau projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **ASP.net**, puis choisissez **ASP.net Core application Web C#-** . Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **C#visuel**, puis choisissez **.net Core**. Dans le volet central, choisissez **ASP.net Core application Web- C#** , puis cliquez sur **OK**.
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet d' **application web ASP.net Core** , vous devez ajouter la charge de travail **ASP.net et développement Web** . Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

1. Une fois que vous avez choisi **créer**, sélectionnez **application Web (Model-View-Controller)** dans la boîte de dialogue, puis choisissez **créer**.

   ![Choisir le modèle MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio crée la solution et ouvre votre projet dans le volet droit.

## <a name="add-some-code"></a>Ajouter du code

1. Dans Explorateur de solutions (volet droit). Cliquez avec le bouton droit sur le nœud du projet et choisissez **gérer les packages NuGet**. Sous l’onglet **Parcourir** , recherchez **Microsoft. dactylographié. MSBuild**, puis cliquez sur **installer** à droite pour installer le package.

   ![Ajouter un package NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio ajoute le package NuGet sous le nœud **dépendances** dans Explorateur de solutions.

   > [!NOTE]
   > Ce didacticiel nécessite le package NuGet. Dans vos propres applications, vous pouvez également utiliser le [package NPM de machine à écrire](https://www.npmjs.com/package/typescript).

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet et choisissez **ajouter > nouveau dossier**. Utilisez les *scripts* de nom pour le nouveau dossier.

1. Cliquez avec le bouton droit sur le dossier *scripts* , puis choisissez **Ajouter > nouvel élément**. Choisissez le **fichier de configuration de la machine à écrire JSON**, puis cliquez sur **Ajouter**.

   Visual Studio ajoute le fichier *tsconfig. JSON* au dossier *scripts* . Vous pouvez utiliser ce fichier pour [configurer les options](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) du compilateur de machine à écrire.

1. Ouvrez *tsconfig. JSON* et remplacez le code par défaut par le code suivant :

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   L’option *outDir* spécifie le dossier de sortie pour les fichiers de plan JavaScript qui sont transpiles par le compilateur de machine à écrire.

   Cette configuration fournit une introduction à l’utilisation de la machine à écrire. Dans d’autres scénarios, par exemple lors de l’utilisation de [Gulp ou WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), vous pouvez avoir besoin d’un emplacement intermédiaire différent pour les fichiers JavaScript, en fonction de vos outils et préférences de configuration, au lieu de *. /wwwroot/js*.

1. Cliquez avec le bouton droit sur le dossier *scripts* , puis choisissez **Ajouter > nouvel élément**. Choisissez le **fichier de machine à écrire**, tapez le nom *app. TS* comme nom de fichier, puis cliquez sur **Ajouter**.

   Visual Studio ajoute *app. TS* au dossier *scripts* .

1. Ouvrez *app. TS* , puis ajoutez le code machine à écrire suivant.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio prend en charge IntelliSense pour votre code de machine à écrire.

    Pour tester cela, supprimez `.lastName` de la fonction `greeter`, puis retapez le « . » et vous voyez IntelliSense.

    ![Afficher IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Sélectionnez `lastName` pour rajouter le nom du dernier au code.

1. Ouvrez le dossier *views/page de démarrage* , puis ouvrez *index. html*.

1. Ajoutez le code HTML suivant à la fin du fichier.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Ouvrez le dossier *Views/Shared* , puis ouvrez *_Layout. cshtml*.

1. Ajoutez la référence de script suivante avant l’appel à `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Générer l’application

1. Choisissez **générer > générer la solution**.

   Bien que l’application soit générée automatiquement lorsque vous l’exécutez, nous souhaitons examiner un problème qui se produit pendant le processus de génération.

1. Ouvrez le dossier *wwwroot/js* . vous trouverez deux nouveaux fichiers, *app. js* et le fichier de mappage source, *app. js. map*. Ces fichiers sont générés par le compilateur de machine à écrire.

   Les fichiers de mappage source sont requis pour le débogage.

## <a name="run-the-application"></a>Exécuter l'application

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    L’application s’ouvre dans un navigateur.

    Dans la fenêtre du navigateur, vous verrez l’en-tête **Bienvenue** et le bouton **cliquez sur moi** .

    ![ASP.NET Core avec la machine à écrire](../javascript/media/aspnet-core-ts-running-app.png)

1. Cliquez sur le bouton pour afficher le message que nous avons spécifié dans le fichier de machine à écrire.

## <a name="debug-the-application"></a>Déboguer l’application

1. Définissez un point d’arrêt dans la fonction `greeter` dans `app.ts` en cliquant dans la marge de gauche de l’éditeur de code.

    ![Définir un point d'arrêt](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Appuyez sur **F5** pour exécuter l’application.

   Vous devrez peut-être répondre à un message pour activer le débogage de script.

   L’application s’interrompt au point d’arrêt. À présent, vous pouvez inspecter les variables et utiliser les fonctionnalités du débogueur.

## <a name="next-steps"></a>Étapes suivantes :

Vous souhaiterez peut-être en savoir plus sur l’utilisation de la fonction de machine à ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core et la machine à écrire](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
