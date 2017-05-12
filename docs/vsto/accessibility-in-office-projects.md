---
title: "Accessibilit&#233; dans les projets Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "accessibilité (développement Office dans Visual Studio)"
  - "développement Office dans Visual Studio, accessibilité"
  - "ruban (développement Office dans Visual Studio), touches de raccourci"
  - "touches de raccourci (développement Office dans Visual Studio)"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Accessibilit&#233; dans les projets Office
  Microsoft Visual Studio et Microsoft Office incluent de nombreuses fonctionnalités d'accessibilité qui vous permettent de générer des solutions personnalisées qui satisfont aux critères d'accessibilité standard.  Microsoft publie des indications pour l'accessibilité sur le Web.  Pour plus de détails, consultez le site Web [Accessibilité \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=37113).  
  
 Dans la plupart des cas, les projets Office dans Visual Studio répondent aux standards d'accessibilité ou exposent des propriétés que vous pouvez définir pour rendre vos solutions accessibles.  Toutefois, il existe quelques fonctionnalités qui ont une accessibilité limitée.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Accessibilité au moment du design  
  
### Utilisation de touches de raccourci dans les projets au niveau du document  
 Lorsqu'un document Word Microsoft Office ou un classeur Microsoft Office Excel est ouvert dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci.  Par défaut, Visual Studio reçoit toutes les commandes générées par les touches de raccourci mais, si vous souhaitez que Word ou Excel les reçoive lorsque le document a le focus, sélectionnez **Schéma de clavier dynamique** dans la page **Paramètres du clavier** de la boîte de dialogue **Options**.  Pour plus d'informations, consultez [Clavier Microsoft Office Word, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) et [Clavier Microsoft Office Excel, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### Affichage des touches de raccourci pour le ruban dans les projets au niveau du document  
 Lorsqu'un document Word ou un classeur Excel est ouvert dans Visual Studio, vous ne pouvez pas appuyer sur la touche Alt pour consulter les touches de raccourci pour les onglets et les contrôles sur le ruban.  Pour consulter les touches de raccourci pendant que le document ou le classeur est ouvert dans le concepteur, effectuez les étapes ci\-dessous.  
  
##### Pour consulter des touches de raccourci pour les onglets et contrôles du ruban dans le concepteur  
  
1.  Dans Visual Studio, dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Développez le nœud **Outils Office** et sélectionnez **Clavier Microsoft Office Excel** ou **Clavier Microsoft Office Word**, selon le cas.  
  
3.  Sélectionnez **Schéma de clavier dynamique**.  
  
     Un message apparaît indiquant que vous devez redémarrer Visual Studio pour que la modification soit prise en compte.  
  
4.  Cliquez sur **OK**.  
  
5.  Redémarrez Visual Studio et rouvrez votre projet.  
  
6.  Ouvrez le document ou le concepteur de classeurs pour votre projet.  
  
7.  Appuyez sur F6 pour afficher les touches de raccourci pour le ruban.  
  
## Accessibilité au moment de l'exécution  
  
### Contrôles Windows Forms dans les documents Office  
 Les contrôles Windows Forms exposent des propriétés d'accessibilité pour fournir des informations sur le contrôle des aides à l'accessibilité, tels que les lecteurs d'écran.  Vous pouvez tirer parti de ces propriétés d'accessibilité lorsque les contrôles sont sur un document Office dans une personnalisation au niveau du document.  Pour plus d’informations, consultez [Informations d'accessibilité sur les contrôles d'un Windows Form](http://msdn.microsoft.com/library/887dee6f-5059-4d57-957d-7c6fcd4acb10).  
  
 Toutefois, il existe quelques limitations d'accessibilité au moment de l'exécution lorsque les contrôles Windows Forms sont hébergés sur un classeur Excel ou un document Word :  
  
-   Vous ne pouvez pas passer d'un contrôle à un autre à l'aide d'une tabulation.  
  
-   Les contrôles situés sur un document sont désactivés lorsque vous définissez un paramètre de zoom autre que 100 % pour le document.  
  
 Pour plus d'informations sur les limitations des contrôles Windows Forms sur les documents, consultez [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### Volets Actions et volets de tâches personnalisés  
 Lorsqu'un volet Actions ou un volet de tâches personnalisé a le focus, vous accédez aux contrôles de la même façon que dans une application Windows Forms.  Pour déplacer votre curseur entre le volet Actions et le document, vous pouvez appuyer sur **F6**.  
  
 Pour plus d'informations sur les volets Actions et les volets de tâches personnalisés, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md) et [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
### Modes d'affichage  
 Visual Studio présente les limitations suivantes connexes aux modes d'affichage :  
  
-   Les contrôles dans un document Word ou une feuille de calcul Excel sont désactivés lorsque vous modifiez le paramètre de zoom du document en une valeur différente de 100 %.  
  
-   La boîte de dialogue **Nouveau projet** n'affiche pas correctement les contrôles si un utilisateur active l'option d'accessibilité **Utiliser le contraste élevé** de l'ordinateur.  
  
 Vous pouvez utiliser la Loupe pour passer outre ces limitations.  La loupe est un utilitaire d'affichage de Windows qui crée une fenêtre distincte et affiche une partie agrandie de l'écran.  
  
## Voir aussi  
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Accessibilité pour les personnes handicapées](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Fonctionnalités d'accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  