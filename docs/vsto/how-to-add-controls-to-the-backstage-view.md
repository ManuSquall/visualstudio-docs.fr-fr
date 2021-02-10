---
title: 'Comment : ajouter des contrôles au mode Backstage '
description: Découvrez comment vous pouvez utiliser le concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur l’onglet fichier.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 830ecea036ee972321d98994ab36924e0c61a09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954265"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Comment : ajouter des contrôles au mode Backstage
  Vous pouvez utiliser le concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur l’onglet **fichier** . Quand vous exécutez l’application, les contrôles que vous ajoutez à l’onglet **fichier** apparaissent un groupe nommé **Add-ins**.

 Vous ne pouvez pas positionner les contrôles avant ou après les contrôles prédéfinis à l’aide du concepteur de ruban dans Visual Studio. Un contrôle intégré est un contrôle qui est déjà affiché en mode Backstage. Si vous souhaitez positionner les contrôles avant ou après les contrôles prédéfinis, vous devez utiliser un ruban XML. Pour plus d’informations sur le **Ruban (XML)**, consultez [Ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) et [Personnalisation du mode backstage d’Office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Pour ajouter des contrôles au mode Backstage

1. Ouvrez l’élément de ruban dans Mode Création.

     Pour plus d’informations sur l’ajout d’un élément **Ruban (concepteur visuel)** à votre projet, consultez [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Dans le concepteur de ruban, cliquez sur l’onglet **fichier** .

     Un concepteur de menus s’affiche. Cette aire de conception ne contient pas de contrôles.

3. À partir de l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser l’un des contrôles suivants sur le concepteur de menus :

    - Bouton

    - Case à cocher

    - Galerie

    - Menu

    - Séparateur

    - SplitButton

    - ToggleButton

4. Faites glisser les contrôles pour les déplacer vers de nouvelles positions dans le menu.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Comment : commencer à personnaliser le ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
