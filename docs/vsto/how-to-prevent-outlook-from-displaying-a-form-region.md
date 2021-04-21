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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825847"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Comment : empêcher Outlook d’afficher une zone de formulaire
  Il peut arriver que vous ne souhaitiez pas que Microsoft Office Outlook affiche une zone de formulaire pour un élément particulier. Par exemple, si un élément de contact ne contient pas d’adresse professionnelle, vous pouvez empêcher une zone de formulaire qui affiche l’emplacement de l’entreprise dans une carte.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Pour empêcher Outlook d’afficher une zone de formulaire

1. Ouvrez le fichier de code de la zone de formulaire que vous souhaitez modifier.

2. Développez la région de code de la **fabrique de zones de formulaire** .

3. Ajoutez du code au `FormRegionInitializing` Gestionnaire d’événements qui affecte la valeur true à la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe. 

   Dans cet exemple, si l’élément de contact ne contient pas d’adresse, la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété a la valeur **true** et la zone de formulaire n’apparaît pas.

## <a name="example"></a>Exemple
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Voir aussi
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
