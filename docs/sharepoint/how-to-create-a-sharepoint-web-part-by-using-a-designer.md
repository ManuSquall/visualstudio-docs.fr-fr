---
title: 'Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur | Microsoft Docs'
titleSuffix: ''
description: Créez un composant WebPart en ajoutant un élément de composant Visual Web part à un projet SharePoint, ce qui permet d’ouvrir le concepteur Visual Web Developer dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112386"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur

  Vous pouvez créer un composant WebPart en ajoutant un élément de **composant Visual Web part** à n’importe quel projet SharePoint. Cela ouvre le concepteur Visual Web Developer dans Visual Studio, où vous pouvez ajouter des contrôles et du code au composant WebPart. La fonction Visual WebPart de la même façon que les composants WebPart. La seule différence est que vous concevez des composants Visual Web parts dans le concepteur Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Pour créer un projet pour des composants Visual Web Parts

1. Dans la barre de menus, choisissez **fichier**  > **nouveau**  >  **projet**.
::: moniker range="=vs-2017"

2. Dans la boîte de dialogue **nouveau projet** , sous **Visual C#** ou **Visual Basic**, développez le nœud **Office/SharePoint** , puis choisissez la catégorie **solutions SharePoint** .

3. Dans la liste des modèles de projet, choisissez **SharePoint 2013-composant Visual Web part**, puis cliquez sur le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.
::: moniker-end
::: moniker range=">=vs-2019"
2. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le *composant Visual Web part de SharePoint** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2019 installation, sélectionnez le modèle **sharepoint 2019-composant Visual Web part** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Modifiez le nom du projet si vous le souhaitez, puis choisissez le bouton **créer** .

::: moniker-end
4. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , spécifiez l’URL d’un site SharePoint qui se trouve sur l’ordinateur local, puis choisissez le bouton **Terminer** .

     Dans **Explorateur de solutions**, un composant WebPart s’affiche. Après avoir conçu le composant WebPart dans le concepteur Visual Web Developer, vous le testerez sur le site que vous spécifiez.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Pour ajouter un composant Visual Web part à un projet SharePoint existant

1. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le nœud **Office/SharePoint** .

3. Dans la liste des modèles de projet, choisissez **composant Visual Web part**, nommez-le, puis cliquez sur le bouton **Ajouter** .

     Dans **Explorateur de solutions**, votre composant WebPart s’affiche. Après avoir conçu le composant WebPart dans le concepteur Visual Web Developer, vous le testerez sur le site que vous spécifiez.

## <a name="see-also"></a>Voir aussi

- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Procédure pas à pas : créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procédure pas à pas : créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
