---
title: "Comment&#160;: enregistrer des documents Visio par programmation | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documents (développement Office dans Visual Studio), enregistrer des documents Visio"
  - "Visio (développement Office dans Visual Studio), enregistrer des documents Visio"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: enregistrer des documents Visio par programmation
  Il existe plusieurs façons d’enregistrer des documents Microsoft Office Visio :  
  
-   Enregistrer les modifications dans un document existant.  
  
-   Enregistrer un nouveau document ou enregistrer un document existant sous un nouveau nom.  
  
-   Enregistrer un document avec des arguments spécifiés.  
  
 Pour plus d’informations, consultez la documentation de référence de VBA pour les méthodes [Microsoft.Office.Interop.Visio.Document.Save](HV10071468), [Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) et [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470).  
  
## Enregistrement d’un document existant  
  
#### Pour enregistrer un document  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.Save de la classe Microsoft.Office.Tools.Visio.Document d’un document enregistré précédemment.  
  
     Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
    > [!NOTE]  
    >  La méthode Microsoft.Office.Interop.Visio.Document.Save lève une exception si aucun nouveau document Visio n’a encore été enregistré.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## Enregistrement d’un document sous un nouveau nom  
 Utilisez la méthode Microsoft.Office.Interop.Visio.Document.SaveAs pour enregistrer un nouveau document ou un document existant sous un nouveau nom. Cette méthode requiert que vous spécifiiez le nouveau nom de fichier.  
  
#### Pour enregistrer le document Visio actif sous un nouveau nom  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.SaveAs du Microsoft.Office.Tools.Visio.Document que vous souhaitez enregistrer, en utilisant un chemin complet incluant un nom du fichier. Si un fichier du même nom existe déjà dans ce dossier, il est automatiquement remplacé.  
  
     Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Enregistrement d’un document sous un nouveau nom et avec des arguments spécifiés  
 Utilisez la méthode Microsoft.Office.Interop.Visio.Document.SaveAsEx pour enregistrer un document sous un nouveau nom et spécifier tous les arguments devant être appliqués au document.  
  
#### Pour enregistrer un document sous un nouveau nom avec des arguments spécifiés  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Document.SaveAsEx du Microsoft.Office.Tools.Visio.Document que vous souhaitez enregistrer, en utilisant un chemin complet incluant un nom du fichier. Si un fichier du même nom existe déjà dans ce dossier, une exception est levée.  
  
     L’exemple de code suivant enregistre le document actif sous un nouveau nom, marque le document en lecture seule et affiche le document dans la liste des derniers fichiers utilisés. Pour utiliser cet exemple de code, exécutez\-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Pour enregistrer un document portant un nouveau nom, un répertoire nommé `Test` doit se trouver dans le dossier Mes documents \(Windows XP ou version antérieure\) ou Documents \(Windows Vista\).  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : créer des documents Visio par programmation](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  