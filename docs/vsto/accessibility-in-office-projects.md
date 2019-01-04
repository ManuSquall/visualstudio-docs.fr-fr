---
title: Accessibilité dans les projets Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32d44c33192d9d4e4fdcf1b8db8cb47102a1df61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833324"
---
# <a name="accessibility-in-office-projects"></a>Accessibilité dans les projets Office

Microsoft Visual Studio et Microsoft Office incluent de nombreuses fonctionnalités d’accessibilité qui vous permettent de créer des solutions personnalisées qui répondent aux critères d’accessibilité standard. Microsoft publie des règles d’accessibilité sur le Web. Pour plus d’informations, consultez le [site Web d’accessibilité](http://go.microsoft.com/fwlink/?LinkID=37113).

Dans la plupart des cas, les projets Office dans Visual Studio répondent à l’accessibilité aux normes ou exposent des propriétés que vous pouvez définir pour rendre vos solutions accessibles. Toutefois, il existe certaines fonctionnalités qui ont une accessibilité limitée.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accessibilité au moment du design

### <a name="use-shortcut-keys-in-document-level-projects"></a>Utiliser les touches de raccourci dans les projets au niveau du document
 Quand un document Microsoft Office Word ou un classeur Microsoft Office Excel est ouvert dans Visual Studio, qu’une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous pouvez rendre Word ou Excel les reçoive lorsque le document a le focus en sélectionnant **schéma de clavier dynamique** sur le **paramètres du clavier** page de la **Options** boîte de dialogue. Pour plus d’informations, consultez [clavier Microsoft Office Word, paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) et [clavier Microsoft Office Excel, les paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Afficher les touches de raccourci pour le ruban dans les projets au niveau du document
 Quand un document Word ou un classeur Excel est ouvert dans Visual Studio, vous ne pouvez pas appuyer sur le **Alt** une touche pour afficher les touches de raccourci pour les onglets et les contrôles sur le ruban. Pour afficher les touches de raccourci pendant que le document ou le classeur est ouvert dans le concepteur, procédez comme suit.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Pour afficher les touches de raccourci pour les commandes et onglets ruban dans le Concepteur

1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Options**.

2.  Développez le **outils Office** nœud, puis sélectionnez **clavier Microsoft Office Excel** ou **clavier Microsoft Office Word**, le cas échéant.

3.  Sélectionnez **schéma de clavier dynamique**.

     Un message s’affiche indiquant que vous devez redémarrer Visual Studio pour que la modification prenne effet.

4.  Cliquez sur **OK**.

5.  Redémarrez Visual Studio et rouvrez votre projet.

6.  Ouvrez le Concepteur de document ou classeur pour votre projet.

7.  Appuyez sur **F6** pour afficher les touches de raccourci pour le ruban.

## <a name="accessibility-at-runtime"></a>Accessibilité lors de l’exécution

### <a name="windows-forms-controls-on-office-documents"></a>Contrôles Windows Forms sur des documents Office
 Contrôles Windows Forms exposent des propriétés d’accessibilité pour fournir des informations sur le contrôle à l’accessibilité, notamment des lecteurs d’écran. Vous pouvez tirer parti de ces propriétés d’accessibilité lorsque les contrôles se trouvent sur un document Office dans une personnalisation au niveau du document. Pour plus d’informations, consultez [fournissent des informations d’accessibilité pour les contrôles sur un formulaire Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Toutefois, il existe certaines limitations d’accessibilité lors de l’exécution lorsque les contrôles Windows Forms sont hébergés sur un classeur Excel ou un document Word :

- Vous ne pouvez pas onglet d’un contrôle à un autre.

- Contrôles sur un document sont désactivés lorsque vous modifiez le paramètre du zoom du document sur n’importe quelle autre que 100 %.

  Pour plus d’informations sur les limitations des contrôles Windows Forms sur des documents, consultez [Limitations of Windows Forms contrôles sur des documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Volets Actions et volets de tâches personnalisés
 Lorsqu’un volet actions ou un volet Office personnalisé a le focus, vous accédez aux contrôles la même façon que vous accédez aux contrôles sur une application Windows Forms. Pour déplacer le curseur entre le volet actions et le document, vous pouvez appuyer sur **F6**.

 Pour plus d’informations sur les volets actions et volets de tâches personnalisés, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md) et [volets de tâches personnalisés](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modes d’affichage

Visual Studio a les limitations suivantes relatives aux modes d’affichage :

- Contrôles sur un document Word ou une feuille de calcul Excel sont désactivés lorsque vous modifiez le paramètre du zoom du document sur n’importe quelle autre que 100 %.

- Le **nouveau projet** boîte de dialogue n’affiche pas correctement les contrôles si un utilisateur modifie les options d’accessibilité de l’ordinateur à **utiliser le contraste élevé**.

Vous pouvez utiliser la loupe pour surmonter ces restrictions. La Loupe est un utilitaire d’affichage de Windows qui crée une fenêtre distincte qui affiche une partie agrandie de l’écran.

## <a name="see-also"></a>Voir aussi

- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)
- [Accessibilité pour les personnes handicapées](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Fonctionnalités d’accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)