---
title: "Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0f50342fd82826aec8cf0d9694454afdc2db4080
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger
  Cette erreur apparaît quand vous ajoutez par programmation un contrôle à un document Word ou une feuille de calcul Excel, enregistrez le document ou le classeur, puis créez une solution au niveau du document basée sur le document ou le classeur.  
  
 Les informations qui décrivent le type managé du contrôle ne sont pas enregistrées avec le document ou le classeur. Quand vous créez une solution basée sur ce document ou classeur, Visual Studio ne possède pas suffisamment d'informations pour charger le contrôle dans le concepteur d'éléments hôtes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ouvrez le document ou le classeur.  
  
2.  Supprimez les contrôles qui ont été ajoutés au moment de l'exécution. Pour cela, sélectionnez-les dans le document ou le classeur et appuyez sur la touche Suppr.  
  
3.  Créez une solution au niveau du document basée sur le document ou le classeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  