---
title: "Proc&#233;dure pas &#224; pas&#160;: &#233;criture d&#39;un visualiseur en C# | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "visualiseurs, écrire"
  - "procédures pas à pas (Visual Studio), visualiseurs"
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: &#233;criture d&#39;un visualiseur en C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment écrire un visualiseur simple en C\#.  Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d'une chaîne à l'aide d'un message Windows Forms.  Ce visualiseur de chaîne simple n'est pas très utile, mais il affiche les étapes élémentaires à suivre pour créer des visualiseurs plus utiles à d'autres types de données.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, dans le menu **Outils**, cliquez sur **Importation et exportation de paramètres**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Le code du visualiseur doit être placé dans une DLL, laquelle sera lue par le débogueur.  Par conséquent, la première étape consiste à créer un projet Bibliothèque de classes pour la DLL.  
  
#### Pour créer un projet Bibliothèque de classes  
  
1.  Dans le menu **Fichier**, choisissez **Nouveau**, puis sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Type de projet**, sélectionnez **Visual C\#**.  
  
3.  Dans la zone **Modèles**, choisissez **Bibliothèque de classes**.  
  
4.  Dans la zone **Nom**, tapez un nom approprié pour la bibliothèque de classes, par exemple MyFirstVisualizer.  
  
5.  Cliquez sur **OK**.  
  
 Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies.  Toutefois, avant d'ajouter la référence, vous devez renommer certaines classes afin qu'elles aient des noms explicites.  
  
#### Pour renommer Class1.cs et ajouter Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur Class1.cs et sélectionnez **Renommer** dans le menu contextuel.  
  
2.  Remplacez le nom Class1.cs par un nom explicite, par exemple DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] remplace automatiquement le nom de la déclaration de classe par DebuggerSide.cs, le nouveau nom du fichier.  
  
3.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis sélectionnez **Ajouter une référence** dans le menu contextuel.  
  
4.  Dans la boîte de dialogue **Ajouter une référence**, sous l'onglet **.NET**, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 Vous êtes désormais prêt à créer du code côté débogueur.  Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter.  En premier lieu, vous devez modifier la déclaration de l'objet `DebuggerSide` afin qu'il hérite de la classe de base `DialogDebuggerVisualizer`.  
  
#### Pour hériter de DialogDebuggerVisualizer  
  
