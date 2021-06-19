---
title: Débogage d’un Windows Form | Microsoft Docs
description: 'Suivez une procédure pas à pas pour voir comment créer et déboguer un Windows Form, une application managée commune. Vous pouvez utiliser C#, Visual Basic, C++ ou F #.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73b58326bb594f275a508e5ba7fb17071f283ac2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385173"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procédure pas à pas : débogage d’un Windows Form
Un Windows Form est l’une des applications gérées les plus courantes. Un Windows Form crée une application Windows standard. Vous pouvez effectuer cette procédure pas à pas à l’aide de Visual Basic, C# ou C++.

 Tout d’abord, vous devez fermer toutes les solutions ouvertes.

### <a name="to-prepare-for-this-walkthrough"></a>Pour vous préparer à cette procédure

- Si vous avez déjà ouvert une solution ouverte, fermez-la. (Dans le menu **fichier** , sélectionnez **Fermer la solution**.)

## <a name="create-a-new-windows-form"></a>Créer un Windows Form
 Ensuite, vous allez créer un nouveau Windows Form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Pour créer le Windows Form pour cette procédure pas à pas

1. Dans le menu **fichier** , choisissez **nouveau** , puis cliquez sur **projet**.

     La boîte de dialogue **Nouveau projet** apparaît.

2. Dans le volet types de projets, ouvrez le nœud **Visual Basic**, **Visual C#** ou **Visual C++** , puis

    1. Pour Visual Basic ou Visual C#, sélectionnez Windows **Desktop**  >  **Windows Form App**.

    2. Pour Visual C++, sélectionnez **application de bureau Windows**.

3. Dans la zone **nom** , attribuez un nom unique au projet (par exemple, Walkthrough_SimpleDebug).

4. Cliquez sur **OK**.

     Visual Studio crée un nouveau projet et affiche un nouveau formulaire dans le concepteur de Windows Forms. Pour plus d’informations, consultez [Concepteur Windows Forms](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. Dans le menu **affichage** , sélectionnez **boîte à outils**.

     La boîte à outils s'ouvre. Pour plus d'informations, consultez [Boîte à outils](../ide/reference/toolbox.md).

6. Dans la boîte à outils, cliquez sur le contrôle **Button** et faites glisser le contrôle vers l’aire de conception de formulaire. Déposez le bouton sur le formulaire.

7. Dans la boîte à outils, cliquez sur le contrôle **TextBox** et faites glisser le contrôle vers l’aire de conception de formulaire. Déposez la **zone de texte** sur le formulaire.

8. Sur l’aire de conception de formulaire, double-cliquez sur le bouton.

     Vous accédez alors à la page de codes. Le curseur doit être dans `button1_Click` .

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
 Vous êtes maintenant prêt à commencer le débogage.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Pour déboguer le Windows Form créé pour cette procédure pas à pas

1. Dans la fenêtre source, cliquez sur la marge de gauche sur la même ligne que le texte que vous avez ajouté :

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Un point rouge s'affiche et le texte de la ligne est surligné en rouge. Le point rouge représente un point d'arrêt. Pour plus d’informations, consultez [Points d’arrêt](/previous-versions/ktf38f66(v=vs.100)). Lorsque vous exécutez l'application dans le débogueur, le débogueur interrompt l'exécution à l'emplacement du code où se trouve ce point d'arrêt. Vous pouvez afficher l'état de votre application et la déboguer.

    > [!NOTE]
    > Vous pouvez également cliquer avec le bouton droit sur n’importe quelle ligne de code, pointer sur **point d’arrêt**, puis cliquer sur Insérer un **point d’arrêt** pour ajouter un point d’arrêt sur cette ligne.

2. DANS le menu **Déboguer** , choisissez **Démarrer**.

     L’exécution du Windows Form démarre.

3. Dans le Windows Form, cliquez sur le bouton que vous avez ajouté.

     Dans Visual Studio, vous accédez à la ligne où vous définissez votre point d’arrêt sur la page de codes. Cette ligne doit être surlignée en jaune. Vous pouvez à présent afficher les variables de votre application et contrôler son exécution. Votre application a cessé de s’exécuter, en attendant une action de votre part.

4. Dans le menu **Déboguer** , choisissez **fenêtres**, **Espion**, puis cliquez sur **Espion1**.

5. Dans la fenêtre **Espion1** , cliquez sur une ligne vide. Dans la colonne **nom** , tapez `textBox1.Text` (si vous utilisez Visual Basic ou Visual C#) ou `textBox1->Text` (si vous utilisez C++), puis appuyez sur entrée.

     La fenêtre **Espion1** affiche la valeur de cette variable entre guillemets comme suit :

    `""`

6. Dans le menu **Déboguer**, choisissez **Pas à pas détaillé**.

     La valeur de textBox1. Text change dans la fenêtre **Espion1** pour :

    `Button was clicked!`

7. Dans le menu **Déboguer** , choisissez **Continuer** pour reprendre le débogage de votre programme.

8. Dans le Windows Form, cliquez à nouveau sur le bouton.

     Visual Studio interrompt l’exécution de nouveau.

9. Cliquez sur le point rouge représentant le point d’arrêt.

     Cela supprime le point d’arrêt de votre code.

10. Dans le menu **Déboguer**, choisissez **Arrêter le débogage**.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Attacher à votre application Windows Forms pour le débogage
 Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], vous pouvez attacher le débogueur à un processus en cours d'exécution. Si vous utilisez une édition Express, cette fonctionnalité n’est pas prise en charge.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Pour attacher l’application Windows Form pour le débogage

1. Dans le projet que vous avez créé ci-dessus, cliquez dans la marge de gauche pour définir à nouveau un point d’arrêt à la ligne que vous avez ajoutée :

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. Dans le menu **Déboguer**, sélectionnez **Démarrer sans débogage**.

     Le Windows Form commence à s’exécuter sous Windows, comme si vous aviez double-cliqué sur son fichier exécutable. Le débogueur n’est pas attaché.

3. Dans le menu **Déboguer** , sélectionnez **attacher au processus**. (Cette commande est également disponible dans le menu **Outils** .)

     La boîte de dialogue **Attacher au processus** s'affiche.

4. Dans le volet **processus disponibles** , recherchez le nom du processus (Walkthrough_SimpleDebug.exe) dans la colonne **traiter** , puis cliquez dessus.

5. Cliquez sur le bouton **attacher** .

6. Dans votre Windows Form, cliquez sur le bouton un et un seul.

     Le débogueur interrompt l’exécution du Windows Form au point d’arrêt.

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)