---
title: Prise en charge de l’Assistant pour les projets imbriqués | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa1dedebab95e1c1b74e1705f3a8b39a1ebe3616
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312925"
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
L’IDE exécute deux Assistants projet parent pour les projets imbriqués peut implémenter : le **nouveau projet** Assistant et le **ajouter un élément** Assistant.

 Si un utilisateur démarre la **nouveau projet** Assistant en sélectionnant **ajouter un projet** et en cliquant sur **nouveau projet** dans le menu fichier ou en sélectionnant **ajouter** et cliquant **nouveau projet** dans l’Explorateur de solutions, l’IDE exécute la **ajouter** commande et l’implémentation du projet parent de la **ajouter**renvoie un fichier de projet de modèle ou un fichier de l’Assistant (.vsz) qui dispose d’un ensemble de paramètres de contexte.

 De même, d’un projet parent mise en œuvre de **AddItem** Assistants retourne un fichier .vsz qui possède un ensemble différent de paramètres de contexte.

 Pour plus d’informations sur les Assistants, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [paramètres de contexte](../../extensibility/internals/context-parameters.md) et [inscription Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)