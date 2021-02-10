---
title: 'Comment : prendre en main la personnalisation du ruban'
description: Découvrez que pour personnaliser le ruban d’une application Microsoft Office, ajoutez un élément Ruban (concepteur visuel) ou ruban (XML) à un projet Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d82d059166b9efbb80ed6ce4cffcbb973235b01b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953914"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Comment : prendre en main la personnalisation du ruban
  Pour personnaliser le ruban d’une application Microsoft Office, ajoutez un élément **Ruban (concepteur visuel)** ou **Ruban (XML)** à un projet Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Pour ajouter un ruban à un projet

1. Dans le menu **projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (concepteur visuel)** ou **Ruban (XML)**. Pour plus d’informations sur ces modèles, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

3. Dans la zone **nom** , tapez un nom pour l’élément de ruban.

    Les noms ne peuvent pas contenir les caractères suivants :

   - dièse (#)

   - Pourcentage (%)

   - Esperluette (&)

   - astérisque (*)

   - barre verticale (|)

   - Barre oblique inverse (\\)

   - deux-points (:)

   - Guillemet double (")

   - Inférieur à (\<)

   - Supérieur à (>)

   - point d'interrogation (?)

   - barre oblique (/)

   - espaces à gauche ou à droite (' ')

   - Noms réservés pour Windows ou DOS, tels que (« nul », « aux », « con », « COM1 », « LPT1 », etc.)

4. Cliquez sur **OK**.

   L’élément du ruban s’affiche dans **Explorateur de solutions**. Pour plus d’informations sur les étapes suivantes, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
