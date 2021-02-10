---
title: Le classeur contient des contrôles ActiveX qui ne peuvent pas être chargés
description: Découvrez comment vous pouvez résoudre l’erreur qui se produit lorsqu’un classeur contient des contrôles ActiveX qui ne peuvent pas être chargés.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4c8039fc2a5df197446873f0b2efef82d9a5f662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940785"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Le classeur contient des contrôles ActiveX qui ne peuvent pas être chargés

  L’erreur « le classeur utilisé pour créer ce projet contient des contrôles ActiveX que le concepteur ne peut pas charger » s’affiche lorsque vous ajoutez par programmation un contrôle à un document Word ou une feuille de calcul Excel, enregistrez le document ou le classeur, puis créez une nouvelle solution au niveau du document basée sur le document ou le classeur.

 Les informations qui décrivent le type managé du contrôle ne sont pas enregistrées avec le document ou le classeur. Quand vous créez une solution basée sur ce document ou classeur, Visual Studio ne possède pas suffisamment d'informations pour charger le contrôle dans le concepteur d'éléments hôtes.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ouvrez le document ou le classeur.

2. Supprimez les contrôles qui ont été ajoutés au moment de l'exécution. Pour ce faire, sélectionnez-les dans le document ou le classeur et appuyez sur la touche **Suppr** .

3. Créez une solution au niveau du document basée sur le document ou le classeur.

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
