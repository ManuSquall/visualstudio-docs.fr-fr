---
title: "Comment : cibler l’Interface utilisateur multilingue Office | Documents Microsoft"
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
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39ee8b6bdcb4ad647164ec555cfa37ee9cfe8f50
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Comment : cibler l'interface utilisateur multilingue d'Office
  L’Interface utilisateur multilingue (MUI) est une fonctionnalité de Microsoft Office qui donne à l’utilisateur final la possibilité de modifier la langue de l’interface utilisateur (IU). Par exemple, un utilisateur final qui travaille avec une interface utilisateur en anglais peut modifier la langue de l’interface utilisateur en espagnol.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si votre application doit être utilisée par des personnes qui utilisent plusieurs versions linguistiques d’Office, vous pouvez ajouter le code pour modifier automatiquement la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par Office sur l’ordinateur de l’utilisateur (si l’utilisateur a installé les ressources appropriées).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Pour connaître la configuration actuelle de l’interface utilisateur Office  
  
1.  Utilisez le <xref:System.Threading.Thread.CurrentUICulture%2A> propriété du thread actuel. Définir la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par la version d’Office en cours d’exécution sur l’ordinateur de l’utilisateur.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Voir aussi  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)  
  
  