---
title: Débogage d’un formulaire Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d0e04b407303b1d6f98862fdef36bb8228fd780
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851967"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procédure pas à pas : débogage d’un Windows Form
Un formulaire Windows est une des applications managées plus courantes. Un formulaire Windows crée une application Windows standard. Vous pouvez effectuer cette procédure pas à pas à l’aide de Visual Basic, C#, ou C++.  
  
 Tout d’abord, vous devez fermer les solutions ouvertes.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Pour vous préparer à cette procédure  
  
-   Si vous avez déjà ouvert une solution ouverte, fermez-la. (Sur le **fichier** menu, sélectionnez **fermer la Solution**.)  
  
## <a name="create-a-new-windows-form"></a>Créer un Windows Form  
 Ensuite, vous allez créer un nouveau formulaire Windows.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Pour créer le formulaire Windows pour cette procédure pas à pas  
  
1.  Sur le **fichier** menu, choisissez **New** et cliquez sur **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans le volet Types de projets, ouvrez le **Visual Basic**, **Visual C#** , ou **Visual C++** nœud, puis  
  
    1.  Pour Visual Basic ou Visual C#, sélectionnez **Windows Desktop** > **application de formulaire Windows**.  
  
    2.  Pour Visual C++, sélectionnez **Application de bureau Windows**.  
  
3.  Dans le **nom** boîte, donnez un nom unique (par exemple, Walkthrough_SimpleDebug) au projet.  
  
4.  Cliquez sur **OK**.  
  
     Visual Studio crée un nouveau projet et affiche un nouveau formulaire dans le Concepteur Windows Forms. Pour plus d’informations, consultez [Windows Forms Designer](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).  
  
5.  Sur le **vue** menu, sélectionnez **boîte à outils**.  
  
     La boîte à outils s'ouvre. Pour plus d'informations, consultez [Boîte à outils](../ide/reference/toolbox.md).  
  
6.  Dans la boîte à outils, cliquez sur le **bouton** contrôler et faites glisser le contrôle sur l’aire de conception du formulaire. Relâchez le bouton sur le formulaire.  
  
7.  Dans la boîte à outils, cliquez sur le **zone de texte** contrôler et faites glisser le contrôle sur l’aire de conception du formulaire. Supprimer le **zone de texte** sur le formulaire.  
  
8. Sur l’aire de conception de formulaire, double-cliquez sur le bouton.  
  
     Vous accédez alors à la page de codes. Le curseur doit se trouver dans `button1_Click`.  
  
10. Dans la fonction `button1_Click`, ajoutez le code suivant :  
  
    ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Dans le menu **Générer**, sélectionnez **Générer la solution**.  
  
     Le projet doit être généré sans erreur.  
  
## <a name="debug-your-form"></a>Déboguer votre formulaire  
 Maintenant, vous êtes prêt à commencer le débogage.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Pour déboguer le formulaire Windows créé pour cette procédure pas à pas  
  
1.  Dans la fenêtre source, cliquez sur la marge de gauche sur la même ligne que le texte que vous avez ajouté :  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ``` 
  
     Un point rouge s'affiche et le texte de la ligne est surligné en rouge. Le point rouge représente un point d'arrêt. Pour plus d’informations, consultez [Points d’arrêt](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Lorsque vous exécutez l'application dans le débogueur, le débogueur interrompt l'exécution à l'emplacement du code où se trouve ce point d'arrêt. Vous pouvez afficher l'état de votre application et la déboguer.  
  
    > [!NOTE]
    >  Vous pouvez également cliquer sur n’importe quelle ligne de code, pointez sur **point d’arrêt**, puis cliquez sur **insérer un point d’arrêt** pour ajouter un point d’arrêt sur cette ligne.  
  
2.  Dans le menu **Déboguer**, choisissez **Démarrer**.  
  
     Le formulaire Windows commence à s’exécuter.  
  
3.  Dans le formulaire Windows, cliquez sur le bouton que vous avez ajouté.  
  
     Dans Visual Studio, vous accédez à la ligne où vous définissez votre point d’arrêt sur la page de codes. Cette ligne doit être surlignée en jaune. Vous pouvez à présent afficher les variables de votre application et contrôler son exécution. Votre application s’est arrêtée et attend une action de votre part.  
  
4.  Sur le **déboguer** menu, choisissez **Windows**, puis **espion**, puis cliquez sur **Espion1**.  
  
5.  Dans le **Espion1** fenêtre, cliquez sur une ligne vide. Dans le **nom** colonne, tapez `textBox1.Text` (si vous utilisez Visual Basic ou Visual C#) ou `textBox1->Text` (si vous utilisez C++), puis appuyez sur ENTRÉE.  
  
     Le **Espion1** fenêtre affiche la valeur de cette variable entre guillemets :  
  
    `""`  
 
6.  Dans le menu **Déboguer**, choisissez **Pas à pas détaillé**.  
  
     La valeur de TextBox1.Text, dans le **Espion1** fenêtre pour :  
  
    `Button was clicked!`  
  
7.  Sur le **déboguer** menu, choisissez **continuer** pour reprendre le débogage de votre programme.  
  
8.  Le formulaire Windows, cliquez sur le bouton Nouveau.  
  
     Visual Studio s’arrête à nouveau l’exécution.  
  
9. Cliquez sur le point rouge qui représente le point d’arrêt.  
  
     Cette opération supprime le point d’arrêt à partir de votre code.  
  
10. Dans le menu **Déboguer**, choisissez **Arrêter le débogage**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Attacher à votre Application de formulaire Windows pour le débogage  
 Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vous pouvez attacher le débogueur à un processus en cours d'exécution. Si vous utilisez une édition Express, cette fonctionnalité n’est pas pris en charge.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Pour attacher à l’Application de formulaire Windows pour le débogage  
  
1.  Dans le projet que vous avez créé ci-dessus, cliquez dans la marge de gauche pour définir une fois encore un point d’arrêt sur la ligne que vous avez ajouté :  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)