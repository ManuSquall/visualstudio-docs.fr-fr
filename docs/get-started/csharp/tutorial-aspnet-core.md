---
title: 'Didacticiel : prise en main de C# et ASP.NET Core'
titleSuffix: ''
description: Découvrez comment créer une application web ASP.NET Core dans Visual Studio avec C#, pas à pas.
ms.custom: seodec18, get-started
ms.date: 02/12/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 58f9604cbecdbe6414e91079a9e0e4691a32b768
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308543"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutoriel : Bien démarrer avec C# et ASP.NET Core dans Visual Studio

Dans ce tutoriel pour le développement C# avec ASP.NET Core à l’aide de Visual Studio, vous allez créer une application web C# ASP.NET Core, y apporter des changements, explorer certaines fonctionnalités de l’environnement IDE, puis exécuter l’application.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="install-visual-studio"></a>Installation de Visual Studio

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

### <a name="update-visual-studio"></a>Mettre à jour Visual Studio 2017

Si vous avez déjà installé Visual Studio, veillez à exécuter la version la plus récente. Pour plus d’informations sur la mise à jour de votre installation, consultez la page [mettre à jour Visual Studio vers la version la plus récente](../../install/update-visual-studio.md) .

### <a name="choose-your-theme-optional"></a>Choisir votre thème (facultatif)

Ce tutoriel contient des captures d’écran qui utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

## <a name="create-a-project"></a>Création d’un projet

