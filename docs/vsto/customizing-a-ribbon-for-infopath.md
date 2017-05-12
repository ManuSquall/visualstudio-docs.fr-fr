---
title: "Personnalisation d&#39;un ruban pour InfoPath"
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
  - "InfoPath (développement Office dans Visual Studio), ruban"
  - "ruban (développement Office dans Visual Studio), InfoPath"
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Personnalisation d&#39;un ruban pour InfoPath
  Quand vous personnalisez le ruban dans Microsoft Office InfoPath, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application.[!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] peut afficher le ruban dans les trois types suivants de fenêtres d'application InfoPath :  
  
-   Fenêtres qui affichent un modèle de formulaire ouvert en mode Création.  
  
-   Fenêtres qui affichent un formulaire basé sur un modèle de formulaire.  
  
-   Fenêtre Aperçu avant impression.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour InfoPath 2010. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Les utilisateurs et les concepteurs ouvrent un modèle de formulaire en mode Création pour modifier l'apparence et la disposition du modèle. Les utilisateurs ouvrent des formulaires basés sur un modèle de formulaire pour ajouter du contenu.  
  
 La fenêtre Aperçu avant impression permet aux concepteurs et aux utilisateurs d'afficher un aperçu des pages d'un formulaire ou d'un modèle de formulaire avant de les imprimer.  
  
> [!NOTE]  
>  L'onglet **Compléments** n'apparaît pas dans la fenêtre Aperçu avant impression. Si vous souhaitez qu'un onglet personnalisé apparaisse dans la fenêtre Aperçu avant impression, assurez\-vous que la propriété **OfficeId** de l'onglet n'a pas la valeur **TabAddIns**.  
  
 Vous devez spécifier le type de ruban de chaque fenêtre dans laquelle vous souhaitez que votre ruban apparaisse.  
  
## Spécification du type de ruban dans le concepteur de ruban  
 Si vous utilisez l'élément **Ruban \(Concepteur visuel\)**, cliquez sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés**, puis sélectionnez l'un des ID de ruban répertoriés dans le tableau ci\-dessous.  
  
|ID de ruban|Fenêtre dans laquelle le ruban s'affichera quand vous exécuterez le projet|  
|-----------------|--------------------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Fenêtres qui affichent un modèle de formulaire ouvert en mode Création.|  
|**Microsoft.InfoPath.Editor**|Fenêtres qui affichent un formulaire basé sur un modèle de formulaire.|  
|**Microsoft.InfoPath.PrintPreview**|Fenêtre Aperçu avant impression.|  
  
 Vous pouvez ajouter plusieurs rubans à un projet. Si plusieurs rubans partagent un ID de ruban, substituez la méthode CreateRibbonExtensibilityObject dans la classe `ThisAddin` de votre projet pour spécifier le ruban à afficher au moment de l'exécution. Pour plus d'informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
## Spécification du type de ruban à l'aide du code XML du ruban  
 Si vous utilisez l'élément **Ruban \(XML\)**, vérifiez la valeur du paramètre *ribbonID* dans la méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> et retournez le ruban approprié.  
  
 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban. Le paramètre *ribbonID* est une chaîne qui identifie le type de fenêtre InfoPath qui s'ouvre.  
  
 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans une fenêtre qui affiche un modèle de formulaire en mode Création. Le ruban à afficher est spécifié dans la méthode `GetResourceText()`, générée dans la classe du ruban. Pour plus d’informations sur la classe du ruban, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/cs/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/vb/ribbon.vb#1)]  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)  
  
  