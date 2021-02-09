---
title: Personnaliser un ruban pour Outlook
description: Découvrez que lorsque vous personnalisez le ruban dans Microsoft Office Outlook, vous devez prendre en compte l’emplacement où votre ruban personnalisé apparaîtra dans l’application.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c12e92ef77130ca2d9b55ccec737f37c73396c2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849877"
---
# <a name="customize-a-ribbon-for-outlook"></a>Personnaliser un ruban pour Outlook
  Quand vous personnalisez le ruban dans Microsoft Office Outlook, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application. Outlook affiche le ruban dans l'interface utilisateur principale de l'application et dans les fenêtres qui s'ouvrent lorsque les utilisateurs effectuent certaines tâches, telles que la création de messages électroniques. Ces fenêtres d'application sont appelées inspecteurs.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Ajouter un ruban personnalisé à l’interface utilisateur principale de l’application
 L'interface utilisateur de l'application principale dans Outlook est appelée l'Explorateur. Si vous utilisez l’élément **Ruban (concepteur visuel)** , vous pouvez ajouter un ruban à l’Explorateur en cliquant sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés** , puis en sélectionnant **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Affecter un ruban à un inspecteur
 Pour identifier l'inspecteur que vous souhaitez personnaliser, vous spécifiez le type de ruban qui correspond à la classe de message de l'inspecteur.

 Si vous utilisez l’élément **Ruban (concepteur visuel)** , cliquez sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés** , puis sélectionnez un ou plusieurs ID de ruban dans la liste des valeurs.

 Vous pouvez ajouter plusieurs rubans à un projet. Si plusieurs rubans partagent un ID de ruban, substituez la méthode `CreateRibbonExtensibilityObject` de la classe `ThisAddin` de votre projet pour spécifier le ruban à afficher au moment de l'exécution. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md). Pour plus d’informations sur chaque type de ruban, consultez l’article technique [personnaliser le ruban dans Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Spécifier le type de ruban à l’aide du ruban XML
 Si vous utilisez l’élément **Ruban (XML)** , vérifiez la valeur du paramètre *ribbonID* dans la <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> méthode et retournez le ruban approprié.

 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban. Le paramètre *ribbonID* est une chaîne qui identifie l’Explorateur ou un type spécifique d’inspecteur. Pour obtenir la liste complète des valeurs possibles du paramètre *ribbonID* , consultez l’article technique [personnaliser le ruban dans Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans l' inspecteur `Microsoft.Outlook.Mail.Compose`. Il s'agit de l'inspecteur qui s'affiche lorsqu'un utilisateur crée un message électronique. Le ruban à afficher est spécifié dans la `GetResourceText()` méthode, qui est générée dans la classe **du ruban** . Pour plus d’informations sur la classe **Ribbon** , consultez [Ruban XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
