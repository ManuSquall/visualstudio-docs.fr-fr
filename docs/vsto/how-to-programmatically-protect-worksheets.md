---
title: "Comment&#160;: prot&#233;ger des feuilles de calcul par programmation"
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
  - "protection du document, ajouter à des feuilles de calcul"
  - "documents (développement Office dans Visual Studio), protection du document"
  - "protection, ajouter à des feuilles de calcul"
  - "feuilles de calcul, protéger"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Comment&#160;: prot&#233;ger des feuilles de calcul par programmation
  La fonctionnalité de protection de Microsoft Office Excel permet d'empêcher les utilisateurs et le code de modifier des objets dans une feuille de calcul.  Par défaut, toutes les cellules sont verrouillées une fois que vous avez activé la protection.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Dans les personnalisations au niveau du document, vous pouvez protéger les feuilles de calcul à l'aide du Concepteur Excel.  Vous pouvez également protéger une feuille de calcul par programmation au moment de l'exécution dans n'importe quel type de projet.  
  
> [!NOTE]  
>  Vous ne pouvez pas ajouter de contrôles Windows Forms aux zones protégées d'une feuille de calcul.  
  
## Utilisation du concepteur  
  
#### Pour protéger une feuille de calcul dans le concepteur  
  
1.  Dans le groupe **Modifications** de l'onglet **Révision**, cliquez sur **Protéger la feuille**.  
  
     La boîte de dialogue **Protéger la feuille** s'affiche.  Vous pouvez définir un mot de passe et spécifier éventuellement certaines actions que les utilisateurs sont autorisés à effectuer sur la feuille de calcul, par exemple appliquer un format aux cellules ou insérer des lignes.  
  
 Vous pouvez également autoriser les utilisateurs à modifier des plages spécifiques dans les feuilles de calcul protégées.  
  
#### Pour autoriser les modifications dans des plages spécifiques  
  
1.  Dans le groupe **Modifications** de l'onglet **Révision**, cliquez sur **Permettre la modification des plages**.  
  
     La boîte de dialogue **Permettre la modification des plages** s'affiche.  Vous pouvez spécifier les plages qui sont déverrouillées à l'aide d'un mot de passe, et désigner les utilisateurs qui peuvent modifier les plages sans mot de passe.  
  
## Utilisation du code au moment de l'exécution  
 Le code suivant définit le mot de passe \(à l'aide de la variable getPasswordFromUser, qui contient un mot de passe fourni par l'utilisateur\) et autorise uniquement le tri.  
  
#### Pour protéger une feuille de calcul en utilisant du code dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la feuille de calcul.  Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### Pour protéger une feuille de calcul en utilisant du code dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ôter la protection des feuilles de calcul par programmation](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Comment : protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  