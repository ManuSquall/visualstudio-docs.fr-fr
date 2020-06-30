---
title: Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537343"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger
  Cette erreur apparaît quand vous ajoutez par programmation un contrôle à un document Word ou une feuille de calcul Excel, enregistrez le document ou le classeur, puis créez une solution au niveau du document basée sur le document ou le classeur.

 Les informations qui décrivent le type managé du contrôle ne sont pas enregistrées avec le document ou le classeur. Quand vous créez une solution basée sur ce document ou classeur, Visual Studio ne possède pas suffisamment d'informations pour charger le contrôle dans le concepteur d'éléments hôtes.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ouvrez le document ou le classeur.

2. Supprimez les contrôles qui ont été ajoutés au moment de l'exécution. Pour ce faire, sélectionnez-les dans le document ou le classeur et appuyez sur la touche **Suppr** .

3. Créez une solution au niveau du document basée sur le document ou le classeur.

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
