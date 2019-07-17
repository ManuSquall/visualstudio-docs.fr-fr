---
title: Écrire un visualiseur en C# | Microsoft Docs
ms.custom: seodec18
ms.date: 04/12/2019
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4e99e0d3e8f212b2fdab52188b8c765610d9ac2f
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890926"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procédure pas à pas : Écriture d’un visualiseur en C\#
Cette procédure pas à pas explique comment écrire un visualiseur simple à l’aide de C#. Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d’une chaîne à l’aide d’un message Windows Forms. Ce visualiseur de chaîne simple n’est pas particulièrement utile en soi, mais il montre les étapes de base que vous devez suivre pour créer des visualiseurs plus utiles pour les autres types de données.

> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, accédez à la **outils** menu et choisissez **importation et exportation de paramètres**. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Le code du visualiseur doit être placé dans une DLL, qui sera lue par le débogueur. Par conséquent, la première étape consiste à créer un projet de bibliothèque de classes pour la DLL.

## <a name="create-a-visualizer-manually"></a>Créer manuellement un visualiseur

Effectuez les tâches suivantes pour créer un visualiseur.

### <a name="to-create-a-class-library-project"></a>Pour créer un projet Bibliothèque de classes

1. Créez un projet de bibliothèque de classes.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Type **Ctrl + Q** pour ouvrir la zone de recherche, tapez **bibliothèque de classes**, choisissez **modèles**, puis choisissez **créer une nouvelle bibliothèque de classes (.NET Standard)** . Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la **nouveau projet** boîte de dialogue **Visual C#** , choisissez **.NET Standard**, puis, dans le volet central, choisissez **bibliothèque de classes (. NET Standard)** .
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, telles que `MyFirstVisualizer`, puis cliquez sur **créer** ou **OK**.

   Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Avant d’ajouter la référence, toutefois, vous devez renommer certaines classes afin qu’ils aient des noms explicites.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Remplacez le nom Class1.cs et ajouter Microsoft.VisualStudio.DebuggerVisualizers

1. Dans **l’Explorateur de solutions**, cliquez sur Class1.cs et choisissez **renommer** dans le menu contextuel.

2. Modifiez le nom Class1.cs par un nom significatif, tel que DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe par DebuggerSide.cs, le nouveau nom de fichier.

3. Dans **l’Explorateur de solutions**, avec le bouton droit **références** et choisissez **ajouter une référence** dans le menu contextuel.

4. Dans le **ajouter une référence** boîte de dialogue le **Parcourir** onglet, sélectionnez **Parcourir** et recherchez le Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Vous pouvez trouver la DLL dans  *\<répertoire d’installation Visual Studio > \Common7\IDE\PublicAssemblies* sous-répertoire du répertoire d’installation de Visual Studio.

5. Cliquez sur **OK**.

6. Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Vous êtes désormais prêt à créer le code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Tout d’abord, vous devez modifier la déclaration de la `DebuggerSide` afin qui hérite de la classe de base de l’objet `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer

1. Dans DebuggerSide.cs, accédez à la ligne de code suivante :

   ```csharp
   public class DebuggerSide
   ```

2. Modifiez le code pour :

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` a une méthode abstraite, `Show`, que vous devez substituer.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show

- Dans `public class DebuggerSide`, ajoutez la méthode **suivante :**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l’aide d’un message Windows Forms. Tout d’abord, vous devez ajouter une référence et `using` instruction pour System.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms

1. Dans **l’Explorateur de solutions**, avec le bouton droit **références** et choisissez **ajouter une référence** dans le menu contextuel.

2. Dans le **ajouter une référence** boîte de dialogue le **Parcourir** onglet, sélectionnez **Parcourir**et recherchez le System.Windows.Forms.DLL.

    Vous pouvez trouver la DLL dans *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Cliquez sur **OK**.

4. Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :

   ```csharp
   using System.Windows.Forms;
   ```

   Vous ajoutez maintenant du code pour créer et afficher l’interface utilisateur du visualiseur. Comme il s’agit de votre premier visualiseur, nous simplifierez l’interface utilisateur simple et utiliser une boîte de Message.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue

1. Dans la méthode `Show`, ajoutez la ligne de code suivante :

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d’application.

