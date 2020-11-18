---
title: 'Comment : créer une page d’application | Microsoft Docs'
description: Créez une page Web ASP.NET (également appelée page d’application) dans Visual Studio pour un ou plusieurs sites SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df52ca75ef99fe98158cb5f874e59fe4ee0c47b4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849855"
---
# <a name="how-to-create-an-application-page"></a>Comment : créer une page d’application
  Vous pouvez créer une page Web ASP.NET pour un ou plusieurs sites SharePoint. Dans SharePoint, ces pages sont appelées pages d’application. Contrairement à une page de site, une page d’application contient le code qui s’exécute derrière la page. Pour plus d’informations, consultez [créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Pour créer une page d’application

1. Dans Visual Studio, ouvrez ou créez un projet SharePoint.

     Pour plus d’informations, consultez [modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

3. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

4. Dans la boîte de dialogue **Ajouter un nouvel élément** , développez le nœud **SharePoint** , puis choisissez l’élément **2010** .

5. Dans la liste des modèles SharePoint, choisissez **page application**.

6. Dans la zone **nom** , spécifiez un nom pour la page de l’application, puis cliquez sur le bouton **Ajouter** .

     Visual Studio ajoute plusieurs dossiers et fichiers à votre projet. Pour plus d’informations sur ces fichiers, consultez [créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     Dans la vue **source** du concepteur Visual Web Developer, le fichier de page ASP.net s’affiche. Vous pouvez concevoir la page en ajoutant des contrôles à partir de la **boîte à outils** et en les plaçant sur des espaces réservés de contenu. Pour plus d’informations, consultez [vue source, concepteur de pages Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Si vous souhaitez gérer des événements de contrôle, ajoutez du code au fichier de code de la page d’application.

     Le fichier de code s’affiche si vous développez le nœud du fichier de la page ASP.NET et que vous avez une extension *. cs* ou *. vb* , selon la langue du projet. Pour obtenir un exemple de bout en bout illustrant comment créer une page d’application, consultez [procédure pas à pas : créer une application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Voir aussi
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Procédure pas à pas : créer une page d’application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
