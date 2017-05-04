---
title: "Vue d&#39;ensemble du ruban | Microsoft Docs"
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
  - "ruban personnalisé, rubans multiples"
  - "personnaliser le ruban, rubans multiples"
  - "ruban (développement Office dans Visual Studio)"
  - "ruban (développement Office dans Visual Studio), à propos du ruban"
  - "ruban (développement Office dans Visual Studio), rubans multiples"
  - "barres d'outils (développement Office dans Visual Studio)"
  - "barres d'outils (développement Office dans Visual Studio), ruban"
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Vue d&#39;ensemble du ruban
  Le ruban est une façon d'organiser des commandes associées pour les retrouver plus facilement.  Les commandes apparaissent sous forme de contrôles sur le ruban.  Les contrôles sont organisés en *groupes* le long d'une bande horizontale en haut d'une fenêtre d'application.  Les groupes connexes sont organisés sur les onglets.  
  
 La plupart des fonctionnalités accessibles via les menus et les barres d'outils des versions antérieures de Microsoft Office System sont désormais accessibles à partir du ruban.  Pour plus d'informations, consultez l'article technique[Présentation orientée développeur de l'interface utilisateur pour Microsoft Office System 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Personnalisation du ruban Microsoft Office  
 Pour personnaliser le ruban, ajoutez l'un des éléments suivants du ruban à votre projet Office :  
  
-   **Ruban \(Concepteur visuel\)**  
  
-   **Ruban \(XML\)**  
  
 Par exemple, pour personnaliser le ruban Excel, ajoutez un élément Ruban à un projet de complément VSTO Excel.  
  
### Élément Ruban \(Concepteur visuel\)  
 L'élément **Ruban \(Concepteur visuel\)** fournit des outils avancés qui rendent plus faciles la conception et le développement d'un ruban personnalisé.  Utilisez le **Ruban \(Concepteur visuel\)** pour personnaliser le ruban comme suit :  
  
-   Ajoutez des onglets personnalisés ou intégrés à un ruban.  
  
-   Ajouter des groupes personnalisés à un onglet personnalisé ou intégré.  
  
    > [!NOTE]  
    >  Un groupe ou onglet intégré est celui qui existe déjà sur le ruban d'une application Microsoft Office.  Par exemple, l'onglet **Données** est un onglet intégré dans Excel.  Le groupe **Connexions** est un groupe intégré de l'onglet **Données**.  
  
-   Ajoutez des contrôles personnalisés à un groupe personnalisé.  
  
-   Ajoutez des contrôles personnalisés au mode Backstage.  
  
 Pour plus d'informations sur la personnalisation d'un ruban à l'aide de l'élément **Ruban \(Concepteur visuel\)**, consultez [Concepteur de ruban](../vsto/ribbon-designer.md).  
  
### Élément Ruban \(XML\)  
 Utilisez l'élément **Ruban \(XML\)** si vous souhaitez personnaliser le ruban d'une façon qui n'est pas prise en charge par l'élément **Ruban \(Concepteur visuel\)**.  Utilisez l'élément **Ruban \(Concepteur visuel\)** pour personnaliser le ruban comme suit :  
  
-   Ajoutez des groupes *intégrés* à un onglet personnalisé ou intégré.  
  
-   Ajoutez des contrôles intégrés à un groupe personnalisé.  
  
-   Ajoutez un code personnalisé pour substituer les gestionnaires d'événements des contrôles intégrés.  
  
-   Personnaliser la barre d'outils Accès rapide  
  
-   Partager une personnalisation de ruban entre le complément VSTO en utilisant un ID qualifié.  
  
 Pour plus d'informations sur la personnalisation d'un ruban à l'aide de l'élément **Ruban \(XML\)**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
