---
title: Activer le démarrage automatique pour les installations de CD | Microsoft Docs
description: Découvrez comment activer le démarrage automatique lors du déploiement d’une application ClickOnce au moyen d’un support amovible tel qu’un CD-ROM ou un DVD-ROM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6ed3df72b98454c4669e7d9bcd21c0612a6fef3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349956"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Guide pratique pour activer le démarrage automatique pour les installations de CD
Lors du déploiement d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application au moyen d’un support amovible tel qu’un CD-ROM ou un DVD-ROM, vous pouvez activer `AutoStart` afin que l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application soit lancée automatiquement lorsque le média est inséré.

 `AutoStart` peut être activé sur la page **publier** du **Concepteur de projets**.

### <a name="to-enable-autostart"></a>Pour activer le démarrage automatique

1. Quand un projet est sélectionné dans **Explorateur de solutions** , dans le menu **projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **Options** .

     La boîte de dialogue **options de publication** s’affiche.

4. Cliquez sur **Déploiement**.

5. Activez la case à cocher **pour les installations de CD, démarrer automatiquement le programme d’installation lorsque le CD est inséré** .

     Un fichier *Autorun. inf* sera copié à l’emplacement de publication lors de la publication de l’application.

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)