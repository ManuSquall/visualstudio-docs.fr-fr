---
title: 'Comment : empêcher Outlook d’afficher une zone de formulaire | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5fffde6cd92d490df2a5567763da77e723ed4f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Comment : empêcher Outlook d'afficher une zone de formulaire
  Il peut y avoir des situations dans lesquelles vous ne souhaitez pas de Microsoft Office Outlook pour afficher une zone de formulaire pour un élément particulier. Par exemple, si un élément de contact ne contient pas d’adresse d’entreprise, vous pouvez empêcher une zone de formulaire qui affiche l’emplacement de l’entreprise dans une carte.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Pour empêcher Outlook d’afficher une zone de formulaire  
  
1.  Ouvrez le fichier de code pour la zone de formulaire que vous souhaitez modifier.  
  
2.  Développez le **fabrique de zones de formulaire** la région de code.  
  
3.  Ajoutez du code pour le `FormRegionInitializing` Gestionnaire d’événements qui définit le <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe **true**.  
  
 Dans cet exemple, si l’élément de contact ne contient pas une adresse, la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> est définie sur **true**, et la zone de formulaire ne s’affiche pas.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procédure pas à pas : importation d’une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  