---
title: "Personnalisation d’un ruban pour InfoPath | Documents Microsoft"
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
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 647f3a61582c58ee2d132ebd0f81fc6ecff44a02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-a-ribbon-for-infopath"></a>Personnalisation d'un ruban pour InfoPath
  Quand vous personnalisez le ruban dans Microsoft Office InfoPath, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] peut afficher le ruban dans les trois types suivants de fenêtres d'application InfoPath :  
  
-   Fenêtres qui affichent un modèle de formulaire ouvert en mode Création.  
  
-   Fenêtres qui affichent un formulaire basé sur un modèle de formulaire.  
  
-   Fenêtre Aperçu avant impression.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour InfoPath 2010. Pour plus d'informations, consultez [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Les utilisateurs et les concepteurs ouvrent un modèle de formulaire en mode Création pour modifier l'apparence et la disposition du modèle. Les utilisateurs ouvrent des formulaires basés sur un modèle de formulaire pour ajouter du contenu.  
  
 La fenêtre Aperçu avant impression permet aux concepteurs et aux utilisateurs d'afficher un aperçu des pages d'un formulaire ou d'un modèle de formulaire avant de les imprimer.  
  
> [!NOTE]  
>  L'onglet **Compléments** n'apparaît pas dans la fenêtre Aperçu avant impression. Si vous souhaitez qu'un onglet personnalisé apparaisse dans la fenêtre Aperçu avant impression, assurez-vous que la propriété **OfficeId** de l'onglet n'a pas la valeur **TabAddIns**.  
  
 Vous devez spécifier le type de ruban de chaque fenêtre dans laquelle vous souhaitez que votre ruban apparaisse.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Spécification du type de ruban dans le concepteur de ruban  
 Si vous utilisez l'élément **Ruban (Concepteur visuel)** , cliquez sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés** , puis sélectionnez l'un des ID de ruban répertoriés dans le tableau ci-dessous.  
  
|ID de ruban|Fenêtre dans laquelle le ruban s'affichera quand vous exécuterez le projet|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Fenêtres qui affichent un modèle de formulaire ouvert en mode Création.|  
|**Microsoft.InfoPath.Editor**|Fenêtres qui affichent un formulaire basé sur un modèle de formulaire.|  
|**Microsoft.InfoPath.PrintPreview**|Fenêtre Aperçu avant impression.|  
  
 Vous pouvez ajouter plusieurs rubans à un projet. Si plusieurs rubans partagent un ID de ruban, substituez la méthode CreateRibbonExtensibilityObject dans la `ThisAddin` classe de votre projet pour spécifier le ruban à afficher au moment de l’exécution. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Spécification du type de ruban à l'aide du code XML du ruban  
 Si vous utilisez l'élément **Ruban (XML)** , vérifiez la valeur du paramètre *ribbonID* dans la méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> et retournez le ruban approprié.  
  
 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban. Le paramètre *ribbonID* est une chaîne qui identifie le type de fenêtre InfoPath qui s'ouvre.  
  
 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans une fenêtre qui affiche un modèle de formulaire en mode Création. Le ruban à afficher est spécifié dans la méthode `GetResourceText()` , générée dans la classe du ruban. Pour plus d’informations sur la classe du ruban, consultez [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)  
  
  