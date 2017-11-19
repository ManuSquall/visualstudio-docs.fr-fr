---
title: "Vue d’ensemble du ruban | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 52583bdbf6edf4f2a698bc8662a0faf659841926
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ribbon-overview"></a>Vue d'ensemble du ruban
  Le ruban est une façon d'organiser des commandes associées pour les retrouver plus facilement. Les commandes apparaissent sous forme de contrôles sur le ruban. Les contrôles sont organisés en *groupes* le long d’une bande horizontale sur le bord supérieur d’une fenêtre d’application. Les groupes connexes sont organisés sur les onglets.  
  
 La plupart des fonctionnalités accessibles via les menus et les barres d’outils des versions antérieures de Microsoft Office System sont désormais accessibles à partir du ruban. Pour plus d’informations, consultez l’article technique [vue du développeur de l’Interface utilisateur pour Microsoft Office System 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>Personnalisation du ruban Microsoft Office  
 Pour personnaliser le ruban, ajoutez l'un des éléments suivants du ruban à votre projet Office :  
  
-   **Ruban (Concepteur visuel)**  
  
-   **Ruban (XML)**  
  
 Par exemple, pour personnaliser le ruban Excel, ajoutez un élément Ruban à un projet de complément VSTO Excel.  
  
### <a name="ribbon-visual-designer-item"></a>Élément Ruban (Concepteur visuel)  
 Le **ruban (Concepteur visuel)** élément fournit des outils avancés qui simplifient la conception et le développement d’un ruban personnalisé. Utilisez le **ruban (Concepteur visuel)** pour personnaliser le ruban comme suit :  
  
-   Ajoutez des onglets personnalisés ou intégrés à un ruban.  
  
-   Ajouter des groupes personnalisés à un onglet personnalisé ou intégré.  
  
    > [!NOTE]  
    >  Un groupe ou onglet intégré est celui qui existe déjà sur le ruban d'une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel. Le **connexions** groupe est un groupe intégré sur le **données** onglet.  
  
-   Ajoutez des contrôles personnalisés à un groupe personnalisé.  
  
-   Ajoutez des contrôles personnalisés au mode Backstage.  
  
 Pour plus d’informations sur la façon de personnaliser un ruban à l’aide de la **ruban (Concepteur visuel)** d’élément, consultez [Concepteur de ruban](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Élément Ruban (XML)  
 Utilisez le **ruban (XML)** élément si vous souhaitez personnaliser le ruban d’une façon qui n’est pas pris en charge par le **ruban (Concepteur visuel)** élément. Utilisez le **ruban (XML)** pour personnaliser le ruban comme suit :  
  
-   Ajouter *intégrés* groupes à un onglet personnalisé ou un onglet intégré.  
  
-   Ajoutez des contrôles intégrés à un groupe personnalisé.  
  
-   Ajoutez un code personnalisé pour substituer les gestionnaires d'événements des contrôles intégrés.  
  
-   Personnaliser la barre d'outils Accès rapide  
  
-   Partager une personnalisation de ruban entre le complément VSTO en utilisant un ID qualifié.  
  
 Pour plus d’informations sur la façon de personnaliser le ruban à l’aide de la **ruban (XML)** d’élément, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportation d'un ruban à partir du Concepteur de ruban vers Ruban XML  
 Si vous créez un ruban à l’aide du Concepteur de ruban et décidez ensuite que vous souhaitez personnaliser le ruban d’une façon qui le **ruban (Concepteur visuel)** élément ne prend pas en charge, vous pouvez exporter le ruban en XML.  
  
 Visual Studio crée automatiquement un **ruban (XML)** et remplit le fichier XML du ruban avec des éléments et attributs pour chaque contrôle sur le ruban.  
  
 Pas toutes les propriétés qui se trouvent dans le **propriétés** fenêtre du Concepteur de ruban sont transférées vers le fichier XML du ruban.  Par exemple, Visual Studio n’exporte pas la valeur de la **Image** ou **texte** propriété. La raison en est que vous devez créer une méthode de rappel dans le fichier de code Ruban du projet exporté pour assigner une image ou définir le texte d'un contrôle. Visual Studio ne génère pas automatiquement les méthodes de rappel dans le cadre du processus d'exportation.  
  
 En outre, les valeurs de propriété par défaut inchangées n'apparaissent pas dans le fichier XML du ruban.  
  
 Pour plus d’informations sur la façon d’exporter le ruban en XML, consultez [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="updating-the-code"></a>Mise à jour du code  
 Un nouveau fichier de code du ruban est ajouté à **l’Explorateur de solutions**. Ce fichier contient la classe Ribbon XML. Vous devez créer des méthodes de rappel dans la région `Ribbon Callbacks` de cette classe pour gérer les actions de l'utilisateur, telles qu'un clic sur un bouton. Déplacez votre code des gestionnaires d'événements vers les méthodes de rappel et modifiez le code pour qu'il fonctionne avec le modèle de programmation de l'extensibilité du ruban (RibbonX). Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).  
  
 Vous devez également ajouter le code pour le `ThisAddIn`, `ThisWorkbook`, ou `ThisDocument` classe qui substitue la méthode CreateRibbonExtensibilityObject et retourne la classe Ribbon XML à l’application Office.  
  
 Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>Ajout de plusieurs éléments de ruban à un projet  
 Vous pouvez ajouter plusieurs éléments de ruban à un seul projet. Cela est utile si vous souhaitez effectuer l’une des deux tâches suivantes :  
  
-   Créer des rubans pour Outlook *inspecteurs*. Pour plus d’informations, consultez [personnalisation d’un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un inspecteur est une fenêtre qui s’ouvre lorsque les utilisateurs effectuent certaines tâches, telles que la création d’un message électronique.  
  
-   Sélectionnez le ruban à afficher au moment de l'exécution.  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>Sélectionnez les rubans à afficher au moment de l'exécution.  
 Comme un projet peut contenir plusieurs rubans, vous pouvez sélectionner le ruban à afficher au moment de l'exécution.  
  
 Pour sélectionner un ruban à afficher au moment de l’exécution, substituez la méthode CreateRibbonExtensibilityObject dans le `ThisAddin`, `ThisWorkbook`, ou `ThisDocument` classe de votre projet et retournez le ruban que vous souhaitez afficher. L'exemple suivant vérifie la valeur d'un champ nommé `myCondition` et retourne le ruban approprié.  
  
> [!NOTE]  
>  La syntaxe utilisée dans cet exemple retourne un ruban qui a été créé à l’aide de la **ruban (Concepteur visuel)** élément. La syntaxe de retour d’un ruban qui est créé en utilisant un **ruban (XML)** élément est légèrement différent. Pour plus d’informations sur le renvoi d’un **ruban (XML)** d’élément, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
 Ajoutez le code suivant :  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour démarrer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)|Montre comment personnaliser le ruban d’une application Microsoft Office, ajoutez un **ruban (Concepteur visuel)** ou **ruban (XML)** élément à un projet Office.|  
|[Concepteur de ruban](../vsto/ribbon-designer.md)|Décrit comment vous pouvez utiliser le Concepteur de ruban pour ajouter des onglets, groupes et contrôles personnalisés au ruban d'une application Microsoft Office.|  
|[Procédure pas à pas : création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l'aide du Concepteur de ruban. Vous pouvez utiliser le Concepteur de ruban pour ajouter et positionner des contrôles sur l'onglet personnalisé.|  
|[Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)|Fournit une vue d'ensemble du modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l'exécution.|  
|[Procédure pas à pas : mise à jour des contrôles d’un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles d'un ruban après le chargement du ruban dans l'application Office.|  
|[Personnalisation d’un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office Outlook.|  
|[Personnalisation d’un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office InfoPath.|  
|[Accès au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)|Montre comment afficher, masquer et modifier le ruban et permettre aux utilisateurs d’exécuter le code à partir de contrôles dans un volet de tâches personnalisé, un volet Actions ou une zone de formulaire Outlook.|  
|[Guide pratique pour modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Montre comment modifier l'ordre des onglets d'un ruban.|  
|[Guide pratique pour personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|Montre comment ajouter des groupes et des contrôles à un onglet intégré.|  
|[Guide pratique pour ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Montre comment ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier**.|  
|[Guide pratique pour ajouter un lanceur de boîte de dialogue à un groupe de ruban](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Montre comment ajouter un lanceur de boîte de dialogue à un groupe de ruban|  
|[Guide pratique pour exporter un ruban à partir du Concepteur de ruban vers l’élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Montre comment personnaliser le ruban de façon avancée en exportant le ruban du Concepteur vers Ruban XML.|  
|[Élément XML Ribbon](../vsto/ribbon-xml.md)|Explique comment vous pouvez personnaliser un ruban en utilisant Ribbon XML.|  
|[Procédure pas à pas : création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l’aide de la **ruban (XML)** élément.|  
  
  