1.  Dans DebuggerSide.cs, allez à la ligne de code suivante :  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  Modifiez le code en :  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` a une méthode abstraite \(`Show`\) que vous devez substituer.  
  
#### Pour substituer la méthode DialogDebuggerVisualizer.Show  
  
-   Dans `public class DebuggerSide`, ajoutez la **méthode** suivante :  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur \(ou une autre interface utilisateur\) et qui affiche les informations passées du débogueur au visualiseur.  Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations.  Cette procédure pas à pas vous montre comment y parvenir à l'aide d'un message Windows Forms.  Vous devez d'abord ajouter une référence et une instruction `using` pour System.Windows.Forms.  
  
#### Pour ajouter System.Windows.Forms  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis sélectionnez **Ajouter une référence** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, sous l'onglet **.NET**, cliquez sur System.Windows.Forms.DLL.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `using` :  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 Puis, vous ajoutez du code pour créer et afficher l'interface utilisateur du visualiseur.  Comme il s'agit de votre premier visualiseur, nous simplifierons l'interface utilisateur simple et utiliserons un message.  
  
#### Pour afficher la sortie du visualiseur dans une boîte de dialogue  
  
1.  Dans la méthode `Show`, ajoutez la ligne de code suivante :  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Cet exemple de code n'inclut pas la gestion des erreurs.  Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d'application.  
  
2.  Dans le menu **Générer**, cliquez sur **Générer MyFirstVisualizer**.  Le projet doit se générer avec succès.  Corrigez toutes les erreurs de build avant de continuer.  
  
 C'est la fin du code côté débogueur.  Il existe toutefois une étape supplémentaire : ajouter l'attribut qui indique côté programme débogué la collection de classes qui compose le visualiseur.  
  
#### Pour ajouter le code côté débogué  
  
1.  Ajoutez le code d'attribut suivant à DebuggerSide.cs, après les instructions `using`, mais avant `namespace MyFirstVisualizer` :  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  Dans le menu **Générer**, cliquez sur **Générer MyFirstVisualizer**.  Le projet doit se générer avec succès.  Corrigez toutes les erreurs de build avant de continuer.  
  
 À ce stade, votre premier visualiseur est terminé.  Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement.  À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Pour ajouter une méthode de test permettant d'afficher le visualiseur  
  
1.  Ajoutez la méthode suivante à la classe `public DebuggerSide`:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Dans le menu **Générer**, cliquez sur **Générer MyFirstVisualizer**.  Le projet doit se générer avec succès.  Corrigez toutes les erreurs de build avant de continuer.  
  
 Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur.  Pour simplifier, nous utiliserons un projet d'application console.  
  
#### Pour ajouter un projet d'application console à la solution  
  
1.  Dans le menu **Fichier**, cliquez sur **Ajouter**, puis sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouveau projet**, dans le volet **Modèles**, choisissez **Application console**.  
  
3.  Dans la zone **Nom**, tapez un nom significatif pour l'application console, par exemple `MyTestConsole`.  
  
4.  Cliquez sur **OK**.  
  
 Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.  
  
#### Pour ajouter les références nécessaires à MyTestConsole  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis sélectionnez **Ajouter une référence** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, sous l'onglet **.NET**, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Cliquez sur **OK**.  
  
4.  Cliquez avec le bouton droit sur **MyTestConsole** et choisissez à nouveau **Ajouter une référence**.  
  
5.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l'onglet **Projets**, puis sur MyFirstVisualizer.  
  
6.  Cliquez sur **OK**.  
  
 Puis, vous ajoutez le code pour terminer l'atelier de test.  
  
#### Pour ajouter le code à MyTestConsole  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur Program.cs et sélectionnez **Renommer** dans le menu contextuel.  
  
2.  Remplacez le nom Program.cs par un nom plus explicite, par exemple TestConsole.cs.  
  
     **Remarque** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans TestConsole.cs pour qu'elle corresponde au nouveau nom de fichier.  
  
3.  Dans TestConsole.cs, ajoutez le code suivant aux instructions `using` :  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  Dans la méthode `Main`, ajoutez le code suivant :  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 Vous êtes désormais prêt à tester votre premier visualiseur.  
  
#### Pour tester le visualiseur  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.  
  
2.  Dans le menu **Déboguer**, choisissez **Démarrer**.  
  
     L'application console démarre et le visualiseur apparaît et affiche la chaîne "Hello, World".  
  
 Félicitations \!  Vous venez de générer et de tester votre premier visualiseur.  
  
 Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer.  Pour plus d'informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).  
  
## Utilisation du modèle d'élément du visualiseur  
 Jusqu'à présent, cette procédure pas à pas vous a indiqué comment créer manuellement un visualiseur.  Elle a été exécutée comme un exercice d'apprentissage.  Maintenant que vous savez comment fonctionne un visualiseur simple, apprenez à en créer plus facilement à l'aide du modèle d'élément du visualiseur.  
  
 D'abord, vous devez créer un projet Bibliothèque de classes.  
  
#### Pour créer un nouveau projet de bibliothèque de classes  
  
1.  Dans le menu **Fichier**, cliquez sur **Ajouter**, puis sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouveau projet**, sous **Type de projet**, sélectionnez **Visual C\#**.  
  
3.  Dans la zone **Modèles**, choisissez **Bibliothèque de classes**.  
  
4.  Dans la zone **Nom**, tapez un nom approprié pour la bibliothèque de classes, par exemple MySecondVisualizer.  
  
5.  Cliquez sur **OK**.  
  
 Maintenant, vous pouvez lui ajouter un élément de visualiseur :  
  
#### Pour ajouter un élément de visualiseur  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur MySecondVisualizer.  
  
2.  Dans le menu contextuel, sélectionnez **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sous **Modèles**, **Modèles Visual Studio installés**, sélectionnez **Visualiseur du débogueur**.  
  
4.  Dans la zone **Nom**, tapez un nom approprié, par exemple SecondVisualizer.cs.  
  
5.  Cliquez sur **Ajouter**.  
  
 Et c'est tout \!  Consultez le fichier SecondVisualizer.cs et examinez le code que le modèle a ajouté pour vous.  Faites des essais avec le code.  Maintenant que vous connaissez les principes de base, vous allez pouvoir créer par vous\-même des visualiseurs plus complexes et plus utiles.  
  
## Voir aussi  
 [Architecture d'un visualiseur](../debugger/visualizer-architecture.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Visualiseurs](../debugger/create-custom-visualizers-of-data.md)