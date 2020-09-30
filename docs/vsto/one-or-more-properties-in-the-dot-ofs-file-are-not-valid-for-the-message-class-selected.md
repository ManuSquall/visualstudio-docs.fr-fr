---
title: Propriétés non valides dans le fichier. OFS pour la classe de message»
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
ms.openlocfilehash: 66e8ecacffb58e945a3f80d03f47edc1329668d1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584657"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Propriétés non valides dans le fichier. OFS pour la classe de message

  L’erreur « une ou plusieurs propriétés dans le fichier. OFS n’est pas valide pour la classe de message sélectionnée » s’affiche lorsque vous importez une zone de formulaire conçue dans Outlook, mais qu’un ou plusieurs champs de la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez dans la dernière page de l’Assistant **nouvelle zone de formulaire** .

Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire contient un champ **adresse professionnelle** , vous recevez cette erreur, car une tâche n’a pas d’adresse professionnelle. Par conséquent, le champ **adresse professionnelle** n’est pas compatible avec la `IPM.Task` classe message.

 Vous pouvez sélectionner **tâche (IPM. Tâche)** sur la dernière page de l’Assistant **nouvelle zone de formulaire** . Si la zone de formulaire contient un champ **adresse professionnelle** , vous recevez cette erreur, car une tâche n’a pas d’adresse professionnelle. Par conséquent, le champ **adresse professionnelle** n’est pas compatible avec la `IPM.Task` classe message.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.

- Dans le concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message. Supprimez les champs que vous envisagez de sélectionner dans la dernière page de l’Assistant **nouvelle zone de formulaire** .

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
