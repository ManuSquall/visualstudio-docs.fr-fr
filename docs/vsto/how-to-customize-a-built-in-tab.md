---
title: 'Comment : personnaliser un onglet intégré'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257265"
---
# <a name="how-to-customize-a-built-in-tab"></a>Comment : personnaliser un onglet intégré
  Vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Un onglet intégré est un onglet qui existe déjà sur le ruban d'une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel. Lorsque vous créez un groupe personnalisé, il apparaît en dernier sous l'onglet, mais vous pouvez déplacer votre groupe n'importe où sur l'onglet.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Vous pouvez ajouter des groupes à un onglet intégré, mais vous ne pouvez pas supprimer les groupes intégrés d'un onglet intégré.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Pour ajouter des groupes à un onglet intégré  
  
1.  Cliquez sur le fichier de code de ruban dans **l’Explorateur de solutions**, puis cliquez sur **Concepteur de vues**.  
  
    > [!NOTE]  
    >  Si le fichier de code du ruban n’apparaît pas dans **l’Explorateur de solutions**, vous devez ajouter un **élément ruban** à votre projet. Consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Avec le bouton droit n’importe quel onglet du Concepteur de ruban, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés** fenêtre, développez le **ControlId** propriété, puis définissez le **ControlIdType** propriété **Office**.  
  
4.  Définir le **OfficeId** propriété le *ID du contrôle* de l’onglet intégré que vous souhaitez personnaliser.  
  
     L'ID de contrôle est le nom qui identifie de façon unique les onglets, les groupes et les contrôles qui sont intégrés aux applications Microsoft Office.  
  
     Pour obtenir la liste d’ID de contrôle, consultez [les fichiers d’aide Office 2010 : identificateurs de contrôle interface Office fluent utilisateur](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser les groupes sur l’onglet.  
  
    > [!NOTE]  
    >  Les groupes intégrés n'apparaissent pas dans le concepteur. Par conséquent, la seule façon de déterminer si vous travaillez avec un onglet intégré consiste à examiner le **ControlId** propriété de l’onglet.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Pour positionner des groupes sur un onglet intégré  
  
1.  Dans le Concepteur de ruban, sélectionnez un groupe personnalisé.  
  
2.  Dans le **propriétés** fenêtre, développez le **Position** propriété.  
  
3.  Définir le **PositionType** propriété à la valeur appropriée :  
  
    -   **BeforeOfficeId** place le groupe avant un groupe intégré spécifié.  
  
    -   **AfterOfficeId** place le groupe après un groupe intégré spécifié.  
  
4.  Définir le **OfficeId** propriété ID du contrôle d’un groupe intégré.  
  
     Pour obtenir la liste d’ID de contrôle, consultez [les fichiers d’aide Office 2010 : identificateurs de contrôle interface Office fluent utilisateur](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Comment : afficher complément, les erreurs d’interface utilisateur](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  