---
title: 'Comment : cibler l’interface utilisateur multilingue d’Office'
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5217f2d6cf67eced00c0c84b9bacda94573c5a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537499"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Comment : cibler l’interface utilisateur multilingue d’Office
  L’interface utilisateur multilingue (MUI) est une fonctionnalité de Microsoft Office qui donne à l’utilisateur final la possibilité de modifier la langue de l’interface utilisateur. Par exemple, un utilisateur final travaillant avec une interface utilisateur en anglais peut modifier la langue de l’interface utilisateur en espagnol.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si votre application doit être utilisée par des personnes qui utilisent de nombreuses langues d’Office, vous pouvez ajouter du code pour modifier automatiquement la langue de vos chaînes d’interface utilisateur afin qu’elle corresponde à la langue utilisée par Office sur l’ordinateur de l’utilisateur (si les ressources appropriées sont installées sur l’utilisateur).

## <a name="to-check-the-current-office-ui-setting"></a>Pour vérifier le paramètre actuel de l’interface utilisateur Office

1. Utilisez la <xref:System.Threading.Thread.CurrentUICulture%2A> propriété du thread actuel. Définissez la langue de vos chaînes d’interface utilisateur pour qu’elle corresponde à la langue utilisée par la version d’Office qui est actuellement exécutée sur l’ordinateur de l’utilisateur.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Voir aussi
- [Comment : cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
