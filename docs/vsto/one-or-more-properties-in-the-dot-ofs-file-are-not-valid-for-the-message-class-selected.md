---
title: "Une ou plusieurs propriétés dans le fichier .ofs ne sont pas valides pour la classe de message sélectionnée | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 6ab0b36921911ac8c70501096868f47a40371f79
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Au moins une propriété du fichier .ofs n'est pas valide pour la classe de message sélectionnée
  Cette erreur s’affiche quand vous importez une zone de formulaire conçue dans Outlook, mais qu’un ou plusieurs champs de la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez à la dernière page de l’Assistant **Nouvelle zone de formulaire** .  
  
 Par exemple, vous pouvez sélectionner **Tâche (IPM.Task)** à la dernière page de l’Assistant **Nouvelle zone de formulaire** . Si la zone de formulaire contient un champ **Adresse professionnelle** , vous recevez cette erreur, car une tâche n’a pas d’adresse d’entreprise. Par conséquent, le champ **Adresse professionnelle** n’est pas compatible avec la classe de message IPM.Task.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   À la dernière page de l’Assistant **Nouvelle zone de formulaire** , sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.  
  
-   Dans le Concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message que vous prévoyez de sélectionner à la dernière page de l’Assistant **Nouvelle zone de formulaire** .  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : importation d’une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  