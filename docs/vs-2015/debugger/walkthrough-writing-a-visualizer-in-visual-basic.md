---
title: 'Procédure pas à pas : Écriture d’un visualiseur en Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 954bd976317f5b5ad577b1236c9d7421c2d50315
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688204"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Procédure pas à pas : Écriture d’un visualiseur en Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas explique comment écrire un visualiseur simple à l'aide de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d'une chaîne à l'aide d'un message Windows Forms. Ce visualiseur de chaîne simple est un exemple de base qui vous montre comment vous pouvez créer des visualiseurs pour d'autres types de données plus applicables à vos projets.  
  
> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, dans le menu **Outils**, cliquez sur **Importer et exporter**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Le code du visualiseur doit être placé dans une DLL qui sera lue par le débogueur. La première étape consiste à créer un projet de bibliothèque de classes pour la DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Créer et préparer un projet Bibliothèque de classes  
  
#### <a name="to-create-a-class-library-project"></a>Pour créer un projet Bibliothèque de classes  
  
1. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Nouveau projet**.  
  
2. Dans le **nouveau projet** boîte de dialogue **Type de projet**s, cliquez sur **Visual Basic**.  
  
3. Dans le **modèles** , cliquez sur **bibliothèque de classes**.  
  
4. Dans la zone **Nom**, tapez un nom approprié pour la bibliothèque de classes, par exemple **MyFirstVisualizer**.  
  
5. Cliquez sur **OK**.  
  
   Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Pourtant, en premier lieu, donnez un nom significatif à votre projet.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Pour renommer Class1.vb et ajouter Microsoft.VisualStudio.DebuggerVisualizers  
  
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Class1.vb** et cliquez sur **Renommer** dans le menu contextuel.  
  
2. Remplacez le nom Class1.vb par un nom explicite, par exemple DebuggerSide.vb.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] remplace automatiquement le nom de la déclaration de classe par DebuggerSide.vb correspondant au nouveau nom du fichier.  
  
3. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **My First Visualizer**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.  
  
4. Dans la boîte de dialogue **Ajouter une référence**, sous l’onglet **.NET**, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Cliquez sur **OK**.  
  
6. Dans DebuggerSide.vb, ajoutez l'instruction suivante aux instructions `Imports` :  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Ajouter le code côté débogueur  
 Vous êtes désormais prêt à créer du code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Tout d'abord, vous devez modifier la déclaration de l'objet `DebuggerSide` afin qu'il hérite de la classe de base `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer  
  
1. Dans DebuggerSide.vb, allez à la ligne de code suivante :  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Modifiez le code pour qu'il se présente comme suit :  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` a une méthode abstraite, `Show`, que vous devez substituer.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show  
  
- Dans `public class DebuggerSide`, ajoutez la méthode suivante :  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l'aide d'un message Windows Forms. Vous devez d'abord ajouter une référence et une instruction `Imports` pour <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms  
  
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.  
  
2. Dans la boîte de dialogue **Ajouter une référence**, sous l’onglet **.NET**, cliquez sur **System.Windows.Forms**.  
  
3. Cliquez sur **OK**.  
  
4. Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `Imports` :  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Créer l'interface utilisateur de votre visualiseur  
 Puis, vous ajoutez du code pour créer et afficher l'interface utilisateur du visualiseur. Comme il s'agit de votre premier visualiseur, vous simplifierez l'interface utilisateur simple et utiliserez un message.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue  
  
1. Dans la méthode `Show`, ajoutez la ligne de code suivante :  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d'application.  
  
2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
## <a name="add-the-necessary-attribute"></a>Ajouter l'attribut nécessaire  
 C'est la fin du code côté débogueur. Il existe toutefois une étape supplémentaire : ajouter l'attribut qui indique côté programme débogué la collection de classes qui compose le visualiseur.  
  
#### <a name="to-add-the-debugee-side-code"></a>Pour ajouter le code côté débogué  
  
1. Ajoutez le code d'attribut suivant à DebuggerSide.vb, après les instructions `Imports`, mais avant `namespace MyFirstVisualizer` :  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
## <a name="create-a-test-harness"></a>Créer un atelier de test  
 À ce stade, votre premier visualiseur est terminé. Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement. À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Pour ajouter une méthode de test permettant d'afficher le visualiseur  
  
1. Ajoutez la méthode suivante à la classe `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.  
  
   Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, utilisez un projet d'application console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution  
  
1. Dans le menu **Fichier**, cliquez sur **Ajouter**, puis sur **Nouveau projet**.  
  
2. Dans le **ajouter un nouveau projet** boîte de dialogue le **modèles** , cliquez sur **Application Console**.  
  
3. Dans la zone **Nom**, tapez un nom significatif pour l’application console, par exemple **MyTestConsole**.  
  
4. Cliquez sur **OK**.  
  
   Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole  
  
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.  
  
2. Dans la boîte de dialogue **Ajouter une référence**, sous l’onglet **.NET**, cliquez sur Microsoft.VisualStudio.DebuggerVisualizers.  
  
3. Cliquez sur **OK**.  
  
4. Cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez sur **Ajouter une référence**.  
  
5. Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l’onglet **Projets**, puis sélectionnez MyFirstVisualizer.  
  
6. Cliquez sur **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Terminer votre atelier de test et tester votre visualiseur  
 Puis, vous ajoutez le code pour terminer l'atelier de test.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole  
  
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Program.vb** et cliquez sur **Renommer** dans le menu contextuel.  
  
2. Remplacez le nom Module1.vb par un nom approprié, tel que **TestConsole.vb**.  
  
    Notez que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] remplace automatiquement le nom de la déclaration de classe par TestConsole.vb correspondant au nouveau nom du fichier.  
  
3. Dans TestConsole. vb, ajoutez le code suivant `Imports` instruction :  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. Dans la méthode `Main`, ajoutez le code suivant :  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Vous êtes désormais prêt à tester votre premier visualiseur.  
  
#### <a name="to-test-the-visualizer"></a>Pour tester le visualiseur  
  
1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez sur **Définir comme projet de démarrage** dans le menu contextuel.  
  
2. Dans le menu **Déboguer**, cliquez sur **Démarrer**.  
  
    L'application console démarre. Le visualiseur apparaît et affiche la chaîne « Hello, World ».  
  
   Félicitations ! Vous venez de générer et de tester votre premier visualiseur.  
  
   Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d'informations, voir [Procédure : Installer un visualiseur](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture du visualiseur](../debugger/visualizer-architecture.md)   
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
