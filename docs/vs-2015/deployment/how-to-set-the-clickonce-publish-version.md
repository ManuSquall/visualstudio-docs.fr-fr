---
title: 'Comment : définir la version de publication ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839601"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Comment : définir la version de publication ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` propriété détermine si l’application que vous publiez sera traitée comme une mise à jour. Chaque fois que la version est incrémentée, l’application est publiée en tant que mise à jour.  
  
 La `Publish Version` propriété peut être définie sur la page **publier** du **Concepteur de projets**.  
  
> [!NOTE]
> Il existe une option de projet qui incrémente automatiquement la `Publish Version` propriété chaque fois que l’application est publiée. cette option est activée par défaut. Pour plus d’informations, consultez Guide pratique [pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Pour modifier la version de publication  
  
1. Quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Dans le champ **version de publication** , incrémentez les numéros de version **majeure**, **mineure**, **Build**ou **révision** .  
  
    > [!NOTE]
    > Vous ne devez jamais décrémenter un numéro de version ; Cela peut entraîner un comportement imprévisible de la mise à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Comment : incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
