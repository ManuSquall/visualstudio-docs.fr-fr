---
title: Actions personnalisées dans les zones de formulaire Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec4c6a0ce361102ab216bc0c9f460a0bdd7a4a0d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="custom-actions-in-outlook-form-regions"></a>Actions personnalisées dans les zones de formulaire Outlook
  Actions affichent des boutons qui permettent aux utilisateurs de répondre à un élément de Microsoft Office Outlook. Par exemple, pour répondre à un élément de messagerie, les utilisateurs cliquent sur le **réponse**, **répondre à tous**, ou **par progression** boutons d’action. Chacune de ces actions crée un élément de messagerie et renseigne les champs de l’élément à l’aide des informations à partir de l’élément d’origine.  
  
 Vous pouvez créer une action personnalisée qui s’ouvre tout type d’élément Outlook. Par exemple, vous pouvez ajouter une action personnalisée qui ouvre un nouvel élément de rendez-vous ou une tâche. Définir les propriétés d’une action personnalisée ou utiliser du code personnalisé pour remplir les champs du nouvel élément. Actions personnalisées s’affichent dans le **Actions personnalisées** liste déroulante d’un élément qui est ouvert dans une fenêtre d’inspecteur Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Ajouter des actions personnalisées à une zone de formulaire  
 Pour ajouter une action personnalisée à une zone de formulaire, utilisez le **personnalisées Actions** boîte de dialogue. Vous pouvez ouvrir le **Actions personnalisées** boîte de dialogue de **l’Explorateur de solutions** en développant le **manifeste** nœud, en sélectionnant le **CustomActions**propriété, puis en cliquant sur le bouton de sélection (![ellipse de concepteur mobile ASP.NET](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")).  
  
 Vous pouvez utiliser la **Actions personnalisées** boîte de dialogue pour spécifier un *cible du formulaire*. Un formulaire de la cible est le formulaire qui apparaît lorsque l’utilisateur exécute l’action personnalisée.  
  
 Vous pouvez également utiliser le **Actions personnalisées** boîte de dialogue pour spécifier la façon dont vous souhaitez des informations à partir de l’élément d’origine s’affiche sous la forme de la cible.  
  
 Le tableau suivant décrit les propriétés qui sont disponibles dans le **Actions personnalisées** boîte de dialogue.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**AddressLike**|Spécifie la façon dont le formulaire cible sera traité.|  
|**Corps**|Spécifie comment le corps de l’élément d’origine est ajouté au formulaire cible.|  
|**Activé**|Indique si l’action personnalisée est activée. Si cette propriété est définie sur **false**, l’action personnalisée est désactivée.|  
|**Méthode**|Spécifie le type de réponse disponible lors de l’exécution de l’action personnalisée. L’action personnalisée peut envoyer le formulaire, ouvrez le formulaire ou inviter l’utilisateur qu’ils souhaitent envoyer ou ouvrir le formulaire.|  
|**Name**|Spécifie le nom interne que vous pouvez utiliser pour référencer cette action personnalisée dans le code.|  
|**ShowOnRibbon**|Indique s’il faut afficher l’action personnalisée sur le ruban de l’élément d’origine.|  
|**SubjectPrefix**|Spécifie le texte est inséré au début de la ligne objet du formulaire cible.|  
|**TargetForm**|Spécifie le nom de classe du formulaire cible. Par exemple, tapez **gestion intégrée. Tâche** pour ouvrir un formulaire de tâche.|  
|**Titre**|Spécifie l’étiquette du bouton d’action personnalisée.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Personnaliser une action personnalisée lors de l’exécution  
 Vous pouvez également ajouter le comportement à l’action personnalisée à l’aide de code. Par exemple, vous pouvez ajouter le code qui prend les noms des destinataires du courrier électronique et ajoute les noms en tant que participants dans un nouvel élément de rendez-vous. Pour ce faire, vous devez gérer le [CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx) l’événement de la [objet MailItem](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  