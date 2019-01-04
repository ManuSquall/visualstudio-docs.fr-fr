---
title: Commande disponibilité | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac9a172ee2cb7a117a1d9b63c4f1fef9f631952
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915864"
---
# <a name="command-availability"></a>Disponibilité de la commande

Le contexte de Visual Studio détermine les commandes qui sont disponibles. Le contexte peut changer selon le projet actuel, l’éditeur actuel, les VSPackages sont chargés et autres aspects de l’environnement de développement intégré (IDE).

## <a name="command-contexts"></a>Contextes de commande

Les contextes de commande suivants sont les plus courantes :

- IDE : Commandes fournies par l’IDE sont toujours disponibles.

- VSPackage : VSPackages peut définir lorsque les commandes sont à être affiché ou masqué.

- Projet : Commandes de projet s’affichent uniquement pour le projet sélectionné actuellement.

- Éditeur : Éditeur qu’une seule peut être actif à la fois. Commandes à partir de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.

- Type de fichier : Un éditeur peut charger plusieurs types de fichier. Les commandes disponibles peuvent varier selon le type de fichier.

- Fenêtre active : La dernière fenêtre de document actif définit le contexte d’interface (UI) utilisateur pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de clé de liaison qui ressemble à du navigateur web interne peut également définir le contexte d’interface utilisateur. Pour les fenêtres de document à plusieurs onglets tels que l’éditeur HTML, chaque onglet possède un contexte de commande autre GUID. Après avoir enregistré une fenêtre outil, il est toujours disponible sur le **vue** menu.

- Contexte d’interface utilisateur : Contextes d’interface utilisateur sont identifiées par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> de classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actives en même temps.

## <a name="define-custom-context-guids"></a>Définir le GUID de contexte personnalisé

Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir un dans votre package Visual Studio et programmez ensuite qu’il soit actif ou inactif, en fonction des besoins pour contrôler la visibilité de vos commandes :

1.  Enregistrez le GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (méthode).

2.  Obtenir l’état d’un GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (méthode).

3.  Activer et désactiver les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (méthode).
   
> [!CAUTION]
> Assurez-vous que votre VSPackage n’affecte pas les GUID de contexte existant, car d’autres packages VS dépendent les.

## <a name="see-also"></a>Voir aussi

- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)