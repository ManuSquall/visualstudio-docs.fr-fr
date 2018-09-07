---
title: 'Comment : enregistrer des documents Visio par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673196"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Comment : enregistrer des documents Visio par programmation
  Il existe plusieurs façons d’enregistrer des documents Microsoft Office Visio :  
  
-   Enregistrer les modifications dans un document existant.  
  
-   Enregistrer un nouveau document ou enregistrer un document existant sous un nouveau nom.  
  
-   Enregistrer un document avec des arguments spécifiés.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour les méthodes [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) et [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="save-an-existing-document"></a>Enregistrer un document existant  
  
### <a name="to-save-a-document"></a>Pour enregistrer un document  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Document.Save` méthode de la `Microsoft.Office.Tools.Visio.Document` classe d’un document qui a été précédemment enregistré.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  Le `Microsoft.Office.Interop.Visio.Document.Save` méthode lève une exception si un nouveau document Visio n’a pas encore été enregistré.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Enregistrer un document sous un nouveau nom  
 Utilisez le `Microsoft.Office.Interop.Visio.Document.SaveAs` méthode pour enregistrer un nouveau document ou un document qui possède un nouveau nom. Cette méthode requiert que vous spécifiiez le nouveau nom de fichier.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Pour enregistrer le document Visio actif sous un nouveau nom  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Document.SaveAs` méthode de la `Microsoft.Office.Tools.Visio.Document` que vous souhaitez enregistrer, à l’aide d’un chemin d’accès qualifié complet, y compris un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Enregistrer un document sous un nouveau nom et les arguments spécifiés  
 Utilisez le `Microsoft.Office.Interop.Visio.Document.SaveAsEx` méthode pour enregistrer un document avec un nouveau nom et spécifier tous les arguments à appliquer au document.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Pour enregistrer un document sous un nouveau nom avec des arguments spécifiés  
  
-   Appelez le `Microsoft.Office.Interop.Visio.Document.SaveAsEx` méthode de la `Microsoft.Office.Tools.Visio.Document` que vous souhaitez enregistrer, à l’aide d’un chemin d’accès qualifié complet, y compris un nom de fichier. Si un fichier du même nom existe déjà dans ce dossier, une exception est levée.  
  
     L’exemple de code suivant enregistre le document actif sous un nouveau nom, marque le document en lecture seule et affiche le document dans la liste des derniers fichiers utilisés. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Pour enregistrer un document qui possède un nouveau nom, un répertoire nommé `Test` doit se trouver dans le *Mes Documents* dossier (pour Windows XP et versions antérieures) ou le *Documents* dossier (Windows Vista).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer par programme des documents Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  