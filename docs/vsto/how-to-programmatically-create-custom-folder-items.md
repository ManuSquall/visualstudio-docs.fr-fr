---
title: 'Comment : créer des éléments de dossier personnalisés par programmation'
description: Découvrez comment vous pouvez créer par programmation des éléments de dossier personnalisés dans Microsoft Outlook à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: f149758665e5d7a7cdf7f4edd5d926e1de632dca
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527792"
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>Comment : créer des éléments de dossier personnalisés par programmation
  Cet exemple crée un nouveau dossier dans Microsoft Office Outlook. Le nom de l’utilisateur qui est connecté est utilisé pour le nom du dossier.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : ajouter une entrée aux contacts Outlook par programmation](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Comment : créer des rendez-vous par programmation](../vsto/how-to-programmatically-create-appointments.md)
