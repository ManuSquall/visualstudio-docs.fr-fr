---
title: 'Comment : cibler l’interface utilisateur multilingue Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Comment : cibler l’interface utilisateur multilingue Office
  L’Interface utilisateur multilingue (MUI) est une fonctionnalité de Microsoft Office qui donne à l’utilisateur final la possibilité de modifier la langue de l’interface utilisateur (IU). Par exemple, un utilisateur final qui travaille avec une interface utilisateur en anglais peut modifier la langue de l’interface utilisateur en espagnol.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si votre application doit être utilisée par des personnes qui utilisent de nombreuses langues d’Office, vous pouvez ajouter le code pour modifier automatiquement la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par Office sur l’ordinateur de l’utilisateur (si l’utilisateur a installé les ressources appropriées).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Pour connaître la configuration actuelle de l’interface utilisateur Office  
  
1.  Utilisez le <xref:System.Threading.Thread.CurrentUICulture%2A> propriété du thread actuel. Définir la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par la version d’Office qui s’exécute actuellement sur l’ordinateur de l’utilisateur.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : applications Office de cible via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)  
  
  