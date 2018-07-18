---
title: Sélection et la devise dans l’IDE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c58cb08f82b10970424600843b0fedcf477fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131263"
---
# <a name="selection-and-currency-in-the-ide"></a>Sélection et la devise dans l’IDE
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) gère plus d’informations sur les utilisateurs les objets actuellement sélectionnés à l’aide de sélection *contexte*. Avec le contexte de sélection, VSPackages peuvent prendre part dans la devise de suivi de deux manières :  
  
-   En propageant les informations de devise sur les VSPackages à l’IDE.  
  
-   En surveillant les sélections d’utilisateurs actuellement actifs dans l’IDE.  
  
## <a name="selection-context"></a>Contexte de sélection  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalement effectue le suivi de devise IDE dans son propre objet de contexte de sélection globale. Le tableau suivant présente les éléments qui composent le contexte de sélection.  
  
|Élément|Description|  
|-------------|-----------------|  
|Hiérarchie actuelle|En général, le projet actuel. une hiérarchie actuelle de valeur NULL indique que la solution dans son ensemble est en cours.|  
|ItemID actuel|L’élément sélectionné dans la hiérarchie actuelle ; Lorsqu’il existe plusieurs sélections dans une fenêtre de projet, il peut y avoir plusieurs éléments en cours.|  
|En cours `SelectionContainer`|Contient l’un ou plusieurs objets pour lesquels la fenêtre Propriétés doit afficher les propriétés.|  
  
 En outre, l’environnement gère deux listes globales :  
  
-   Une liste d’identificateurs de commande actives l’interface utilisateur  
  
-   Liste des types d’éléments actuellement actif.  
  
### <a name="window-types-and-selection"></a>Sélection et les Types de fenêtres  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE windows organise deux types généraux :  
  
-   Windows de type de hiérarchie  
  
-   Fenêtres frame, tels que les fenêtres Outil et document  
  
 L’IDE effectue le suivi de devise différemment pour chacun de ces types de fenêtre.  
  
 La fenêtre de type de projet plus courante est l’Explorateur de solutions, qui contrôle de l’IDE. Une fenêtre de type de projet effectue le suivi de la hiérarchie globale et ItemID du contexte global de sélection et la fenêtre s’appuie sur la sélection de l’utilisateur pour déterminer la hiérarchie actuelle. Pour windows de type de projet, l’environnement fournit le service global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, via lesquelles VSPackages peut surveiller les valeurs actuelles des éléments ouverts. Propriété de navigation dans l’environnement est pilotée par ce service global.  
  
 Fenêtres frame, utilisent quant à eux, sera imprimé dans la fenêtre frame pour envoyer la valeur SelectionContext (trio de la hiérarchie/ItemID/SelectionContainer). . Fenêtres frame utilisent le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> à cet effet. Le DocObject pousser uniquement des valeurs pour le conteneur de sélection, en laissant les valeurs locales pour la hiérarchie et ItemID sans le modifier, comme cela est courant pour les documents enfants MDI.  
  
### <a name="events-and-currency"></a>Événements et devise  
 Deux types d’événements peuvent se produire et affectent la notion de l’environnement de devise :  
  
-   Événements qui sont propagées au niveau global et de modifient le contexte de sélection de fenêtre frame. Une fenêtre enfant MDI en cours d’ouverture, une fenêtre outil global en cours d’ouverture ou une fenêtre d’outil de type de projet en cours d’ouverture sont des exemples de ce type d’événement.  
  
-   Événements qui modifient les éléments suivis dans le contexte de sélection de fenêtre frame. Exemples incluent la modification de sélection dans DocObject ou la modification de sélection dans une fenêtre de type de projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)