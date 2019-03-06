---
title: 'Procédure : Rechercher par programmation dans un dossier spécifique'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638008"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procédure : Rechercher par programmation dans un dossier spécifique
  Cet exemple de code utilise le `Find` et `FindNext` méthodes pour rechercher du texte dans le champ objet des messages électroniques qui se trouvent dans le **boîte de réception**. Cette méthode utilise un filtre de chaîne à rechercher la lettre T comme la lettre de départ de la `Subject` texte.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des dossiers](../vsto/working-with-folders.md)
- [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)
- [Guide pratique pour Récupérer par programme un dossier par nom](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
