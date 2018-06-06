---
title: Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692497"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
  Cette erreur s’affiche lorsque vous importez une zone de formulaire conçue dans Outlook, mais un ou plusieurs champs dans la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez dans la page finale de le **nouvelle zone de formulaire** Assistant.  

Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.  
  
 Vous pouvez sélectionner **tâche (gestion intégrée. Tâche)** sur la page finale de le **nouvelle zone de formulaire** Assistant. Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.  
  
-   Dans le Concepteur de formulaires dans Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message. Supprimer des champs que vous envisagez de sélectionner sur la dernière page de la **nouvelle zone de formulaire** Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Importation d’une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  