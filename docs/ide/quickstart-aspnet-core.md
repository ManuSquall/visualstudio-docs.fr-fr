---
title: "Utiliser Visual Studio pour créer une application web ASP.NET Core dans C# | Microsoft Docs"
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: cfcb85704302303704ef9b4bb1affc60031793d9
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web ASP.NET Core

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application web ASP.NET Core C# simple. Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application web ASP.NET Core. Le type de projet est fourni avec les fichiers modèles qui constituent une application web fonctionnelle, avant même que vous ayez ajouté quoi que ce soit.

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier**, **Nouveau**, **Projet...**

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**, puis **OK**.

     Si vous ne voyez pas le modèle de projet **.NET Core**, quittez la boîte de dialogue **Nouveau projet**, puis dans la barre de menus supérieure, choisissez **Outils**, **Obtenir les outils et fonctionnalités...** Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

     ![Charge de travail ASP.NET dans Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.0** dans le menu déroulant supérieur. (Si **ASP.NET Core 2.0** ne figure pas dans la liste, installez-le en suivant le lien **Télécharger** qui doit s’afficher dans une barre jaune située en haut de la boîte de dialogue.) Cliquez sur **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Dans la barre d’outils de l’**Explorateur de solutions**, développez le dossier **Pages**, puis choisissez **About.cshtml** pour l’ouvrir dans l’éditeur. Ce fichier correspond à une page appelée **À propos de** dans l’application web.

1. Dans l’éditeur, choisissez `AboutModel`, puis appuyez sur **F12** ou choisissez **Atteindre la définition** dans le menu contextuel (clic droit). Cette commande affiche la définition de la classe C# `AboutModel`.

   ![Menu contextuel Atteindre la définition](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Ensuite, nous allons nettoyer les directives `using` en haut du fichier à l’aide d’un simple raccourci. Choisissez l’une des directives using grisées. Une ampoule [Actions rapides](../ide/quick-actions.md) apparaît alors juste en dessous du signe insertion ou dans la marge de gauche. Choisissez l’ampoule, puis **Supprimer les Usings inutiles**.

     Les instructions using inutiles sont supprimées du fichier.

1. Remplacez le corps de la méthode `OnGet()` par le code suivant :

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Deux soulignements ondulés s’affichent sous **Environment** et **String**, car ces types ne sont pas dans la portée. Ouvrez la barre d’outils **Liste d’erreurs** où sont répertoriées ces mêmes erreurs. (Si la barre d’outils **Liste d’erreurs** n’est pas visible, choisissez **Afficher**, **Liste d’erreurs** dans la barre de menus supérieure.)

   ![Liste d'erreurs](../ide/media/quickstart-aspnet-errorlist.png)

1. Dans la fenêtre d’éditeur, placez votre curseur sur l’une des lignes contenant l’erreur, puis choisissez l’ampoule Actions rapides dans la marge de gauche. Dans le menu déroulant, choisissez **using System;** pour ajouter cette directive en haut de votre fichier et résoudre les erreurs.

## <a name="run-the-application"></a>Exécuter l'application

1. Appuyez sur **Ctrl+F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

1. En haut du site web, choisissez **À propos de** pour afficher le message de répertoire que vous avez ajouté dans la méthode `OnGet()` pour la page **À propos de**.

1. Fermez le navigateur web.

> [!NOTE]
> Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web 'IIS Express'**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur l’IDE de Visual Studio. Si vous souhaitez en savoir plus sur ses fonctionnalités, poursuivez avec un didacticiel de la section **Didacticiels** dans la table des matières.

## <a name="see-also"></a>Voir aussi

[Bien démarrer avec C# et Visual Basic à l’aide de Visual Studio](getting-started-with-visual-csharp-and-visual-basic.md)  
[Bien démarrer avec des pages Razor dans ASP.NET Core](/aspnet/core/tutorials/razor-pages/razor-pages-start)