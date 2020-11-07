---
title: Définir la version de publication ClickOnce | Microsoft Docs
description: Découvrez comment définir la propriété de version de publication ClickOnce, qui détermine si l’application est une mise à jour.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 100c3cd12a3011d35445ac885333802e28b4a92f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349787"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Guide pratique pour définir la version de publication ClickOnce
La [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propriété détermine si l’application que vous publiez sera traitée comme une mise à jour. Chaque fois que la version est incrémentée, l’application est publiée en tant que mise à jour.

 La `Publish Version` propriété peut être définie sur la page **publier** du **Concepteur de projets**.

> [!NOTE]
> Il existe une option de projet qui incrémente automatiquement la `Publish Version` propriété chaque fois que l’application est publiée. cette option est activée par défaut. Pour plus d’informations, consultez Guide pratique [pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Pour modifier la version de publication

1. Quand un projet est sélectionné dans **Explorateur de solutions** , dans le menu **projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans le champ **version de publication** , incrémentez les numéros de version **majeure** , **mineure** , **Build** ou **révision** .

    > [!NOTE]
    > Vous ne devez jamais décrémenter un numéro de version ; Cela peut entraîner un comportement imprévisible de la mise à jour.

## <a name="see-also"></a>Voir aussi
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Guide pratique pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)