---
title: Accéder au ruban au moment de l’exécution
description: Vous pouvez écrire du code pour afficher, masquer et modifier le ruban, et permettre aux utilisateurs d'exécuter ce code à partir de contrôles dans un volet de tâches personnalisé, un volet Actions ou une zone de formulaire Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20c9a54d2fa352c51d5ae5383f5c5b7861e0fdf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825223"
---
# <a name="access-the-ribbon-at-run-time"></a>Accéder au ruban au moment de l’exécution
  Vous pouvez écrire du code pour afficher, masquer et modifier le ruban, et permettre aux utilisateurs d'exécuter ce code à partir de contrôles dans un volet de tâches personnalisé, un volet Actions ou une zone de formulaire Outlook.

 Vous pouvez accéder au ruban à l'aide de la classe `Globals`. Pour les projets Outlook, vous pouvez accéder au ruban qui s'affiche dans une fenêtre de l'explorateur ou de l'inspecteur Outlook spécifique.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Accéder au ruban à l’aide de la classe Globals
 Vous pouvez utiliser la classe `Globals` pour accéder au ruban dans un projet au niveau du document ou un projet de complément VSTO, où que vous soyez dans le projet.

 Pour plus d’informations sur la `Globals` classe, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

 L'exemple suivant utilise la classe `Globals` pour accéder à un ruban personnalisé nommé `Ribbon1` et définir le texte qui apparaît dans une zone de liste modifiable du ruban sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet4":::

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Accéder à une collection de rubans qui s’affichent dans une fenêtre d’inspecteur Outlook spécifique
 Vous pouvez accéder à une collection de rubans qui s’affichent dans les *inspecteurs* Outlook. Un inspecteur est une fenêtre qui s’ouvre dans Outlook quand les utilisateurs effectuent certaines tâches, telles que la création d’un message électronique. Pour accéder au ruban d'une fenêtre d'inspecteur, appelez la propriété `Ribbons` de la classe `Globals` et passez-lui un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui représente l'inspecteur.

 L’exemple suivant obtient la collection de rubans de l’inspecteur actif. Cet exemple accède ensuite à un ruban nommé `Ribbon1` et définit le texte qui s'affiche dans une zone de liste modifiable du ruban sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet5":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet5":::

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Accéder à une collection de rubans qui s’affichent pour un explorateur Outlook spécifique
 Vous pouvez accéder à une collection de rubans qui s’affichent dans un *Explorateur* Outlook. Un explorateur est l'interface utilisateur principale de l'application pour une instance d'Outlook. Pour accéder au ruban d'une fenêtre d'explorateur, appelez la propriété `Ribbons` de la classe `Globals` et passez-lui un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> qui représente l'explorateur.

 L'exemple suivant obtient la collection de rubans de l'explorateur actif. Cet exemple accède ensuite à un ruban nommé `Ribbon1` et définit le texte qui s'affiche dans une zone de liste modifiable du ruban sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : mettre à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
