---
title: "Prise en charge de l’Assistant pour les projets imbriqués | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7191d31d4ec53fb26f4ab20114201836f1b58fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE exécute deux Assistants projet parent pour les projets imbriqués peut implémenter : le **nouveau projet** Assistant et **ajouter un élément** Assistant.  
  
 Si un utilisateur lance le **nouveau projet** Assistant en sélectionnant **ajouter un projet** et en cliquant sur **nouveau projet** dans le menu fichier, ou en sélectionnant **ajouter** et cliquant **nouveau projet** dans l’Explorateur de solutions, l’IDE exécute la **AddProject** commande et l’implémentation du projet parent de la **AddProject**renvoie un fichier de projet de modèle ou un fichier de l’Assistant (.vsz) qui possède un jeu de paramètres de contexte.  
  
 De même, d’un projet parent mise en œuvre de **AddItem** Assistants retourne un fichier .vsz qui possède un ensemble différent de paramètres de contexte.  
  
 Pour plus d’informations sur les Assistants, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [des paramètres de contexte](../../extensibility/internals/context-parameters.md) et [l’enregistrement de modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)