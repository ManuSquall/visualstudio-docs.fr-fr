---
title: "Procédure pas à pas : Écriture d’un visualiseur en c# | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6e161b3c914d0a87a720f1217b52a571b85f5ff9
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procédure pas à pas : écriture d'un visualiseur en C# #
Cette procédure pas à pas montre comment écrire un visualiseur simple à l’aide de c#. Le visualiseur que vous allez créer dans cette procédure pas à pas affiche le contenu d’une chaîne à l’aide d’une boîte de message Windows forms. Ce visualiseur de chaîne simple n’est pas particulièrement utile en soi, mais il illustre les étapes de base que vous devez suivre pour créer des visualiseurs plus utiles pour d’autres types de données.  
  
> [!NOTE]
>  Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, accédez à la **outils** menu et choisissez **importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Le code du visualiseur doit être placé dans une DLL, qui sera lue par le débogueur. Par conséquent, la première étape consiste à créer un projet de bibliothèque de classes pour la DLL.  

## <a name="create-a-visualizer-manually"></a>Créer manuellement un visualiseur

Effectuez les tâches suivantes pour créer un visualiseur.
  
#### <a name="to-create-a-class-library-project"></a>Pour créer un projet Bibliothèque de classes  
  
1.  Sur le **fichier** menu, choisissez **Nouveau > projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **Visual C#**, sélectionnez **.NET Standard**.  
  
3.  Dans le volet central, sélectionnez **bibliothèque de classes**.  
  
4.  Dans le **nom** , tapez un nom approprié pour la bibliothèque de classes, par exemple MyFirstVisualizer.  
  
5.  Cliquez sur **OK**.  
  
 Après avoir créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin que vous puissiez utiliser les classes définies il. Avant d’ajouter la référence, toutefois, vous devez renommer certaines classes afin qu’ils aient des noms explicites.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Le nom Class1.cs et ajouter Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit Class1.cs et choisissez **renommer** dans le menu contextuel.  
  
2.  Modifiez le nom Class1.cs par un nom significatif, tel que DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]modifie automatiquement la déclaration de classe par DebuggerSide.cs, le nouveau nom de fichier.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit **références** et choisissez **ajouter une référence** dans le menu contextuel.  
  
4.  Dans le **ajouter une référence** boîte de dialogue le **.NET** onglet, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :  
  
    ```csharp  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 Vous êtes maintenant prêt à créer du code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Vous devez tout d’abord, modifiez la déclaration de la `DebuggerSide` objet qui hérite de la classe de base `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer  
  
1.  Dans DebuggerSide.cs, accédez à la ligne de code suivante :  
  
    ```csharp  
    public class DebuggerSide  
    ```  
  
2.  Modifiez le code pour :  
  
    ```csharp  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`a une méthode abstraite (`Show`) que vous devez substituer.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show  
  
-   Dans `public class DebuggerSide`, ajoutez le code suivant **méthode :**  
  
    ```csharp  
    protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 Le `Show` méthode contient le code qui crée la boîte de dialogue visualiseur ou une autre interface utilisateur et affiche les informations passées à partir du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Dans cette procédure pas à pas, vous effectuerez les opérations à l’aide d’une boîte de message Windows forms. Tout d’abord, vous devez ajouter une référence et `using` instruction pour System.Windows.Forms.  
  
#### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **références** et choisissez **ajouter une référence** dans le menu contextuel.  
  
2.  Dans le **ajouter une référence** boîte de dialogue le **.NET** onglet, cliquez sur System.Windows.Forms.DLL.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
 Maintenant, vous allez ajouter du code pour créer et afficher l’interface utilisateur de votre visualiseur. Comme il s’agit de votre premier visualiseur, nous conserve l’interface utilisateur simple et utiliser une boîte de Message.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue  
  
1.  Dans la méthode `Show`, ajoutez la ligne de code suivante :  
  
    ```csharp  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d’application.  
  
2.  Sur le **générer** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
 C’est la fin du code côté débogueur. Il existe une étape supplémentaire l’attribut qui indique côté programme débogué la collection de classes qui compose le visualiseur.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Pour ajouter le code côté programme débogué  
  
1.  Ajoutez le code d’attribut suivant à DebuggerSide.cs, après le `using` instructions mais avant que `namespace MyFirstVisualizer`:  
  
    ```csharp  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target = typeof(System.String),  
    Description = "My First Visualizer")]  
    ```  
  
