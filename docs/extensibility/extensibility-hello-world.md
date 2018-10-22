---
title: Hello World | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91d9c809d16a3763bed75d5de4c03bd7112c6e8a
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356754"
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

## <a name="prerequisites"></a>Prérequis

Avant de commencer, assurez-vous que vous avez installé le **développement d’extensions Visual Studio** charge de travail qui inclut le modèle VSIX, vous avez besoin et exemple de code.

> [!NOTE]
> Vous pouvez utiliser n’importe quelle édition de Visual Studio (Community, Professional ou Enterprise) pour créer un projet d’extensibilité de Visual Studio.

## <a name="create-an-extensibility-project"></a>Créer un projet d’extensibilité

Étape 1. À partir de la **fichier** menu, cliquez sur **nouveau projet**. En bas de l’écran, entrez le nom de votre projet.

Étape 2. À partir de la **modèles** menu, cliquez sur **Visual C#**, cliquez sur **extensibilité**, puis cliquez sur **projet VSIX**.

![nouveau projet](media/hello-world-new-project.png)

Vous devez maintenant voir la page mise en route et certains exemples de ressources.

Si vous devez laisser ce didacticiel et revenir à ce dernier, vous pouvez trouver votre nouveau projet HelloWorld sur le **Page de démarrage** dans le **récents** section.

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée

Étape 1. Si vous sélectionnez le manifeste, vous pouvez voir quelles sont les options modifiables, pour l’instance, métadonnées, la description et version.

Étape 2. Cliquez sur le projet (pas la solution). Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.

Étape 3. Sélectionnez le **extensibilité** section, puis cliquez sur **commande personnalisée**.

Étape 4. Dans le **nom** champ du bas, donnez-lui un nom, par exemple *Command.cs*.

![commande personnalisée](media/hello-world-custom-command.png)

Votre nouvelle commande est répertorié dans **l’Explorateur de solutions** sous le **ressources** branche. Il s’agit également où vous trouverez les autres fichiers associés à votre commande, telles que les fichiers PNG et ICO, si vous souhaitez modifier l’image.

## <a name="modify-the-source-code"></a>Modifier le code source

À ce stade, le bouton que vous ajoutez est relativement générique. Vous devrez modifier le fichier VSCT et le fichier CS si vous souhaitez apporter des modifications.

* Le fichier VSCT est où vous pouvez renommer vos commandes, ainsi définir où ils vont dans le système de commande de Visual Studio. À mesure que vous explorez le fichier VSCT, vous remarquerez un grand nombre de commentaires de code qui explique le contenu de chaque section de contrôles de code.

* Le fichier CS est dans laquelle vous pouvez définir des actions, telles que le Gestionnaire de clic.

Étape 1. Dans **l’Explorateur de solutions**, recherchez le fichier VSCT pour votre nouvelle commande. Dans ce cas, elle sera appelée *CommandPackage.vsct*.

![commande package vsct](media/hello-world-command-package-vsct.png)

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

Étape 3. Revenez à **l’Explorateur de solutions** et recherchez le *Command.cs* fichier. Modifier la chaîne `message` pour la commande `string.Format(..)` à `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Étape 1. Cliquez sur **Démarrer** dans la barre d’outils. Cela génère votre projet et démarre le débogueur, lancer une nouvelle instance de Visual Studio appelé le **Instance expérimentale**.

Vous verrez les mots **Instance expérimentale** dans la barre de titre de Visual Studio.

![barre de titre d’instance expérimentale](media/hello-world-exp-instance.png)

Étape 2. Sur le **outils** menu de la **Instance expérimentale**, cliquez sur **Say Hello World !**.

![résultat final](media/hello-world-final-result.png)

Vous devriez voir la sortie de votre nouvelle commande personnalisée, dans ce cas, la boîte de dialogue dans le centre de l’écran qui vous donne le **Hello World !** « Operation Not Found! ».

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les principes fondamentaux de l’utilisation de l’extensibilité de Visual Studio, voici où vous pouvez en savoir plus :

* [Commencer à développer des extensions Visual Studio](starting-to-develop-visual-studio-extensions.md) -exemples, didacticiels. et la publication de votre extension.
* [Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -nouvelles fonctionnalités d’extensibilité dans Visual Studio 2017
* [À l’intérieur de Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -Découvrez les détails de l’extensibilité de Visual Studio
