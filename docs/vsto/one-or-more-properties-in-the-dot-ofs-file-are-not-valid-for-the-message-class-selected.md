---
title: Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095267"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
  Cette erreur apparaît lorsque vous importez une zone de formulaire conçue dans Outlook, mais un ou plusieurs champs sur la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez dans la page finale de le **nouvelle zone de formulaire** Assistant.

Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.

 Vous pouvez sélectionner **tâche (gestion intégrée. Tâche)** sur la page finale de le **nouvelle zone de formulaire** Assistant. Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.

- Dans le Concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message. Supprimer des champs que vous souhaitez sélectionner dans la page finale de le **nouvelle zone de formulaire** Assistant.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
