---
title: "Comment&#160;: rechercher du texte dans les plages de la feuille de calcul par programmation"
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
  - "texte (développement Office dans Visual Studio), rechercher dans les feuilles de calcul"
  - "recherches de texte, feuilles de calcul"
  - "feuilles de calcul, rechercher"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Comment&#160;: rechercher du texte dans les plages de la feuille de calcul par programmation
  La méthode <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> de l'objet <xref:Microsoft.Office.Interop.Excel.Range> vous permet de rechercher du texte dans la plage.  Ce texte peut également correspondre à n'importe quelle chaîne d'erreur susceptible d'apparaître dans une cellule de feuille de calcul telle que `#NULL!` ou `#VALUE!`.  Pour plus d'informations sur les chaînes d'erreur, consultez [Valeurs d'erreur de cellule](HV10038459).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 L'exemple suivant recherche une plage nommée `Fruits` et modifie la police des cellules contenant le mot « apples ».  Cette procédure fait également appel à la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, qui utilise les paramètres de recherche définis précédemment pour poursuivre la recherche.  Vous spécifiez la cellule à partir de laquelle la recherche doit commencer et la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> gère le reste.  
  
> [!NOTE]  
>  La recherche de la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> revient au début de la plage de recherche lorsqu'elle en a atteint la fin.  Votre code ne doit pas décrire une boucle infinie.  L'exemple de procédure indique comment éviter cela à l'aide de la propriété <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [Comment faire pour utiliser la méthode Find dans un complément Excel ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### Pour rechercher du texte dans une plage de feuille de calcul  
  
1.  Déclarez les variables pour le suivi de la plage complète, de la première plage trouvée et de la plage trouvée actuelle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  Recherchez la première correspondance, en spécifiant tous les paramètres à l'exception de la cellule à partir de laquelle la recherche doit commencer.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  Poursuivez la recherche tant que vous trouvez des correspondances.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  Comparez la première plage trouvée \(`firstFind`\) à **Nothing**.  Si `firstFind` ne contient aucune valeur, le code stocke la plage trouvée \(`currentFind`\).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  Si l'adresse de la plage trouvée correspond à celle de la première plage trouvée, le code sort de la boucle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  Définissez l'apparence de la plage trouvée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  Procédez à une autre recherche.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 L'exemple suivant illustre la méthode complète.  
  
## Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  