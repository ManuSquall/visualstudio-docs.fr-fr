---
title: Créer une application ASP.NET Core avec TypeScript
description: Dans ce tutoriel, vous créez une application à l’aide de ASP.NET Core et TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988549"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Tutorial: Créer une application ASP.NET Core avec TypeScript dans Visual Studio

Dans ce tutoriel pour le développement Visual Studio ASP.NET Core et TypeScript, vous créez une application web simple, ajoutez un code TypeScript, puis exécutez l’application. 

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
> * Créer un projet ASP.NET Core
> * Ajouter le forfait NuGet pour le support TypeScript
> * Ajouter un peu de code TypeScript
> * Exécuter l’application
> * Ajouter une bibliothèque tierce à l’aide de npm

## <a name="prerequisites"></a>Conditions préalables requises

* Vous devez avoir Visual Studio installé et le ASP.NET charge de travail de développement web.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, rendez-vous sur la page [de téléchargements](https://visualstudio.microsoft.com/downloads/) Visual Studio pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, rendez-vous sur la page [de téléchargements](https://visualstudio.microsoft.com/downloads/) Visual Studio pour l’installer gratuitement.
    ::: moniker-end

    Si vous avez besoin d’installer la charge de travail, mais ont déjà Visual Studio, allez à **Tools** > **Get Tools and Features ...**, qui ouvre l’installateur Studio visuel. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Créer un nouveau projet ASP.NET Core MVC

Visual Studio gère les fichiers d’une seule application dans un *projet*. Le projet comprend le code source, les ressources et les fichiers config.

>[!NOTE]
> Pour commencer par un projet de base ASP.NET vide et ajouter un frontend TypeScript, voir [ASP.NET Core avec TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) à la place.

Dans ce tutoriel, vous commencez par un projet simple contenant du code pour une application ASP.NET Core MVC.

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"
    Si la fenêtre de démarrage n’est pas ouverte, choisissez **File** > **Start Window**. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**. Dans la liste d’abandon de la langue, choisissez **C .** Dans la boîte de recherche, tapez **ASP.NET,** puis choisissez **ASP.NET’application Web de base**. Choisissez **La prochaine**.

    Tapez un nom pour le projet et choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    De la barre de menu haut, choisissez **File** > **New** > **Project**. Dans le volet gauche de la boîte de dialogue **New Project,** étendre **Visual C ,** puis choisissez **.NET Core**. Dans la vitre du milieu, choisissez **ASP.NET application Web de base - C ,** puis choisissez **OK**.
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet **ASP.NET Core Web Application,** vous devez ajouter la charge de travail **de développement ASP.NET et Web.** Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

1. Dans la boîte de dialogue qui apparaît, sélectionnez **l’application Web (Model-View-Controller)** dans la boîte de dialogue, puis choisissez **Create** (ou **OK**).

   ![Choisissez le modèle MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio crée la solution et ouvre votre projet dans le volet droit.

## <a name="add-some-code"></a>Ajouter du code

1. Dans Solution Explorer (droite). cliquez sur le nœud du projet et choisissez **Manage NuGet Packages**. Dans l’onglet **Parcourir,** recherchez **Microsoft.TypeScript.MSBuild,** puis cliquez sur **Installer** sur la droite pour installer le paquet.

   ![Ajouter le paquet NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio ajoute le paquet NuGet sous le nœud **dépendances** dans Solution Explorer.

   > [!NOTE]
   > Ce tutoriel nécessite le paquet NuGet. Alternativement, dans vos propres applications, vous pouvez utiliser le [paquet TypeScript npm](https://www.npmjs.com/package/typescript).

1. Dans Solution Explorer, cliquez à droite sur le nœud du projet et choisissez **Ajouter > nouveau dossier**. Utilisez les *scripts nominaux* pour le nouveau dossier.

1. Cliquez à droite sur le dossier *des scripts* et choisissez **Ajouter > Nouvel Élément**. Choisissez le **fichier de configuration TypeScript JSON**, puis cliquez sur **Ajouter**.

   Visual Studio ajoute le fichier *tsconfig.json* au dossier *de scripts.* Vous pouvez utiliser ce fichier pour [configurer](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) les options pour le compilateur TypeScript.

1. Ouvrez *tsconfig.json* et remplacez le code par défaut par le code suivant :

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

   *L’option outDir* spécifie le dossier de sortie pour les fichiers JavaScript plan qui sont transpilés par le compilateur TypeScript.

   Cette configuration fournit une introduction de base à l’utilisation de TypeScript. Dans d’autres scénarios, par exemple lors de l’utilisation [de gorgée ou de webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), vous pouvez vouloir un emplacement intermédiaire différent pour les fichiers JavaScript transpilés, en fonction de vos outils et préférences de configuration, au lieu de *.. /wwwroot/js*.

1. Cliquez à droite sur le dossier *des scripts* et choisissez **Ajouter > Nouvel Élément**. Choisissez le **fichier TypeScript**, tapez *l’application nom.ts* pour le nom de fichier, puis cliquez sur **Ajouter**.

   Visual Studio ajoute *app.ts* au dossier *de scripts.*

1. Ouvrez *app.ts* et ajoutez le code TypeScript suivant.

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

    Visual Studio fournit un support IntelliSense pour votre code TypeScript.

    Pour tester cela, `.lastName` `greeter` retirez de la fonction, puis retypez le ".", et vous voyez IntelliSense.

    ![Voir IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Sélectionnez `lastName` pour ajouter le nom de famille au code.

1. Ouvrez le dossier *Vues / Accueil,* puis ouvrez *index.html*.

1. Ajoutez le code HTML suivant à la fin du fichier.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Ouvrez le *dossier Vues / Partage,* puis ouvrez *_Layout.cshtml*.

1. Ajoutez la référence de script `@RenderSection("Scripts", required: false)`suivante avant l’appel à :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Créer l’application

1. Choisissez **Construire > Construire la solution**.

   Bien que l’application se construit automatiquement lorsque vous l’exécutez, nous voulons jeter un oeil à quelque chose qui se passe pendant le processus de construction.

1. Ouvrez le dossier *wwwroot / js,* et vous trouverez deux nouveaux fichiers, *app.js* et le fichier de carte source, *app.js.map*. Ces fichiers sont générés par le compilateur TypeScript.

   Les fichiers de carte source sont nécessaires pour débogage.

## <a name="run-the-application"></a>Exécuter l’application

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    L’application s’ouvre dans un navigateur.

    Dans la fenêtre du navigateur, vous verrez le titre **Bienvenue** et le bouton **Click Me.**

    ![ASP.NET core avec TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Cliquez sur le bouton pour afficher le message que nous avons spécifié dans le fichier TypeScript.

## <a name="debug-the-application"></a>Déboguer l’application

1. Définissez un point `greeter` d’arrêt dans la fonction en `app.ts` cliquant sur la marge gauche dans l’éditeur de code.

    ![Définir un point d'arrêt](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Appuyez sur **F5** pour exécuter l'application.

   Vous devrez peut-être répondre à un message pour activer le débogage du script.

   L’application s’arrête au point d’arrêt. Maintenant, vous pouvez inspecter les variables et utiliser des fonctionnalités de débbugger.

## <a name="add-typescript-support-for-a-third-party-library"></a>Ajouter le support TypeScript pour une bibliothèque tierce

1. Suivez les instructions dans la `package.json` gestion du paquet [npm](../javascript/npm-package-management.md#aspnet-core-projects) pour ajouter un fichier à votre projet. Cela ajoute un soutien npm à votre projet.

   >[!NOTE]
   > Pour ASP.NET projets Core, vous pouvez également utiliser [Library Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) ou fil au lieu de npm pour installer des fichiers JavaScript et CSS côté client.

1. Dans cet exemple, ajoutez un fichier de définition TypeScript pour jQuery à votre projet. Inclure ce qui suit dans votre fichier *package.json.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Cela ajoute le support TypeScript pour jQuery. La bibliothèque jQuery elle-même est déjà incluse dans le modèle de projet MVC (regardez sous wwwroot/lib dans Solution Explorer). Si vous utilisez un modèle différent, vous devrez peut-être inclure le paquet npm jquery ainsi.

1. Si le paquet dans Solution Explorer n’est pas installé, cliquez à droite sur le nœud npm et choisissez **des paquets de restauration**.

   >[!NOTE]
   > Dans certains scénarios, Solution Explorer peut indiquer qu’un paquet npm est désynchronisé avec *package.json* en raison d’un problème connu décrit [ici](https://github.com/aspnet/Tooling/issues/479). Par exemple, le paquet peut apparaître comme non installé lorsqu’il est installé. Dans la plupart des cas, vous pouvez mettre à jour Solution Explorer en supprimant *package.json*, redémarrer Visual Studio, et re-ajouter le fichier *package.json* comme décrit précédemment dans cet article.

1. Dans Solution Explorer, cliquez à droite sur le dossier des scripts et choisissez **Ajouter** > **un nouvel article**.

1. Choisissez **TypeScript File**, type *library.ts*, et choisissez **Ajouter**.

1. Dans *library.ts*, ajouter le code suivant.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Pour plus de simplicité, ce code affiche un message à l’aide de jQuery et d’une alerte.

   Avec les définitions de type TypeScript pour jQuery ajouté, vous obtenez le support IntelliSense sur les objets jQuery lorsque vous tapez un "." suivant un objet jQuery, comme indiqué ici.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. Dans _Layout.cshtml, mettre à jour les `library.js`références de script pour inclure .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Dans Index.cshtml, ajoutez le HTML suivant à la fin du fichier.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    L’application s’ouvre dans le navigateur.

    Cliquez **SUR OK** dans l’alerte pour voir la page mise à jour à la version **jQuery est: 3.3.1!!**.

    ![jquery exemple](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Étapes suivantes

Vous voudrez peut-être en savoir plus sur l’utilisation de TypeScript avec ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core et TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