## Exportation d'un ruban à partir du Concepteur de ruban vers Ruban XML  
 Si vous créez un ruban en utilisant le Concepteur de ruban et décidez ensuite que vous souhaitez personnaliser le ruban d'une façon que l'élément **Ruban \(Concepteur visuel\)** ne prend pas en charge, vous pouvez exporter le ruban vers XML.  
  
 Visual Studio crée automatiquement un **Ruban \(XML\)** et remplit le fichier Ruban XML avec les éléments et les attributs de chaque contrôle sur le ruban.  
  
 Toutes les propriétés qui  se trouvent pas dans la fenêtre **Propriétés** du Concepteur de ruban ne sont pas transférées vers le fichier XML du ruban.  Par exemple, Visual Studio n'exporte pas la valeur de la propriété **Image** ou **Texte**.  La raison en est que vous devez créer une méthode de rappel dans le fichier de code Ruban du projet exporté pour assigner une image ou définir le texte d'un contrôle.  Visual Studio ne génère pas automatiquement les méthodes de rappel dans le cadre du processus d'exportation.  
  
 En outre, les valeurs de propriété par défaut inchangées n'apparaissent pas dans le fichier XML du ruban.  
  
 Pour plus d'informations sur la façon d'exporter le ruban vers XML, consultez[Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### Mise à jour du code  
 Un nouveau fichier de code de ruban est ajouté à l'**Explorateur de solutions**.  Ce fichier contient la classe Ribbon XML.  Vous devez créer des méthodes de rappel dans la région `Ribbon Callbacks` de cette classe pour gérer les actions de l'utilisateur, telles qu'un clic sur un bouton.  Déplacez votre code des gestionnaires d'événements vers les méthodes de rappel et modifiez le code pour qu'il fonctionne avec le modèle de programmation de l'extensibilité du ruban \(RibbonX\).  Pour plus d'informations, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
 Vous devez également ajouter le code à la classe `ThisAddIn`, `ThisWorkbook` ou `ThisDocument` qui remplace la méthode CreateRibbonExtensibilityObject et retourne la classe Ribbon XML à l'application Office.  
  
 Pour plus d'informations, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
## Ajout de plusieurs éléments de ruban à un projet  
 Vous pouvez ajouter plusieurs éléments de ruban à un seul projet.  Cela est utile si vous souhaitez effectuer l'une des deux tâches suivantes :  
  
-   Créer des rubans pour les *Inspecteurs* Outlook.  Pour plus d'informations, consultez [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un inspecteur est une fenêtre qui s'ouvre lorsque les utilisateurs effectuent certaines tâches, telles que la création d'un message électronique.  
  
-   Sélectionnez le ruban à afficher au moment de l'exécution.  
  
### Sélectionnez les rubans à afficher au moment de l'exécution.  
 Comme un projet peut contenir plusieurs rubans, vous pouvez sélectionner le ruban à afficher au moment de l'exécution.  
  
 Pour sélectionner un ruban à afficher au moment de l'exécution, substituez la méthode CreateRibbonExtensibilityObject de la classe`ThisAddin`, `ThisWorkbook` ou `ThisDocument` de votre projet et retournez le ruban que vous souhaitez afficher.  L'exemple suivant vérifie la valeur d'un champ nommé `myCondition` et retourne le ruban approprié.  
  
> [!NOTE]  
>  La syntaxe utilisée dans cet exemple retourne un ruban qui a été créé à l'aide de l'élément **Ruban \(Concepteur visuel\)**.  La syntaxe de retour d'un ruban créé en utilisant un élément **Ruban \(XML\)** est légèrement différente.  Pour plus d'informations sur le retour d'un élément **Ruban \(XML\)**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
 Ajoutez le code suivant :  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
### Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)|Montre comment personnaliser le ruban d'une application Microsoft Office, ajouter un **Ruban \(Concepteur visuel\)** ou un élément **Ruban \(XML\)** à un projet Office.|  
|[Concepteur de ruban](../vsto/ribbon-designer.md)|Décrit comment vous pouvez utiliser le Concepteur de ruban pour ajouter des onglets, groupes et contrôles personnalisés au ruban d'une application Microsoft Office.|  
|[Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l'aide du Concepteur de ruban.  Vous pouvez utiliser le Concepteur de ruban pour ajouter et positionner des contrôles sur l'onglet personnalisé.|  
|[Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)|Fournit une vue d'ensemble du modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l'exécution.|  
|[Procédure pas à pas : mise à niveau des contrôles sur un ruban au moment de l'exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles d'un ruban après le chargement du ruban dans l'application Office.|  
|[Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office Outlook.|  
|[Personnalisation d'un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office InfoPath.|  
|[Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)|Montre comment afficher, masquer et modifier le ruban et permettre aux utilisateurs d'exécuter le code à partir de contrôles dans un volet de tâches personnalisé, un volet Actions ou une zone de formulaire Outlook.|  
|[Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Montre comment modifier l'ordre des onglets d'un ruban.|  
|[Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|Montre comment ajouter des groupes et des contrôles à un onglet intégré.|  
|[Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Montre comment ajouter des contrôles au menu qui s'ouvre lorsque vous cliquez sur **Fichier**.|  
|[Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Montre comment ajouter un lanceur de boîte de dialogue à un groupe de ruban|  
|[Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Montre comment personnaliser le ruban de façon avancée en exportant le ruban du Concepteur vers Ruban XML.|  
|[Élément XML Ribbon](../vsto/ribbon-xml.md)|Explique comment vous pouvez personnaliser un ruban en utilisant Ribbon XML.|  
|[Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l'aide de l'élément  **Ruban \(XML\)**.|  
  
  