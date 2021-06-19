---
title: Déboguer un formulaire Web | Microsoft Docs
description: Suivez une procédure pas à pas pour voir comment déboguer une application Web ASP.NET (Web Form), notamment comment définir des points d’arrêt et examiner des variables.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18347b7ba9ff52778b5acef685acd8f1ee400793
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385204"
---
# <a name="walkthrough-debugging-a-web-form"></a>Procédure pas à pas : Débogage d’un formulaire web
Les étapes de cette procédure pas à pas vous expliquent comment déboguer une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], également connue sous le nom de Web Form. Elle vous explique également comment démarrer et arrêter l’exécution, définir des points d’arrêt et examiner des variables dans la fenêtre **Espion**.

> [!NOTE]
> Pour exécuter cette procédure pas à pas, vous devez avoir des privilèges d'administrateur de l'ordinateur serveur. Par défaut, le processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet_wp.exe ou w3wp.exe, s'exécute comme un processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Pour déboguer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devez avoir des privilèges d'administrateur sur l'ordinateur où [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] s'exécute. Pour plus d’informations, consultez [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md).

Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Pour créer le Web Form

1. Si une solution est déjà ouverte, fermez-la.

2. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Site web**.

    La boîte de dialogue **Nouveau site web** s’affiche.

3. Dans le volet **Modèles**, cliquez sur **Site web ASP.NET**.

4. Sur la ligne **emplacement** , cliquez sur **http** dans la liste, puis dans la zone de texte, tapez **http://localhost/WebSite** .

5. Dans la liste **Langage**, cliquez sur **Visual C#** ou sur **Visual Basic**.

6. Cliquez sur **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée un projet et affiche le code source HTML par défaut. Il crée également un répertoire virtuel nommé **WebSite** sous **Site web par défaut** dans IIS.

7. Cliquez sur l’onglet **Conception** dans la marge inférieure.

8. Cliquez sur l’onglet **Boîte à outils** dans la marge gauche ou sélectionnez-le dans le menu **Affichage**.

    La **boîte à outils** s’ouvre.

9. Dans la **Boîte à outils**, cliquez sur le contrôle **Bouton** et ajoutez-le à l’aire de conception principale, Default.aspx.

10. Dans la **Boîte à outils**, cliquez sur le contrôle **Zone de texte** et faites-le glisser sur l’aire de conception principale, Default.aspx.

11. Double-cliquez sur le contrôle Button que vous avez déposé.

     Cette opération vous permet d'atteindre la page de codes : Default.aspx.cs pour C# ou Default.aspx.vb pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Le curseur doit se trouver dans la fonction `Button1_Click`.

12. Dans la fonction `Button1_Click`, ajoutez le code suivant :

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. Dans le menu **Générer**, cliquez sur **Générer la solution**.

     Le projet doit être généré sans erreur.

     Vous pouvez maintenant commencer le débogage.

## <a name="to-debug-the-web-form"></a>Pour déboguer le Web FOrm

1. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur la marge gauche de la ligne sur laquelle vous avez ajouté le texte :

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Un point rouge s'affiche et le texte de la ligne est surligné en rouge. Le point rouge représente un point d'arrêt. Lorsque vous exécutez l'application dans le débogueur, le débogueur interrompt l'exécution à l'emplacement du code où se trouve ce point d'arrêt. Vous pouvez afficher l'état de votre application et la déboguer. Pour plus d’informations, consultez [Points d’arrêt](/previous-versions/ktf38f66(v=vs.100)).

2. Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.

3. La boîte de dialogue **Débogage non activé** s’affiche. Sélectionnez l’option **Modifier le fichier Web.config pour activer le débogage**, puis cliquez sur **OK**.

    Internet Explorer démarre et affiche la page que vous venez de créer.

4. Dans Internet Explorer, cliquez sur le bouton.

    Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cette opération vous permet d'atteindre la ligne où vous définissez votre point d'arrêt sur la page de codes Default.aspx.cs ou Default.aspx.vb. Cette ligne doit être surlignée en jaune. Vous pouvez à présent afficher les variables de votre application et contrôler son exécution. Votre application s'arrête et attend une commande de votre part.

5. Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Espion**, puis sur **Espion1**.

6. Dans la fenêtre **Espion**, tapez **TextBox1.Text**.

    La fenêtre **Espion** affiche la valeur de la variable `TextBox1.Text` :

   '""'

7. Dans le menu **Déboguer**, cliquez sur **Pas à pas principal**.

    La valeur de `TextBox1.Text` change dans la fenêtre **Espion** et devient :

   `"Button was clicked!"`

8. Dans le menu **Déboguer**, cliquez sur **Continuer**.

9. Dans Internet Explorer, cliquez de nouveau sur le bouton.

     L'exécution s'arrête de nouveau sur le point d'arrêt.

10. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur le point rouge dans la marge de gauche.

     Cela supprime le point d'arrêt.

11. Dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Pour attacher au Web Form pour le débogage

1. Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez attacher le débogueur à un processus en cours d'exécution. Pour un débogage plus efficace, compilez le fichier exécutable sous forme de version Debug avec des fichiers de symboles (PDB).

2. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez dans la marge de gauche pour définir à nouveau un point d'arrêt à la ligne que vous avez ajoutée :

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Dans le menu **Déboguer**, cliquez sur **Exécuter sans débogage**.

    Le Web Form commence à s'exécuter sous Internet Explorer, mais le débogueur n'est pas attaché.

4. Attachez-le au processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Pour plus d’informations, consultez [débogage d’applications Web déployées](../debugger/debugging-deployed-web-applications.md).

5. Dans Internet Explorer, cliquez sur le bouton sur votre formulaire.

    Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez atteindre le point d'arrêt dans Default.aspx.cs, Default.aspx.vb ou Default.aspx.

6. Quand vous avez fini de déboguer, dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.

## <a name="see-also"></a>Voir aussi

- [Déboguer des applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)