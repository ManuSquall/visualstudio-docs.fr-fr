---
title: 'Procédure : Cible de l’interface utilisateur multilingue d’Office'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c495f8a83b58c53404056befd2227b295c3324d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961137"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procédure : Cible de l’interface utilisateur multilingue d’Office
  L’Interface MUI (Multilingual User Interface) est une fonctionnalité de Microsoft Office qui permet à l’utilisateur final de changer la langue de l’interface utilisateur (IU). Par exemple, un utilisateur final qui travaille avec une interface utilisateur anglais peut modifier la langue de l’interface utilisateur vers l’espagnol.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si votre application doit être utilisée par les personnes qui utilisent de nombreuses langues d’Office, vous pouvez ajouter le code pour modifier automatiquement la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par Office sur l’ordinateur de l’utilisateur (si l’utilisateur a installé les ressources appropriées).

## <a name="to-check-the-current-office-ui-setting"></a>Pour vérifier le paramètre actuel de l’interface utilisateur Office

1. Utilisez le <xref:System.Threading.Thread.CurrentUICulture%2A> propriété du thread actuel. Définir la langue de vos chaînes d’interface utilisateur pour correspondre à la langue utilisée par la version d’Office qui s’exécute actuellement sur l’ordinateur de l’utilisateur.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Cibler les applications Office via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
