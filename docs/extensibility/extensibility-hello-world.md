---
title: Hello World | Documents Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c531d8acddfebcd2656d6dca05b95244f54ec01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-your-first-extension-hello-world"></a>Création de votre première Extension : Hello World

Cet exemple Hello World vous guide tout au long de la création de votre première extension pour Visual Studio. Ce didacticiel vous indiquera comment ajouter une nouvelle commande à Visual Studio.

Dans le processus, vous allez apprendre comment :

* **[Créer un projet d’extensibilité](#create-an-extensibility-project)**
* **[Ajouter une commande personnalisée](#add-a-custom-command)**
* **[Modifier le code source](#modify-the-source-code)**
* **[Exécuter](#run-it)**

Pour cet exemple, vous allez utiliser Visual c# pour ajouter qu'un bouton de menu personnalisé nommé « Par exemple Hello World ! » qui ressemble à ceci :

![commande de Hello world](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vérifiez que vous avez installé le **le développement d’extensions Visual Studio** charge de travail qui inclut le modèle VSIX, vous avez besoin et exemple de code.

Remarque : Vous pouvez utiliser n’importe quelle version de Visual Studio (Community, Professional ou Enterprise) pour créer un projet d’extensibilité de Visual Studio.

## <a name="create-an-extensibility-project"></a>Créer un projet d’extensibilité

Étape 1. À partir de la **fichier** menu, cliquez sur **nouveau projet**. Au bas de l’écran, vous pouvez entrer le nom de votre projet.

Étape 2. À partir de la **modèles** menu, cliquez sur **Visual C#**, cliquez sur **extensibilité**, puis cliquez sur **projet VSIX**.

![nouveau projet](media/hello-world-new-project.png)

Vous devez maintenant voir la page mise en route et quelques exemples de ressources.

Si vous devez laisser ce didacticiel et revenir à ce dernier, vous pouvez trouver votre nouveau projet HelloWorld sur le **Page de démarrage** dans les **récents** section.

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée

Étape 1. Si vous sélectionnez le manifeste, vous pouvez voir quelles options sont modifiables, pour l’instance de métadonnées, de désignation et de version.

Étape 2. Cliquez sur le projet (pas la solution). Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **contrôle utilisateur**.

Étape 3. Revenez à la **extensibilité** section, puis cliquez sur **commande personnalisée**.

Étape 4. Dans le **nom** champ en bas, attribuez-lui un nom, par exemple Command.cs.

![commande personnalisée](media/hello-world-custom-command.png)

Votre nouvelle commande est répertorié dans le **l’Explorateur de solutions** sous le **ressources** branche. Il s’agit également où vous trouverez les autres fichiers associés à votre commande, tels que les fichiers PNG et ICO si vous souhaitez modifier l’image.

## <a name="modify-the-source-code"></a>Modifier le code source

À ce stade, le bouton que vous ajoutez est relativement générique. Vous devrez modifier le fichier VSCT et le fichier CS, si vous souhaitez apporter des modifications.

* Le fichier VSCT est où vous pouvez renommer vos commandes, ainsi que définir où elles sont placées dans le système de commande de Visual Studio. Pendant que vous explorez le fichier VSCT, vous pouvez remarquer un grand nombre des commentaires de code qui explique le contenu de chaque section des contrôles de code.

* Le fichier CS est où vous pouvez définir des actions, telles que l’événements Click.

Étape 1. Dans **l’Explorateur de solutions**, recherchez le fichier VSCT pour votre nouvelle commande. Dans ce cas, elle sera appelée CommandPackage.vsct.

![commande package vsct](media/hello-world-command-package-vsct.png)

Étape 2. Modifier la `ButtonText` paramètre « Dire Hello World ! »

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

Étape 3. Revenez à **l’Explorateur de solutions** et recherchez le fichier Command.cs. Modifier la chaîne de `message` pour la commande `string.Format(..)` à « Hello World ! »

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

## <a name="run-it"></a>Exécuter

Vous pouvez maintenant exécuter le code source dans l’Instance expérimentale de Visual Studio.

Étape 1. Cliquez sur **Démarrer** dans la barre d’outils. Cela génère votre projet et démarrer le débogueur, lancer une nouvelle instance de Visual Studio appelé le **Instance expérimentale**.

Vous verrez les mots « Instance expérimentale » dans la barre de titre de Visual Studio.

![barre de titre d’instance expérimentale](media/hello-world-exp-instance.png)

Étape 2. Sur le **outils** menu de la **Instance expérimentale**, cliquez sur **Say Hello World !**.

![résultat final](media/hello-world-final-result.png)

Vous devez voir la sortie à partir de votre nouvelle commande personnalisée, dans ce cas la boîte de dialogue dans le centre de l’écran qui vous donne « Hello World ! » « Operation Not Found! ».

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez les principes fondamentaux de l’utilisation de l’extensibilité de Visual Studio, voici où vous pouvez en savoir plus :

* [Commencer à développer des Extensions Visual Studio](starting-to-develop-visual-studio-extensions.md) -exemples, didacticiels. et publication de votre extension.
* [Nouveautés dans le Kit de développement logiciel Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -nouvelles fonctionnalités d’extensibilité dans Visual Studio 2017
* [À l’intérieur de Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -en savoir plus les détails de l’extensibilité de Visual Studio