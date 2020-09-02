---
title: 'Comment : créer des gestionnaires d’événements dans les projets Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee85d89dcb990cebd595dadbd7b28add4a7b371a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538305"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Comment : créer des gestionnaires d’événements dans les projets Office
  Il existe plusieurs façons de créer des gestionnaires d’événements en Visual Basic et en C#. En mode Design, vous pouvez créer les gestionnaires d’événements par défaut des contrôles en double-cliquant sur le contrôle, ou utiliser le volet événements de la fenêtre **Propriétés** pour créer des gestionnaires pour tout événement sur le contrôle. Toutefois, si vous êtes en mode Code, vous pouvez ne pas vouloir basculer vers Mode Création pour créer un gestionnaire d’événements.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Pour créer un gestionnaire d’événements dans Visual Basic

1. Dans la liste déroulante nom de la **classe** en haut de l’éditeur de code, sélectionnez l’objet pour lequel vous souhaitez créer un gestionnaire d’événements.

    > [!NOTE]
    > Si vous souhaitez créer des gestionnaires d’événements pour `ThisDocument` ou `ThisWorkbook` , vous devez sélectionner **(événements ThisDocument)** ou **(événements ThisWorkbook)** dans la liste déroulante nom de la **classe** .

2. Dans la liste déroulante nom de la **méthode** en haut de l’éditeur de code, sélectionnez l’événement.

     Visual Studio crée le gestionnaire d’événements et déplace le point d’insertion vers le gestionnaire d’événements nouvellement créé. Si le gestionnaire d’événements existe déjà, le point d’insertion se déplace vers le gestionnaire d’événements existant.

### <a name="to-create-an-event-handler-in-c"></a>Pour créer un gestionnaire d’événements en C\#

1. Créez le délégué d’événement dans l’événement **Startup** de la classe en tapant le nom d’événement qualifié suivi d’un espace, puis **+=** en tapant sans espace après. Par exemple :

     `this.<object name>.<event name> +=`

2. À la fin de la ligne de code, appuyez deux fois sur la touche TAB.

     Visual Studio complète automatiquement la ligne de code, crée le gestionnaire d’événements et déplace le point d’insertion vers le gestionnaire d’événements nouvellement créé.

## <a name="see-also"></a>Voir aussi
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Procédure pas à pas : programmer sur les événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Créer des solutions Office](../vsto/building-office-solutions.md)
