---
title: 'Procédure : Créer un composant WebPart SharePoint à l’aide d’un concepteur | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 354fe62914a8708ac63acdde7d30060aca8d52fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966821"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Procédure : Créer un composant WebPart SharePoint à l’aide d’un concepteur
  Vous pouvez créer un composant WebPart en ajoutant un **composant Visual Web Part** élément à un projet SharePoint. Cela ouvre le concepteur Visual Web Developer dans Visual Studio où vous pouvez ajouter des contrôles et du code au composant WebPart. Composants Visual web parts fonctionnent de la même manière que faire des composants WebPart. La seule différence est que vous concevez des composants visual web parts dans le concepteur Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Pour créer un projet pour les composants visual web parts

1. Dans la barre de menus, choisissez **Fichier** >**Nouveau** > **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

2. Dans le **nouveau projet** boîte de dialogue, sous **Visual C#**  ou **Visual Basic**, développez le **Office/SharePoint** nœud, puis Choisissez le **Solutions SharePoint** catégorie.

3. Dans la liste des modèles de projet, choisissez **SharePoint 2013 - composant Visual Web Part**, puis choisissez le **OK** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

4. Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, spécifiez l’URL d’un site SharePoint qui se trouve sur l’ordinateur local, et puis choisissez le **Terminer** bouton.

     Dans **l’Explorateur de solutions**, un composant WebPart s’affiche. Après avoir créé le composant WebPart dans le concepteur Visual Web Developer, vous allez le tester sur le site que vous spécifiez.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Pour ajouter un composant visual web part à un projet SharePoint existant

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

2. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **Office/SharePoint** nœud.

3. Dans la liste des modèles de projet, choisissez **composant Visual Web Part**, nommez-le et choisissez le **ajouter** bouton.

     Dans **l’Explorateur de solutions**, votre composant WebPart s’affiche. Après avoir créé le composant WebPart dans le concepteur Visual Web Developer, vous allez le tester sur le site que vous spécifiez.

## <a name="see-also"></a>Voir aussi
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Guide pratique pour Créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Procédure pas à pas : Créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procédure pas à pas : Créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
