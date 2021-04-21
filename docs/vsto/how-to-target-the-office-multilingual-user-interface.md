---
title: 'Comment : cibler l’interface utilisateur multilingue d’Office'
description: Découvrez comment vous pouvez utiliser Visual Studio pour cibler par programmation l’interface utilisateur multilingue Microsoft Office.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cf838b544ec78c8c7d6e9e2d6f1cb747e999ccd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823911"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Comment : cibler l’interface utilisateur multilingue d’Office
  L’interface utilisateur multilingue (MUI) est une fonctionnalité de Microsoft Office qui donne à l’utilisateur final la possibilité de modifier la langue de l’interface utilisateur. Par exemple, un utilisateur final travaillant avec une interface utilisateur en anglais peut modifier la langue de l’interface utilisateur en espagnol.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si votre application doit être utilisée par des personnes qui utilisent de nombreuses langues d’Office, vous pouvez ajouter du code pour modifier automatiquement la langue de vos chaînes d’interface utilisateur afin qu’elle corresponde à la langue utilisée par Office sur l’ordinateur de l’utilisateur (si les ressources appropriées sont installées sur l’utilisateur).

## <a name="to-check-the-current-office-ui-setting"></a>Pour vérifier le paramètre actuel de l’interface utilisateur Office

1. Utilisez la <xref:System.Threading.Thread.CurrentUICulture%2A> propriété du thread actuel. Définissez la langue de vos chaînes d’interface utilisateur pour qu’elle corresponde à la langue utilisée par la version d’Office qui est actuellement exécutée sur l’ordinateur de l’utilisateur.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Voir aussi
- [Comment : cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
