---
title: "Comment : ajouter par programmation des formes à un Document Visio | Documents Microsoft"
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
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39843950cb592aa40b11e098f62018a4dc6e2983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Comment : ajouter des formes à un document Visio par programmation
  Vous pouvez ajouter des formes à un document Microsoft Office Visio en récupérant les formes de base d’un gabarit et en déplaçant les formes sur la page active.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) , la propriété [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) et la méthode [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) .  
  
## <a name="adding-shapes-to-a-visio-document"></a>Ajout de formes à un document Visio  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>Pour ajouter des formes à un document Visio  
  
-   Dans un document actif, récupérez les formes de base de la collection Documents.Masters et déplacez les formes sur celui-ci. Vous pouvez récupérer une forme de base à l’aide du nom de l’index ou de la forme de base.  
  
     L’exemple de code suivant crée un document Visio vierge, puis l’ouvre avec le gabarit **Formes de base** ancré. Le code récupère ensuite plusieurs formes et les déplace sur la page active.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Utilisation des formes Visio](../vsto/working-with-visio-shapes.md)   
 [Guide pratique pour copier et coller des formes dans un document Visio par programmation](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  