---
title: Créer une application ASP.NET Core avec TypeScript
description: Dans ce didacticiel, vous allez créer une application à l’aide de ASP.NET Core et de la machine à écrire
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0728011c05d47996a313c11a18f31a196ec08e10
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306497"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Didacticiel : créer une application ASP.NET Core avec une machine à écrire dans Visual Studio

Dans ce didacticiel pour le développement Visual Studio ASP.NET Core et la création d’une machine à écrire, vous créez une application Web simple, ajoutez du code machine à écrire, puis exécutez l’application.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
> * Créer un projet ASP.NET Core
> * Ajouter le package NuGet pour la prise en charge de la machine à écrire
> * Ajouter du code de machine à écrire
> * Exécuter l’application
> * Ajouter une bibliothèque tierce à l’aide de NPM

## <a name="prerequisites"></a>Prérequis

* Vous devez avoir installé Visual Studio et la charge de travail de développement Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail mais que vous disposez déjà de Visual Studio, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Créer un projet ASP.NET Core MVC

Visual Studio gère les fichiers d’une seule application dans un *projet*. Le projet comprend le code source, les ressources et les fichiers config.

>[!NOTE]
> Pour commencer avec un projet de ASP.NET Core vide et ajouter un serveur frontal de machine à écrire, consultez [ASP.net core avec la fonction à](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) la place.

