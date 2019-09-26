---
title: Vue d’ensemble du ruban
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5067a52fb9d6a0b6d8991b68a2fce8cdbae987c9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255942"
---
# <a name="ribbon-overview"></a>Vue d’ensemble du ruban
  Le ruban est un moyen d’organiser les commandes associées afin qu’elles soient plus faciles à trouver. Les commandes apparaissent sous forme de contrôles sur le ruban. Les contrôles sont organisés en *groupes* le long d’une bande horizontale au bord supérieur d’une fenêtre d’application. Les groupes connexes sont organisés sur les onglets.

 Vous pouvez désormais accéder à la plupart des fonctionnalités accessibles à l’aide des menus et des barres d’outils dans les versions antérieures du système Microsoft Office à l’aide du ruban. Pour plus d’informations, consultez l’article technique [Developer Overview of the user interface for the 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personnaliser le ruban Microsoft Office
 Pour personnaliser le ruban, ajoutez l’un des éléments de ruban suivants à votre projet Office :

- **Ruban (concepteur visuel)**

- **Ruban (XML)**

  Par exemple, pour personnaliser le ruban Excel, ajoutez un élément Ruban à un projet de complément VSTO Excel.

### <a name="ribbon-visual-designer-item"></a>Élément Ruban (concepteur visuel)
 L’élément **Ruban (concepteur visuel)** fournit des outils avancés qui facilitent la conception et le développement d’un ruban personnalisé. Utilisez l’élément **Ruban (concepteur visuel)** pour personnaliser le ruban comme suit :

- Ajoutez des onglets personnalisés ou intégrés à un ruban.

- Ajouter des groupes personnalisés à un onglet personnalisé ou intégré.

  > [!NOTE]
  > Un groupe ou un onglet intégré est un groupe qui existe déjà sur le ruban d’une application Microsoft Office. Par exemple, l’onglet **données** est un onglet intégré dans Excel. Le groupe **connexions** est un groupe intégré sur l’onglet **données** .

- Ajoutez des contrôles personnalisés à un groupe personnalisé.

- Ajoutez des contrôles personnalisés au mode Backstage.

  Pour plus d’informations sur la personnalisation d’un ruban à l’aide de l’élément **Ruban (concepteur visuel)** , consultez [Concepteur de ruban](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Élément Ruban (XML)
 Utilisez l’élément **Ruban (XML)** si vous souhaitez personnaliser le ruban d’une façon qui n’est pas prise en charge par l’élément **Ruban (concepteur visuel)** . Utilisez l’élément **Ruban (XML)** pour personnaliser le ruban comme suit :

- Ajoutez des groupes *prédéfinis* à un onglet personnalisé ou à un onglet intégré.

- Ajoutez des contrôles intégrés à un groupe personnalisé.

- Ajoutez un code personnalisé pour substituer les gestionnaires d'événements des contrôles intégrés.

- Personnaliser la barre d'outils Accès rapide

- Partager une personnalisation de ruban entre le complément VSTO en utilisant un ID qualifié.

  Pour plus d’informations sur la personnalisation du ruban à l’aide de l’élément **Ruban (XML)** , consultez [Ruban XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exporter un ruban à partir du concepteur de ruban vers le ruban XML
 Si vous créez un ruban à l’aide du concepteur de ruban, puis décidez que vous souhaitez personnaliser le ruban de manière non prise en charge par l’élément **Ruban (concepteur visuel)** , vous pouvez exporter le ruban vers XML.

 Visual Studio crée automatiquement un élément **Ruban (XML)** et remplit le fichier XML du ruban avec des éléments et des attributs pour chaque contrôle sur le ruban.

 Toutes les propriétés figurant dans la fenêtre **Propriétés** du concepteur de ruban ne sont pas transférées vers le fichier XML du ruban.  Par exemple, Visual Studio n’exporte pas la valeur de la propriété **image** ou **Text** . La raison en est que vous devez créer une méthode de rappel dans le fichier de code Ruban du projet exporté pour assigner une image ou définir le texte d'un contrôle. Visual Studio ne génère pas automatiquement les méthodes de rappel dans le cadre du processus d'exportation.

 En outre, les valeurs de propriété par défaut inchangées n'apparaissent pas dans le fichier XML du ruban.

 Pour plus d’informations sur l’exportation du ruban vers XML, consultez [procédure : Exporter un ruban à partir du concepteur de ruban vers](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)le ruban XML.

### <a name="update-the-code"></a>Mettre à jour le code
 Un nouveau fichier de code du ruban est ajouté à **Explorateur de solutions**. Ce fichier contient la classe Ribbon XML. Vous devez créer des méthodes de rappel dans la région `Ribbon Callbacks` de cette classe pour gérer les actions de l'utilisateur, telles qu'un clic sur un bouton. Déplacez votre code des gestionnaires d'événements vers les méthodes de rappel et modifiez le code pour qu'il fonctionne avec le modèle de programmation de l'extensibilité du ruban (RibbonX). Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).

 Vous devez également ajouter le code à la classe `ThisAddIn`, `ThisWorkbook` ou `ThisDocument` qui remplace la méthode `CreateRibbonExtensibilityObject` et retourne la classe Ribbon XML à l'application Office.

 Pour plus d'informations, consultez [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Ajouter plusieurs éléments de ruban à un projet
 Vous pouvez ajouter plusieurs éléments de ruban à un seul projet. Cela est utile si vous souhaitez effectuer l'une des deux tâches suivantes :

- Créer des rubans pour les *inspecteurs*Outlook. Pour plus d’informations, consultez [personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Un inspecteur est une fenêtre qui s'ouvre lorsque les utilisateurs effectuent certaines tâches, telles que la création d'un message électronique.

- Sélectionnez le ruban à afficher au moment de l’exécution.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Sélectionner les rubans à afficher au moment de l’exécution
 Étant donné qu’un projet peut contenir plusieurs rubans, vous pouvez sélectionner le ruban à afficher au moment de l’exécution.

 Pour sélectionner un ruban à afficher au moment de `CreateRibbonExtensibilityObject` l’exécution, substituez la méthode dans la `ThisAddin`classe `ThisDocument` , `ThisWorkbook`ou de votre projet et retournez le ruban que vous souhaitez afficher. L’exemple suivant vérifie la valeur d’un champ nommé `myCondition` et retourne le ruban approprié.

> [!NOTE]
> La syntaxe utilisée dans cet exemple retourne un ruban qui a été créé à l’aide de l’élément **Ruban (concepteur visuel)** . La syntaxe permettant de retourner un ruban créé à l’aide d’un élément **Ruban (XML)** est légèrement différente. Pour plus d'informations sur le retour d'un élément **Ruban (XML)** , consultez [Ruban XML](../vsto/ribbon-xml.md).

 Ajoutez le code suivant :

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Guide pratique pour Prise en main de la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)|Montre comment personnaliser le ruban d’une application Microsoft Office, ajouter un **Ruban (concepteur visuel)** ou un élément **Ruban (XML)** à un projet Office.|
|[Concepteur de ruban](../vsto/ribbon-designer.md)|Décrit comment vous pouvez utiliser le concepteur de ruban pour ajouter des onglets, des groupes et des contrôles personnalisés au ruban d’une application Microsoft Office.|
|[Procédure pas à pas : Créer un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l'aide du Concepteur de ruban. Vous pouvez utiliser le Concepteur de ruban pour ajouter et positionner des contrôles sur l'onglet personnalisé.|
|[Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)|Fournit une vue d'ensemble du modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l'exécution.|
|[Procédure pas à pas : Mettre à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles d’un ruban après le chargement du ruban dans l’application Office.|
|[Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office Outlook.|
|[Personnaliser un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fournit des conseils pour la personnalisation du ruban dans Microsoft Office InfoPath.|
|[Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)|Montre comment afficher, masquer et modifier le ruban, et permettre aux utilisateurs d’exécuter le code à partir de contrôles dans un volet de tâches personnalisé, un volet actions ou une zone de formulaire Outlook.|
|[Guide pratique pour Modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Montre comment modifier l’ordre des onglets sur un ruban.|
|[Guide pratique pour Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|Montre comment ajouter des groupes et des contrôles à un onglet intégré.|
|[Guide pratique pour Ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Montre comment ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier**.|
|[Guide pratique pour Ajouter un lanceur de boîte de dialogue à un groupe de ruban](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Montre comment ajouter un lanceur de boîte de dialogue à n’importe quel groupe sur un ruban.|
|[Guide pratique pour Exporter un ruban à partir du concepteur de ruban vers le ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Montre comment personnaliser le ruban de manière avancée en exportant le ruban du concepteur vers le ruban XML.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Explique comment personnaliser un ruban à l’aide du ruban XML.|
|[Procédure pas à pas : Créer un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Montre comment créer un onglet de ruban personnalisé à l’aide de l’élément **Ruban (XML)** .|
