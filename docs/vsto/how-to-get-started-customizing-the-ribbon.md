---
title: 'Procédure : Prise en main de la personnalisation du ruban'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9b0f1ef704f5dd1426374e23806e5950ed5f6bb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255861"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procédure : Prise en main de la personnalisation du ruban
  Pour personnaliser le ruban d’une application Microsoft Office, ajoutez un élément **Ruban (concepteur visuel)** ou **Ruban (XML)** à un projet Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Pour ajouter un ruban à un projet

1. Dans le menu **projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (concepteur visuel)** ou **Ruban (XML)** . Pour plus d’informations sur ces modèles, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

3. Dans la zone **nom** , tapez un nom pour l’élément de ruban.

    Les noms ne peuvent pas contenir les caractères suivants :

   - Dièse (#)

   - Pourcentage (%)

   - Perluète (&)

   - astérisque (*)

   - barre verticale (|)

   - Barre oblique inverse (\\)

   - Deux-points ( :)

   - Guillemet double (")

   - Inférieur à (\<)

   - Supérieur à (>)

   - point d'interrogation (?)

   - Barre oblique (/)

   - Espaces de début ou de fin (' ')

   - Noms réservés pour Windows ou DOS, tels que (« nul », « aux », « con », « COM1 », « LPT1 », etc.)

4. Cliquez sur **OK**.

   L’élément du ruban s’affiche dans **Explorateur de solutions**. Pour plus d’informations sur les étapes suivantes, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