Tout d’abord, nous allons créer un projet ASP.NET Core. Le type de projet inclut tous les fichiers de modèles nécessaires à un site web parfaitement fonctionnel, avant même d’avoir ajouté quoi que ce soit !

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual C#**, **Web**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Nommez ensuite le fichier *MyCoreApp*, puis choisissez **OK**.

   ![Modèle de projet d’application web ASP.NET Core dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Ajouter une charge de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application web ASP.NET Core**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement web et ASP.NET**. Vous pouvez ajouter cette charge de travail de l’une des deux manières suivantes, en fonction des mises à jour de Visual Studio 2017 qui sont installées sur votre ordinateur.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Sélectionnez le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. (Selon vos paramètres d’affichage, vous devrez peut-être faire défiler l’écran pour le voir.)

   ![Sélectionnez le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../media/tutorial-aspnet-workload.png)

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Annulez la boîte de dialogue **Nouveau projet**. Puis, dans la barre de menus supérieure, choisissez **Outils**  >  **accéder aux outils et aux fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

### <a name="add-a-project-template"></a>Ajouter un modèle de projet

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, choisissez le modèle de projet **Application web**.

1. Vérifiez **qu’ASP.NET Core 2.1** apparaît dans le menu déroulant supérieur. Puis, choisissez **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Si vous ne voyez pas **ASP.NET Core 2.1** dans le menu déroulant du haut, vérifiez que vous exécutez la mise en production la plus récente de Visual Studio. Pour plus d’informations sur la mise à jour de votre installation, consultez la page [mettre à jour Visual Studio vers la version la plus récente](../../install/update-visual-studio.md) .

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Afficher la fenêtre « Créer un projet »":::

1. Dans la fenêtre **créer un nouveau projet** , choisissez **C#** dans la liste langue. Ensuite, choisissez **Windows** dans la liste plateforme et **Web** dans la liste types de projets.

      Après avoir appliqué les filtres de langue, de plateforme et de type de projet, choisissez le modèle d' **application Web ASP.net Core** , puis choisissez **suivant**.

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Choisir le modèle C# pour l’application Web ASP.NET Core":::

   > [!NOTE]
   > Si vous ne voyez pas le modèle d' **application Web ASP.net Core** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement web et ASP.NET**.
   >
   > ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Si vous êtes invité à enregistrer votre travail, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *MyCoreApp* dans la zone **Nom du projet**. Ensuite, choisissez **suivant**.

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « MyCoreApp »":::

1. Dans la fenêtre **informations supplémentaires** , vérifiez que **.net Core 3,1** s’affiche dans le menu déroulant supérieur. Notez que vous pouvez choisir d’activer la prise en charge de l’ancrage en activant la case à cocher. Vous pouvez également ajouter la prise en charge de l’authentification en cliquant sur le bouton modifier l’authentification. Plusieurs options sont disponibles :
    - None : aucune authentification.
    - Comptes individuels : ceux-ci sont stockés dans une base de données locale ou basée sur Azure.
    - Plateforme d’identité Microsoft : cette option utilise Active Directory, Azure AD ou Microsoft 365 pour l’authentification.
    - Windows : adapté aux applications intranet.
    
    Laissez la case **activer l’ancrage** désactivée et sélectionnez **aucune** pour type d’authentification. Sélectionnez ensuite **Create** (Créer).

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="dans la fenêtre « informations supplémentaires », vérifiez que .NET Core 3,1 est sélectionné et laissez tous les paramètres par défaut":::

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

### <a name="about-your-solution"></a>À propos de votre solution

Cette solution suit le modèle de conception **Razor Pages**. Il diffère du modèle de conception [modèle-vue-contrôleur (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) en ce qu’il est simplifié de façon à intégrer le code du modèle et du contrôleur dans la Razor Page proprement dite.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Visite guidée de votre solution

 1. Le modèle de projet crée une solution avec un seul projet ASP.NET Core nommé _MyCoreApp_. Choisissez l’onglet **Explorateur de solutions** pour afficher son contenu.

    ![Explorateur de solutions ASP.NET dans Visual Studio pour la solution Razor Pages nommée MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Développez le dossier **Pages**, puis *About.cshtml*.

     ![Fichier About.cshtml dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Affichez le fichier **About.cshtml** dans l’éditeur de code.

     ![Capture d’écran montrant les dix premières lignes du fichier about. cshtml dans l’éditeur de code Visual Studio.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Choisissez le fichier **About.cshtml.cs**.

     ![Choisir le fichier About.cshtml dans l’éditeur de code Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Affichez le fichier **About.cshtml.cs** dans l’éditeur de code.

     ![Capture d’écran montrant les 18 premières lignes du fichier about. cshtml. cs dans l’éditeur de code Visual Studio. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Le projet contient un dossier **wwwroot** qui représente la racine de votre site web. Développez le dossier pour voir son contenu.

     ![Dossier wwwroot dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Vous pouvez placer du contenu de site statique, par exemple &mdash;des feuilles de style CSS, des images et des bibliothèques JavaScript&mdash;, directement dans les chemins souhaités.

 1. Le projet contient également des fichiers de configuration qui gèrent l’application Web au moment de l’exécution. La [configuration](/aspnet/core/fundamentals/configuration) de l’application par défaut est stockée dans *appsettings.json*. Toutefois, vous pouvez remplacer ces paramètres à l’aide de *appsettings.Development.json*. Développez le fichier **appsettings.json** pour voir le fichier **appsettings.Development.json**.

     ![Fichiers de configuration dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Exécuter, déboguer et apporter des changements

1. Choisissez le bouton **IIS Express** dans l’IDE pour générer et exécuter l’application en mode débogage. (Vous pouvez aussi appuyer sur **F5**, ou choisir **Déboguer** > **Démarrer le débogage** dans la barre de menus.)

     ![Sélectionnez le bouton IIS Express dans Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web « IIS Express »**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.
     >
     > Vous pouvez également recevoir un message qui vous demande si vous voulez accepter un certificat Express SSL IIS. Pour voir le code dans un navigateur web, choisissez **Oui**, puis choisissez à nouveau **Oui** si vous recevez un message d’avertissement de sécurité.

1. Visual Studio lance une fenêtre de navigateur. Les pages **Home**, **About** et **Contact** apparaissent dans la barre de menus. (Si ce n’est pas le cas, sélectionnez l’élément de menu « hamburger » pour les afficher.)

    ![Sélectionner l’élément de menu « hamburger » dans la barre de menus de l’application web](media/csharp-aspnet-razor-browser-page.png)

1. Choisissez **About** dans la barre de menus.

   ![Sélectionner About dans la barre de menus de la fenêtre du navigateur de l’application](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Entre autres choses, la page **About** du navigateur affiche le texte défini dans le fichier *About.cshtml*.

   ![Afficher le texte dans la page About](media/csharp-aspnet-razor-browser-page-about.png)

1. Retournez dans Visual Studio, puis appuyez sur **MAJ+F5** pour arrêter le mode Déboguer. Cela ferme également le projet dans la fenêtre du navigateur.

1. Dans Visual Studio, choisissez **About.cshtml**. Ensuite, supprimez le mot _additional_ et ajoutez à la place les mots _file and directory_.

    ![Modifier le texte dans le fichier About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Choisissez **About.cshtml.cs**. Ensuite, nettoyez les directives `using` en haut du fichier à l’aide du raccourci suivant :

   Choisissez l’une des directives `using` grisées. Une ampoule [Actions rapides](../../ide/quick-actions.md) apparaît alors juste au-dessous du signe insertion ou dans la marge de gauche. Choisissez l’ampoule, puis **Supprimer les Usings inutiles**.

   ![Supprimer les instructions using inutiles dans le fichier About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio supprime les directives `using` inutiles du fichier.

1. Ensuite, remplacez le corps de la méthode `OnGet()` par le code suivant :

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Remarquez les deux soulignements ondulés qui s’affichent sous **Environment** et **String**. Les soulignements ondulés signifient que ces types sont hors de portée.

   ![Erreurs signalées par des soulignements ondulés dans la méthode OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Ouvrez la barre d’outils **Liste d’erreurs** où sont répertoriées ces mêmes erreurs. (Si la barre d’outils **Liste d’erreurs** n’est pas visible, choisissez **Afficher** > **Liste d’erreurs** dans la barre de menus supérieure.)

   ![Liste d’erreurs dans Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Nous allons résoudre ce problème. Dans l’éditeur de code, placez votre curseur sur l’une des lignes contenant l’erreur, puis choisissez l’ampoule Actions rapides dans la marge de gauche. Ensuite, dans le menu déroulant, choisissez **using System;** pour ajouter cette directive en haut de votre fichier et résoudre les erreurs.

   ![Ajouter la directive « using System; »](media/csharp-aspnet-razor-add-usings.png)

1. Appuyez sur **CTRL** + **S** pour enregistrer vos modifications, puis appuyez sur **F5** pour ouvrir votre projet dans le navigateur Web.

1. En haut du site web, choisissez **About** pour afficher vos modifications.

   ![Afficher la page About mise à jour comportant les modifications effectuées](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Fermez le navigateur Web, appuyez sur **MAJ** + **F5** pour arrêter le mode débogage, puis fermez Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Visite guidée de votre solution

 1. Le modèle de projet crée une solution avec un seul projet ASP.NET Core nommé _MyCoreApp_. Choisissez l’onglet **Explorateur de solutions** pour afficher son contenu.

    ![Explorateur de solutions ASP.NET dans Visual Studio pour la solution Razor Pages nommée MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Développez le dossier **pages** .

     ![Le dossier pages dans Explorateur de solutions](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Affichez le fichier **index. cshtml** dans l’éditeur de code.

     ![Afficher le fichier index. cshtml dans l’éditeur de code Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Chaque fichier. cshtml est associé à un fichier de code. Pour ouvrir le fichier de code dans l’éditeur, développez le nœud **index. cshtml** dans Explorateur de solutions, puis choisissez le fichier **index. cshtml. cs** .

     ![Choisir le fichier index. cshtml. cs dans l’éditeur de code Visual Studio](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Affichez le fichier **index. cshtml. cs** dans l’éditeur de code.

     ![Afficher le fichier About.cshtml dans l’éditeur de code Visual Studio](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Le projet contient un dossier **wwwroot** qui représente la racine de votre site web. Développez le dossier pour voir son contenu.

     ![Dossier wwwroot dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Vous pouvez placer du contenu de site statique, par exemple &mdash;des feuilles de style CSS, des images et des bibliothèques JavaScript&mdash;, directement dans les chemins souhaités.

 1. Le projet contient également des fichiers de configuration qui gèrent l’application Web au moment de l’exécution. La [configuration](/aspnet/core/fundamentals/configuration) de l’application par défaut est stockée dans *appsettings.json*. Toutefois, vous pouvez remplacer ces paramètres à l’aide de *appsettings.Development.json*. Développez le fichier **appsettings.json** pour voir le fichier **appsettings.Development.json**.

     ![Fichiers de configuration dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Exécuter, déboguer et apporter des changements

1. Choisissez le bouton **IIS Express** dans l’IDE pour générer et exécuter l’application en mode débogage. (Vous pouvez aussi appuyer sur **F5**, ou choisir **Déboguer** > **Démarrer le débogage** dans la barre de menus.)

     ![Sélectionnez le bouton IIS Express dans Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web « IIS Express »**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.
     >
     > Vous pouvez également recevoir un message qui vous demande si vous voulez accepter un certificat Express SSL IIS. Pour voir le code dans un navigateur web, choisissez **Oui**, puis choisissez à nouveau **Oui** si vous recevez un message d’avertissement de sécurité.

1. Visual Studio lance une fenêtre de navigateur. Vous devez ensuite voir page d' **hébergement** et pages de **confidentialité** dans la barre de menus.

1. Dans la barre de menus, choisissez **confidentialité** .

   La page **confidentialité** dans le navigateur affiche le texte qui est défini dans le fichier *privacy. cshtml* .

   ![Afficher le texte sur la page confidentialité](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Retournez dans Visual Studio, puis appuyez sur **MAJ+F5** pour arrêter le mode Déboguer. Cela ferme également le projet dans la fenêtre du navigateur.

1. Dans Visual Studio, ouvrez **privacy. cshtml** pour le modifier. Ensuite, supprimez les mots _Utilisez cette page pour détailler la politique de confidentialité de votre site_ et, à la place, ajoutez les mots _que cette page est en cours de construction en tant que @ViewData [« timestamp »]_.

    ![Modifier le texte dans le fichier privacy. cshtml](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. À présent, nous allons modifier le code. Choisissez **privacy. cshtml. cs**. Ensuite, nettoyez les directives `using` en haut du fichier à l’aide du raccourci suivant :

   Choisissez l’une des directives `using` grisées. Une ampoule [Actions rapides](../../ide/quick-actions.md) apparaît alors juste au-dessous du signe insertion ou dans la marge de gauche. Choisissez l’ampoule, puis pointez sur **Supprimer les utilisations inutiles**.

   ![Supprimer les using inutiles dans le fichier privacy. cshtml. cs](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Choisissez maintenant **aperçu des modifications** pour voir ce qui va changer.

   ![Prévisualiser les modifications](media/vs-2019/csharp-aspnet-preview-changes.png)

   Choisissez **Appliquer**. Visual Studio supprime les directives `using` inutiles du fichier.

1. Ensuite, remplacez le corps de la méthode `OnGet()` par le code suivant :

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. Notez que deux soulignements ondulés s’affichent sous **DateTime**. Les soulignements ondulés s’affichent, car ces types ne sont pas dans la portée.

   ![Erreurs signalées par des soulignements ondulés dans la méthode OnGet](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Ouvrez la barre d’outils **Liste d’erreurs** où sont répertoriées ces mêmes erreurs. (Si la barre d’outils **Liste d’erreurs** n’est pas visible, choisissez **Afficher** > **Liste d’erreurs** dans la barre de menus supérieure.)

   ![Liste d’erreurs dans Visual Studio](media/vs-2019/csharp-aspnet-error-list.png)

1. Nous allons résoudre ce problème. Dans l’éditeur de code, placez votre curseur sur l’une des lignes contenant l’erreur, puis choisissez l’ampoule Actions rapides dans la marge de gauche. Ensuite, dans le menu déroulant, choisissez **using System;** pour ajouter cette directive en haut de votre fichier et résoudre les erreurs.

   ![Ajouter la directive « using System; »](media/vs-2019/csharp-aspnet-add-usings.png)

1. Appuyez sur **F5** pour ouvrir votre projet dans le navigateur Web.

1. En haut du site Web, choisissez **confidentialité** pour afficher vos modifications.

   ![Afficher la page de confidentialité mise à jour qui comprend les modifications que vous avez apportées](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Fermez le navigateur Web, appuyez sur **MAJ** + **F5** pour arrêter le mode débogage, puis fermez Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Questions fréquentes (FAQ) et réponses rapides

Voici des Questions fréquentes (FAQ) rapides pour mettre en lumière certains concepts clés.

### <a name="what-is-c"></a>Qu’est-ce que C# ?

[C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/) est un langage de programmation orienté objet et de type sécurisé conçu pour être robuste et facile à apprendre.

### <a name="what-is-aspnet-core"></a>Qu’est-ce qu’ASP.NET Core ?

ASP.NET Core est un framework open source et multiplateforme qui permet de créer des applications connectées à internet, telles que des applications et des services web. Les applications ASP.NET Core peuvent s’exécuter sur le .NET Framework ou .NET Core. Vous pouvez développer et exécuter des applications multiplateformes ASP.NET Core sur Windows, Mac et Linux. ASP.NET Core est open source dans [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Qu’est-ce que Visual Studio ?

Visual Studio est une suite de développement intégrée d’outils de productivité pour les développeurs. Il s’agit d’un programme qui sert à créer des applications et des programmes.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’IDE Visual Studio. Pour en savoir plus sur la création d’une application web ou d’un site web en C# et avec ASP.NET, suivez les tutoriels suivants :

> [!div class="nextstepaction"]
> [Créer une application web Razor Pages avec ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
