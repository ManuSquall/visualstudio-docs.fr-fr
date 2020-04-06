---
title: Bonjour World tutoriel d’extension (fr) Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711661"
---
# <a name="create-your-first-extension-hello-world"></a>Créez votre première extension : Hello World

Cet exemple Hello World vous guide à travers la création de votre première extension pour Visual Studio. Ce tutoriel vous montre comment ajouter une nouvelle commande à Visual Studio.

Dans le processus, vous apprendrez à :

* **[Créer un projet d’extéabilité](#create-an-extensibility-project)**
* **[Ajouter une commande personnalisée](#add-a-custom-command)**
* **[Modifier le code source](#modify-the-source-code)**
* **[Exécutez le script](#run-it)**

Pour cet exemple, vous utiliserez Visual C pour ajouter un bouton de menu personnalisé intitulé « Dis bonjour dans le monde ! » qui ressemble à ceci:

![Bonjour World commande](media/hello-world-say-hello-world.png)

> [!NOTE]
> Cet article s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, voir [Extensibility walkthrough dans Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prérequis

Avant de commencer, assurez-vous d’avoir installé la charge de travail **de développement d’extension Visual Studio,** qui comprend le modèle VSIX dont vous aurez besoin et l’échantillon de code.

> [!NOTE]
> Vous pouvez utiliser n’importe quelle édition de Visual Studio (Community, Professional, or Enterprise) pour créer un projet d’extéabilité Visual Studio.

## <a name="create-an-extensibility-project"></a>Créer un projet d’extéabilité

::: moniker range="vs-2017"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

Étape 2. Dans la zone de recherche en haut à droite, tapez «vsix» et sélectionnez le projet VISUAL C **VSIX**. Entrez "HelloWorld" pour le **nom** au bas du dialogue et sélectionnez **OK**.

![Nouveau projet](media/hello-world-new-project.png)

Vous devriez maintenant voir la page Getting Started et quelques ressources d’échantillon.

Si vous avez besoin de quitter ce tutoriel et y revenir, vous pouvez trouver votre nouveau projet HelloWorld sur la **page de démarrage** dans la section **récente.**

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**. Recherchez "vsix" et sélectionnez le projet VISUAL C **VSIX,** puis **suivant**.

Étape 2. Entrez "HelloWorld" pour le nom du **projet** et sélectionnez **Créer**.

![Nouveau projet](media/hello-world-new-project-2019.png)

Vous devriez maintenant voir le projet HelloWorld dans **Solution Explorer**.

::: moniker-end

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée

Étape 1. Si vous sélectionnez le fichier manifeste *.vsixmanifest,* vous pouvez voir quelles options sont modifiables, telles que la description, l’auteur et la version.

Étape 2. Cliquez à droite sur le projet (pas la solution). Sur le menu du contexte, sélectionnez **Ajouter**, puis **Nouvel Article**.

Étape 3. Sélectionnez la section **Extensibility,** puis choisissez **Command**.

Étape 4. Dans le champ **Nom** en bas, entrez un nom de fichier tel que *Command.cs*.

![commande personnalisée](media/hello-world-vsix-command.png)

Votre nouveau fichier de commande est visible dans **Solution Explorer**. Sous le nœud **Ressources,** vous trouverez d’autres fichiers liés à votre commande. Par exemple, si vous souhaitez modifier l’image, le fichier PNG est ici.

## <a name="modify-the-source-code"></a>Modifier le code source

À ce stade, la commande et le texte de bouton sont autogénérés et pas très intéressants. Vous pouvez modifier le fichier VSCT et le fichier CS si vous souhaitez apporter des modifications.

* Le fichier VSCT est l’endroit où vous pouvez renommer vos commandes, ainsi que définir où ils vont dans le système de commande Visual Studio. Lorsque vous explorez le fichier VSCT, vous remarquerez des commentaires qui expliquent ce que chaque section du code VSCT contrôle.

* Le fichier CS est l’endroit où vous pouvez définir des actions, telles que le gestionnaire de clics.

::: moniker range="vs-2017"

Étape 1. Dans **Solution Explorer**, trouvez le fichier VSCT pour votre nouvelle commande. Dans ce cas, il sera appelé *CommandPackage.vsct*.

![paquet de commande vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Étape 1. Dans **Solution Explorer**, trouvez le fichier VSCT pour votre package VS d’extension. Dans ce cas, il sera appelé *HelloWorldPackage.vsct*.

::: moniker-end

Étape 2. Modifier `ButtonText` le `Say Hello World!`paramètre pour .

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

Étape 3. Retournez à **Solution Explorer** et trouvez le *fichier Command.cs.* Dans `Execute` la méthode, `message` changer `string.Format(..)` `Hello World!`la chaîne de .

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

Assurez-vous d’enregistrer vos modifications à chaque fichier.

## <a name="run-it"></a>Exécutez le script

Vous pouvez maintenant exécuter le code source dans l’instance expérimentale Visual Studio.

Étape 1. Appuyez sur **F5** pour exécuter la commande **Start Debugging.** Cette commande construit votre projet et démarre le débbugger, le lancement d’une nouvelle instance de Visual Studio appelé **l’instance expérimentale**.

::: moniker range="vs-2017"

Vous verrez les mots **Experimental Instance** dans la barre de titre Visual Studio.

![barre de titre d’instance expérimentale](media/hello-world-exp-instance.png)

::: moniker-end

Étape 2. Sur le menu **Tools** de l’instance **expérimentale**, cliquez sur **Say Hello World!**.

![résultat final](media/hello-world-final-result.png)

Vous devriez voir la sortie de votre nouvelle commande personnalisée, dans ce cas le dialogue au centre de l’écran qui vous donne le **monde Bonjour!** .

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les bases de travailler avec Visual Studio Extensibility, voici où vous pouvez en apprendre davantage :

* [Commencez à développer des extensions Visual Studio](starting-to-develop-visual-studio-extensions.md) - Échantillons, tutoriels. et la publication de votre extension
* [Nouveautés dans le Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) - Nouvelles fonctionnalités d’extensibility dans Visual Studio 2017
* [Nouveautés dans le Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) - Nouvelles fonctionnalités d’extensibility dans Visual Studio 2019
* [Inside the Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) - Apprenez les détails de Visual Studio Extensibility
