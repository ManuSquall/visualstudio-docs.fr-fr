---
title: "Comment&#160;: remplir automatiquement des plages avec des donn&#233;es soumises &#224; modification incr&#233;mentielle par programmation | Microsoft Docs"
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
  - "Autofill (méthode Excel)"
  - "remplir automatiquement des plages"
  - "plages, remplissage automatique"
  - "classeurs, remplir des plages"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Comment&#160;: remplir automatiquement des plages avec des donn&#233;es soumises &#224; modification incr&#233;mentielle par programmation
  La méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> de l'objet <xref:Microsoft.Office.Interop.Excel.Range> vous permet de remplir automatiquement une plage d'une feuille de calcul avec des valeurs.  En règle générale, la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> est utilisée pour stocker dans une plage des valeurs soumises à une augmentation ou une diminution incrémentielle.  Vous pouvez spécifier son comportement en fournissant une constante facultative provenant de l'énumération <xref:Microsoft.Office.Interop.Excel.XlAutoFillType>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous devez spécifier deux plages lors de l'utilisation de <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :  
  
-   La plage appelant la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>, qui spécifie le point de départ du remplissage et contient une valeur initiale.  
  
-   La plage à remplir, passée comme paramètre à la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  Cette plage de destination doit inclure la plage qui contient la valeur initiale.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas passer un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la place du contrôle <xref:Microsoft.Office.Interop.Excel.Range>.  Pour plus d’informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## Compilation du code  
 La première cellule de la plage à remplir doit contenir une valeur initiale.  
  
 L'exemple requiert que vous remplissiez trois régions :  
  
-   La colonne B doit inclure cinq jours de semaine.  Pour la valeur initiale, tapez **Lundi** dans la cellule B1.  
  
-   La colonne C doit inclure cinq mois.  Pour la valeur initiale, tapez **Janvier** dans la cellule C1.  
  
-   La colonne D doit inclure une série de chiffres, augmentant de deux unités pour chaque ligne.  Pour les valeurs initiales, tapez **4** dans la cellule D1 et **6** dans la cellule D2.  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  