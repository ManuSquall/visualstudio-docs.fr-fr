---
title: "Ajout d’un contr&#244;le utilisateur dans une fen&#234;tre Outil | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtres Outil, ajouter des contrôles utilisateur"
  - "contrôles utilisateur [Kit de développement logiciel (SDK) Visual Studio], ajouter aux fenêtres Outil"
  - "contrôles utilisateur [Kit de développement logiciel (SDK) Visual Studio]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Ajout d’un contr&#244;le utilisateur dans une fen&#234;tre Outil
Cette procédure pas à pas montre comment ajouter un contrôle utilisateur à une fenêtre Outil.  
  
 Un contrôle utilisateur est une collection de contrôles Windows liés dans un contrôle. Pour ajouter un contrôle utilisateur à une fenêtre Outil, il vous suffit de faire apparaître le contrôle utilisateur dans la **boîte à outils**. Le contrôle utilisateur qui est utilisé dans cette procédure pas à pas est le contrôle horloge développé dans [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md).  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Création du contrôle utilisateur  
  
1.  Suivez les étapes de [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md) pour créer le contrôle horloge. Ne créez pas le contrôle réveil.  
  
> [!NOTE]
>  Les étapes suivantes supposent que vous avez nommé le contrôle horloge `ctlClock`.  
  
## Création d’une extension de fenêtre Outil  
  
1.  Créez un projet VSIX nommé `MyToolWindowPackageUC` qui comporte une fenêtre Outil nommée `MyToolWindow`. Si vous avez besoin d’aide pour cette opération, consultez [Création d'une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Ajout du contrôle utilisateur  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **MyToolWindowPackageUC**, pointez sur **Ajouter**, puis cliquez sur **Projet existant**.  
  
2.  Dans la boîte de dialogue **Ajouter un projet existant**, ouvrez le projet ctlClockLib et sélectionnez le fichier projet ctlClock.lib.csproj. Cliquez sur **OK**. Vous activez ainsi le contrôle utilisateur que vous pouvez utiliser dans le concepteur.  
  
3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur MyToolWindowControl.cs, puis sélectionnez **Concepteur de vues**. Cela ouvre le Concepteur de formulaires qui affiche le contrôle généré pour la fenêtre Outil.  
  
4.  Ouvrez la **boîte à outils**, recherchez la section intitulée **Composants ctlClockLib** et double\-cliquez sur le contrôle **ctlClock** dans cette section pour ajouter le contrôle au formulaire. Dès que vous masquez la **boîte à outils**, une heure doit s’afficher dans le formulaire de la fenêtre Outil.  
  
5.  Dans le concepteur, sélectionnez le contrôle horloge qui vient d’être ajouté et affectez à la propriété **Anchor** la seule valeur **Haut**.  
  
6.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet ctlClockLib, puis cliquez sur **Propriétés**.  
  
7.  Sous l’onglet **Signature**, sélectionnez **Signer l’assembly**. Dans la zone **Choisir un fichier de clé de nom fort**, cliquez sur **\<parcourir\>** et accédez au fichier key.snk dans le dossier du projet **MyToolWindowPackageUC**.  
  
8.  Compilez le programme et vérifiez l’absence d’erreurs. Cette étape inscrit le VSPackage et sa fenêtre Outil auprès de Visual Studio.  
  
9. Appuyez sur F5 pour ouvrir une instance de Visual Studio dans la ruche expérimentale.  
  
10. Dans la ruche expérimentale Visual Studio, dans le menu **Affichage**, pointez sur **Autres fenêtres** et cliquez sur **MyToolWindow**. La fenêtre Outil apparaît, avec l’affichage de l’heure d’exécution.  
  
## Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)