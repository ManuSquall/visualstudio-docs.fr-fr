---
title: "Proc&#233;dure pas &#224; pas&#160;: Appel dans le Kit de d&#233;veloppement logiciel (SDK) Visual Studio &#224; l’aide d’Automation | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procédures pas à pas [SDK Visual Studio], appel avec Automation"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: Appel dans le Kit de d&#233;veloppement logiciel (SDK) Visual Studio &#224; l’aide d’Automation
Cette procédure pas à pas montre comment créer un complément Visual Studio qui consomme un service Visual Studio. Le complément que vous créez obtient un fournisseur de services et l’utilise pour obtenir un service. Vous pouvez utiliser cette même technique pour obtenir un service Visual Studio proposé. Pour plus d’informations sur les services et fournisseurs de services, consultez [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md). Les procédures ci\-après montrent comment créer un complément et obtenir un service à partir du complément.  
  
## Création d’un complément  
 Dans cette section, vous créez un complément Visual Studio à l’aide du modèle de projet Complément Visual Studio.  
  
#### Pour créer un complément  
  
1.  Créez un projet Visual Studio \(**Fichier\/Nouveau\/Projet**\).  
  
2.  Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez le nœud **Autres types de projets**, puis cliquez sur le nœud **Extensibilité**. Sélectionnez **Complément Visual Studio**.  
  
3.  Créez un projet de complément nommé `Addin`.  
  
     Dans l’Assistant Complément [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner un langage de programmation** , sélectionnez **Créer un complément à l’aide de Visual C\#** ou **Créer un complément à l’aide de Visual Basic**.  
  
5.  Dans la page **Sélectionner une application hôte** sélectionnez **Microsoft Visual Studio \<version\>**.  
  
6.  Dans la page **Entrer un nom et une description**, tapez `MyAddin` dans la zone **Nom** et `MyAddin Walkthrough` dans la zone **Description**.  
  
7.  Dans la page **Choisir les options du complément**, sélectionnez l’option d’un élément de menu Outils sous **Voulez\-vous créer une interface utilisateur de barre de commandes pour votre complément ?** Décochez les autres cases.  
  
8.  Acceptez toutes les autres valeurs par défaut.  
  
9. Générez la solution et vérifiez qu’elle est compilée sans erreur.  
  
## Obtention d’un service à partir d’un complément  
 Les étapes suivantes vous guident tout au long de l’acquisition d’un service à partir de votre complément.  
  
#### Pour obtenir un service  
  
1.  Ouvrez le fichier Connect.cs ou Connect.vb et ajoutez ces lignes aux instructions `using` \(C\#\) ou `Imports` \(Visual Basic\) :  
  
     [!code-cs[VSSDKAddin#1](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.cs)]
     [!code-vb[VSSDKAddin#1](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.vb)]  
  
2.  Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions** et ajoutez ces références .NET :  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  Ajoutez ces lignes de code à la clause `if(commandName == "Addin.Connect.Addin")` ou `If commandName = "Addin.Connect.Addin" Then` de la méthode `Exec` :  
  
     [!code-cs[VSSDKAddin#2](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.cs)]
     [!code-vb[VSSDKAddin#2](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.vb)]  
  
     Ce code effectue un cast de l’objet d’application actuel \(type `DTE2`\) dans un `IOleServiceProvider`, puis appelle `QueryService` pour obtenir le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Ce service fournit une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> affiche une boîte de message quand le complément s’exécute.  
  
4.  Créez et démarrez le projet de complément en mode débogage en appuyant sur F5.  
  
     Une autre instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] démarre.  
  
5.  Dans la nouvelle instance [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans le menu **Outils**, cliquez sur **Complément**. La boîte de message indique :  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## Voir aussi  
 [Comment : désactiver et supprimer un complément](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)