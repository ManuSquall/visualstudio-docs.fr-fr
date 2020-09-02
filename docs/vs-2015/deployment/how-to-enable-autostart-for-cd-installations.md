---
title: 'Procédure : activer le démarrage automatique pour les installations à partir d’un CD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153784"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Comment : activer le démarrage automatique pour les installations depuis un CD-ROM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors du déploiement d’une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application au moyen d’un support amovible tel qu’un CD-ROM ou un DVD-ROM, vous pouvez activer `AutoStart` afin que l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application soit lancée automatiquement lorsque le média est inséré.  
  
 `AutoStart` peut être activé sur la page **publier** du **Concepteur de projets**.  
  
### <a name="to-enable-autostart"></a>Pour activer le démarrage automatique  
  
1. Quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Cliquez sur le bouton **Options** .  
  
     La boîte de dialogue **options de publication** s’affiche.  
  
4. Cliquez sur **Déploiement**.  
  
5. Activez la case à cocher **pour les installations de CD, démarrer automatiquement le programme d’installation lorsque le CD est inséré** .  
  
     Un fichier autorun. inf sera copié à l’emplacement de publication lors de la publication de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
