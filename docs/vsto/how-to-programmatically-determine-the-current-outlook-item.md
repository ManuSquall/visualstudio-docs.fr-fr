---
title: 'Procédure : Déterminer par programme l’élément Outlook actuel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3608f516eb9206bc5b4c232c227d3e49c2414be7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599751"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procédure : Déterminer par programme l’élément Outlook actuel
  Cet exemple utilise le `Explorer.SelectionChange` événement pour afficher le nom du dossier actuel et des informations sur l’élément sélectionné. Le code affiche ensuite l’élément sélectionné.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

-   Rendez-vous, de contacts et éléments de messagerie dans Microsoft Office Outlook.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)
- [Guide pratique pour Récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Guide pratique pour Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
