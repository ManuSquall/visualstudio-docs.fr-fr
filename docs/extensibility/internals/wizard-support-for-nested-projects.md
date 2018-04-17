---
title: Prise en charge de l’Assistant pour les projets imbriqués | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE exécute deux Assistants projet parent pour les projets imbriqués peut implémenter : le **nouveau projet** Assistant et **ajouter un élément** Assistant.  
  
 Si un utilisateur lance le **nouveau projet** Assistant en sélectionnant **ajouter un projet** et en cliquant sur **nouveau projet** dans le menu fichier, ou en sélectionnant **ajouter** et cliquant **nouveau projet** dans l’Explorateur de solutions, l’IDE exécute la **AddProject** commande et l’implémentation du projet parent de la **AddProject**renvoie un fichier de projet de modèle ou un fichier de l’Assistant (.vsz) qui possède un jeu de paramètres de contexte.  
  
 De même, d’un projet parent mise en œuvre de **AddItem** Assistants retourne un fichier .vsz qui possède un ensemble différent de paramètres de contexte.  
  
 Pour plus d’informations sur les Assistants, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [des paramètres de contexte](../../extensibility/internals/context-parameters.md) et [l’enregistrement de modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)