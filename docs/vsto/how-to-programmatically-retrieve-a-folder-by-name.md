---
title: 'Procédure : Récupérer par programme un dossier par nom'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a494f954f3f670fb796b33a0dbd01e2512ad1d26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955727"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Procédure : Récupérer par programme un dossier par nom
  Cet exemple obtient une référence à un dossier personnalisé nommé, puis affiche le contenu du dossier.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Un dossier nommé TestFolder.

## <a name="see-also"></a>Voir aussi
- [Travailler avec des dossiers](../vsto/working-with-folders.md)
- [Guide pratique pour Rechercher par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Guide pratique pour Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Guide pratique pour Créer par programmation des éléments de dossier personnalisés](../vsto/how-to-programmatically-create-custom-folder-items.md)
