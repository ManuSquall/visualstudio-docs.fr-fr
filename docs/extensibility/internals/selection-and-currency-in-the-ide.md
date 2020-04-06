---
title: Sélection et monnaie dans l’IDE Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705579"
---
# <a name="selection-and-currency-in-the-ide"></a>Sélection et devise dans l’IDE
L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) conserve des informations sur les objets actuellement sélectionnés par les utilisateurs en utilisant le *contexte*de sélection . Avec le contexte de sélection, VSPackages peut participer au suivi des devises de deux façons :

- En propageant des informations de devises sur les VSPackages à l’IDE.

- En surveillant les sélections actuellement actives des utilisateurs au sein de l’IDE.

## <a name="selection-context"></a>Contexte de sélection
 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’échelle mondiale suit la monnaie IDE dans son propre objet de contexte de sélection global. Le tableau suivant montre les éléments qui composent le contexte de sélection.

|Élément|Description|
|-------------|-----------------|
|Hiérarchie actuelle|Typiquement le projet actuel; une hiérarchie actuelle NULL indique que la solution dans son ensemble est actuelle.|
|Article actuelID|L’élément sélectionné dans la hiérarchie actuelle; lorsqu’il y a plusieurs sélections dans une fenêtre de projet, il peut y avoir plusieurs éléments actuels.|
|Actuelle`SelectionContainer`|Contient un ou plusieurs objets pour lesquels la fenêtre Propriétés doit afficher des propriétés.|

 En outre, l’environnement maintient deux listes mondiales :

- Une liste d’identifiants de commande d’interface utilisateur actif

- Une liste des types d’éléments actuellement actifs.

### <a name="window-types-and-selection"></a>Types de fenêtres et sélection
 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organise les fenêtres en deux types généraux :

- Fenêtres de type Hiérarchique

- Fenêtres de cadre, telles que les fenêtres d’outil et de document

  L’IDE suit la monnaie différemment pour chacun de ces types de fenêtres.

  La fenêtre de type projet la plus courante est l’explorateur de solution, que l’IDE contrôle. Une fenêtre de type projet suit la hiérarchie globale et l’itemID du contexte de sélection global, et la fenêtre s’appuie sur la sélection de l’utilisateur pour déterminer la hiérarchie actuelle. Pour les fenêtres de type projet, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>l’environnement fournit le service global, grâce auquel VSPackages peut surveiller les valeurs actuelles pour les éléments ouverts. La navigation immobilière dans l’environnement est guidée par ce service mondial.

  Les fenêtres de cadre, d’autre part, utilisent le DocObject dans la fenêtre de cadre pour pousser la valeur SelectionContext (le trio hiérarchie/ItemID/SelectionContainer). . Les fenêtres de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> cadre utilisent le service à cette fin. Le DocObject ne peut pousser que des valeurs pour le conteneur de sélection, laissant les valeurs locales pour la hiérarchie et ItemID inchangé, comme c’est le cas pour les documents pour enfants MDI.

### <a name="events-and-currency"></a>Événements et devises
 Deux types d’événements peuvent se produire qui affectent la notion de monnaie de l’environnement :

- Événements qui se propagent au niveau mondial et modifient le contexte de sélection du cadre de fenêtre. Parmi les exemples de ce type d’événement, mentionnons l’ouverture d’une fenêtre MDI Child, l’ouverture d’une fenêtre d’outils globale ou l’ouverture d’une fenêtre d’outil de type projet.

- Événements qui modifient les éléments tracés dans le contexte de sélection du cadre de fenêtre. Par exemple, changer de sélection au sein d’un DocObject ou modifier la sélection dans une fenêtre de type projet.

## <a name="see-also"></a>Voir aussi
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)
