---
title: Écrire un visualiseur en C# | Microsoft Docs
description: Suivez une procédure pas à pas pour créer un visualiseur simple en C#. Il montre les étapes requises avec et sans utiliser le modèle d’élément de visualiseur.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 86123ece79f7bbde4f4f91fac657dcc235056c0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384991"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procédure pas à pas : écriture d’un visualiseur en C\#

Cette procédure pas à pas explique comment écrire un visualiseur simple à l’aide de C#. Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d’une chaîne à l’aide d’un message Windows Forms. Ce visualiseur de chaîne simple n’est pas particulièrement utile dans lui-même, mais il montre les étapes de base que vous devez suivre pour créer des visualiseurs plus utiles pour d’autres types de données.

> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, accédez au menu **Outils** , puis choisissez **importation et exportation de paramètres**. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Le code du visualiseur doit être placé dans une DLL, qui sera lue par le débogueur. Par conséquent, la première étape consiste à créer un projet de bibliothèque de classes pour la DLL.

## <a name="create-a-visualizer-manually"></a>Créer un visualiseur manuellement

Suivez les étapes ci-dessous pour créer un visualiseur.

### <a name="to-create-a-class-library-project"></a>Pour créer un projet de bibliothèque de classes

1. Créez un projet de bibliothèque de classes.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **bibliothèque de classes**, choisissez **modèles**, puis **créer une bibliothèque de classes (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , sous **Visual C#**, choisissez **.NET Framework**, puis dans le volet central, choisissez **bibliothèque de classes (.NET Framework)**.
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyFirstVisualizer` , puis cliquez sur **créer** ou **OK**.

   Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Toutefois, avant d’ajouter la référence, vous devez renommer certaines classes afin qu’elles aient des noms explicites.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Pour renommer Class1. cs et ajouter Microsoft. VisualStudio. DebuggerVisualizers

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur Class1. cs et choisissez **Renommer** dans le menu contextuel.

2. Remplacez le nom classe1. cs par un nom explicite, tel que DebuggerSide. cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans DebuggerSide. cs pour qu’elle corresponde au nouveau nom de fichier.

3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références** , puis choisissez **Ajouter une référence** dans le menu contextuel.

4. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **Parcourir** et recherchez le Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Vous pouvez trouver la DLL dans le sous-répertoire *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* du répertoire d’installation de Visual Studio.

5. Cliquez sur **OK**.

6. Dans DebuggerSide. cs, ajoutez les éléments suivants aux `using` directives :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Vous êtes désormais prêt à créer le code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Tout d’abord, vous devez modifier la déclaration de l' `DebuggerSide` objet afin que hérite de la classe de base `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer

1. Dans DebuggerSide. cs, accédez à la ligne de code suivante :

   ```csharp
   public class DebuggerSide
   ```

2. Remplacez le code par :

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` a une méthode abstraite, `Show`, que vous devez substituer.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show

- Dans `public class DebuggerSide` , ajoutez la **méthode suivante :**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l’aide d’un message Windows Forms. Tout d’abord, vous devez ajouter une référence et une `using` directive pour System. Windows. Forms.

### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références** , puis choisissez **Ajouter une référence** dans le menu contextuel.

2. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **parcourir**, puis recherchez le System.Windows.Forms.DLL.

    Vous pouvez trouver la DLL dans *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Cliquez sur **OK**.

4. Dans DebuggerSide. cs, ajoutez les éléments suivants aux `using` directives :

   ```csharp
   using System.Windows.Forms;
   ```

   Vous ajoutez maintenant du code pour créer et afficher l’interface utilisateur du visualiseur. Comme il s’agit de votre premier visualiseur, nous conservons l’interface utilisateur simple et utilisons une boîte de message.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue

1. Dans la méthode `Show`, ajoutez la ligne de code suivante :

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d’application.

2. Dans le menu **générer** , choisissez **générer MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   C’est la fin du code côté débogueur. Il existe toutefois une étape supplémentaire : ajouter l’attribut qui indique côté élément débogué la collection de classes qui compose le visualiseur.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Pour ajouter le type à visualiser pour le code côté débogué

Dans le code côté débogueur, vous spécifiez le type à visualiser (la source de l’objet) pour le programme débogué à l’aide de l' <xref:System.Diagnostics.DebuggerVisualizerAttribute> attribut. La `Target` propriété définit le type à visualiser.

1. Ajoutez le code d’attribut suivant à DebuggerSide. cs, après les `using` directives mais avant `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Dans le menu **générer** , choisissez **générer MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   À ce stade, votre premier visualiseur est terminé. Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement. À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Pour ajouter une méthode de test permettant d’afficher le visualiseur

1. Ajoutez la méthode suivante à la classe `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Dans le menu **générer** , choisissez **générer MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, nous utiliserons un projet d’application console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis cliquez sur **nouveau projet**.

    ::: moniker range=">=vs-2019"
    Dans la zone de recherche, tapez **application console**, choisissez **modèles**, puis choisissez **créer une application console (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual C#**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)**.
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyTestConsole` , puis cliquez sur **créer** ou **OK**.

   Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole** et choisissez **Ajouter une référence** dans le menu contextuel.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **Parcourir** , puis sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Cliquez sur **OK**.

4. Cliquez avec le bouton droit sur **MyTestConsole** , puis cliquez à nouveau sur **Ajouter une référence** .

5. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **projets** , puis cliquez sur MyFirstVisualizer.

6. Cliquez sur **OK**.

   Puis, vous ajoutez le code pour terminer l'atelier de test.

### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur Program. cs et choisissez **Renommer** dans le menu contextuel.

2. Modifiez le nom du programme. cs pour qu’il soit plus explicite, par exemple TestConsole. cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans TestConsole. cs pour qu’elle corresponde au nouveau nom de fichier.

3. Dans TestConsole. cs, ajoutez le code suivant aux `using` directives :

   ```csharp
   using MyFirstVisualizer;
   ```

4. Dans la méthode `Main`, ajoutez le code suivant :

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Vous êtes désormais prêt à tester votre premier visualiseur.

### <a name="to-test-the-visualizer"></a>Pour tester le visualiseur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole** et choisissez **définir comme projet de démarrage** dans le menu contextuel.

2. Dans le menu **Déboguer**, choisissez **Démarrer**.

    L’application console démarre et le visualiseur apparaît et affiche la chaîne « Hello, World ».

   Félicitations ! Vous venez de générer et de tester votre premier visualiseur.

   Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Créer un visualiseur à l’aide du modèle d’élément de visualiseur

Jusqu’à présent, cette procédure pas à pas vous a montré comment créer un visualiseur manuellement. Cela a été fait comme un exercice d’apprentissage. Maintenant que vous savez comment fonctionne un visualiseur simple, il existe un moyen plus simple d’en créer un : à l’aide du modèle d’élément de visualiseur.

Tout d’abord, vous devez créer un projet de bibliothèque de classes.

### <a name="to-create-a-new-class-library"></a>Pour créer une bibliothèque de classes

1. Dans le menu **fichier** , choisissez **nouveau > projet**.

2. Dans la boîte de dialogue **nouveau projet** , sous **Visual C#**, sélectionnez **.NET Framework**.

3. Dans le volet central, choisissez **bibliothèque de classes**.

4. Dans la zone **nom** , tapez un nom approprié pour la bibliothèque de classes, par exemple MySecondVisualizer.

5. Cliquez sur **OK**.

   Vous pouvez maintenant y ajouter un élément de visualiseur :

### <a name="to-add-a-visualizer-item"></a>Pour ajouter un élément de visualiseur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur MySecondVisualizer.

2. Dans le menu contextuel, choisissez **Ajouter** , puis cliquez sur **nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , sous **éléments Visual C#**, sélectionnez **visualiseur du débogueur**.

4. Dans la zone **nom** , tapez un nom approprié, tel que SecondVisualizer. cs.

5. Cliquez sur **Add**.

   C’est tout. Examinez le fichier SecondVisualizer. cs et affichez le code que le modèle a ajouté pour vous. Poursuivez et expérimentez le code. Maintenant que vous connaissez les principes de base, vous avez la possibilité de créer vos propres visualiseurs plus complexes et utiles.
::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Architecture du visualiseur](../debugger/visualizer-architecture.md)
- [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
