---
title: "Comment&#160;: ouvrir des fichiers texte en tant que classeurs par programmation"
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
  - "texte (développement Office dans Visual Studio), fichiers texte"
  - "fichiers texte, ouvrir en tant que classeurs"
  - "classeurs, ouvrir des fichiers texte en tant que"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: ouvrir des fichiers texte en tant que classeurs par programmation
  Vous pouvez ouvrir un fichier texte en tant que classeur.  Vous devez passer le nom du fichier texte à ouvrir.  Vous pouvez spécifier plusieurs paramètres optionnels, tels que le numéro de ligne auquel démarrer l'analyse et le format de colonne des données du fichier.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## Compilation du code  
 Cet exemple requiert les composants suivants :  
  
-   Un fichier texte délimité par des virgules nommé `Test.txt` qui contient au moins trois lignes de texte.  
  
-   Le fichier texte `Test.txt` à stocker sur le lecteur C.  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)   
 [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  