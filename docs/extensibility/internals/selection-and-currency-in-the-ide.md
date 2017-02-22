---
title: "S&#233;lection et la devise dans l’IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "devise, l’IDE de Visual Studio"
  - "IDE, sélection"
  - "sélection, l’IDE de Visual Studio"
  - "IDE, devise"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# S&#233;lection et la devise dans l’IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tient à jour l’environnement de développement intégré \(IDE\) plus d’informations sur les utilisateurs les objets actuellement sélectionnés à l’aide de sélection *contexte*. Avec le contexte de sélection, les VSPackages peuvent prendre part à monétaire suivi de deux manières :  
  
-   Par la propagation des informations de devise sur les packages VS pour l’IDE.  
  
-   En surveillant les sélections actives d’utilisateurs dans l’IDE.  
  
## Contexte de sélection  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalement effectue le suivi des devises IDE dans son propre objet de contexte de sélection global. Le tableau suivant présente les éléments qui composent le contexte de sélection.  
  
|Élément|Description|  
|-------------|-----------------|  
|Hiérarchie actuelle|En général, le projet actuel. une hiérarchie actuelle NULL indique que la solution dans son ensemble est en cours.|  
|ItemID actuel|L’élément sélectionné dans la hiérarchie actuelle ; Lorsqu’il existe plusieurs sélections dans une fenêtre de projet, il peut y avoir plusieurs éléments en cours.|  
|En cours `SelectionContainer`|Contient un ou plusieurs objets dont la fenêtre Propriétés doit afficher les propriétés.|  
  
 En outre, l’environnement gère deux listes globales :  
  
-   Une liste d’identificateurs de commande actives l’interface utilisateur  
  
-   Une liste des types d’élément actif.  
  
### Sélection et Types de fenêtres  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE windows organise deux types généraux :  
  
-   Windows de type de hiérarchie  
  
-   Fenêtres frame, telles que des fenêtres d’outils et de documents  
  
 L’IDE effectue le suivi de devise différemment pour chacun de ces types de fenêtres.  
  
 La fenêtre de type de projet plus courante est l’Explorateur de solutions, qui contrôle l’IDE. Une fenêtre de projet effectue le suivi de la hiérarchie globale et ItemID du contexte global de sélection et la fenêtre dépend de la sélection de l’utilisateur afin de déterminer la hiérarchie actuelle. Pour windows de type de projet, l’environnement fournit le service global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, via lesquelles VSPackages peut surveiller les valeurs actuelles des éléments ouverts. Propriété de navigation dans l’environnement est pilotée par ce service global.  
  
 Fenêtres frame, utilisent quant à eux, sera imprimé dans la fenêtre frame pour envoyer la valeur de SelectionContext \(le trio hiérarchie\/ItemID\/SelectionContainer\). . Fenêtres frame utilisent le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> à cet effet. Le DocObject pousser uniquement des valeurs pour le conteneur de sélection, en laissant les valeurs locales pour la hiérarchie et ItemID inchangé, comme cela est courant pour les documents enfants MDI.  
  
### Événements et devise  
 Deux types d’événements peuvent se produire et affectent la notion de l’environnement de devise :  
  
-   Événements qui sont propagées au niveau global et de modifier le contexte de sélection de fenêtre frame. Ce type d’événement comprennent une fenêtre enfant MDI en cours, une fenêtre outil global en cours d’ouverture ou une fenêtre d’outil de type de projet en cours d’ouverture.  
  
-   Événements qui modifient les éléments suivis dans le contexte de sélection de fenêtre frame. Exemples incluent la modification de sélection au sein de DocObject ou la modification de sélection dans une fenêtre de projet.  
  
## Voir aussi  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Vos commentaires à l'utilisateur](../../extensibility/internals/feedback-to-the-user.md)