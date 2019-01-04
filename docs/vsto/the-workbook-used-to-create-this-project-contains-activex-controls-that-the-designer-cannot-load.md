---
title: Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a48cff6b3d2e2b4a090ee5ec5cd879b272593cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876430"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger
  Cette erreur apparaît quand vous ajoutez par programmation un contrôle à un document Word ou une feuille de calcul Excel, enregistrez le document ou le classeur, puis créez une solution au niveau du document basée sur le document ou le classeur.  
  
 Les informations qui décrivent le type managé du contrôle ne sont pas enregistrées avec le document ou le classeur. Quand vous créez une solution basée sur ce document ou classeur, Visual Studio ne possède pas suffisamment d'informations pour charger le contrôle dans le concepteur d'éléments hôtes.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ouvrez le document ou le classeur.  
  
2.  Supprimez les contrôles qui ont été ajoutés lors de l’exécution. Vous pouvez faire en les sélectionnant dans un document ou classeur et en appuyant sur la **supprimer** clé.  
  
3.  Créez une solution au niveau du document basée sur le document ou le classeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
