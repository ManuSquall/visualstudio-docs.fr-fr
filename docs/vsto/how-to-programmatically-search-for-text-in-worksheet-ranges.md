---
title: 'Comment : rechercher le texte dans les plages de feuille de calcul par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2749834f459085b8d182b58f12a4c372f7493cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Comment : rechercher du texte dans les plages de la feuille de calcul par programmation
  Le <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> méthode de la <xref:Microsoft.Office.Interop.Excel.Range> objet vous permet de rechercher du texte dans la plage. Ce texte peut être également une des chaînes d’erreur qui peuvent apparaître dans une cellule de feuille de calcul, tel que `#NULL!` ou `#VALUE!`. Pour plus d’informations sur les chaînes d’erreur, consultez [valeurs d’erreur](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 L’exemple suivant recherche une plage nommée `Fruits` et modifie la police des cellules qui contiennent le mot « apples ». Cette procédure utilise également le <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> (méthode), qui utilise la recherche des paramètres pour répéter la recherche. Vous spécifiez la cellule à partir de laquelle effectuer la recherche et le <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> méthode gère le reste.  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> recherche de la méthode encapsule jusqu’au début de la plage de recherche une fois qu’il a atteint la fin de la plage. Votre code doit s’assurer que la recherche n’encapsule pas autour d’une boucle infinie. L’exemple de procédure montre une façon de gérer cette situation à l’aide de la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propriété.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour utiliser la méthode Find dans un complément à Excel ?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Pour rechercher du texte dans une plage de feuille de calcul  
  
1.  Déclarez les variables pour le suivi de l’intégralité de la plage, de la première plage trouvée et de la plage trouvée actuelle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Recherchez la première correspondance, en spécifiant tous les paramètres à l’exception de la cellule à rechercher.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Continuer la recherche aussi longtemps qu’il existe des correspondances.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Comparez la première plage trouvée (`firstFind`) à **rien**. Si `firstFind` ne contient aucune valeur, le code stocke la plage trouvée (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Quitter la boucle si l’adresse de la plage trouvée correspond à l’adresse de la première plage trouvée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Définir l’apparence de la plage trouvée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Effectuer une autre recherche.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 L'exemple suivant montre la méthode complète.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : appliquer des Styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : faire référence par programmation aux plages de feuille de calcul dans le Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  