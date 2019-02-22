---
title: 'Procédure : Afficher des erreurs d’interface utilisateur du complément'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12fc82fd0c04e9f05ff55be24c3527ca95a357fb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596008"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Procédure : Afficher des erreurs d’interface utilisateur du complément
  Par défaut, si un complément, VSTO tente de manipuler l’interface utilisateur de Microsoft Office (IU) et échoue, aucun message d’erreur ne s’affiche. Toutefois, vous pouvez configurer les applications Microsoft Office pour afficher des messages en cas d’erreur liée à l’interface utilisateur. Vous pouvez utiliser ces messages pour aider à déterminer pourquoi un ruban personnalisé n’apparaît pas, ou pourquoi un ruban apparaît mais pas les contrôles.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Pour afficher les erreurs d’interface utilisateur du complément VSTO

1.  Démarrez l’application.

2.  Cliquez sur l'onglet **Fichier** .

3.  Cliquez sur **Options**.

4.  Dans le volet des catégories, cliquez sur **Avancé**.

5.  Dans le volet d’informations, sélectionnez **Afficher les erreurs d’interface utilisateur du complément VSTO**, puis cliquez sur **OK**.

    > [!NOTE]
    >  Pour Outlook, la case à cocher **Afficher les erreurs d’interface utilisateur du complément VSTO** se trouve dans la section **Développeur** du volet d’informations. Pour les autres applications, elle se trouve dans la section **Général** du volet d’informations.

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
