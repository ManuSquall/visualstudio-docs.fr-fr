---
title: "Comment&#160;: cr&#233;er des documents Visio par programmation"
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
  - "Visio (développement Office dans Visual Studio), création de documents Visio"
  - "documents (développement Office dans Visual Studio), création de documents Visio"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: cr&#233;er des documents Visio par programmation
  Quand vous créez un dessin Microsoft Office Visio, vous l’ajoutez à la collection Microsoft.Office.Interop.Visio.Documents de documents Visio ouverts. Ainsi, la méthode Microsoft.Office.Interop.Visio.Documents.Add crée un dessin Visio. Pour plus d’informations, consultez la documentation de référence VBA de la méthode [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241).  
  
## Création de documents vierges  
  
#### Pour créer un document  
  
-   Utilisez la méthode Microsoft.Office.Interop.Visio.Documents.Add pour créer un document vierge qui n’est pas basé sur un modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Création de documents copiés à partir de documents existants  
 La méthode Microsoft.Office.Interop.Visio.Documents.Add peut créer un document qui est une copie d’un document Visio existant. Vous devez fournir le nom de fichier et le chemin complet du diagramme.  
  
#### Pour créer un document copié à partir d’un document existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin du diagramme Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Création de gabarits copiés à partir de gabarits existants  
 La méthode [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) peut créer un gabarit qui est une copie d’un gabarit Visio existant. Vous devez fournir le nom de fichier et le chemin complet du gabarit.  
  
#### Pour créer un gabarit copié à partir d’un gabarit existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin du gabarit.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Création de documents basés sur des modèles existants  
 La méthode Microsoft.Office.Interop.Visio.Documents.Add peut créer un document \(fichier .vsd\) qui se base sur un modèle Visio existant \(fichier .vst\). Cette méthode copie les gabarits, styles et paramètres qui font partie de l’espace de travail du modèle. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.  
  
#### Pour créer un document basé sur un modèle existant  
  
-   Appelez la méthode Microsoft.Office.Interop.Visio.Documents.Add et spécifiez le chemin du modèle.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Compilation du code  
 Cet exemple de code requiert ce qui suit :  
  
-   Un document Visio nommé `myDrawing.vsd` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents \(Windows XP ou version antérieure\) ou du dossier Documents \(Windows Vista\).  
  
-   Un document Visio nommé `myStencil.vss` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents \(Windows XP ou version antérieure\) ou du dossier Documents \(Windows Vista\).  
  
-   Un document Visio nommé `myTemplate.vst` doit se trouver dans un répertoire nommé `Test` du dossier Mes documents \(Windows XP ou version antérieure\) ou du dossier Documents \(Windows Vista\).  
  
## Voir aussi  
 [Solutions Visio](../vsto/visio-solutions.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Comment : ouvrir des documents Visio par programmation](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Comment : fermer des documents Visio par programmation](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Comment : enregistrer des documents Visio par programmation](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Comment : imprimer des documents Visio par programmation](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  