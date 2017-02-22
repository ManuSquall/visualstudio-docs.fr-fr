---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;un formulaire Web | Microsoft Docs"
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
  - "pages Web ASP.NET, débogage"
  - "sites Web ASP.NET, débogage"
  - "ASP.NET, déboguer les applications Web"
  - "déboguer (Visual Studio), Web Forms"
  - "déboguer les applications Web ASP.NET, Web Forms"
  - "applications Web (.NET Framework), débogage"
  - "pages Web (.NET Framework), débogage"
  - "sites Web (.NET Framework), débogage"
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage d&#39;un formulaire Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas vous expliquent comment déboguer une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], également connue sous le nom de Web Form.  Elle vous explique également comment démarrer et arrêter l'exécution, définir des points d'arrêt et examiner des variables dans la fenêtre **Espion**.  
  
> [!NOTE]
>  Pour exécuter cette procédure pas à pas, vous devez avoir des privilèges d'administrateur de l'ordinateur serveur.  Par défaut, le processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet\_wp.exe ou w3wp.exe, s'exécute comme un processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Pour déboguer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devez avoir des privilèges d'administrateur sur l'ordinateur où [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] s'exécute.  Pour plus d'informations, consultez [Configuration requise](../debugger/aspnet-debugging-system-requirements.md).  
  
 Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer le Web Form  
  
1.  Si une solution est déjà ouverte, fermez\-la.  
  
2.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Site Web**.  
  
     La boîte de dialogue **Nouveau site Web** s'affiche.  
  
3.  Dans le volet **Modèles**, cliquez sur **Site Web ASP.NET**.  
  
4.  Sur la ligne **Emplacement**, cliquez sur **HTTP** dans la liste, et dans la zone de texte, tapez http:\/\/localhost\/WebSite.  
  
5.  Dans la liste **Langage**, cliquez sur **Visual C\#** ou **Visual Basic**.  
  
6.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée un projet et affiche le code source HTML par défaut.  Il crée également un répertoire virtuel nommé **WebSite** sous **Site Web par défaut** dans IIS.  
  
7.  Cliquez sur l'onglet **Design** dans la marge inférieure.  
  
8.  Cliquez sur l'onglet **Boîte à outils** dans la marge gauche ou sélectionnez\-le dans le menu **Affichage**.  
  
     La **Boîte à outils** s'ouvre.  
  
9. Dans la **Boîte à outils**, cliquez sur le contrôle **Button** et ajoutez\-le à l'aire de conception principale, Default.aspx.  
  
10. Dans la **Boîte à outils**, cliquez sur le contrôle **Textbox** et faites\-le glisser sur l'aire de conception principale, Default.aspx.  
  
11. Double\-cliquez sur le contrôle Button que vous avez déposé.  
  
     Cette opération vous permet d'atteindre la page de codes : Default.aspx.cs pour C\# ou Default.aspx.vb pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  Le curseur doit se trouver dans la fonction `Button1_Click`.  
  
12. Dans la fonction `Button1_Click`, ajoutez le code suivant :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Le projet doit être généré sans erreur.  
  
     Vous pouvez maintenant commencer le débogage.  
  
### Pour déboguer le Web FOrm  
  
1.  Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur la marge gauche de la ligne sur laquelle vous avez ajouté le texte :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Un point rouge s'affiche et le texte de la ligne est surligné en rouge.  Le point rouge représente un point d'arrêt.  Lorsque vous exécutez l'application dans le débogueur, le débogueur interrompt l'exécution à l'emplacement du code où se trouve ce point d'arrêt.  Vous pouvez afficher l'état de votre application et la déboguer.  Pour plus d'informations, consultez [Points d'arrêt](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
3.  La boîte de dialogue **Débogage non activé** s'affiche.  Sélectionnez l'option **Modifier le fichier Web.config pour activer le débogage** et cliquez sur **OK**.  
  
     Internet Explorer démarre et affiche la page que vous venez de créer.  
  
4.  Dans Internet Explorer, cliquez sur le bouton.  
  
     Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cette opération vous permet d'atteindre la ligne où vous définissez votre point d'arrêt sur la page de codes Default.aspx.cs ou Default.aspx.vb.  Cette ligne doit être surlignée en jaune.  Vous pouvez à présent afficher les variables de votre application et contrôler son exécution.  Votre application s'arrête et attend une commande de votre part.  
  
5.  Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Espion**, puis sur **Espion1.**  
  
6.  Dans la fenêtre **Espion**, tapez TextBox1.Text.  
  
     La fenêtre **Espion** affiche la valeur de la variable `TextBox1.Text` :  
  
    ```  
    ""  
    ```  
  
7.  Dans le menu **Déboguer**, cliquez sur **Pas à pas principal**.  
  
     La valeur de `TextBox1.Text` change dans la fenêtre **Espion** et devient :  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Dans le menu **Déboguer**, cliquez sur **Continuer**.  
  
9. Dans Internet Explorer, cliquez de nouveau sur le bouton.  
  
     L'exécution s'arrête de nouveau sur le point d'arrêt.  
  
10. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur le point rouge dans la marge de gauche.  
  
     Cela supprime le point d'arrêt.  
  
11. Dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.  
  
### Pour attacher au Web Form pour le débogage  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez attacher le débogueur à un processus en cours d'exécution.  Pour un débogage plus efficace, compilez le fichier exécutable sous forme de version Debug avec des fichiers de symboles \(PDB\).  
  
2.  Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez dans la marge de gauche pour définir à nouveau un point d'arrêt à la ligne que vous avez ajoutée :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Dans le menu **Déboguer**, cliquez sur **Exécuter sans débogage**.  
  
     Le Web Form commence à s'exécuter sous Internet Explorer, mais le débogueur n'est pas attaché.  
  
4.  Attachez\-le au processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Pour plus d'informations, consultez [Débogage d'applications Web déployées](../debugger/debugging-deployed-web-applications.md).  
  
5.  Dans Internet Explorer, cliquez sur le bouton sur votre formulaire.  
  
     Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez atteindre le point d'arrêt dans Default.aspx.cs, Default.aspx.vb ou Default.aspx.  
  
6.  Lorsque vous avez fini de déboguer, dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.  
  
## Voir aussi  
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)