---
title: Didacticiel de Hello World extension | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3beedce039d1c093b5dfebce07b09d7d3a5795dc
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194734"
---
# <a name="create-your-first-extension-hello-world"></a>Créer votre première extension : Hello World

Cet exemple Hello World vous explique comment créer votre première extension pour Visual Studio. Ce didacticiel vous montre comment ajouter une nouvelle commande à Visual Studio.

Dans le processus, vous allez apprendre comment :

* **[Créer un projet d’extensibilité](#create-an-extensibility-project)**
* **[Ajouter une commande personnalisée](#add-a-custom-command)**
* **[Modifier le code source](#modify-the-source-code)**
* **[Exécutez-le](#run-it)**

Pour cet exemple, vous utiliserez Visual c# pour ajouter qu'un bouton de menu personnalisé nommé « Dire Hello World ! » qui ressemble à ceci :

![Commande de Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Cet article s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [procédure pas à pas d’extensibilité dans Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prérequis

Avant de commencer, assurez-vous que vous avez installé le **développement d’extensions Visual Studio** charge de travail, qui inclut le modèle VSIX, vous avez besoin et exemple de code.

> [!NOTE]
> Vous pouvez utiliser n’importe quelle édition de Visual Studio (Community, Professional ou Enterprise) pour créer un projet d’extensibilité de Visual Studio.

## <a name="create-an-extensibility-project"></a>Créer un projet d’extensibilité

::: moniker range="vs-2017"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

Étape 2. Dans la zone de recherche en haut à droite, tapez « vsix » et sélectionnez le visuel C# **projet VSIX**. Entrez « HelloWorld » pour le **nom** en bas de la boîte de dialogue et sélectionnez **OK**.

![nouveau projet](media/hello-world-new-project.png)

Vous devez maintenant voir la page mise en route et certains exemples de ressources.

Si vous devez laisser ce didacticiel et revenir à ce dernier, vous pouvez trouver votre nouveau projet HelloWorld sur le **Page de démarrage** dans le **récents** section.

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**. Recherchez « vsix » et sélectionnez le visuel C# **projet VSIX** , puis **suivant**.

Étape 2. Entrez « HelloWorld » pour le **nom_projet** et sélectionnez **créer**.

![nouveau projet](media/hello-world-new-project-2019.png)

Vous devriez maintenant voir le projet HelloWorld dans **l’Explorateur de solutions**.

::: moniker-end

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée

Étape 1. Si vous sélectionnez le *.vsixmanifest* fichier manifeste, vous pouvez voir quelles sont les options modifiables, telles que la description, auteur et la version.

Étape 2. Cliquez sur le projet (pas la solution). Dans le menu contextuel, sélectionnez **ajouter**, puis **un nouvel élément**.

Étape 3. Sélectionnez le **extensibilité** section, puis choisissez **commande personnalisée**.

Étape 4. Dans le **nom** en bas, entrez un nom de fichier tel que *Command.cs*.

![commande personnalisée](media/hello-world-custom-command.png)

Votre nouveau fichier de commandes est visible dans **l’Explorateur de solutions**. Sous le **ressources** nœud, vous trouverez des autres fichiers associés à votre commande. Par exemple, si vous souhaitez modifier l’image, le fichier PNG est ici.

## <a name="modify-the-source-code"></a>Modifier le code source

À ce stade, la commande et le texte du bouton sont générés automatiquement et pas très intéressant. Si vous souhaitez apporter des modifications, vous pouvez modifier le fichier VSCT et le fichier CS.

* Le fichier VSCT est où vous pouvez renommer vos commandes, ainsi définir où ils vont dans le système de commande de Visual Studio. À mesure que vous explorez le fichier VSCT, vous remarquerez des commentaires qui expliquent chaque section des contrôles de code VSCT.

* Le fichier CS est dans laquelle vous pouvez définir des actions, telles que le Gestionnaire de clic.

::: moniker range="vs-2017"

Étape 1. Dans **l’Explorateur de solutions**, recherchez le fichier VSCT pour votre nouvelle commande. Dans ce cas, elle sera appelée *CommandPackage.vsct*.

![commande package vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans **l’Explorateur de solutions**, recherchez le fichier VSCT pour votre package d’extension Visual Studio. Dans ce cas, elle sera appelée *HelloWorldPackage.vsct*.

::: moniker-end

Étape 2. Modifier le `ButtonText` paramètre `Say Hello World!`.

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

Étape 3. Revenez à **l’Explorateur de solutions** et recherchez le *Command.cs* fichier. Dans le `Execute` (méthode), modifiez la chaîne de `message` de `string.Format(..)` à `Hello World!`.

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

Veillez à enregistrer vos modifications dans chaque fichier.

## <a name="run-it"></a>Exécutez-le

Vous pouvez maintenant exécuter le code source dans l’Instance expérimentale de Visual Studio.

Étape 1. Appuyez sur **F5** pour exécuter le **démarrer le débogage** commande. Cette commande génère votre projet et démarre le débogueur, lancer une nouvelle instance de Visual Studio appelé le **Instance expérimentale**.

::: moniker range="vs-2017"

Vous verrez les mots **Instance expérimentale** dans la barre de titre de Visual Studio.

![barre de titre d’instance expérimentale](media/hello-world-exp-instance.png)

::: moniker-end

Étape 2. Sur le **outils** menu de la **Instance expérimentale**, cliquez sur **Say Hello World !**.

![résultat final](media/hello-world-final-result.png)

Vous devriez voir la sortie de votre nouvelle commande personnalisée, dans ce cas, la boîte de dialogue dans le centre de l’écran qui vous donne le **Hello World !** « Operation Not Found! ».

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les principes fondamentaux de l’utilisation de l’extensibilité de Visual Studio, voici où vous pouvez en savoir plus :

* [Commencer à développer des extensions Visual Studio](starting-to-develop-visual-studio-extensions.md) -exemples, didacticiels. et la publication de votre extension
* [Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -nouvelles fonctionnalités d’extensibilité dans Visual Studio 2017
* [Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2019](whats-new-visual-studio-2019-sdk.md) -nouvelles fonctionnalités d’extensibilité dans Visual Studio 2019
* [À l’intérieur de Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -Découvrez les détails de l’extensibilité de Visual Studio