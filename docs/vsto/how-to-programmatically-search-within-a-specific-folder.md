---
title: 'Comment : effectuer une recherche par programmation dans un dossier spécifique'
description: Découvrez comment vous pouvez utiliser Visual Studio pour effectuer une recherche par programmation dans un dossier Microsoft Outlook spécifique.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824755"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Comment : effectuer une recherche par programmation dans un dossier spécifique
  Cet exemple de code utilise `Find` les `FindNext` méthodes et pour rechercher du texte dans le champ objet des messages électroniques qui se trouvent dans la **boîte de réception**. Cette méthode utilise un filtre de chaîne pour vérifier la lettre T comme lettre de départ du `Subject` texte.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemple
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des dossiers](../vsto/working-with-folders.md)
- [Vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md)
- [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
