---
title: 'Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur | Microsoft Docs'
titleSuffix: ''
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d19822237f61d5404f42e30078541a735eb206bc
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584111"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur
  Vous pouvez créer un composant WebPart en ajoutant un élément de **composant Visual Web part** à n’importe quel projet SharePoint. Cela ouvre le concepteur Visual Web Developer dans Visual Studio, où vous pouvez ajouter des contrôles et du code au composant WebPart. La fonction Visual WebPart de la même façon que les composants WebPart. La seule différence est que vous concevez des composants Visual Web parts dans le concepteur Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Pour créer un projet pour des composants Visual Web Parts

1. Dans la barre de menus, choisissez **fichier**  > **nouveau**  >  **projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

2. Dans la boîte de dialogue **nouveau projet** , sous **Visual C#** ou **Visual Basic**, développez le nœud **Office/SharePoint** , puis choisissez la catégorie **solutions SharePoint** .

3. Dans la liste des modèles de projet, choisissez **SharePoint 2013-composant Visual Web part**, puis cliquez sur le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

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
