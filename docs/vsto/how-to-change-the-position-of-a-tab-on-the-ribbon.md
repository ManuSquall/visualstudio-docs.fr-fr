---
title: 'Procédure : Modifier la position d’un onglet dans le ruban'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 512dfda8c95ecd56fe44eb6878e6abc0d942a782
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091900"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Procédure : Modifier la position d’un onglet dans le ruban
  Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban à l’aide de la **éditeur de collections Tab**. Vous pouvez positionner les onglets personnalisés avant ou après un onglet prédéfini du ruban. Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Pour modifier l’ordre des onglets du ruban

1. Sélectionnez le fichier de code de ruban (*.vb* ou *.cs* fichier) dans **l’Explorateur de solutions**.

2. Sur le **vue** menu, cliquez sur **concepteur**.

3. Cliquez sur le Concepteur de ruban, puis cliquez sur **propriétés**.

4. Dans le **propriétés** fenêtre, sélectionnez le **onglets** propriété, puis cliquez sur le bouton de sélection (![ellipse concepteur mobile ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Ellipse de concepteur")).

     Le **éditeur de collections Tab** s’affiche.

5. Dans le **éditeur de collections Tab**, dans le **membres** , sélectionnez l’onglet que vous souhaitez déplacer et cliquez sur le haut ou flèches de direction pour modifier l’ordre de tabulation.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Pour positionner un onglet avant ou après un onglet intégré du ruban

1. Dans le Concepteur de ruban, sélectionnez un onglet personnalisé.

2. Dans le **propriétés** fenêtre, développez le **ControlId** propriété et assurez-vous que la valeur de la **ControlIdType** propriété est définie sur **personnalisé**.

3. Dans le **propriétés** fenêtre, développez le **Position** propriété.

4. Définir le **PositionType** propriété à la valeur appropriée :

    - **BeforeOfficeId** avant un onglet intégré spécifié.

    - **AfterOfficeId** place le groupe après un onglet intégré spécifié.

5. Définir le **OfficeId** propriété ID de contrôle d’un onglet intégré.

     Pour obtenir la liste d’ID de contrôle, consultez [les fichiers d’aide Office 2010 : Identificateurs de contrôle interface Office fluent utilisateur](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