Dans ce didacticiel, vous commencez avec un projet simple contenant du code pour une application ASP.NET Core MVC.

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez **créer un nouveau projet** dans la fenêtre démarrer. Si la fenêtre de démarrage n’est pas ouverte , choisissez  >  **fenêtre démarrage** de fichier. Tapez **application Web**, choisissez **C#** comme langage, puis **ASP.net Core application Web (Model-View-Controller)**, puis choisissez **suivant**. Dans l’écran suivant, nommez le projet, puis choisissez **suivant**.

    Choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **Visual C#**, puis choisissez **.net Core**. Dans le volet central, choisissez **ASP.net Core application Web-C#**, puis cliquez sur **OK**.

    Dans la boîte de dialogue qui s’affiche, sélectionnez **application Web (Model-View-Controller)** dans la boîte de dialogue, puis choisissez **créer** (ou **OK**).

    ![Choisir le modèle MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet d' **application web ASP.net Core** , vous devez ajouter la charge de travail **ASP.net et développement Web** . Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée la solution et ouvre votre projet dans le volet droit.

## <a name="add-some-code"></a>Ajouter du code

1. Dans Explorateur de solutions (volet droit). Cliquez avec le bouton droit sur le nœud du projet et choisissez **gérer les packages NuGet**. Sous l’onglet **Parcourir** , recherchez **Microsoft. dactylographié. MSBuild**, puis cliquez sur **installer** à droite pour installer le package.

   ![Ajouter un package NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio ajoute le package NuGet sous le nœud **dépendances** dans Explorateur de solutions.

1. Cliquez avec le bouton droit sur le nœud du projet et choisissez **ajouter > nouvel élément**. Choisissez le **fichier de configuration de la machine à écrire JSON**, puis cliquez sur **Ajouter**.

   Visual Studio ajoute le *tsconfig.jssur* le fichier à la racine du projet. Vous pouvez utiliser ce fichier pour [configurer les options](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) du compilateur de machine à écrire.

1. Ouvrez *tsconfig.jssur* et remplacez le code par défaut par le code suivant :

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   L’option *outDir* spécifie le dossier de sortie pour les fichiers JavaScript ordinaires qui sont transpiles par le compilateur de machine à écrire.

   Cette configuration fournit une introduction à l’utilisation de la machine à écrire. Dans d’autres scénarios, par exemple lors de l’utilisation de [Gulp ou WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), vous pouvez avoir besoin d’un emplacement intermédiaire différent pour les fichiers JavaScript en cours de compilation, en fonction de vos outils et préférences de configuration, au lieu de *wwwroot/js*.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet et choisissez **ajouter > nouveau dossier**. Utilisez les *scripts* de nom pour le nouveau dossier.

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

    Pour tester cela, supprimez `.lastName` de la `greeter` fonction, puis retapez le « . » et vous voyez IntelliSense.

    ![Afficher IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Sélectionnez `lastName` cette option pour rajouter le nom au code.

1. Ouvrez le dossier *views/page de démarrage* , puis ouvrez *index. cshtml*.

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

1. Ajoutez la référence de script suivante avant l’appel à `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Créer l’application

1. Choisissez **générer > générer la solution**.

   Bien que l’application soit générée automatiquement lorsque vous l’exécutez, nous souhaitons examiner un problème qui se produit pendant le processus de génération.

1. Ouvrez le dossier *wwwroot/js* . vous trouverez deux nouveaux fichiers, *app.js* et le fichier de mappage source, *app.js. map*. Ces fichiers sont générés par le compilateur de machine à écrire.

   Les fichiers de mappage source sont requis pour le débogage.

## <a name="run-the-application"></a>Exécution de l'application

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    L’application s’ouvre dans un navigateur.

    Dans la fenêtre du navigateur, vous verrez l’en-tête **Bienvenue** et le bouton **cliquez sur moi** .

    ![ASP.NET Core avec la machine à écrire](../javascript/media/aspnet-core-ts-running-app.png)

1. Cliquez sur le bouton pour afficher le message que nous avons spécifié dans le fichier de machine à écrire.

## <a name="debug-the-application"></a>Déboguer l’application

1. Définissez un point d’arrêt dans la `greeter` fonction dans `app.ts` en cliquant dans la marge de gauche de l’éditeur de code.

    ![Définir un point d'arrêt](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Appuyez sur **F5** pour exécuter l'application.

   Vous devrez peut-être répondre à un message pour activer le débogage de script.

   L’application s’interrompt au point d’arrêt. À présent, vous pouvez inspecter les variables et utiliser les fonctionnalités du débogueur.

## <a name="add-typescript-support-for-a-third-party-library"></a>Ajout de la prise en charge de la machine à écrire pour une bibliothèque tierce

1. Suivez les instructions de la [gestion des packages NPM](../javascript/npm-package-management.md#aspnet-core-projects) pour ajouter un `package.json` fichier à votre projet. Cela ajoute la prise en charge de NPM à votre projet.

   >[!NOTE]
   > Pour les projets ASP.NET Core, vous pouvez également utiliser le [Gestionnaire de bibliothèque](/aspnet/core/client-side/libman/) ou le fil à la place de NPM pour installer des fichiers JavaScript et CSS côté client.

1. Dans cet exemple, ajoutez un fichier de définition de machine à écrire pour jQuery à votre projet. Incluez ce qui suit dans votre *package.js* fichier.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Cela ajoute la prise en charge de la méthode de réécrire pour jQuery. La bibliothèque jQuery elle-même est déjà incluse dans le modèle de projet MVC (Regardez sous wwwroot/lib dans Explorateur de solutions). Si vous utilisez un autre modèle, vous devrez peut-être inclure également le package jQuery NPM.

1. Si le package dans Explorateur de solutions n’est pas installé, cliquez avec le bouton droit sur le nœud NPM et choisissez **restaurer les packages**.

   >[!NOTE]
   > Dans certains scénarios, Explorateur de solutions peut indiquer qu’un package NPM n’est pas synchronisé avec *package.js* en raison d’un problème connu décrit [ici](https://github.com/aspnet/Tooling/issues/479). Par exemple, le package peut apparaître comme n’étant pas installé lors de son installation. Dans la plupart des cas, vous pouvez mettre à jour Explorateur de solutions en supprimant *package.jssur*, en redémarrant Visual Studio, puis en rajoutant le *package.jssur* le fichier, comme décrit précédemment dans cet article.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le dossier scripts et choisissez **Ajouter**  >  **un nouvel élément**.

1. Choisissez **fichier d’accès** à la machine, tapez *Library. TS*, puis choisissez **Ajouter**.

1. Dans *Library. TS*, ajoutez le code suivant.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString() + " " + v + "!!");
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Par souci de simplicité, ce code affiche un message à l’aide de jQuery et une alerte.

   Avec les définitions de type de machine à écrire pour jQuery ajoutées, vous bénéficiez d’une prise en charge IntelliSense sur les objets jQuery lorsque vous tapez un « . » à la suite d’un objet jQuery, comme indiqué ici.

   ![jQuery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. Dans _Layout. cshtml, mettez à jour les références de script à inclure `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Dans index. cshtml, ajoutez le code HTML suivant à la fin du fichier.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    L’application s’ouvre dans le navigateur.

    Cliquez sur **OK** dans l’alerte pour voir la page mise à jour vers la **version jQuery : 3.3.1 !!**.

    ![exemple jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Étapes suivantes

Vous souhaiterez peut-être en savoir plus sur l’utilisation de la fonction de machine à ASP.NET Core. Si vous êtes intéressé par la programmation AngularJS dans Visual Studio, vous pouvez utiliser l' [extension du service de langage AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) pour Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core et la machine à écrire](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [Extension du service de langage AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
