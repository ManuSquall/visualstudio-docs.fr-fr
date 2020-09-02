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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977859"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
  Cette erreur apparaît lorsque vous importez une zone de formulaire conçue dans Outlook, mais qu’un ou plusieurs champs de la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez dans la dernière page de l’Assistant **nouvelle zone de formulaire** .

Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire contient un champ **adresse professionnelle** , vous recevez cette erreur, car une tâche n’a pas d’adresse professionnelle. Par conséquent, le champ **adresse professionnelle** n’est pas compatible avec la `IPM.Task` classe message.

 Vous pouvez sélectionner **tâche (IPM. Tâche)** sur la dernière page de l’Assistant **nouvelle zone de formulaire** . Si la zone de formulaire contient un champ **adresse professionnelle** , vous recevez cette erreur, car une tâche n’a pas d’adresse professionnelle. Par conséquent, le champ **adresse professionnelle** n’est pas compatible avec la `IPM.Task` classe message.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.

- Dans le concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message. Supprimez les champs que vous envisagez de sélectionner dans la dernière page de l’Assistant **nouvelle zone de formulaire** .

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
