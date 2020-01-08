---
title: Didacticiel sur l’extension de Hello World | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404137"
---
# <a name="create-your-first-extension-hello-world"></a>Créer votre première extension : Hello World

Cet exemple de Hello World vous guide tout au long de la création de votre première extension pour Visual Studio. Ce didacticiel vous montre comment ajouter une nouvelle commande à Visual Studio.

Dans le processus, vous allez apprendre à :

* **[Créer un projet d’extensibilité](#create-an-extensibility-project)**
* **[Ajouter une commande personnalisée](#add-a-custom-command)**
* **[Modifier le code source](#modify-the-source-code)**
* **[Exécuter](#run-it)**

Pour cet exemple, vous allez utiliser Visual C# pour ajouter un bouton de menu personnalisé nommé « disons Hello World ! » Cela ressemble à ceci :

![Commande Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Cet article s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [procédure pas à pas d’extensibilité dans Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Configuration requise

Avant de commencer, assurez-vous que vous avez installé la charge de travail développement de l' **extension Visual Studio** , qui comprend le modèle VSIX dont vous aurez besoin et un exemple de code.

> [!NOTE]
> Vous pouvez utiliser n’importe quelle édition de Visual Studio (Community, Professional ou Enterprise) pour créer un projet d’extensibilité Visual Studio.

## <a name="create-an-extensibility-project"></a>Créer un projet d’extensibilité

::: moniker range="vs-2017"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

Étape 2. Dans la zone de recherche dans l’angle supérieur droit, tapez « VSIX », puis C# sélectionnez le **projet Visual VSIX**. Entrez « HelloWorld » comme **nom** en bas de la boîte de dialogue, puis sélectionnez **OK**.

![nouveau projet](media/hello-world-new-project.png)

Vous devez maintenant voir la page Prise en main et des exemples de ressources.

Si vous devez conserver ce didacticiel et y revenir, vous pouvez trouver votre nouveau projet HelloWorld dans la **page de démarrage** de la section **récent** .

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**. Recherchez « VSIX » et sélectionnez le projet Visual C# **VSIX** , puis **suivant**.

Étape 2. Entrez « HelloWorld » comme **nom de projet** , puis sélectionnez **créer**.

![nouveau projet](media/hello-world-new-project-2019.png)

Vous devez maintenant voir le projet HelloWorld dans **Explorateur de solutions**.

::: moniker-end

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée

Étape 1. Si vous sélectionnez le fichier manifeste *. vsixmanifest* , vous pouvez voir les options qui peuvent être modifiées, telles que la description, l’auteur et la version.

Étape 2. Cliquez avec le bouton droit sur le projet (pas la solution). Dans le menu contextuel, sélectionnez **Ajouter**, puis **nouvel élément**.

Étape 3. Sélectionnez la section **extensibilité** , puis choisissez **commande**.

Étape 4. Dans le champ **nom** en bas, entrez un nom de fichier tel que *Command.cs*.

![commande personnalisée](media/hello-world-vsix-command.png)

Votre nouveau fichier de commandes est visible dans **Explorateur de solutions**. Sous le nœud **ressources** , vous trouverez d’autres fichiers associés à votre commande. Par exemple, si vous souhaitez modifier l’image, le fichier PNG est ici.

## <a name="modify-the-source-code"></a>Modifier le code source

À ce stade, le texte de la commande et du bouton est généré automatiquement et n’est pas très intéressant. Vous pouvez modifier le fichier VSCT et le fichier CS si vous souhaitez apporter des modifications.

* Le fichier VSCT est l’emplacement où vous pouvez renommer vos commandes, ainsi que définir leur emplacement dans le système de commandes de Visual Studio. À mesure que vous explorez le fichier VSCT, vous remarquerez des commentaires qui expliquent ce que chaque section du code VSCT contrôle.

* Le fichier CS est l’emplacement où vous pouvez définir des actions, telles que le gestionnaire de clics.

::: moniker range="vs-2017"

Étape 1. Dans **Explorateur de solutions**, recherchez le fichier vsct pour votre nouvelle commande. Dans ce cas, il sera appelé *CommandPackage. vsct*.

![vsct du package de commandes](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans **Explorateur de solutions**, recherchez le fichier vsct de votre extension vs package. Dans ce cas, il sera appelé *HelloWorldPackage. vsct*.

::: moniker-end

Étape 2. Remplacez le paramètre `ButtonText` par `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Étape 3. Revenez à **Explorateur de solutions** et recherchez le fichier *Command.cs* . Dans la méthode `Execute`, remplacez la chaîne `message` de `string.Format(..)` par `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Veillez à enregistrer les modifications apportées à chaque fichier.

## <a name="run-it"></a>Exécutez le script

Vous pouvez maintenant exécuter le code source dans l’instance expérimentale de Visual Studio.

Étape 1. Appuyez sur **F5** pour exécuter la commande **Démarrer le débogage** . Cette commande génère votre projet et démarre le débogueur, en lançant une nouvelle instance de Visual Studio appelée l' **instance expérimentale**.

::: moniker range="vs-2017"

Les mots **instance expérimentale** s’affichent dans la barre de titre de Visual Studio.

![barre de titre de l’instance expérimentale](media/hello-world-exp-instance.png)

::: moniker-end

Étape 2. Dans le menu **Outils** de l' **instance expérimentale**, cliquez sur **Say Hello World !** .

![résultat final](media/hello-world-final-result.png)

Vous devez voir la sortie de votre nouvelle commande personnalisée, dans ce cas la boîte de dialogue au centre de l’écran qui vous donne le **Hello World !** « Operation Not Found! ».

## <a name="next-steps"></a>Étapes suivantes :

Maintenant que vous connaissez les bases de l’utilisation de l’extensibilité Visual Studio, voici ce que vous pouvez en savoir plus :

* [Commencez à développer des extensions Visual Studio](starting-to-develop-visual-studio-extensions.md) , des exemples, des didacticiels. et la publication de votre extension
* [Nouveautés du kit de développement logiciel (SDK) Visual studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -nouvelles fonctionnalités d’extensibilité dans visual studio 2017
* [Nouveautés du kit de développement logiciel (SDK) Visual studio 2019](whats-new-visual-studio-2019-sdk.md) -nouvelles fonctionnalités d’extensibilité dans visual studio 2019
* [Dans le kit de développement logiciel (SDK) Visual Studio](internals/inside-the-visual-studio-sdk.md) , Découvrez les détails de l’extensibilité Visual Studio
