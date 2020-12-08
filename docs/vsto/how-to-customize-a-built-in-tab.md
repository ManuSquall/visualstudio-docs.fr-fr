---
title: 'Comment : personnaliser un onglet intégré'
description: Découvrez comment vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ac002b4c9ebacaf9cb522b583d6c4c9580b7bf2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846634"
---
# <a name="how-to-customize-a-built-in-tab"></a>Comment : personnaliser un onglet intégré
  Vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office. Par exemple, l’onglet **données** est un onglet intégré dans Excel. Lorsque vous créez un groupe personnalisé, il apparaît en dernier sous l'onglet, mais vous pouvez déplacer votre groupe n'importe où sur l'onglet.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Vous pouvez ajouter des groupes à un onglet intégré, mais vous ne pouvez pas supprimer les groupes intégrés d'un onglet intégré.

### <a name="to-add-groups-to-a-built-in-tab"></a>Pour ajouter des groupes à un onglet intégré

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.

    > [!NOTE]
    > Si le fichier de code du ruban n’apparaît pas dans **Explorateur de solutions**, vous devez ajouter un **élément de ruban** à votre projet. Consultez [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Cliquez avec le bouton droit sur un onglet dans le concepteur de ruban, puis cliquez sur **Propriétés**.

3. Dans la fenêtre **Propriétés** , développez la propriété **ControlID** , puis affectez à la propriété **ControlIdType** la valeur **Office**.

4. Affectez à la propriété **OfficeId** l' *ID de contrôle* de l’onglet intégré que vous souhaitez personnaliser.

     L'ID de contrôle est le nom qui identifie de façon unique les onglets, les groupes et les contrôles qui sont intégrés aux applications Microsoft Office.

     Pour obtenir la liste des ID de contrôle, consultez [fichiers d’aide office 2010 : identificateurs de contrôle d’interface utilisateur Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

5. Sous l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser des groupes sur l’onglet.

    > [!NOTE]
    > Les groupes intégrés n'apparaissent pas dans le concepteur. Par conséquent, la seule façon de déterminer si vous utilisez un onglet intégré consiste à examiner la propriété **ControlID** de l’onglet.

### <a name="to-position-groups-on-a-built-in-tab"></a>Pour positionner des groupes sur un onglet intégré

1. Dans le Concepteur de ruban, sélectionnez un groupe personnalisé.

2. Dans la fenêtre **Propriétés** , développez la propriété **position** .

3. Affectez à la propriété **PositionType** la valeur appropriée :

    - **BeforeOfficeId** positionne le groupe avant un groupe prédéfini spécifié.

    - **AfterOfficeId** positionne le groupe après un groupe intégré spécifié.

4. Affectez à la propriété **OfficeId** l’ID de contrôle d’un groupe intégré.

     Pour obtenir la liste des ID de contrôle, consultez [fichiers d’aide office 2010 : identificateurs de contrôle d’interface utilisateur Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Comment : modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Comment : afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)
