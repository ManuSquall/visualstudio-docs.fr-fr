---
title: 'Comment : associer une page Web à un dossier Outlook par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b8d44ffc46557243d2681b8f8b4a3b85d1cd9be6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546144"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Comment : associer une page Web à un dossier Outlook par programmation
  Cet exemple recherche un dossier nommé `HtmlView` dans Microsoft Office Outlook. Si le dossier n’existe pas, le code crée le dossier et lui attribue une page Web. Si le dossier existe, le code affiche le contenu du dossier.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Comment : créer des éléments de dossier personnalisés par programmation](../vsto/how-to-programmatically-create-custom-folder-items.md)
