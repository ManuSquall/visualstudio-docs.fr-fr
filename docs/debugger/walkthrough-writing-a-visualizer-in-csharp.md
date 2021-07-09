---
title: Écrire un visualiseur en C# | Microsoft Docs
description: Suivez une procédure pas à pas pour créer un visualiseur simple en C#. Il montre les étapes requises avec et sans utiliser le modèle d’élément de visualiseur.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
ms.openlocfilehash: a6ce1a6d9f2f8a36d892d484cf9353e1312758b4
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549509"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procédure pas à pas : écriture d’un visualiseur en C\#

Cette procédure pas à pas explique comment écrire un visualiseur simple à l’aide de C#. le visualiseur que vous allez créer dans cette procédure pas à pas affiche le contenu d’une chaîne à l’aide d’un formulaire de Windows. Ce visualiseur de chaîne simple n’est pas particulièrement utile dans lui-même, mais il montre les étapes de base que vous devez suivre pour créer des visualiseurs plus utiles pour d’autres types de données.

> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. pour modifier vos paramètres, accédez au menu **outils** , puis choisissez **importer et exporter des Paramètres**. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Le code du visualiseur doit être placé dans une DLL, qui sera lue par le débogueur. Par conséquent, la première étape consiste à créer un projet de bibliothèque de classes pour la DLL.

## <a name="create-a-visualizer-manually"></a>Créer un visualiseur manuellement

Suivez les étapes ci-dessous pour créer un visualiseur.

### <a name="to-create-a-class-library-project"></a>Pour créer un projet de bibliothèque de classes

* Créez un projet de bibliothèque de classes.

    ::: moniker range=">=vs-2019"
    choisissez **fichier**  >  **nouveau**  >  **Project**. Dans la liste déroulante langue, choisissez **C#**. Dans la zone de recherche, tapez **bibliothèque de classes**, puis choisissez **bibliothèque de classes (.NET Framework)**. Cliquez sur **Suivant**. Dans la boîte de dialogue qui s’affiche, tapez le nom `MyFirstVisualizer` , puis cliquez sur **créer**.

    pour le projet du visualiseur, veillez à sélectionner une bibliothèque de classes .NET Framework et non .net. bien que le visualiseur doive être .NET Framework, l’application appelante peut être .net Core.
    ::: moniker-end
    ::: moniker range="vs-2017"
    dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **Project**. dans le volet gauche de la boîte de dialogue **nouveau projet** , sous **Visual C#**, choisissez **.NET Framework**, puis dans le volet central, choisissez **bibliothèque de classes (.NET Framework)**.

    Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyFirstVisualizer` , puis cliquez sur **créer** ou **OK**.
    ::: moniker-end

   Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Toutefois, avant d’ajouter la référence, vous devez renommer certaines classes afin qu’elles aient des noms explicites.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Pour renommer Class1. cs et ajouter Microsoft. VisualStudio. DebuggerVisualizers

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur Class1. cs et choisissez **Renommer** dans le menu contextuel.

2. Remplacez le nom classe1. cs par un nom explicite, tel que DebuggerSide. cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans DebuggerSide. cs pour qu’elle corresponde au nouveau nom de fichier.

3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références** , puis choisissez **Ajouter une référence** dans le menu contextuel.

4. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **Parcourir** et recherchez le Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    vous pouvez trouver la DLL dans le sous-répertoire *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* du répertoire d’installation de Visual Studio.

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

  La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l'aide d'un message Windows Forms. Tout d’abord, vous devez ajouter une référence et une `using` directive pour System. Windows. Forms.

### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références** , puis choisissez **Ajouter une référence** dans le menu contextuel.

2. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **parcourir**, puis recherchez le System.Windows.Forms.DLL.

    vous pouvez trouver la DLL dans *C:\ Windows \Microsoft.NET\Framework\v4.0.30319*.

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

   Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Pour plus de simplicité, utilisez un projet d’application console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis cliquez sur **nouveau Project**.

    ::: moniker range=">=vs-2019"

    choisissez **fichier**  >  **nouveau**  >  **Project**. Dans la liste déroulante langue, choisissez **C#**. dans la zone de recherche, tapez **console app**, puis choisissez application **console (.NET Framework)** ou **Application console** pour .net. Cliquez sur **Suivant**. Dans la boîte de dialogue qui s’affiche, tapez le nom `MyTestConsole` , puis cliquez sur **créer**.

    > [!NOTE]
    > si vous souhaitez tester facilement le visualiseur à l’aide d’un atelier de test, créez une application console .NET Framework. Vous pouvez créer une application console .NET à la place, mais l’atelier de test décrit ultérieurement n’est pas encore pris en charge pour .NET. vous devrez donc installer le visualiseur pour le tester. Pour une application console .NET, commencez par créer l’application console ici, ajoutez la DLL requise et les références de projet, puis suivez les étapes décrites dans [Ajouter un objet de données côté débogué](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **Project**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual C#**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)**.

    Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyTestConsole` , puis cliquez sur **OK**.
    ::: moniker-end

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

1. dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole** et choisissez **définir comme Project de démarrage** dans le menu contextuel.

2. Dans le menu **Déboguer**, choisissez **Démarrer**.

    L’application console démarre et le visualiseur apparaît et affiche la chaîne « Hello, World ».

   Félicitations ! Vous venez de créer et de tester votre premier visualiseur !

   Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Ajouter un objet de données côté débogué

Dans cette section, vous passez de l' `System.String` objet de données à un objet de données personnalisé.  

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis cliquez sur **nouveau Project**. Dans la liste déroulante langue, choisissez **C#**. dans la zone de recherche, tapez **bibliothèque** de classes, puis sélectionnez **bibliothèque de classes (.NET Framework)** ou **bibliothèque de classes** pour .NET Standard.

   >[!NOTE]
   >si vous utilisez une application de console de test .NET Framework, veillez à créer un projet de bibliothèque de classes .NET Framework.

1. Cliquez sur **Suivant**. Dans la boîte de dialogue qui s’affiche, tapez le nom `MyDataObject` , puis cliquez sur **créer**.

1. (.NET Standard bibliothèque de classes uniquement) dans Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis choisissez **modifier le fichier Project**. Remplacez la `<TargetFramework>` valeur par `netstandard2.0` .

   ```xml
   <TargetFramework>netstandard2.0</TargetFramework>
   ```

1. À l’intérieur de l' `MyDataObject` espace de noms, remplacez le code par défaut par le code suivant.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   Pour un visualiseur en lecture seule, comme dans cet exemple, il n’est pas nécessaire d’implémenter les méthodes de [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   Ensuite, mettez à jour le projet MyFirstVisualizer pour utiliser le nouvel objet de données.

1. Dans Explorateur de solutions sous le projet MyFirstVisualizer, cliquez avec le bouton droit sur le nœud **références** , puis choisissez **Ajouter une référence**.

1. Sous **projets**, sélectionnez le projet **myDataObject** .

1. Dans le code d’attribut de DebuggerSide. cs, mettez à jour la valeur cible, `System.String` en remplaçant par `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. Dans le projet MyFirstVisualizer, remplacez le code de la `Show` méthode par le code suivant.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Le code précédent utilise une propriété de l’objet de données à afficher dans le titre du formulaire.

   Ensuite, mettez à jour l’application console pour utiliser l’objet de données personnalisé.

1. Dans Explorateur de solutions sous le projet MyTestConsole, cliquez avec le bouton droit sur le nœud **références** ou **dépendances** , puis ajoutez une référence de projet à `MyDataObject` .

1. Dans Program. cs, remplacez le code dans la `Main` méthode par le code suivant.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (Application console .NET) Placez l’appel à `TestShowVisualizer` dans une instruction try-catch, car l’atelier de test n’est pas pris en charge.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   L’application console a besoin d’une référence d’exécution au visualiseur. Vous pouvez conserver la référence en conservant le code précédent au lieu de le commenter.

1. pour une application console .NET Framework, vous pouvez exécuter l’atelier de test (appuyez sur **F5**) ou suivre les instructions de la rubrique [comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

   si vous exécutez l’application à l’aide de l’atelier de test, l’application affiche le formulaire Windows.

1. Pour une application console .NET, copiez `MyFirstVisualizer.dll` et `MyDataObject.dll` dans les dossiers décrits dans Guide pratique [pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

1. Après avoir installé le visualiseur, définissez un point d’arrêt, exécutez l’application console, puis pointez sur `customDataObject` . Si tout est correctement configuré, vous devriez voir l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Icône de loupe du visualiseur.":::

   Quand vous choisissez **MyFirstVisualizer** dans la loupe, vous voyez le formulaire avec le texte de l’objet de données dans le titre.

   ![visualiseur présentant un formulaire de Windows](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Créer un visualiseur à l’aide du modèle d’élément de visualiseur

Jusqu’à présent, cette procédure pas à pas vous a montré comment créer un visualiseur manuellement. Cela a été fait comme un exercice d’apprentissage. Maintenant que vous savez comment fonctionne un visualiseur simple, il existe un moyen plus simple d’en créer un : à l’aide du modèle d’élément de visualiseur.

Tout d’abord, vous devez créer un projet de bibliothèque de classes.

### <a name="to-create-a-new-class-library"></a>Pour créer une bibliothèque de classes

1. Dans le menu **fichier** , choisissez **nouveau > Project**.

2. dans la boîte de dialogue **nouveau Project** , sous **Visual C#**, sélectionnez **.NET Framework**.

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
