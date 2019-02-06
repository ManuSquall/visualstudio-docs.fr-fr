---
title: 'Démarrage rapide : Créer un service web ASP.NET Core en F#'
description: Découvrez comment créer un service web ASP.NET Core dans Visual Studio en F#, pas à pas.
ms.date: 08/24/2018
ms.prod: visual-studio-dev15
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e57f78fa0886a985bb830f3f279984893566bdb4
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690552"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Démarrage rapide : Utiliser Visual Studio pour créer votre premier service web ASP.NET Core en F#

Dans cette présentation de 5 à 10 minutes de F# dans Visual Studio, vous allez créer une application web ASP.NET Core en F#.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’API web ASP.NET Core. Le type de projet est fourni avec des fichiers de modèles qui constituent un service web opérationnel, avant même que vous ajoutiez quoi que ce soit !

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual F#**, puis choisissez **Web**. Dans le volet central, choisissez **Application web ASP.NET Core**, puis **OK**.

     Si vous ne voyez pas la catégorie du modèle de projet **.NET Core**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

     ![Charge de travail ASP.NET dans Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)

4. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.1** dans le menu déroulant supérieur. (Si **ASP.NET Core 2.1** ne figure pas dans la liste, installez-le en suivant le lien **Télécharger** qui doit s’afficher dans une barre jaune située en haut de la boîte de dialogue.) Cliquez sur **OK**.

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

## <a name="run-the-application"></a>Exécuter l'application

1. Appuyez sur **Ctrl**+**F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

2. La page doit accéder à l’itinéraire `/api/values`, mais si ce n’est pas le cas, entrez `https://localhost:44396/api/values` dans votre navigateur.

Le navigateur web affiche désormais le contenu JSON correspondant à ce que vous venez de taper.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur F#, ASP.NET Core et l’IDE Visual Studio. Pour voir l’application en cours d’exécution sur un serveur public, sélectionnez le bouton suivant.

> [!div class="nextstepaction"]
> [Déployer l’application sur Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Pour en savoir plus sur F#, consultez le [Guide F#](/dotnet/fsharp/index) officiel.