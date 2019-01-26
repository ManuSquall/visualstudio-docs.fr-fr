---
title: 'Procédure : Enregistrer des documents Visio par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 228152b668908c89c288f518465fe7ace92a03d6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875431"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Procédure : Enregistrer des documents Visio par programmation
  Il existe plusieurs façons d’enregistrer des documents Microsoft Office Visio :  
  
- Enregistrer les modifications dans un document existant.  
  
- Enregistrer un nouveau document ou enregistrer un document existant sous un nouveau nom.  
  
- Enregistrer un document avec des arguments spécifiés.  
  
  Pour plus d’informations, consultez la documentation de référence de VBA pour les méthodes [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) et [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .  
  
## <a name="save-an-existing-document"></a>Enregistrer un document existant  
  
### <a name="to-save-a-document"></a>Pour enregistrer un document  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Document.Save` de la classe `Microsoft.Office.Tools.Visio.Document` d’un document enregistré précédemment.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  La méthode `Microsoft.Office.Interop.Visio.Document.Save` lève une exception si aucun nouveau document Visio n’a encore été enregistré.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Enregistrer un document sous un nouveau nom  
 Utilisez la méthode `Microsoft.Office.Interop.Visio.Document.SaveAs` pour enregistrer un nouveau document ou un document existant sous un nouveau nom. Cette méthode requiert que vous spécifiiez le nouveau nom de fichier.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Pour enregistrer le document Visio actif sous un nouveau nom  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Document.SaveAs` du `Microsoft.Office.Tools.Visio.Document` que vous souhaitez enregistrer, en utilisant un chemin complet incluant un nom du fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Enregistrer un document sous un nouveau nom et les arguments spécifiés  
 Utilisez la méthode `Microsoft.Office.Interop.Visio.Document.SaveAsEx` pour enregistrer un document sous un nouveau nom et spécifier tous les arguments devant être appliqués au document.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Pour enregistrer un document sous un nouveau nom avec des arguments spécifiés  
  
-   Appelez la méthode `Microsoft.Office.Interop.Visio.Document.SaveAsEx` du `Microsoft.Office.Tools.Visio.Document` que vous souhaitez enregistrer, en utilisant un chemin complet incluant un nom du fichier. Si un fichier du même nom existe déjà dans ce dossier, une exception est levée.  
  
     L’exemple de code suivant enregistre le document actif sous un nouveau nom, marque le document en lecture seule et affiche le document dans la liste des derniers fichiers utilisés. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Pour enregistrer un document qui possède un nouveau nom, un répertoire nommé `Test` doit se trouver dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Guide pratique pour Créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Guide pratique pour Ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Guide pratique pour Fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Guide pratique pour Imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
