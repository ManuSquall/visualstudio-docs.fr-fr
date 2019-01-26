---
title: 'Procédure : Ajouter par programmation des formes à un document Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: accb45527d73c041600dd3216c85e54bdadd5f4a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862601"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Procédure : Ajouter par programmation des formes à un document Visio
  Vous pouvez ajouter des formes à un document Microsoft Office Visio en récupérant les formes de base d’un gabarit et en déplaçant les formes sur la page active.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour la méthode [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) , la propriété [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) et la méthode [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .  
  
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
 [Guide pratique pour Copier et coller des formes dans un document Visio par programme](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
