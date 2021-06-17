---
title: 'Démarrage rapide : créer un service web ASP.NET Core en F#'
description: Découvrez comment créer un service web ASP.NET Core dans Visual Studio en F#, pas à pas.
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: acquisition
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cbb85c41a01a03461bc1a73bdb58620e8a0c472f
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113200"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Démarrage rapide : utiliser Visual Studio pour créer votre premier service Web ASP.NET Core en F\#

Dans cette présentation de 5 à 10 minutes de F# dans Visual Studio, vous allez créer une application web ASP.NET Core en F#.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Vous allez d’abord créer un projet d’API web ASP.NET Core. Le type de projet est fourni avec des fichiers de modèles qui constituent un service web opérationnel, avant même que vous ajoutiez quoi que ce soit !

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

2. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual F#**, puis choisissez **Web**. Dans le volet central, choisissez **Application web ASP.NET Core**, puis **OK**.

     Si vous ne voyez pas la catégorie du modèle de projet **.NET Core**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

     ![Charge de travail ASP.NET dans Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)

4. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.1** dans le menu déroulant supérieur. (Si vous ne voyez pas **ASP.NET Core 2,1** dans la liste, installez-le en suivant le lien de **Téléchargement** qui doit apparaître dans une barre jaune en haut de la boîte de dialogue.) Choisissez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Sur la page **Créer un projet**, tapez **f# web** dans la zone de recherche, puis choisissez le modèle de projet **Application web ASP.NET Core**. Choisissez **Suivant**.

4. Sur la page **Configurer votre nouveau projet**, entrez un nom, puis choisissez **Créer**.

5. Sur la page **Créer une application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.1** dans le menu déroulant supérieur, puis choisissez **Créer**.

::: moniker-end

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Dans la barre d’outils de l’**Explorateur de solutions**, développez le dossier **Contrôleurs**, puis choisissez **ValuesController.fs** pour l’ouvrir dans l’éditeur.

   ![Explorateur de solutions avec le dossier Contrôleurs développé dans le projet d’API web F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Modifiez ensuite le membre `Get()` comme suit :

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Le code est simple. Un tableau de valeurs F# est lié au nom `values`, puis passé au framework ASP.NET Core MVC en tant que `ActionResult`. ASP.NET Core s’occupe du reste à votre place.

Le résultat doit ressembler à ceci dans l’éditeur :

![Membre Get modifié](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Exécution de l'application

1. Appuyez sur **CTRL** + **F5** pour exécuter l’application et l’ouvrir dans un navigateur Web.

2. La page doit accéder à l’itinéraire `/api/values`, mais si ce n’est pas le cas, entrez `https://localhost:44396/api/values` dans votre navigateur.

Le navigateur web affiche désormais le contenu JSON correspondant à ce que vous venez de taper.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur F#, ASP.NET Core et l’IDE Visual Studio. Pour voir l’application en cours d’exécution sur un serveur public, sélectionnez le bouton suivant.

> [!div class="nextstepaction"]
> [Déployer l’application sur Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Pour en savoir plus sur F#, consultez le [Guide F#](/dotnet/fsharp/index) officiel.
