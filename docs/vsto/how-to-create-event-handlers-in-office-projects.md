---
title: "Comment : créer des gestionnaires d’événements dans les projets Office | Documents Microsoft"
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
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c392d365ca14daeb204f4ee2f331bb1fe86ad304
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Comment : créer des gestionnaires d'événements dans les projets Office
  Il existe plusieurs façons de créer des gestionnaires d’événements en Visual Basic et c#. En mode conception, vous pouvez créer des gestionnaires d’événements pour les contrôles de la valeur par défaut en double-cliquant sur le contrôle, ou utiliser le volet d’événements de la **propriétés** fenêtre pour créer des gestionnaires pour tout événement sur le contrôle. Toutefois, si vous êtes en mode Code, vous ne souhaitez ne peut-être pas basculer vers l’affichage de conception pour créer un gestionnaire d’événements.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Pour créer un gestionnaire d’événements en Visual Basic  
  
1.  À partir de la **nom de la classe** la liste déroulante en haut de l’éditeur de Code, sélectionnez l’objet que vous souhaitez créer un gestionnaire d’événements.  
  
    > [!NOTE]  
    >  Si vous souhaitez créer des gestionnaires d’événements pour `ThisDocument` ou `ThisWorkbook`, vous devez sélectionner **(événements ThisDocument)** ou **(événements ThisWorkbook)** dans le **nom de la classe**liste déroulante  
  
2.  À partir de la **nom de la méthode** liste déroulante en haut de l’éditeur de Code, sélectionnez l’événement.  
  
     Visual Studio crée le Gestionnaire d’événements et déplace le point d’insertion au gestionnaire d’événements nouvellement créé. Si le Gestionnaire d’événements existe déjà, le point d’insertion se déplace vers le Gestionnaire d’événements existant.  
  
### <a name="to-create-an-event-handler-in-c"></a>Pour créer un gestionnaire d’événements en c#  
  
1.  Créer le délégué d’événement dans le **démarrage** événement de la classe en tapant le nom d’événement qualifié suivi d’un espace, puis en tapant  **+=**  par la suite sans espace. Exemple :  
  
     `this.<object name>.<event name> +=`  
  
2.  À la fin de la ligne de code, appuyez deux fois sur la touche TAB.  
  
     Visual Studio automatiquement termine à la ligne de code, crée le Gestionnaire d’événements et déplace le point d’insertion au gestionnaire d’événements nouvellement créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Procédure pas à pas : Programmation d’événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)  
  
  