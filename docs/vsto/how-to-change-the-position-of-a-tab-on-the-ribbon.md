---
title: "Comment : modifier la Position d’un onglet sur le ruban | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40907d71bae8c8c25f06b3b1f3d4af8b9f79c385
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Comment : modifier la position d'un onglet dans le ruban
  Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban à l’aide de la **éditeur de collections Tab**. Vous pouvez placer des onglets personnalisés avant ou après un onglet intégré du ruban. Un onglet intégré est un onglet qui existe déjà sur le ruban d’une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Pour modifier l’ordre des onglets du ruban  
  
1.  Sélectionnez le fichier de code du ruban (fichier .vb ou .cs) dans **l’Explorateur de solutions**.  
  
2.  Sur le **vue** menu, cliquez sur **concepteur**.  
  
3.  Cliquez sur le Concepteur de ruban, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés** fenêtre, sélectionnez le **onglets** propriété, puis cliquez sur le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "Mobile ASP.NET Ellipse de concepteur")).  
  
     Le **éditeur de collections Tab** s’affiche.  
  
5.  Dans le **éditeur de collections Tab**, dans le **membres** , sélectionnez l’onglet que vous souhaitez déplacer et cliquez sur l’ou les flèches pour modifier l’ordre de tabulation.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Pour positionner un onglet avant ou après un onglet intégré du ruban  
  
1.  Dans le Concepteur de ruban, sélectionnez un onglet personnalisé.  
  
2.  Dans le **propriétés** fenêtre, développez le **ControlId** propriété et assurez-vous que la valeur de la **ControlIdType** est définie sur **personnalisé**.  
  
3.  Dans le **propriétés** fenêtre, développez le **Position** propriété.  
  
4.  Définir le **PositionType** propriété la valeur appropriée :  
  
    -   **BeforeOfficeId** avant un onglet intégré spécifié.  
  
    -   **AfterOfficeId** positionne le groupe après un onglet intégré spécifié.  
  
5.  Définir le **OfficeId** propriété de l’ID de contrôle d’un onglet intégré.  
  
     Pour obtenir la liste des ID de contrôle, consultez [fichiers d’aide Office 2010 : identificateurs de contrôle d’Interface utilisateur Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : création d’un onglet personnalisé à l’aide d’un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  