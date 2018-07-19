---
title: 'Comment : ajouter par programmation des formes à un document Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32fc1b61505711cbcf353819372bcd1452bf3716
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256667"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Comment : ajouter par programmation des formes à un document Visio
  Vous pouvez ajouter des formes à un document Microsoft Office Visio en récupérant les formes de base d’un gabarit et en déplaçant les formes sur la page active.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) , la propriété [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) et la méthode [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) .  
  
## <a name="add-shapes-to-a-visio-document"></a>Ajouter des formes à un Visio Document  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Pour ajouter des formes à un document Visio  
  
-   Dans un document actif, récupérez les formes de base de la collection Documents.Masters et déplacez les formes sur celui-ci. Vous pouvez récupérer une forme de base à l’aide du nom de l’index ou de la forme de base.  
  
     L’exemple de code suivant crée un document Visio vierge, puis l’ouvre avec le gabarit **Formes de base** ancré. Le code récupère ensuite plusieurs formes et les déplace sur la page active.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Utilisez des formes Visio](../vsto/working-with-visio-shapes.md)   
 [Comment : copier et coller des formes dans un document Visio par programme](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  