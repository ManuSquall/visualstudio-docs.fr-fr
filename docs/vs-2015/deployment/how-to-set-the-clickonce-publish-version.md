---
title: 'Comment : définir la publication ClickOnce Version | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: b3965e9600fa3ef6a091ae8e32439e8e4f420668
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271711"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Comment : définir la version de publication ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` propriété détermine si l’application que vous publiez sera traitée comme une mise à jour. Chaque version de l’heure est incrémentée, l’application sera publiée en tant qu’une mise à jour.  
  
 Le `Publish Version` propriété peut être définie sur le **publier** page de la **Concepteur de projet**.  
  
> [!NOTE]
>  Il existe une option de projet qui incrémente automatiquement le `Publish Version` propriété chaque fois que l’application est publiée ; cette option est activée par défaut. Pour plus d’informations, consultez [Comment : incrémenter automatiquement la Version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Pour modifier la Version de publication  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans **Version de publication** champ, incrémentez la **majeure**, **mineure**, **générer**, ou **révision** version nombres.  
  
    > [!NOTE]
    >  Vous ne devez jamais décrémenter un numéro de version ; Cela peut provoquer comportement imprévisible de mise à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Guide pratique pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