2.  Sur le **générer** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
 À ce stade, votre premier visualiseur est terminé. Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement. À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Pour ajouter une méthode de Test pour afficher le visualiseur  
  
1.  Ajoutez la méthode suivante à la classe `public DebuggerSide`:  
  
    ```csharp  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Sur le **générer** menu, choisissez **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
 Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, nous allons utiliser un projet d’Application Console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution  
  
1.  Sur le **fichier** menu, choisissez **ajouter** puis cliquez sur **nouveau projet**.  
  
2.  Dans le **ajouter un nouveau projet** boîte de dialogue le **modèles** , choisissez **Application Console**.  
  
3.  Dans le **nom** , tapez un nom explicite pour l’application console, tel que `MyTestConsole`.  
  
4.  Cliquez sur **OK**.  
  
 Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole** et choisissez **ajouter une référence** dans le menu contextuel.  
  
2.  Dans le **ajouter une référence** boîte de dialogue, **.NET** onglet, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Cliquez sur **OK**.  
  
4.  Avec le bouton droit **MyTestConsole** et choisissez **ajouter une référence** à nouveau.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet, puis sur MyFirstVisualizer.  
  
6.  Cliquez sur **OK**.  
  
 Puis, vous ajoutez le code pour terminer l'atelier de test.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole  
  
1.  Dans **l’Explorateur de solutions**, Program.cs d’avec le bouton droit et choisissez **renommer** dans le menu contextuel.  
  
2.  Modifier le nom de Program.cs un nom plus significatif, tel que TestConsole.cs.  
  
     **Remarque** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans TestConsole.cs pour le nouveau nom de fichier.  
  
3.  Dans TestConsole.cs, ajoutez le code suivant à la `using` instructions :  
  
    ```csharp  
    using MyFirstVisualizer;  
    ```  
  
4.  Dans la méthode `Main`, ajoutez le code suivant :  
  
    ```csharp  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 Maintenant, vous êtes prêt à tester votre premier visualiseur.  
  
#### <a name="to-test-the-visualizer"></a>Pour tester le visualiseur  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole** et choisissez **définir comme projet de démarrage** dans le menu contextuel.  
  
2.  Sur le **déboguer** menu, choisissez **Démarrer**.  
  
     L’application console démarre et le visualiseur apparaît et affiche la chaîne « Hello, World ».  
  
 Félicitations ! Vous venez de générer et de tester votre premier visualiseur.  
  
 Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Créez un visualiseur en utilisant le modèle d’élément de visualiseur  
 Jusqu'à présent, cette procédure pas à pas vous a montré comment créer manuellement un visualiseur. Ces actions étaient exécutées comme un exercice d’apprentissage. Maintenant que vous connaissez le fonctionne d’un visualiseur simple, il existe un moyen plus simple pour en créer un : à l’aide du modèle d’élément visualiseur.  
  
 Tout d’abord, vous devez créer un nouveau projet de bibliothèque de classes.  
  
#### <a name="to-create-a-new-class-library"></a>Pour créer une nouvelle bibliothèque de classes  
  
1.  Sur le **fichier** menu, choisissez **Nouveau > projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **Visual C#**, sélectionnez **.NET Standard**.  
  
3.  Dans le volet central, sélectionnez **bibliothèque de classes**.   
  
4.  Dans le **nom** , tapez un nom approprié pour la bibliothèque de classes, telles que MySecondVisualizer.  
  
5.  Cliquez sur **OK**.  
  
 Maintenant, vous pouvez ajouter un élément de visualiseur à celui-ci :  
  
#### <a name="to-add-a-visualizer-item"></a>Pour ajouter un élément de visualiseur  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit MySecondVisualizer.  
  
2.  Dans le menu contextuel, choisissez **ajouter** puis cliquez sur **un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue **éléments Visual c#**, sélectionnez **visualiseur du débogueur**.  
  
4.  Dans le **nom** , tapez un nom approprié, tel que SecondVisualizer.cs.  
  
5.  Cliquez sur **Ajouter**.  
  
 Qui est tout à ce dernier. Examinez le fichier SecondVisualizer.cs et afficher le code que le modèle est ajouté à votre place. Continuez et faire des essais avec le code. Maintenant que vous connaissez les principes de base, vous êtes prêt à créer des visualiseurs plus complexes et utiles de votre choix.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture du visualiseur](../debugger/visualizer-architecture.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
