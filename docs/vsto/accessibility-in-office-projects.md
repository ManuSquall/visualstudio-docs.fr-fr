---
title: Accessibilité dans les projets Office
description: Découvrez comment Microsoft Office projets incluent de nombreuses fonctionnalités d’accessibilité qui vous permettent de créer des solutions personnalisées qui répondent aux exigences d’accessibilité standard.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de877ccc2d2a036bf03b0888a7edf455b17788a4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847362"
---
# <a name="accessibility-in-office-projects"></a>Accessibilité dans les projets Office

Microsoft Visual Studio et Microsoft Office incluent de nombreuses fonctionnalités d’accessibilité qui vous permettent de créer des solutions personnalisées répondant aux exigences standard en matière d’accessibilité. Microsoft publie des instructions pour l’accessibilité sur le Web. Pour plus d’informations, consultez le [site Web d’accessibilité](https://www.microsoft.com/accessibility/).

Dans la plupart des cas, les projets Office dans Visual Studio répondent aux normes d’accessibilité ou exposent des propriétés que vous pouvez définir pour rendre vos solutions accessibles. Toutefois, certaines fonctionnalités ont une accessibilité limitée.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accessibilité au moment du design

### <a name="use-shortcut-keys-in-document-level-projects"></a>Utiliser les touches de raccourci dans les projets au niveau du document
 Quand un document Word Microsoft Office ou un classeur Excel Microsoft Office est ouvert dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous pouvez faire en sorte que Word ou Excel les reçoit lorsque le document a le focus en sélectionnant **schéma de clavier dynamique** dans la page **paramètres du clavier** de la boîte de dialogue **options** . Pour plus d’informations, consultez [Microsoft Office clavier Word, Microsoft Office paramètres du clavier, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) et [Microsoft Office clavier Excel, Microsoft Office paramètres du clavier, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Afficher les touches de raccourci du ruban dans les projets au niveau du document
 Quand un document Word ou un classeur Excel est ouvert dans Visual Studio, vous ne pouvez pas appuyer sur la touche **ALT** pour afficher les touches de raccourci des onglets et des contrôles sur le ruban. Pour afficher les touches de raccourci lorsque le document ou le classeur est ouvert dans le concepteur, procédez comme suit.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Pour afficher les touches de raccourci des contrôles et onglets du ruban dans le concepteur

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **options**.

2. Développez le nœud **Outils Office** , puis sélectionnez **Microsoft Office clavier Excel** ou **Microsoft Office clavier Word**, selon le cas.

3. Sélectionnez **schéma de clavier dynamique**.

     Un message s’affiche, indiquant que vous devez redémarrer Visual Studio pour que la modification prenne effet.

4. Cliquez sur **OK**.

5. Redémarrez Visual Studio, puis rouvrez votre projet.

6. Ouvrez le document ou le concepteur de classeurs pour votre projet.

7. Appuyez sur **F6** pour afficher les touches de raccourci du ruban.

## <a name="accessibility-at-run-time"></a>Accessibilité au moment de l’exécution

### <a name="windows-forms-controls-on-office-documents"></a>Contrôles de Windows Forms sur les documents Office
 Les contrôles Windows Forms exposent des propriétés d’accessibilité pour fournir des informations sur le contrôle aux aides à l’accessibilité, telles que les lecteurs d’écran. Vous pouvez tirer parti de ces propriétés d’accessibilité lorsque les contrôles sont sur un document Office dans une personnalisation au niveau du document. Pour plus d’informations, consultez [fournir des informations d’accessibilité pour les contrôles d’un Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Toutefois, il existe des limitations d’accessibilité au moment de l’exécution lorsque Windows Forms contrôles sont hébergés sur un classeur Excel ou un document Word :

- Vous ne pouvez pas effectuer une tabulation d’un contrôle à un autre.

- Les contrôles d’un document sont désactivés lorsque vous modifiez le paramètre de zoom du document sur une valeur autre que 100%.

  Pour plus d’informations sur les limitations des contrôles de Windows Forms sur les documents, consultez [limitations des contrôles de Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Volets actions et volets de tâches personnalisés
 Quand un volet actions ou un volet de tâches personnalisé a le focus, vous accédez aux contrôles de la même façon que vous accédez aux contrôles d’une application Windows Forms. Pour déplacer le curseur entre le volet Actions et le document, vous pouvez appuyer sur **F6**.

 Pour plus d’informations sur les volets actions et les volets de tâches personnalisés, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md) et [volets de tâches personnalisés](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modes d’affichage

Visual Studio présente les limitations suivantes en ce qui concerne les modes d’affichage :

- Les contrôles sur un document Word ou une feuille de calcul Excel sont désactivés lorsque vous modifiez le paramètre de zoom du document sur une valeur autre que 100%.

- La boîte de dialogue **nouveau projet** n’affiche pas correctement les contrôles si un utilisateur modifie les options d’accessibilité de l’ordinateur pour **utiliser contraste élevé**.

Vous pouvez utiliser la loupe pour surmonter ces limitations. La loupe est un utilitaire d’affichage de Windows qui crée une fenêtre distincte qui affiche une partie agrandie de l’écran.

## <a name="see-also"></a>Voir aussi

- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Accessibilité pour les personnes handicapées](../ide/reference/accessibility-features-of-visual-studio.md)
- [Fonctionnalités d’accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)