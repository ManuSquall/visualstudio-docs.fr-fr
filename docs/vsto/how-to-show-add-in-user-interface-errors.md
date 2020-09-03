---
title: 'Comment : afficher les erreurs d’interface utilisateur du complément'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 49985589c021192454bf0dd58929c9ef5646aec9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545780"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Comment : afficher les erreurs d’interface utilisateur du complément
  Par défaut, si un complément VSTO tente de manipuler la Microsoft Office interface utilisateur et échoue, aucun message d’erreur n’est affiché. Toutefois, vous pouvez configurer les applications Microsoft Office pour afficher des messages en cas d’erreur liée à l’interface utilisateur. Vous pouvez utiliser ces messages pour vous aider à déterminer pourquoi un ruban personnalisé n’apparaît pas, ou pourquoi un ruban apparaît mais aucun contrôle n’apparaît.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Pour afficher les erreurs d’interface utilisateur du complément VSTO

1. Lancez l’application.

2. Cliquez sur l'onglet **Fichier** .

3. Cliquez sur **Options**.

4. Dans le volet des catégories, cliquez sur **Avancé**.

5. Dans le volet d’informations, sélectionnez **Afficher les erreurs d’interface utilisateur du complément VSTO**, puis cliquez sur **OK**.

    > [!NOTE]
    > Pour Outlook, la case à cocher **Afficher les erreurs d’interface utilisateur du complément VSTO** se trouve dans la section **Développeur** du volet d’informations. Pour les autres applications, elle se trouve dans la section **Général** du volet d’informations.

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
