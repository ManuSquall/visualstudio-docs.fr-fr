---
title: "Comment : ajouter des contrôles au mode Backstage | Documents Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7a58b9b59dd3625b3b9b7d8e9e3e77964eb0f2a5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Comment : ajouter des contrôles au mode Backstage
  Vous pouvez utiliser le Concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier** onglet lorsque vous exécutez l’application, les contrôles que vous ajoutez à la **fichier** onglet s’affiche un groupe nommé  **Les compléments**.  
  
 Vous ne pouvez pas positionner des contrôles avant ou après les contrôles prédéfinis à l’aide du Concepteur de ruban dans Visual Studio. Un contrôle intégré est un contrôle qui figure déjà dans le mode Backstage. Si vous souhaitez positionner des contrôles avant ou après les contrôles intégrés, vous devez utiliser un fichier XML de ruban. Pour plus d’informations sur **ruban (XML)**, consultez [ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [présentation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [personnalisation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Pour ajouter des contrôles au mode Backstage  
  
1.  Ouvrez l’élément Ruban en mode Création.  
  
     Pour plus d’informations sur l’ajout d’un **ruban (Concepteur visuel)** d’élément à votre projet, consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Dans le Concepteur de ruban, cliquez sur le **fichier** onglet.  
  
     Un concepteur de menu s’affiche. Cette aire de conception ne contient pas de contrôles.  
  
3.  À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un des contrôles suivants vers le Concepteur de menus :  
  
    -   Bouton  
  
    -   Case à cocher  
  
    -   Galerie  
  
    -   Menu  
  
    -   Séparateur  
  
    -   SplitButton  
  
    -   Bouton bascule  
  
4.  Faites glisser les contrôles pour les déplacer vers de nouveaux emplacements sur le menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procédure pas à pas : création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  