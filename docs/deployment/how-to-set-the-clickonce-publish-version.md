---
title: 'Comment : définir la publication ClickOnce Version | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ea53e5e50aebc7c8ad201f6dae1003350f9fa4e2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633445"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Guide pratique pour définir la version de publication ClickOnce
Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propriété détermine si l’application que vous publiez sera traitée comme une mise à jour. Chaque version de l’heure est incrémentée, l’application sera publiée en tant qu’une mise à jour.

 Le `Publish Version` propriété peut être définie sur le **publier** page de la **Concepteur de projet**.

> [!NOTE]
>  Il existe une option de projet qui incrémente automatiquement le `Publish Version` propriété chaque fois que l’application est publiée ; cette option est activée par défaut. Pour plus d’informations, consultez [Comment : incrémenter automatiquement la Version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Pour modifier la version de publication

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Cliquez sur l’onglet **Publier**.

3.  Dans **Version de publication** champ, incrémentez la **majeure**, **mineure**, **générer**, ou **révision** version nombres.

    > [!NOTE]
    >  Vous ne devez jamais décrémenter un numéro de version ; Cela peut provoquer comportement imprévisible de mise à jour.

## <a name="see-also"></a>Voir aussi
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Guide pratique pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)