---
title: Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
ms.date: 02/02/2017
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
ms.openlocfilehash: 6d6469c48def1a5d21eb160cb4ad6d14704bc101
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909123"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
  Cette erreur apparaît lorsque vous importez une zone de formulaire conçue dans Outlook, mais un ou plusieurs champs sur la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez dans la page finale de le **nouvelle zone de formulaire** Assistant.  

Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.  
  
 Vous pouvez sélectionner **tâche (gestion intégrée. Tâche)** sur la page finale de le **nouvelle zone de formulaire** Assistant. Si la zone de formulaire a un **adresse professionnelle** champ, vous recevez cette erreur, car une tâche n’a pas une adresse professionnelle. Par conséquent, le **adresse professionnelle** champ n’est pas compatible avec la `IPM.Task` classe de message.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.  
  
-   Dans le Concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message. Supprimer des champs que vous souhaitez sélectionner dans la page finale de le **nouvelle zone de formulaire** Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
