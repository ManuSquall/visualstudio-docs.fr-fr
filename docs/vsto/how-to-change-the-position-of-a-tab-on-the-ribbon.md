---
title: 'Comment : modifier la position d’un onglet sur le ruban'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f821ea2a469fc06f80a7aaea96d07274d02a81d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544857"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Comment : modifier la position d’un onglet sur le ruban
  Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban à l’aide de l' **éditeur de collections Tab**. Vous pouvez positionner les onglets personnalisés avant ou après un onglet intégré sur le ruban. Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office. Par exemple, l’onglet **données** est un onglet intégré dans Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Pour modifier l’ordre des onglets sur le ruban

1. Sélectionnez le fichier de code du ruban (fichier *. vb* ou *. cs* ) dans **Explorateur de solutions**.

2. Dans le menu **affichage** , cliquez sur **Concepteur**.

3. Cliquez avec le bouton droit sur le concepteur de ruban, puis cliquez sur **Propriétés**.

4. Dans la fenêtre **Propriétés** , sélectionnez la propriété **tabulations** , puis cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")).

     L' **éditeur de collections Tab** s’affiche.

5. Dans l' **éditeur de collections Tab**, dans la liste **membres** , sélectionnez l’onglet que vous souhaitez déplacer, puis cliquez sur les flèches haut ou bas pour modifier l’ordre de tabulation.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Pour positionner un onglet avant ou après un onglet intégré sur le ruban

1. Dans le concepteur de ruban, sélectionnez un onglet personnalisé.

2. Dans la fenêtre **Propriétés** , développez la propriété **ControlID** , puis assurez-vous que la valeur de la propriété **ControlIdType** est définie sur **personnalisé**.

3. Dans la fenêtre **Propriétés** , développez la propriété **position** .

4. Affectez à la propriété **PositionType** la valeur appropriée :

    - **BeforeOfficeId** positionne le groupe avant un onglet prédéfini spécifié.

    - **AfterOfficeId** positionne le groupe après un onglet prédéfini spécifié.

5. Affectez à la propriété **OfficeId** l’ID de contrôle d’un onglet intégré.

     Pour obtenir la liste des ID de contrôle, consultez [fichiers d’aide office 2010 : identificateurs de contrôle d’interface utilisateur Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
