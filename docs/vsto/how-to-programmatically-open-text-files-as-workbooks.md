---
title: 'Comment : ouvrir des fichiers texte en tant que classeurs par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7bc7caa5dbceb727394b8543b7659cc43e64a36
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257645"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Comment : ouvrir des fichiers texte en tant que classeurs par programmation
  Vous pouvez ouvrir un fichier texte comme un classeur. Vous devez passer le nom du fichier texte que vous souhaitez ouvrir. Vous pouvez spécifier plusieurs paramètres facultatifs, tels que le numéro de ligne à démarrer l’analyse et le format de colonne des données dans le fichier.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite les composants suivants :  
  
-   Un fichier texte délimité par des virgules nommé `Test.txt` qui contient au moins trois lignes de texte.  
  
-   Le fichier texte `Test.txt` à stocker sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)   
 [Comment : créer par programmation des classeurs](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  