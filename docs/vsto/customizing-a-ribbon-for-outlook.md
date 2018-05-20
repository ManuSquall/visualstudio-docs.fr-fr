---
title: Personnaliser un ruban pour Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef1c72d5c24c70a539b909e8d338a235ceb52a49
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="customize-a-ribbon-for-outlook"></a>Personnaliser un ruban pour Outlook
  Quand vous personnalisez le ruban dans Microsoft Office Outlook, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application. Outlook affiche le ruban dans l'interface utilisateur principale de l'application et dans les fenêtres qui s'ouvrent lorsque les utilisateurs effectuent certaines tâches, telles que la création de messages électroniques. Ces fenêtres d'application sont appelées inspecteurs.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : utiliser le Concepteur de ruban pour personnaliser le ruban dans Outlook ?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Ajouter un ruban personnalisé à l’application principale de l’interface utilisateur  
 L'interface utilisateur de l'application principale dans Outlook est appelée l'Explorateur. Si vous utilisez la **ruban (Concepteur visuel)** élément, vous pouvez ajouter un ruban à l’Explorateur en cliquant sur le **RibbonType** propriété du ruban dans le **propriétés** fenêtre, puis en sélectionnant **Microsoft.Outlook.Explorer**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Affecter un ruban à un inspecteur  
 Pour identifier l'inspecteur que vous souhaitez personnaliser, vous spécifiez le type de ruban qui correspond à la classe de message de l'inspecteur.  
  
 Si vous utilisez la **ruban (Concepteur visuel)** , cliquez sur le **RibbonType** propriété du ruban dans le **propriétés** fenêtre et puis sélectionnez un ou plusieurs ID à partir du ruban la liste de valeurs.  
  
 Vous pouvez ajouter plusieurs rubans à un projet. Si plusieurs rubans partagent un ID de ruban, substituez la méthode `CreateRibbonExtensibilityObject` de la classe `ThisAddin` de votre projet pour spécifier le ruban à afficher au moment de l'exécution. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md). Pour plus d’informations sur chaque type de ruban, consultez l’article technique [personnaliser le ruban dans Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Spécifier le type de ruban à l’aide du ruban XML  
 Si vous utilisez la **ruban (XML)** d’élément, vérifiez la valeur de la *ribbonID* paramètre dans le <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> méthode et retournez le ruban approprié.  
  
 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban. Le *ribbonID* paramètre est une chaîne qui identifie l’Explorateur ou un type spécifique d’inspecteur. Pour obtenir la liste complète des valeurs possibles de la *ribbonID* paramètre, consultez l’article technique [personnaliser le ruban dans Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans l' inspecteur `Microsoft.Outlook.Mail.Compose`. Il s'agit de l'inspecteur qui s'affiche lorsqu'un utilisateur crée un message électronique. Le ruban à afficher est spécifié dans le `GetResourceText()` (méthode), qui est généré dans le **ruban** classe. Pour plus d’informations sur la **ruban** de classe, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)  
  
  