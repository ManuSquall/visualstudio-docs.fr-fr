---
title: 'Procédure : Créer des gestionnaires d’événements dans les projets Office'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 537bae766b71744a61e5158b1a859cade4cdcda7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419649"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Procédure : Créer des gestionnaires d’événements dans les projets Office
  Il existe plusieurs façons de créer des gestionnaires d’événements en Visual Basic et c#. En mode conception, vous pouvez créer des gestionnaires d’événements pour les contrôles de la valeur par défaut en double-cliquant sur le contrôle, ou utiliser le volet événements de la **propriétés** fenêtre pour créer des gestionnaires pour tout événement sur le contrôle. Toutefois, si vous êtes en mode Code, vous ne souhaitez ne peut-être pas basculer en mode Design pour créer un gestionnaire d’événements.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Pour créer un gestionnaire d’événements en Visual Basic

1. À partir de la **nom de la classe** liste déroulante en haut de l’éditeur de Code, sélectionnez l’objet que vous souhaitez créer un gestionnaire d’événements.

    > [!NOTE]
    > Si vous souhaitez créer des gestionnaires d’événements pour `ThisDocument` ou `ThisWorkbook`, vous devez sélectionner **(événements ThisDocument)** ou **(événements ThisWorkbook)** dans le **nom de la classe**liste déroulante

2. À partir de la **nom de la méthode** liste déroulante en haut de l’éditeur de Code, sélectionnez l’événement.

     Visual Studio crée le Gestionnaire d’événements et déplace le point d’insertion vers le Gestionnaire d’événements nouvellement créé. Si le Gestionnaire d’événements existe déjà, le point d’insertion se déplace vers le Gestionnaire d’événements existant.

### <a name="to-create-an-event-handler-in-c"></a>Pour créer un gestionnaire d’événements en C\#

1. Créer le délégué d’événement dans le **démarrage** événement de la classe en tapant le nom d’événement qualifié suivi d’un espace, puis en tapant **+=** par la suite sans espace. Exemple :

     `this.<object name>.<event name> +=`

2. À la fin de la ligne de code, appuyez deux fois sur la touche TAB.

     Visual Studio automatiquement termine à la ligne de code crée le Gestionnaire d’événements et déplace le point d’insertion vers le Gestionnaire d’événements nouvellement créé.

## <a name="see-also"></a>Voir aussi
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Procédure pas à pas : Programmer par rapport aux événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Générer des solutions Office](../vsto/building-office-solutions.md)
