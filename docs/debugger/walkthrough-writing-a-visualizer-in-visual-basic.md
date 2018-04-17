---
title: 'Procédure pas à pas : Écriture d’un visualiseur en Visual Basic | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7076e85701551e884c3126c7acd235b45a81aff5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Procédure pas à pas : écriture d'un visualiseur en Visual Basic
Cette procédure pas à pas explique comment écrire un visualiseur simple à l'aide de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d'une chaîne à l'aide d'un message Windows Forms. Ce visualiseur de chaîne simple est un exemple de base qui vous montre comment vous pouvez créer des visualiseurs pour d'autres types de données plus applicables à vos projets.  
  
> [!NOTE]
>  Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, accédez à la **outils** menu et choisissez **importer et exporter des** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Le code du visualiseur doit être placé dans une DLL qui sera lue par le débogueur. La première étape consiste à créer un projet de bibliothèque de classes pour la DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Créer et préparer un projet Bibliothèque de classes  
  
#### <a name="to-create-a-class-library-project"></a>Pour créer un projet Bibliothèque de classes  
  
1.  Sur le **fichier** menu, choisissez **nouveau** et cliquez sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **Type de projet**s, cliquez sur **Visual Basic**.  
  
3.  Dans le **modèles** , cliquez sur **bibliothèque de classes**.  
  
4.  Dans le **nom** , tapez un nom approprié pour la bibliothèque de classes, telles que **MyFirstVisualizer**.  
  
5.  Cliquez sur **OK**.  
  
 Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Pourtant, en premier lieu, donnez un nom significatif à votre projet.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Pour renommer Class1.vb et ajouter Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Class1.vb**, dans le menu contextuel, cliquez sur **renommer**.  
  
2.  Remplacez le nom Class1.vb par un nom explicite, par exemple DebuggerSide.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] remplace automatiquement le nom de la déclaration de classe par DebuggerSide.vb correspondant au nouveau nom du fichier.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit **My First Visualizer**, dans le menu contextuel, cliquez sur **ajouter une référence**.  
  
4.  Dans le **ajouter une référence** boîte de dialogue le **.NET** , cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans DebuggerSide.vb, ajoutez l'instruction suivante aux instructions `Imports` :  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Ajouter le code côté débogueur  
 Vous êtes désormais prêt à créer du code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Tout d'abord, vous devez modifier la déclaration de l'objet `DebuggerSide` afin qu'il hérite de la classe de base `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer  
  
1.  Dans DebuggerSide.vb, allez à la ligne de code suivante :  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Modifiez le code pour qu'il se présente comme suit :  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` a une méthode abstraite, `Show`, que vous devez substituer.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show  
  
-   Dans `public class DebuggerSide`, ajoutez la méthode suivante :  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l'aide d'un message Windows Forms. Vous devez d'abord ajouter une référence et une instruction `Imports` pour <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **références**, dans le menu contextuel, cliquez sur **ajouter une référence**.  
  
2.  Dans le **ajouter une référence** boîte de dialogue le **.NET** , cliquez sur **System.Windows.Forms**.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `Imports` :  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Créer l'interface utilisateur de votre visualiseur  
 Puis, vous ajoutez du code pour créer et afficher l'interface utilisateur du visualiseur. Comme il s'agit de votre premier visualiseur, vous simplifierez l'interface utilisateur simple et utiliserez un message.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue  
  
1.  Dans la méthode `Show`, ajoutez la ligne de code suivante :  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d'application.  
  
2.  Sur le **générer** menu, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
## <a name="add-the-necessary-attribute"></a>Ajouter l'attribut nécessaire  
 C'est la fin du code côté débogueur. Il existe toutefois une étape supplémentaire : ajouter l'attribut qui indique côté programme débogué la collection de classes qui compose le visualiseur.  
  
#### <a name="to-add-the-debugee-side-code"></a>Pour ajouter le code côté débogué  
  
1.  Ajoutez le code d'attribut suivant à DebuggerSide.vb, après les instructions `Imports`, mais avant `namespace MyFirstVisualizer` :  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Sur le **générer** menu, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
## <a name="create-a-test-harness"></a>Créer un atelier de test  
 À ce stade, votre premier visualiseur est terminé. Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement. À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Pour ajouter une méthode de test permettant d'afficher le visualiseur  
  
1.  Ajoutez la méthode suivante à la classe `public DebuggerSide`:  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  Sur le **générer** menu, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
 Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, utilisez un projet d'application console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution  
  
1.  Sur le **fichier** menu, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
2.  Dans le **ajouter un nouveau projet** boîte de dialogue le **modèles** , cliquez sur **Application Console**.  
  
3.  Dans le **nom** , tapez un nom explicite pour l’application console, tel que **MyTestConsole**.  
  
4.  Cliquez sur **OK**.  
  
 Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole**, dans le menu contextuel, cliquez sur **ajouter une référence**.  
  
2.  Dans le **ajouter une référence** boîte de dialogue le **.NET** , cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Cliquez sur **OK**.  
  
4.  Avec le bouton droit **MyTestConsole**, puis cliquez sur **ajouter une référence** à nouveau.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **projets** onglet, puis sélectionnez MyFirstVisualizer.  
  
6.  Cliquez sur **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Terminer votre atelier de test et tester votre visualiseur  
 Puis, vous ajoutez le code pour terminer l'atelier de test.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Program.vb**, dans le menu contextuel, cliquez sur **renommer**.  
  
2.  Modifier le nom Module1.vb par un nom approprié, tel que **TestConsole.vb**.  
  
     Notez que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] remplace automatiquement le nom de la déclaration de classe par TestConsole.vb correspondant au nouveau nom du fichier.  
  
3.  Dans TestConsole. vb, ajoutez le code suivant `Imports` instruction :  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  Dans la méthode `Main`, ajoutez le code suivant :  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 Vous êtes désormais prêt à tester votre premier visualiseur.  
  
#### <a name="to-test-the-visualizer"></a>Pour tester le visualiseur  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **MyTestConsole**, dans le menu contextuel, cliquez sur **définir comme projet de démarrage**.  
  
2.  Sur le **déboguer** menu, cliquez sur **Démarrer**.  
  
     L'application console démarre. Le visualiseur apparaît et affiche la chaîne « Hello, World ».  
  
 Félicitations ! Vous venez de générer et de tester votre premier visualiseur.  
  
 Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture du visualiseur](../debugger/visualizer-architecture.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)