2. Sur le **Build** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   C’est la fin du code côté débogueur. Il existe toutefois une étape supplémentaire : ajouter l’attribut qui indique côté élément débogué la collection de classes qui compose le visualiseur.

### <a name="to-add-the-debuggee-side-code"></a>Pour ajouter le code côté programme débogué

1. Ajoutez le code d’attribut suivant à DebuggerSide.cs, après le `using` instructions mais avant que `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Sur le **Build** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

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

2. Sur le **Build** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, nous allons utiliser un projet d’Application de Console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution

1. Dans l’Explorateur de solutions, cliquez sur la solution, choisissez **ajouter**, puis cliquez sur **nouveau projet**.

    ::: moniker range=">=vs-2019"
    Dans la zone de recherche, tapez **application console**, choisissez **modèles**, puis choisissez **créer une application Console (.NET Framework)** . Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual C#** , choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)** .
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, telles que `MyTestConsole`, puis cliquez sur **créer** ou **OK**.

   Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole

1. Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole** et choisissez **ajouter une référence** dans le menu contextuel.

2. Dans le **ajouter une référence** boîte de dialogue, **Parcourir** onglet, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Cliquez sur **OK**.

4. Avec le bouton droit **MyTestConsole** et choisissez **ajouter une référence** à nouveau.

5. Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet, puis sur MyFirstVisualizer.

6. Cliquez sur **OK**.

   Puis, vous ajoutez le code pour terminer l'atelier de test.

### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole

1. Dans **l’Explorateur de solutions**, cliquez sur Program.cs et choisissez **renommer** dans le menu contextuel.

2. Modifier le nom de Program.cs en un nom plus significatif, tel que TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans TestConsole.cs pour correspondre au nouveau nom de fichier.

3. Dans TestConsole.cs, ajoutez le code suivant à la `using` instructions :

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

1. Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole** et choisissez **définir comme projet de démarrage** dans le menu contextuel.

2. Dans le menu **Déboguer**, choisissez **Démarrer**.

    Démarrage de l’application de console et le visualiseur apparaît et affiche la chaîne « Hello, World ».

   Félicitations ! Vous venez de générer et de tester votre premier visualiseur.

   Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Guide pratique pour Installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Créer un visualiseur en utilisant le modèle d’élément visualiseur

Jusqu'à présent, cette procédure pas à pas vous a montré comment créer manuellement un visualiseur. Ces actions étaient exécutées comme un exercice d’apprentissage. Maintenant que vous connaissez le fonctionne d’un visualiseur simple, il est un moyen plus simple pour créer un : à l’aide du modèle d’élément visualiseur.

Tout d’abord, vous devez créer un nouveau projet de bibliothèque de classes.

### <a name="to-create-a-new-class-library"></a>Pour créer une nouvelle bibliothèque de classes

1. Dans le menu **Fichier**, choisissez **Nouveau > Projet**.

2. Dans le **nouveau projet** boîte de dialogue **Visual C#** , sélectionnez **.NET Standard**.

3. Dans le volet central, choisissez **bibliothèque de classes**.

4. Dans le **nom** , tapez un nom approprié pour la bibliothèque de classes, telles que MySecondVisualizer.

5. Cliquez sur **OK**.

   Maintenant, vous pouvez ajouter un élément de visualiseur à celui-ci :

### <a name="to-add-a-visualizer-item"></a>Pour ajouter un élément de visualiseur

1. Dans **l’Explorateur de solutions**, avec le bouton droit MySecondVisualizer.

2. Dans le menu contextuel, choisissez **ajouter** puis cliquez sur **un nouvel élément**.

3. Dans le **ajouter un nouvel élément** boîte de dialogue **éléments Visual c#** , sélectionnez **visualiseur du débogueur**.

4. Dans le **nom** , tapez un nom approprié, tel que SecondVisualizer.cs.

5. Cliquez sur **Ajouter**.

   Qui est tout à ce dernier. Examinez le fichier SecondVisualizer.cs et afficher le code qui le modèle ajouté pour vous. Continuons et faire des essais avec le code. Maintenant que vous connaissez les principes de base, vous êtes sur la bonne voie pour créer des visualiseurs plus complexes et utiles de votre choix.

## <a name="see-also"></a>Voir aussi

- [Architecture d’un visualiseur](../debugger/visualizer-architecture.md)
- [Guide pratique : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)