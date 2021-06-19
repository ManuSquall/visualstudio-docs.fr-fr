---
title: Écrire un visualiseur dans Visual Basic | Microsoft Docs
description: Suivez une procédure pas à pas pour créer un visualiseur simple dans Visual Basic. Vous créez également un atelier de test pour tester votre visualiseur.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a4fc7d6f33d1bdfd469ec352674b08dd2495e6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385004"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Procédure pas à pas : écriture d'un visualiseur en Visual Basic

Cette procédure pas à pas explique comment écrire un visualiseur simple à l'aide de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Le visualiseur que permet de créer cette procédure pas à pas affiche le contenu d'une chaîne à l'aide d'un message Windows Forms. Ce visualiseur de chaîne simple est un exemple de base qui vous montre comment vous pouvez créer des visualiseurs pour d'autres types de données plus applicables à vos projets.

> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, dans le menu **Outils**, cliquez sur **Importer et exporter**. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Le code du visualiseur doit être placé dans une DLL qui sera lue par le débogueur. La première étape consiste à créer un projet de bibliothèque de classes pour la DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Créer et préparer un projet Bibliothèque de classes

### <a name="to-create-a-class-library-project"></a>Pour créer un projet de bibliothèque de classes

1. Créez un projet de bibliothèque de classes.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **Visual Basic**, choisissez **modèles**, puis **créer une bibliothèque de classes (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , sous **Visual Basic**, choisissez **.NET standard**, puis dans le volet central, choisissez **bibliothèque de classes (.NET standard)**.
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyFirstVisualizer` , puis cliquez sur **créer** ou **OK**.

   Une fois que vous avez créé la bibliothèque de classes, vous devez ajouter une référence à Microsoft.VisualStudio.DebuggerVisualizers.DLL afin de pouvoir utiliser les classes qui y sont définies. Pourtant, en premier lieu, donnez un nom significatif à votre projet.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Pour renommer Class1.vb et ajouter Microsoft.VisualStudio.DebuggerVisualizers

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Class1.vb** et cliquez sur **Renommer** dans le menu contextuel.

2. Remplacez le nom Class1.vb par un nom explicite, par exemple DebuggerSide.vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifie automatiquement la déclaration de classe dans DebuggerSide. vb pour qu’elle corresponde au nouveau nom de fichier.

3. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **My First Visualizer**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.

4. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **Parcourir** et recherchez le Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Vous pouvez trouver la DLL dans le sous-répertoire *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* du répertoire d’installation de Visual Studio.

5. Cliquez sur **OK**.

6. Dans DebuggerSide.vb, ajoutez l'instruction suivante aux instructions `Imports` :

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Ajouter le code côté débogueur
 Vous êtes désormais prêt à créer du code côté débogueur. Il s'agit du code qui s'exécute dans le débogueur pour afficher les informations que vous souhaitez consulter. Tout d'abord, vous devez modifier la déclaration de l'objet `DebuggerSide` afin qu'il hérite de la classe de base `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Pour hériter de DialogDebuggerVisualizer

1. Dans DebuggerSide.vb, allez à la ligne de code suivante :

   ```vb
   Public Class DebuggerSide
   ```

2. Modifiez le code pour qu'il se présente comme suit :

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` a une méthode abstraite, `Show` , que vous devez substituer.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pour substituer la méthode DialogDebuggerVisualizer.Show

- Dans `public class DebuggerSide`, ajoutez la méthode suivante :

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  La méthode `Show` contient le code qui crée en fait la boîte de dialogue du visualiseur, ou une autre interface utilisateur, et qui affiche les informations passées du débogueur au visualiseur. Vous devez ajouter le code qui crée la boîte de dialogue et affiche les informations. Cette procédure pas à pas vous montre comment y parvenir à l'aide d'un message Windows Forms. Vous devez d'abord ajouter une référence et une instruction `Imports` pour <xref:System.Windows.Forms>.

### <a name="to-add-systemwindowsforms"></a>Pour ajouter System.Windows.Forms

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , sélectionnez **parcourir**, puis recherchez le System.Windows.Forms.DLL.

    Vous pouvez trouver la DLL dans *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Cliquez sur **OK**.

4. Dans DebuggerSide.cs, ajoutez l'instruction suivante aux instructions `Imports` :

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Créer l'interface utilisateur de votre visualiseur
 Puis, vous ajoutez du code pour créer et afficher l'interface utilisateur du visualiseur. Comme il s'agit de votre premier visualiseur, vous simplifierez l'interface utilisateur simple et utiliserez un message.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Pour afficher la sortie du visualiseur dans une boîte de dialogue

1. Dans la méthode `Show`, ajoutez la ligne de code suivante :

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Cet exemple de code n'inclut pas la gestion des erreurs. Vous devez inclure la gestion des erreurs dans un véritable visualiseur ou tout autre type d'application.

2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

## <a name="add-the-necessary-attribute"></a>Ajouter l'attribut nécessaire
 C'est la fin du code côté débogueur. Il existe toutefois une étape supplémentaire : ajouter l'attribut qui indique côté programme débogué la collection de classes qui compose le visualiseur.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Pour ajouter le type à visualiser pour le code côté débogué

Dans le code côté débogueur, vous spécifiez le type à visualiser (la source de l’objet) pour le programme débogué à l’aide de l' <xref:System.Diagnostics.DebuggerVisualizerAttribute> attribut. La `Target` propriété définit le type à visualiser.

1. Ajoutez le code d'attribut suivant à DebuggerSide.vb, après les instructions `Imports`, mais avant `namespace MyFirstVisualizer` :

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

## <a name="create-a-test-harness"></a>Créer un atelier de test
 À ce stade, votre premier visualiseur est terminé. Si vous avez suivi les étapes correctement, vous devez être en mesure de générer le visualiseur et de l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Toutefois, avant d'installer un visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez le tester pour vous assurer qu'il s'exécute correctement. À présent, vous devez créer un atelier de test pour exécuter le visualiseur sans l'installer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Pour ajouter une méthode de test permettant d'afficher le visualiseur

1. Ajoutez la méthode suivante à la classe `public DebuggerSide`:

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. Dans le menu **Générer**, cliquez sur **Build MyFirstVisualizer**. Le projet doit se générer avec succès. Corrigez toutes les erreurs de build avant de continuer.

   Ensuite, vous devez créer un projet exécutable pour appeler la DLL du visualiseur. Par souci de simplicité, utilisez un projet d'application console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Pour ajouter un projet d'application console à la solution

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis cliquez sur **nouveau projet**.

    ::: moniker range=">=vs-2019"
    Dans la zone de recherche, tapez **Visual Basic**, choisissez **modèles**, puis **créer une application de console (.NET Framework)**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual Basic**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)**.
    ::: moniker-end

2. Tapez un nom approprié pour la bibliothèque de classes, par exemple `MyTestConsole` , puis cliquez sur **créer** ou **OK**.

   Puis, vous devez ajouter les références nécessaires afin que MyTestConsole puisse appeler MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Pour ajouter les références nécessaires à MyTestConsole

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez dans le menu contextuel sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , sous l’onglet **Parcourir** , cliquez sur Microsoft. VisualStudio. DebuggerVisualizers.

3. Cliquez sur **OK**.

4. Cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez sur **Ajouter une référence**.

5. Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l’onglet **Projets**, puis sélectionnez MyFirstVisualizer.

6. Cliquez sur **OK**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Terminer votre atelier de test et tester votre visualiseur
 Puis, vous ajoutez le code pour terminer l'atelier de test.

### <a name="to-add-code-to-mytestconsole"></a>Pour ajouter le code à MyTestConsole

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Program.vb** et cliquez sur **Renommer** dans le menu contextuel.

2. Remplacez le nom Module1.vb par un nom approprié, tel que **TestConsole.vb**.

    Notez que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] remplace automatiquement le nom de la déclaration de classe par TestConsole.vb correspondant au nouveau nom du fichier.

3. Dans TestConsole. VB, ajoutez l' `Imports` instruction suivante :

   ```vb
   Imports MyFirstVisualizer
   ```

4. Dans la méthode `Main`, ajoutez le code suivant :

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Vous êtes désormais prêt à tester votre premier visualiseur.

### <a name="to-test-the-visualizer"></a>Pour tester le visualiseur

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **MyTestConsole**, puis cliquez sur **Définir comme projet de démarrage** dans le menu contextuel.

2. Dans le menu **Déboguer** , cliquez sur **Démarrer**.

    L'application console démarre. Le visualiseur apparaît et affiche la chaîne « Hello, World ».

   Félicitations ! Vous venez de générer et de tester votre premier visualiseur.

   Pour utiliser votre visualiseur dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au lieu de simplement l'appeler de l'atelier de test, vous devez l'installer. Pour plus d’informations, consultez [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Voir aussi

- [Architecture du visualiseur](../debugger/visualizer-architecture.md)
- [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)