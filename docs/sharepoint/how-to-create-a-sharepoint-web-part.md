---
title: 'Procédure : Créer un composant WebPart SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 304e9f29d317a5258467e4ff45248d0dd2066d4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966807"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Procédure : Créer un composant WebPart SharePoint
  Vous pouvez créer et personnaliser un composant WebPart en ajoutant un **WebPart** d’élément à un projet SharePoint, puis en modifiant le fichier de code pour le composant WebPart ou à l’aide d’un concepteur. Pour plus d'informations, voir [Procédure : Créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Pour créer un composant WebPart SharePoint

1. Créez ou ouvrez un projet SharePoint.

     Pour plus d’informations, consultez [SharePoint modèles d’élément de projet et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Choisissez le nœud de projet SharePoint dans **l’Explorateur de solutions** , puis **projet** > **ajouter un nouvel élément**.

3. Dans le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

4. Dans la liste de modèles SharePoint, choisissez **WebPart**.

5. Dans le **nom** zone, spécifiez un nom pour le composant WebPart, puis choisissez le **ajouter** bouton.

     Le composant WebPart s’affiche dans **l’Explorateur de solutions**. Pour plus d’informations sur les fichiers qui inclut un composant WebPart, consultez [créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. Dans **l’Explorateur de solutions**, ouvrez le fichier de code pour le composant WebPart que vous venez de créer.

     Par exemple, si le nom de votre composant WebPart est *WebPart1*, ouvrez *WebPart1.vb* (en Visual Basic) ou *WebPart1.cs* (en c#).

7. Dans le fichier de code, ajouter des contrôles à la <xref:System.Web.UI.Control.CreateChildControls%2A> (méthode).

     Pour obtenir un exemple, consultez [Procédure pas à pas : Créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Voir aussi
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Guide pratique pour Créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Procédure pas à pas : Créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procédure pas à pas : Créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
