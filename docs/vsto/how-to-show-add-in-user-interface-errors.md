---
title: "Comment : afficher les erreurs d’Interface utilisateur du complément | Documents Microsoft"
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
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4ce5204855cd6ebe468d652b8420cddc7fd19a1a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Comment : afficher les erreurs de l'interface utilisateur du complément
  Par défaut, si un complément VSTO tente de manipuler l’interface utilisateur de Microsoft Office et qu’il échoue, aucun message d’erreur n’est affiché. Toutefois, vous pouvez configurer les applications Microsoft Office pour afficher des messages en cas d’erreur liée à l’interface utilisateur. Vous pouvez utiliser ces messages pour vous aider à déterminer pourquoi un ruban personnalisé n’est pas affiché, ou pourquoi un ruban apparaît mais pas les contrôles.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Pour afficher les erreurs d’interface utilisateur du complément VSTO  
  
1.  Démarrez l’application.  
  
2.  Cliquez sur l'onglet **Fichier** .  
  
3.  Cliquez sur **Options**.  
  
4.  Dans le volet des catégories, cliquez sur **Avancé**.  
  
5.  Dans le volet d’informations, sélectionnez **Afficher les erreurs d’interface utilisateur du complément VSTO**, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Pour Outlook, la case à cocher **Afficher les erreurs d’interface utilisateur du complément VSTO** se trouve dans la section **Développeur** du volet d’informations. Pour les autres applications, elle se trouve dans la section **Général** du volet d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)  
  
  