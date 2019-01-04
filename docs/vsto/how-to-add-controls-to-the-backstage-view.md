---
title: 'Procédure : Ajouter des contrôles au mode Backstage '
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6500118f775f9dfab75b615f28fab9e166a0104a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924655"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procédure : Ajouter des contrôles au mode Backstage
  Vous pouvez utiliser le Concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier** onglet. Lorsque vous exécutez l’application, les contrôles que vous ajoutez à la **fichier** onglet s’affiche un groupe nommé **Add-ins**.  
  
 Vous ne pouvez pas placer des contrôles avant ou après les contrôles prédéfinis à l’aide du Concepteur de ruban dans Visual Studio. Un contrôle intégré est un contrôle qui figure déjà dans le mode Backstage. Si vous souhaitez positionner des contrôles avant ou après les contrôles prédéfinis, vous devez utiliser un fichier XML du ruban. Pour plus d’informations sur **ruban (XML)**, consultez [ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [Introduction à la Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [personnaliser la Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Pour ajouter des contrôles au mode Backstage  
  
1.  Ouvrez l’élément Ruban en mode Design.  
  
     Pour plus d’informations sur la façon d’ajouter un **ruban (Concepteur visuel)** d’élément à votre projet, consultez [Comment : Commencer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Dans le Concepteur de ruban, cliquez sur le **fichier** onglet.  
  
     Un concepteur de menus s’affiche. Cette aire de conception ne contient pas tous les contrôles.  
  
3.  À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser les contrôles suivants sur le Concepteur de menus :  
  
    -   Bouton  
  
    -   Case à cocher  
  
    -   Galerie  
  
    -   Menu  
  
    -   Séparateur  
  
    -   SplitButton  
  
    -   Bouton bascule  
  
4.  Faites glisser les contrôles pour les déplacer vers les nouveaux emplacements sur le menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Guide pratique pour Prise en main personnaliser le ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
