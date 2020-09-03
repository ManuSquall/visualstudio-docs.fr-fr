---
title: Le concepteur ne peut pas être modifié pendant le débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8e393ad46b6d37bd74806a0a4b84825bd059457
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672275"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Le concepteur ne peut pas être modifié lors du débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce message apparaît lors d'une tentative de modification des éléments dans le Concepteur O/R alors que l'application s'exécute en mode de débogage. Lorsque l'application s'exécute en mode de débogage, le Concepteur O/R est accessible en lecture seule.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Cliquez sur **arrêter le débogage** dans le menu **Déboguer** .

     L'application cesse de déboguer et les éléments du Concepteur O/R peuvent être modifiés.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes de LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
