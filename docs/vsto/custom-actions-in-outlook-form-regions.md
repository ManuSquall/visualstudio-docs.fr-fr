---
title: "Actions personnalis&#233;es dans les zones de formulaire Outlook | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "actions personnalisées (développement Office dans Visual Studio)"
  - "zones de formulaire (développement Office dans Visual Studio), actions personnalisées"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Actions personnalis&#233;es dans les zones de formulaire Outlook
  Les actions affichent des boutons qui permettent aux utilisateurs de répondre à un élément de Microsoft Office Outlook.  Par exemple, les utilisateurs cliquent sur le bouton d'action **Répondre**, **Répondre à tous** ou **Transférer** pour répondre à un élément de messagerie.  Chacune de ces actions crée un élément de messagerie et remplit les champs de l'élément avec les informations de l'élément d'origine.  
  
 Vous pouvez créer une action personnalisée qui ouvre n'importe quel type d'élément Outlook.  Par exemple, vous pouvez ajouter une action personnalisée qui ouvre un nouvel élément de rendez\-vous ou de tâche.  Définissez les propriétés d'une action personnalisée ou utilisez du code personnalisé pour renseigner les champs du nouvel élément.  Les actions personnalisées s'affichent dans la liste déroulante **Actions personnalisées** d'un élément ouvert dans une fenêtre d'Inspecteur Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ajout d'actions personnalisées à une zone de formulaire  
 Pour ajouter une action personnalisée à une zone de formulaire, utilisez la boîte de dialogue **Actions personnalisées**.  Vous pouvez ouvrir la boîte de dialogue **actions personnalisées** dans **Explorateur de solutions** en développant le nœud **manifeste** , en sélectionnant la propriété **CustomActions** , puis en cliquant sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\).  
  
 Vous pouvez utiliser la boîte de dialogue **Actions personnalisées** pour spécifier un *formulaire cible*.  Le formulaire cible est le formulaire qui s'affiche lorsque l'utilisateur exécute l'action personnalisée.  
  
 Vous pouvez également utiliser la boîte de dialogue **Actions personnalisées** pour spécifier la manière dont vous souhaitez que les informations de l'élément d'origine s'affichent dans le formulaire cible.  
  
 Le tableau suivant décrit les propriétés disponibles dans la boîte de dialogue **Actions personnalisées**.  
  
|Propriété|Description|  
|---------------|-----------------|  
|**AddressLike**|Spécifie la manière dont le formulaire cible sera adressé.|  
|**Body**|Spécifie la manière dont le corps de l'élément d'origine est ajouté au formulaire cible.|  
|**Activé**|Indique si l'action personnalisée est activée.  Si cette propriété a la valeur **false**, l'action personnalisée est désactivée.|  
|**Méthode**|Spécifie le type de réponse disponible lorsque l'action personnalisée est exécutée.  L'action personnalisée peut envoyer ou ouvrir le formulaire ou demander à l'utilisateur s'il souhaite envoyer ou ouvrir le formulaire.|  
|**Nom**|Spécifie le nom interne que vous pouvez utiliser pour référencer cette action personnalisée dans le code.|  
|**ShowOnRibbon**|Indique si l'action personnalisée doit être affichée sur le ruban de l'élément d'origine.|  
|**SubjectPrefix**|Spécifie le texte inséré au début de la ligne Objet du formulaire cible.|  
|**TargetForm**|Spécifie le nom de classe de message du formulaire cible.  Par exemple, entrez **IPM.Task** pour ouvrir un formulaire de tâche.|  
|**Titre**|Spécifie l'étiquette du bouton d'action personnalisée.|  
  
## Personnalisation d'une action personnalisée au moment de l'exécution  
 Vous pouvez utiliser du code pour ajouter un comportement à l'action personnalisée.  Par exemple, vous pouvez ajouter du code qui ajoute les noms des destinataires en tant que participants à un nouvel élément de rendez\-vous.  À cette fin, gérez l'événement [CustomAction](HV05247448) de l'objet [Action](HV05247650).  
  
## Voir aussi  
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Association d'une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  