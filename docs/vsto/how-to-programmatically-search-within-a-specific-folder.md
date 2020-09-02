---
title: 'Comment : effectuer une recherche par programmation dans un dossier spécifique'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8f5e0f098edcffce07eb2c3f243b994d1a53cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547015"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Comment : effectuer une recherche par programmation dans un dossier spécifique
  Cet exemple de code utilise `Find` les `FindNext` méthodes et pour rechercher du texte dans le champ objet des messages électroniques qui se trouvent dans la **boîte de réception**. Cette méthode utilise un filtre de chaîne pour vérifier la lettre T comme lettre de départ du `Subject` texte.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
