---
title: 'Comment : empêcher Outlook d’afficher une zone de formulaire'
description: Découvrez comment empêcher Microsoft Office Outlook d’afficher une zone de formulaire pour un élément particulier.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f247bf82d51fda6d321b45c16f91b857300cc1e4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847674"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Comment : empêcher Outlook d’afficher une zone de formulaire
  Il peut arriver que vous ne souhaitiez pas que Microsoft Office Outlook affiche une zone de formulaire pour un élément particulier. Par exemple, si un élément de contact ne contient pas d’adresse professionnelle, vous pouvez empêcher une zone de formulaire qui affiche l’emplacement de l’entreprise dans une carte.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Pour empêcher Outlook d’afficher une zone de formulaire

1. Ouvrez le fichier de code de la zone de formulaire que vous souhaitez modifier.

2. Développez la région de code de la **fabrique de zones de formulaire** .

3. Ajoutez du code au `FormRegionInitializing` Gestionnaire d’événements qui affecte la valeur true à la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe. **true**

   Dans cet exemple, si l’élément de contact ne contient pas d’adresse, la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété a la valeur **true** et la zone de formulaire n’apparaît pas.

## <a name="example"></a>Exemple
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Voir aussi
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
