---
title: 'Comment : ouvrir des fichiers texte en tant que classeurs par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a0f1b384aafb491183a750f17653ab55f2003e2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519827"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Comment : ouvrir des fichiers texte en tant que classeurs par programmation
  Vous pouvez ouvrir un fichier texte en tant que classeur. Vous devez passer le nom du fichier texte que vous souhaitez ouvrir. Vous pouvez spécifier plusieurs paramètres facultatifs, tels que le numéro de ligne sur lequel commencer l’analyse et le format de colonne des données dans le fichier.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert les composants suivants :

- Fichier texte délimité par des virgules nommé `Test.txt` qui contient au moins trois lignes de texte.

- Fichier texte `Test.txt` à stocker sur le lecteur C.

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)
- [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)
- [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
