---
title: 'Comment : récupérer un dossier par nom par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour récupérer par programme un dossier par son nom, puis afficher le contenu du dossier.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c05f8bc0174807a5336a9d9f79ac3dc81e87476e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953875"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Comment : récupérer un dossier par nom par programmation
  Cet exemple obtient une référence à un dossier personnalisé nommé, puis affiche le contenu du dossier.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite :

- Un dossier nommé TestFolder.

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : effectuer une recherche par programmation dans un dossier spécifique](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Comment : Rechercher un contact spécifique par programmation](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Comment : créer des éléments de dossier personnalisés par programmation](../vsto/how-to-programmatically-create-custom-folder-items.md)
