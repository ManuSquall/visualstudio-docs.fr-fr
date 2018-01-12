---
title: "Comment : créer un composant WebPart SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27826859d2bac9b247132e7fcb2c3721b6d38092
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Comment : créer un composant WebPart SharePoint
  Vous pouvez créer et personnaliser un composant WebPart en ajoutant un **WebPart** d’élément à un projet SharePoint, puis en modifiant le fichier de code pour le composant WebPart ou à l’aide d’un concepteur. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Pour créer un composant WebPart SharePoint  
  
1.  Créez ou ouvrez un projet SharePoint.  
  
     Pour plus d’informations, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Choisissez le nœud de projet SharePoint dans **l’Explorateur de solutions** , puis **projet**, **ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans la liste de modèles SharePoint, choisissez **WebPart**.  
  
5.  Dans le **nom** zone, spécifiez un nom pour le composant WebPart, puis choisissez le **ajouter** bouton.  
  
     Le composant WebPart s’affiche dans **l’Explorateur de solutions**. Pour plus d’informations sur les fichiers contenant un composant WebPart, consultez [création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  Dans **l’Explorateur de solutions**, ouvrez le fichier de code pour le composant WebPart que vous venez de créer.  
  
     Par exemple, si le nom de votre composant WebPart est WebPart1, ouvrez WebPart1.vb (en Visual Basic) ou WebPart1.cs (en c#).  
  
7.  Dans le fichier de code, ajouter des contrôles à la <xref:System.Web.UI.Control.CreateChildControls%2A> (méthode).  
  
     Pour obtenir un exemple, consultez [procédure pas à pas : création d’un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : Création d’un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Procédure pas à pas : création d’un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  